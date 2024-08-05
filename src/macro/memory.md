# 内存

## __pa_symbol
计算虚拟地址计算物理地址

使用案例，根据`_text`计算内核二进制的起始物理地址：
```c
memblock_reserve(__pa_symbol(_text),
			 (unsigned long)__end_of_kernel_reserve - (unsigned long)_text);
```

宏展开：
```c
// arch/x86/include/asm/page.h
/* __pa_symbol should be used for C visible symbols.
   This seems to be the official gcc blessed way to do such arithmetic. */
/*
 * We need __phys_reloc_hide() here because gcc may assume that there is no
 * overflow during __pa() calculation and can optimize it unexpectedly.
 * Newer versions of gcc provide -fno-strict-overflow switch to handle this
 * case properly. Once all supported versions of gcc understand it, we can
 * remove this Voodoo magic stuff. (i.e. once gcc3.x is deprecated)
 */
#define __pa_symbol(x) \
	__phys_addr_symbol(__phys_reloc_hide((unsigned long)(x)))

#define __phys_addr_symbol(x) \
	((unsigned long)(x) - __START_KERNEL_map + phys_base)

// arch/x86/include/asm/page_64_types.h
#define __START_KERNEL_map	_AC(0xffffffff80000000, UL)

```

## pgd_index 

```c
#ifndef pgd_index
/* Must be a compile-time constant, so implement it as a macro */
#define pgd_index(a)  (((a) >> PGDIR_SHIFT) & (PTRS_PER_PGD - 1))
#endif
```

传入的a是虚拟地址。

`PGDIR_SHIFT`默认值为39，如果支持5级那么该值将在`configure_5level_paging`方法中更新为48。

`PTRS_PER_PGD`值为512，也就是9为的mask，加上shift，也就是5级分页57位，4级分页48位。

那么该宏计算出的是虚拟地址a在pgd中的偏移。

## pud_index

```c
#define pud_index(x)	(((x) >> PUD_SHIFT) & (PTRS_PER_PUD-1))
```

```c
/*
 * 3rd level page
 */
#define PUD_SHIFT	30
#define PTRS_PER_PUD	512
```