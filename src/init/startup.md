# 内核起始

完成引导之后，内核起始的代码位于`arch/x86/kernel/head_64.S`。

通过链接脚本`arch/x86/kernel/vmlinux.lds.S`可见虚拟地址`__START_KERNEL`：
```x86asm
SECTIONS
{
#ifdef CONFIG_X86_32
	. = LOAD_OFFSET + LOAD_PHYSICAL_ADDR;
	phys_startup_32 = ABSOLUTE(startup_32 - LOAD_OFFSET);
#else
	. = __START_KERNEL;
	phys_startup_64 = ABSOLUTE(startup_64 - LOAD_OFFSET);
#endif

	/* Text and read-only data */
	.text :  AT(ADDR(.text) - LOAD_OFFSET) {
		_text = .;
		_stext = .;
		/* bootstrapping code */
		HEAD_TEXT
		TEXT_TEXT
		SCHED_TEXT
		LOCK_TEXT
		KPROBES_TEXT
		SOFTIRQENTRY_TEXT
```

虚拟地址的值定义在`arch/x86/include/asm/page_types.h`：
```c
#define __PHYSICAL_START	ALIGN(CONFIG_PHYSICAL_START, \
				      CONFIG_PHYSICAL_ALIGN)

#define __START_KERNEL		(__START_KERNEL_map + __PHYSICAL_START)
```

* 虚拟地址为`0xffffffff81000000`
* 物理地址为`0x1000000`

这两个地址是对应的，但是由于基于安全诉求的kaslr，运行时的地址相对与编译时的地址会有随机偏移。这个随机偏移的机制是在『引导』阶段解压缩的时候进行的。

所以进入`arch/x86/kernel/head64.c`的`__startup_64`方法后，首先就会进行地址的修正。

```c
static void __head *fixup_pointer(void *ptr, unsigned long physaddr)
{
	return ptr - (void *)_text + (void *)physaddr;
}
```
通过该方法计算出“运行时”的物理地址，首先修正的就是页表。

```x86asm
SYM_DATA_START_PTI_ALIGNED(early_top_pgt)
	.fill	512,8,0
	.fill	PTI_USER_PGD_FILL,8,0
SYM_DATA_END(early_top_pgt)

L3_START_KERNEL = pud_index(__START_KERNEL_map)

SYM_DATA_START_PAGE_ALIGNED(level3_kernel_pgt)
	.fill	L3_START_KERNEL,8,0
	/* (2^48-(2*1024*1024*1024)-((2^39)*511))/(2^30) = 510 */
	.quad	level2_kernel_pgt - __START_KERNEL_map + _KERNPG_TABLE_NOENC
	.quad	level2_fixmap_pgt - __START_KERNEL_map + _PAGE_TABLE_NOENC
SYM_DATA_END(level3_kernel_pgt)

SYM_DATA_START_PAGE_ALIGNED(level2_kernel_pgt)
	/*
	 * Kernel high mapping.
	 *
	 * The kernel code+data+bss must be located below KERNEL_IMAGE_SIZE in
	 * virtual address space, which is 1 GiB if RANDOMIZE_BASE is enabled,
	 * 512 MiB otherwise.
	 *
	 * (NOTE: after that starts the module area, see MODULES_VADDR.)
	 *
	 * This table is eventually used by the kernel during normal runtime.
	 * Care must be taken to clear out undesired bits later, like _PAGE_RW
	 * or _PAGE_GLOBAL in some cases.
	 */
	PMDS(0, __PAGE_KERNEL_LARGE_EXEC, KERNEL_IMAGE_SIZE/PMD_SIZE)
SYM_DATA_END(level2_kernel_pgt)

/* Automate the creation of 1 to 1 mapping pmd entries */
#define PMDS(START, PERM, COUNT)			\
	i = 0 ;						\
	.rept (COUNT) ;					\
	.quad	(START) + (i << PMD_SHIFT) + (PERM) ;	\
	i = i + 1 ;					\
	.endr

	__INITDATA
	.balign 4



```

创建512个PGD条目，在4级分页的情况下，设置`__START_KERNEL_map`对应的PGD条目指向的地址为`level3_kernel_pgt`。

`level3_kernel_pgt`是PUD（直接跳过了P4D）


```
	/* set init_top_pgt kernel high mapping*/
	init_top_pgt[511] = early_top_pgt[511];

```