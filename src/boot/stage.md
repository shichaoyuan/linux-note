# 阶段

BIOS将硬盘的第一个扇区，也就是MBR（Master Boot Record），加载到内存地址`0x7C00`，然后跳转到该地址执行指令启动引导程序，通常是GRUB。

GRUB会进一步引导Linux内核，引导的协议见文档[The Linux/x86 Boot Protocol](https://docs.kernel.org/arch/x86/boot.html)。

```plain
              ~                        ~
              |  Protected-mode kernel |
      100000  +------------------------+
              |  I/O memory hole       |
      0A0000  +------------------------+
              |  Reserved for BIOS     |      Leave as much as possible unused
              ~                        ~
              |  Command line          |      (Can also be below the X+10000 mark)
      X+10000 +------------------------+
              |  Stack/heap            |      For use by the kernel real-mode code.
      X+08000 +------------------------+
              |  Kernel setup          |      The kernel real-mode code.
              |  Kernel boot sector    |      The kernel legacy boot sector.
      X       +------------------------+
              |  Boot loader           |      <- Boot sector entry point 0000:7C00
      001000  +------------------------+
              |  Reserved for MBR/BIOS |
      000800  +------------------------+
              |  Typically used by MBR |
      000600  +------------------------+
              |  BIOS use only         |
      000000  +------------------------+

... where the address X is as low as the design of the boot loader permits.
```

### 实模式阶段

从GRUB到Kernel boot sector，内存入口地址没有固定值，通常是`0x10000`，此阶段CPU还处于『实模式』。

内核起始执行的代码位于`arch/x86/boot/header.S`的`_start`：
```x86asm
	.globl	hdr
hdr:
		.byte setup_sects - 1
root_flags:	.word ROOT_RDONLY
syssize:	.long ZO__edata / 16
ram_size:	.word 0			/* Obsolete */
vid_mode:	.word SVGA_MODE
root_dev:	.word 0			/* Default to major/minor 0/0 */
boot_flag:	.word 0xAA55

	# offset 512, entry point

	.globl	_start
_start:
		# Explicitly enter this as bytes, or the assembler
		# tries to generate a 3-byte jump here, which causes
		# everything else to push off to the wrong offset.
		.byte	0xeb		# short (2-byte) jump
		.byte	start_of_setup-1f
```

最后`call main`跳转到了C代码`arch/x86/boot/main.c`：
```c
void main(void)
{
	init_default_io_ops();

	/* First, copy the boot header into the "zeropage" */
	copy_boot_params();

	/* Initialize the early-boot console */
	console_init();
	if (cmdline_find_option_bool("debug"))
		puts("early console in setup code\n");

	/* End of heap check */
	init_heap();

	/* Make sure we have all the proper CPU support */
	if (validate_cpu()) {
		puts("Unable to boot - please use a kernel appropriate "
		     "for your CPU.\n");
		die();
	}

	/* Tell the BIOS what CPU mode we intend to run in. */
	set_bios_mode();

	/* Detect memory layout */
	detect_memory();

	/* Set keyboard repeat rate (why?) and query the lock flags */
	keyboard_init();

	/* Query Intel SpeedStep (IST) information */
	query_ist();

	/* Query APM information */
#if defined(CONFIG_APM) || defined(CONFIG_APM_MODULE)
	query_apm_bios();
#endif

	/* Query EDD information */
#if defined(CONFIG_EDD) || defined(CONFIG_EDD_MODULE)
	query_edd();
#endif

	/* Set the video mode */
	set_video();

	/* Do the last things and invoke protected mode */
	go_to_protected_mode();
}
```

`go_to_protected_mode()`转为保护模式。

在`arch/x86/boot/pm.c`设置GDT：
```c
static void setup_gdt(void)
{
	/* There are machines which are known to not boot with the GDT
	   being 8-byte unaligned.  Intel recommends 16 byte alignment. */
	static const u64 boot_gdt[] __attribute__((aligned(16))) = {
		/* CS: code, read/execute, 4 GB, base 0 */
		[GDT_ENTRY_BOOT_CS] = GDT_ENTRY(0xc09b, 0, 0xfffff),
		/* DS: data, read/write, 4 GB, base 0 */
		[GDT_ENTRY_BOOT_DS] = GDT_ENTRY(0xc093, 0, 0xfffff),
		/* TSS: 32-bit tss, 104 bytes, base 4096 */
		/* We only have a TSS here to keep Intel VT happy;
		   we don't actually use it for anything. */
		[GDT_ENTRY_BOOT_TSS] = GDT_ENTRY(0x0089, 4096, 103),
	};
	/* Xen HVM incorrectly stores a pointer to the gdt_ptr, instead
	   of the gdt_ptr contents.  Thus, make it static so it will
	   stay in memory, at least long enough that we switch to the
	   proper kernel GDT. */
	static struct gdt_ptr gdt;

	gdt.len = sizeof(boot_gdt)-1;
	gdt.ptr = (u32)&boot_gdt + (ds() << 4);

	asm volatile("lgdtl %0" : : "m" (gdt));
}
```

最后在汇编代码`arch/x86/boot/pmjump.S`中执行：
```x86asm
/*
 * void protected_mode_jump(u32 entrypoint, u32 bootparams);
 */
SYM_FUNC_START_NOALIGN(protected_mode_jump)
	movl	%edx, %esi		# Pointer to boot_params table

	xorl	%ebx, %ebx
	movw	%cs, %bx
	shll	$4, %ebx
	addl	%ebx, 2f
	jmp	1f			# Short jump to serialize on 386/486
1:

	movw	$__BOOT_DS, %cx
	movw	$__BOOT_TSS, %di

	movl	%cr0, %edx
	orb	$X86_CR0_PE, %dl	# Protected mode
	movl	%edx, %cr0

	# Transition to 32-bit mode
	.byte	0x66, 0xea		# ljmpl opcode
2:	.long	.Lin_pm32		# offset
	.word	__BOOT_CS		# segment
SYM_FUNC_END(protected_mode_jump)
```

最后跳转的地址是定义在`arch/x86/boot/header.S`中的`boot_params.hdr.code32_start`，是个固定值`0x100000`。

### 保护模式阶段

保护模式起始执行的代码位于`arch/x86/boot/compressed/head_64.S`的`startup_32`：


```x86asm
SYM_DATA_START_LOCAL(gdt64)
	.word	gdt_end - gdt - 1
	.quad   gdt - gdt64
SYM_DATA_END(gdt64)
	.balign	8
SYM_DATA_START_LOCAL(gdt)
	.word	gdt_end - gdt - 1
	.long	0
	.word	0
	.quad	0x00cf9a000000ffff	/* __KERNEL32_CS */
	.quad	0x00af9a000000ffff	/* __KERNEL_CS */
	.quad	0x00cf92000000ffff	/* __KERNEL_DS */
	.quad	0x0080890000000000	/* TS descriptor */
	.quad   0x0000000000000000	/* TS continued */
SYM_DATA_END_LABEL(gdt, SYM_L_LOCAL, gdt_end)
```
准备长模式下的GDT。


```x86asm
	/* Initialize Page tables to 0 */
	leal	rva(pgtable)(%ebx), %edi
	xorl	%eax, %eax
	movl	$(BOOT_INIT_PGT_SIZE/4), %ecx
	rep	stosl
table + 0)(%ebx), %edi
	leal	0x1007 (%edi), %eax
	movl	%eax, 0(%edi)
	addl	%edx, 4(%edi)

	/* Build Level 4 */
	leal	rva(pg
	/* Build Level 3 */
	leal	rva(pgtable + 0x1000)(%ebx), %edi
	leal	0x1007(%edi), %eax
	movl	$4, %ecx
1:	movl	%eax, 0x00(%edi)
	addl	%edx, 0x04(%edi)
	addl	$0x00001000, %eax
	addl	$8, %edi
	decl	%ecx
	jnz	1b

	/* Build Level 2 */
	leal	rva(pgtable + 0x2000)(%ebx), %edi
	movl	$0x00000183, %eax
	movl	$2048, %ecx
1:	movl	%eax, 0(%edi)
	addl	%edx, 4(%edi)
	addl	$0x00200000, %eax
	addl	$8, %edi
	decl	%ecx
	jnz	1b

	/* Enable the boot page tables */
	leal	rva(pgtable)(%ebx), %eax
	movl	%eax, %cr3
```
准备页表。

```x86asm
	/* Enable Long mode in EFER (Extended Feature Enable Register) */
	movl	$MSR_EFER, %ecx
	rdmsr
	btsl	$_EFER_LME, %eax
	wrmsr
...
	pushl	$__KERNEL_CS
	pushl	%eax

	/* Enter paged protected Mode, activating Long Mode */
	movl	$CR0_STATE, %eax
	movl	%eax, %cr0

	/* Jump from 32bit compatibility mode into 64bit mode. */
	lret
SYM_FUNC_END(startup_32)
```
最终进入了长模式。

### 长模式阶段

长模式起始执行的代码位于`arch/x86/boot/compressed/head_64.S`的`startup_64`：

```c
/*
 * The compressed kernel image (ZO), has been moved so that its position
 * is against the end of the buffer used to hold the uncompressed kernel
 * image (VO) and the execution environment (.bss, .brk), which makes sure
 * there is room to do the in-place decompression. (See header.S for the
 * calculations.)
 *
 *                             |-----compressed kernel image------|
 *                             V                                  V
 * 0                       extract_offset                      +INIT_SIZE
 * |-----------|---------------|-------------------------|--------|
 *             |               |                         |        |
 *           VO__text      startup_32 of ZO          VO__end    ZO__end
 *             ^                                         ^
 *             |-------uncompressed kernel image---------|
 *
 */
asmlinkage __visible void *extract_kernel(void *rmode, unsigned char *output)
{
	unsigned long virt_addr = LOAD_PHYSICAL_ADDR;
	memptr heap = (memptr)boot_heap;
	unsigned long needed_size;
	size_t entry_offset;

	/* Retain x86 boot parameters pointer passed from startup_32/64. */
	boot_params = rmode;

	/* Clear flags intended for solely in-kernel use. */
	boot_params->hdr.loadflags &= ~KASLR_FLAG;

	parse_mem_encrypt(&boot_params->hdr);

	sanitize_boot_params(boot_params);

	if (boot_params->screen_info.orig_video_mode == 7) {
		vidmem = (char *) 0xb0000;
		vidport = 0x3b4;
	} else {
		vidmem = (char *) 0xb8000;
		vidport = 0x3d4;
	}

	lines = boot_params->screen_info.orig_video_lines;
	cols = boot_params->screen_info.orig_video_cols;

	init_default_io_ops();

	/*
	 * Detect TDX guest environment.
	 *
	 * It has to be done before console_init() in order to use
	 * paravirtualized port I/O operations if needed.
	 */
	early_tdx_detect();

	console_init();

	/*
	 * Save RSDP address for later use. Have this after console_init()
	 * so that early debugging output from the RSDP parsing code can be
	 * collected.
	 */
	boot_params->acpi_rsdp_addr = get_rsdp_addr();

	debug_putstr("early console in extract_kernel\n");

	free_mem_ptr     = heap;	/* Heap */
	free_mem_end_ptr = heap + BOOT_HEAP_SIZE;

	/*
	 * The memory hole needed for the kernel is the larger of either
	 * the entire decompressed kernel plus relocation table, or the
	 * entire decompressed kernel plus .bss and .brk sections.
	 *
	 * On X86_64, the memory is mapped with PMD pages. Round the
	 * size up so that the full extent of PMD pages mapped is
	 * included in the check against the valid memory table
	 * entries. This ensures the full mapped area is usable RAM
	 * and doesn't include any reserved areas.
	 */
	needed_size = max_t(unsigned long, output_len, kernel_total_size);
#ifdef CONFIG_X86_64
	needed_size = ALIGN(needed_size, MIN_KERNEL_ALIGN);
#endif

	/* Report initial kernel position details. */
	debug_putaddr(input_data);
	debug_putaddr(input_len);
	debug_putaddr(output);
	debug_putaddr(output_len);
	debug_putaddr(kernel_total_size);
	debug_putaddr(needed_size);

#ifdef CONFIG_X86_64
	/* Report address of 32-bit trampoline */
	debug_putaddr(trampoline_32bit);
#endif

	choose_random_location((unsigned long)input_data, input_len,
				(unsigned long *)&output,
				needed_size,
				&virt_addr);

	/* Validate memory location choices. */
	if ((unsigned long)output & (MIN_KERNEL_ALIGN - 1))
		error("Destination physical address inappropriately aligned");
	if (virt_addr & (MIN_KERNEL_ALIGN - 1))
		error("Destination virtual address inappropriately aligned");
#ifdef CONFIG_X86_64
	if (heap > 0x3fffffffffffUL)
		error("Destination address too large");
	if (virt_addr + needed_size > KERNEL_IMAGE_SIZE)
		error("Destination virtual address is beyond the kernel mapping area");
#else
	if (heap > ((-__PAGE_OFFSET-(128<<20)-1) & 0x7fffffff))
		error("Destination address too large");
#endif
#ifndef CONFIG_RELOCATABLE
	if (virt_addr != LOAD_PHYSICAL_ADDR)
		error("Destination virtual address changed when not relocatable");
#endif

	debug_putstr("\nDecompressing Linux... ");

	if (init_unaccepted_memory()) {
		debug_putstr("Accepting memory... ");
		accept_memory(__pa(output), __pa(output) + needed_size);
	}

	entry_offset = decompress_kernel(output, virt_addr, error);

	debug_putstr("done.\nBooting the kernel (entry_offset: 0x");
	debug_puthex(entry_offset);
	debug_putstr(").\n");

	/* Disable exception handling before booting the kernel */
	cleanup_exception_handling();

	return output + entry_offset;
}
```
首先要解压缩，然后移动到ELF中定义的位置，默认是`0x1000000`(`arch/x86/Kconfig`)，如果开启KASLR那么会随机偏移。


