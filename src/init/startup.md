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