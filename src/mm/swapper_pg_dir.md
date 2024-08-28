# 内核页表

内核页表定义在`arch/x86/include/asm/pgtable_64.h`
```
extern p4d_t level4_kernel_pgt[512];
extern p4d_t level4_ident_pgt[512];
extern pud_t level3_kernel_pgt[512];
extern pud_t level3_ident_pgt[512];
extern pmd_t level2_kernel_pgt[512];
extern pmd_t level2_fixmap_pgt[512];
extern pmd_t level2_ident_pgt[512];
extern pte_t level1_fixmap_pgt[512 * FIXMAP_PMD_NUM];
extern pgd_t init_top_pgt[];

#define swapper_pg_dir init_top_pgt
```

```
(gdb) info registers
cr3            0x2a2e000           [ PDBR=10798 PCID=0 ]

(gdb) print init_top_pgt
$1 = 0xffffffff82a2e000 <init_top_pgt>
```

内核部分的逻辑地址与物理地址的偏移是`#define __START_KERNEL_map	_AC(0xffffffff80000000, UL)`。


```
(gdb) print/x init_top_pgt[511]
$18 = {pgd = 0x2a31067}
(gdb) print/x init_top_pgt[510]
$19 = {pgd = 0x3484067}
(gdb) print/x init_top_pgt[273]
$6 = {pgd = 0x3601067}
```

页表项的结构为，低12位（4KB，也就是1页）是控制位。
```
//arch/x86/include/asm/pgtable_types.h

#define _PAGE_BIT_PRESENT	0	/* is present */
#define _PAGE_BIT_RW		1	/* writeable */
#define _PAGE_BIT_USER		2	/* userspace addressable */
#define _PAGE_BIT_PWT		3	/* page write through */
#define _PAGE_BIT_PCD		4	/* page cache disabled */
#define _PAGE_BIT_ACCESSED	5	/* was accessed (raised by CPU) */
#define _PAGE_BIT_DIRTY		6	/* was written to (raised by CPU) */
#define _PAGE_BIT_PSE		7	/* 4 MB (or 2MB) page */
#define _PAGE_BIT_PAT		7	/* on 4KB pages */
#define _PAGE_BIT_GLOBAL	8	/* Global TLB entry PPro+ */
#define _PAGE_BIT_SOFTW1	9	/* available for programmer */
#define _PAGE_BIT_SOFTW2	10	/* " */
#define _PAGE_BIT_SOFTW3	11	/* " */
#define _PAGE_BIT_PAT_LARGE	12	/* On 2MB or 1GB pages */
#define _PAGE_BIT_SOFTW4	57	/* available for programmer */
#define _PAGE_BIT_SOFTW5	58	/* available for programmer */
#define _PAGE_BIT_PKEY_BIT0	59	/* Protection Keys, bit 1/4 */
#define _PAGE_BIT_PKEY_BIT1	60	/* Protection Keys, bit 2/4 */
#define _PAGE_BIT_PKEY_BIT2	61	/* Protection Keys, bit 3/4 */
#define _PAGE_BIT_PKEY_BIT3	62	/* Protection Keys, bit 4/4 */
#define _PAGE_BIT_NX		63	/* No execute: only valid after cpuid check */
```

`init_top_pgt[511]`的低12位为0b1100111，代码中定义为 `#define _PAGE_TABLE_NOENC	 (__PP|__RW|_USR|___A|   0|___D|   0|   0)`，

`init_top_pgt[511]`的虚拟地址范围为 0xffffff8000000000 -- 0xffffffffffffffff

`init_top_pgt[511]`指向的PUD是`level3_kernel_pgt`
```
(gdb) print/x &level3_kernel_pgt
$2 = 0xffffffff82a31000
(gdb) print/x level3_kernel_pgt
$3 = {{pud = 0x0} <repeats 510 times>, {pud = 0x2a32063}, {pud = 0x2a33067}}
```

`level3_kernel_pgt[510]`的虚拟地址范围为 0xffffffff80000000(__START_KERNEL_map) -- 0xffffffffbfffffff

`level3_kernel_pgt[510]`的低12位为0b1100011，代码中定义为 `#define _KERNPG_TABLE_NOENC	 (__PP|__RW|   0|___A|   0|___D|   0|   0)`，没有了`_USR`表示这是内核空间。


`level3_kernel_pgt[510]`指向的PMD是`level2_kernel_pgt`
```
(gdb) print/x &level2_kernel_pgt
$4 = 0xffffffff82a32000
(gdb) print/x level2_kernel_pgt
$5 = {{pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x0}, {pmd = 0x10001a1}, {
    pmd = 0x12001a1}, {pmd = 0x14001a1}, {pmd = 0x16001a1}, {pmd = 0x18001a1}, {pmd = 0x1a001a1}, {pmd = 0x1c001a1}, {
    pmd = 0x1e001a1}, {pmd = 0x20001a1}, {pmd = 0x80000000022001a1}, {pmd = 0x80000000024001a1}, {pmd = 0x80000000026001a1}, {
    pmd = 0x433b063}, {pmd = 0x8000000002a001e3}, {pmd = 0x8000000002c001e3}, {pmd = 0x8000000002e001e3}, {pmd = 0x100ec5063}, {
    pmd = 0x80000000032001e3}, {pmd = 0x3920063}, {pmd = 0x80000000036001e3}, {pmd = 0x0} <repeats 484 times>}
```

|level2_kernel_pgt索引|地址空间||
|---|---|---|
|7|0xffffffff81000000 -- 0xffffffff811fffff|Kernel code .text|
|8|0xffffffff81200000 -- 0xffffffff813fffff|Kernel code .text|
|9|0xffffffff81400000 -- 0xffffffff815fffff|Kernel code .text|
|10|0xffffffff81600000 -- 0xffffffff817fffff|Kernel code .text|
|11|0xffffffff81800000 -- 0xffffffff819fffff|Kernel code .text|
|12|0xffffffff81a00000 -- 0xffffffff81bfffff|Kernel code .text|
|13|0xffffffff81c00000 -- 0xffffffff81dfffff|Kernel code .text|
|14|0xffffffff81e00000 -- 0xffffffff81ffffff|Kernel code .text|
|15|0xffffffff82000000 -- 0xffffffff821fffff|Kernel code .text|
|16|0xffffffff82200000 -- 0xffffffff823fffff|Kernel rodata (NX=1)|
|17|0xffffffff82400000 -- 0xffffffff825fffff|Kernel rodata (NX=1)|
|18|0xffffffff82600000 -- 0xffffffff827fffff|Kernel rodata (NX=1)|
|19|0xffffffff82800000 -- 0xffffffff829fffff| 0x433b063 |
|20|0xffffffff82a00000 -- 0xffffffff82bfffff|Kernel data (NX=1)|
|21|0xffffffff82c00000 -- 0xffffffff82dfffff|Kernel data (NX=1)|
|22|0xffffffff82e00000 -- 0xffffffff82ffffff| (NX=1)|
|23|0xffffffff83000000 -- 0xffffffff831fffff| 0x100ec5063 |
|24|0xffffffff83200000 -- 0xffffffff833fffff| (NX=1)|
|25|0xffffffff83400000 -- 0xffffffff835fffff|Kernel bss 0x3920063|
|26|0xffffffff83600000 -- 0xffffffff837fffff| (NX=1)|

低12位0x1a1为0b110100001，其中关键的是第7位，也就是2MB的大页，不再有PT。
低12位0x1e3为0b111100011，其中关键的是第7位，也就是2MB的大页，不再有PT。


以上的物理地址与逻辑地址（线性地址）有固定的偏移量 `0xffffffff80000000(__START_KERNEL_map)`，另外还有一种 fix-mapped address，也就是`level3_kernel_pgt[511]`指向的level2_fixmap_pgt。

`level3_kernel_pgt[511]`的虚拟地址范围为 0xffffffffc0000000 -- 0xffffffffffffffff

```
(gdb) print/x &level2_fixmap_pgt
$25 = 0xffffffff82a33000
(gdb) print/x level2_fixmap_pgt
$26 = {{pmd = 0x0} <repeats 505 times>, {pmd = 0x3485067}, {pmd = 0x2a34067}, {pmd = 0x2a35067}, {pmd = 0x0}, {pmd = 0x0}, {
    pmd = 0x0}, {pmd = 0x0}}
```

```
(gdb) print/x (pte_t[512])*0xffffffff82a34000
$27 = {{pte = 0x0} <repeats 507 times>, {pte = 0x80000000fec0017b}, {pte = 0x80000000fee0017b}, {pte = 0x0}, {pte = 0x0}, {
    pte = 0x0}}
(gdb) print/x (pte_t[512])*0xffffffff82a35000
$28 = {{pte = 0x0} <repeats 512 times>}
(gdb) print/x (pte_t[512])*0xffffffff83485000
$30 = {{pte = 0x0} <repeats 512 times>}
```

`PAGE_OFFSET`为`#define __PAGE_OFFSET_BASE_L4	_AC(0xffff888000000000, UL)`

```
(gdb) print/x (pud_t[512])*0xffff888003601000
$11 = {{pud = 0x3602067}, {pud = 0x80000000400001e3}, {pud = 0x13ffff067}, {pud = 0x0}, {pud = 0x80000001000001e3}, {
    pud = 0x0} <repeats 507 times>}
(gdb) print/x (pmd_t[512])*0xffff888003602000
$12 = {{pmd = 0x3603067}, {pmd = 0x80000000002001e3}, {pmd = 0x80000000004001e3}, {pmd = 0x80000000006001e3}, {
    pmd = 0x80000000008001e3}, {pmd = 0x8000000000a001e3}, {pmd = 0x8000000000c001e3}, {pmd = 0x8000000000e001e3}, {
    pmd = 0x80000000010001a1}, {pmd = 0x80000000012001a1}, {pmd = 0x80000000014001a1}, {pmd = 0x80000000016001a1}, {
    pmd = 0x80000000018001a1}, {pmd = 0x8000000001a001a1}, {pmd = 0x8000000001c001a1}, {pmd = 0x8000000001e001a1}, {
    pmd = 0x80000000020001a1}, {pmd = 0x80000000022001a1}, {pmd = 0x80000000024001a1}, {pmd = 0x80000000026001a1}, {
    pmd = 0x41dc063}, {pmd = 0x8000000002a001e3}, {pmd = 0x8000000002c001e3}, {pmd = 0x8000000002e001e3}, {
    pmd = 0x80000000030001e3}, {pmd = 0x80000000032001e3}, {pmd = 0x3921063}, {pmd = 0x80000000036001e3}, {
    pmd = 0x80000000038001e3}, {pmd = 0x8000000003a001e3}, {pmd = 0x8000000003c001e3}, {pmd = 0x8000000003e001e3}, {
    pmd = 0x4141063}, {pmd = 0x80000000042001e3}, {pmd = 0x80000000044001e3}, {pmd = 0x80000000046001e3}, {
    pmd = 0x80000000048001e3}, {pmd = 0x8000000004a001e3}, {pmd = 0x8000000004c001e3}, {pmd = 0x8000000004e001e3}, {
    pmd = 0x80000000050001e3}, {pmd = 0x80000000052001e3}, {pmd = 0x80000000054001e3}, {pmd = 0x80000000056001e3}, {
    pmd = 0x80000000058001e3}, {pmd = 0x8000000005a001e3}, {pmd = 0x8000000005c001e3}, {pmd = 0x8000000005e001e3}, {
    pmd = 0x80000000060001e3}, {pmd = 0x80000000062001e3}, {pmd = 0x80000000064001e3}, {pmd = 0x80000000066001e3}, {
    pmd = 0x80000000068001e3}, {pmd = 0x8000000006a001e3}, {pmd = 0x8000000006c001e3}, {pmd = 0x8000000006e001e3}, {
    pmd = 0x80000000070001e3}, {pmd = 0x80000000072001e3}, {pmd = 0x80000000074001e3}, {pmd = 0x80000000076001e3}, {
    pmd = 0x80000000078001e3}, {pmd = 0x8000000007a001e3}, {pmd = 0x8000000007c001e3}, {pmd = 0x8000000007e001e3}, {
    pmd = 0x80000000080001e3}, {pmd = 0x80000000082001e3}, {pmd = 0x80000000084001e3}, {pmd = 0x80000000086001e3}, {
    pmd = 0x80000000088001e3}, {pmd = 0x8000000008a001e3}, {pmd = 0x8000000008c001e3}, {pmd = 0x8000000008e001e3}, {
    pmd = 0x80000000090001e3}, {pmd = 0x80000000092001e3}, {pmd = 0x80000000094001e3}, {pmd = 0x80000000096001e3}, {
    pmd = 0x80000000098001e3}, {pmd = 0x8000000009a001e3}, {pmd = 0x8000000009c001e3}, {pmd = 0x8000000009e001e3}, {
    pmd = 0x800000000a0001e3}, {pmd = 0x800000000a2001e3}, {pmd = 0x800000000a4001e3}, {pmd = 0x800000000a6001e3}, {
    pmd = 0x800000000a8001e3}, {pmd = 0x800000000aa001e3}, {pmd = 0x800000000ac001e3}, {pmd = 0x800000000ae001e3}, {
    pmd = 0x800000000b0001e3}, {pmd = 0x800000000b2001e3}, {pmd = 0x800000000b4001e3}, {pmd = 0x800000000b6001e3}, {
    pmd = 0x800000000b8001e3}, {pmd = 0x800000000ba001e3}, {pmd = 0x800000000bc001e3}, {pmd = 0x800000000be001e3}, {
    pmd = 0x800000000c0001e3}, {pmd = 0x800000000c2001e3}, {pmd = 0x800000000c4001e3}, {pmd = 0x800000000c6001e3}, {
    pmd = 0x800000000c8001e3}, {pmd = 0x800000000ca001e3}, {pmd = 0x800000000cc001e3}, {pmd = 0x800000000ce001e3}, {
    pmd = 0x800000000d0001e3}, {pmd = 0x800000000d2001e3}, {pmd = 0x800000000d4001e3}, {pmd = 0x800000000d6001e3}, {
    pmd = 0x800000000d8001e3}, {pmd = 0x800000000da001e3}, {pmd = 0x800000000dc001e3}, {pmd = 0x800000000de001e3}, {
    pmd = 0x800000000e0001e3}, {pmd = 0x800000000e2001e3}, {pmd = 0x800000000e4001e3}, {pmd = 0x800000000e6001e3}, {
    pmd = 0x800000000e8001e3}, {pmd = 0x800000000ea001e3}, {pmd = 0x800000000ec001e3}, {pmd = 0x800000000ee001e3}, {
    pmd = 0x800000000f0001e3}, {pmd = 0x800000000f2001e3}, {pmd = 0x800000000f4001e3}, {pmd = 0x800000000f6001e3}, {
    pmd = 0x800000000f8001e3}, {pmd = 0x800000000fa001e3}, {pmd = 0x800000000fc001e3}, {pmd = 0x800000000fe001e3}, {
    pmd = 0x80000000100001e3}, {pmd = 0x80000000102001e3}, {pmd = 0x80000000104001e3}, {pmd = 0x80000000106001e3}, {
    pmd = 0x80000000108001e3}, {pmd = 0x8000000010a001e3}, {pmd = 0x8000000010c001e3}, {pmd = 0x8000000010e001e3}, {
    pmd = 0x80000000110001e3}, {pmd = 0x80000000112001e3}, {pmd = 0x80000000114001e3}, {pmd = 0x80000000116001e3}, {
    pmd = 0x80000000118001e3}, {pmd = 0x8000000011a001e3}, {pmd = 0x8000000011c001e3}, {pmd = 0x8000000011e001e3}, {
    pmd = 0x80000000120001e3}, {pmd = 0x80000000122001e3}, {pmd = 0x80000000124001e3}, {pmd = 0x80000000126001e3}, {
    pmd = 0x80000000128001e3}, {pmd = 0x8000000012a001e3}, {pmd = 0x8000000012c001e3}, {pmd = 0x8000000012e001e3}, {
    pmd = 0x80000000130001e3}, {pmd = 0x80000000132001e3}, {pmd = 0x80000000134001e3}, {pmd = 0x80000000136001e3}, {
    pmd = 0x80000000138001e3}, {pmd = 0x8000000013a001e3}, {pmd = 0x8000000013c001e3}, {pmd = 0x8000000013e001e3}, {
    pmd = 0x80000000140001e3}, {pmd = 0x80000000142001e3}, {pmd = 0x80000000144001e3}, {pmd = 0x80000000146001e3}, {
    pmd = 0x80000000148001e3}, {pmd = 0x8000000014a001e3}, {pmd = 0x8000000014c001e3}, {pmd = 0x8000000014e001e3}, {
    pmd = 0x80000000150001e3}, {pmd = 0x80000000152001e3}, {pmd = 0x80000000154001e3}, {pmd = 0x80000000156001e3}, {
    pmd = 0x80000000158001e3}, {pmd = 0x8000000015a001e3}, {pmd = 0x8000000015c001e3}, {pmd = 0x8000000015e001e3}, {
    pmd = 0x80000000160001e3}, {pmd = 0x80000000162001e3}, {pmd = 0x80000000164001e3}, {pmd = 0x80000000166001e3}, {
    pmd = 0x80000000168001e3}, {pmd = 0x8000000016a001e3}, {pmd = 0x8000000016c001e3}, {pmd = 0x8000000016e001e3}, {
    pmd = 0x80000000170001e3}, {pmd = 0x80000000172001e3}, {pmd = 0x80000000174001e3}, {pmd = 0x80000000176001e3}, {
    pmd = 0x80000000178001e3}, {pmd = 0x8000000017a001e3}, {pmd = 0x8000000017c001e3}, {pmd = 0x8000000017e001e3}, {
    pmd = 0x80000000180001e3}, {pmd = 0x80000000182001e3}, {pmd = 0x80000000184001e3}, {pmd = 0x80000000186001e3}, {
    pmd = 0x80000000188001e3}, {pmd = 0x8000000018a001e3}, {pmd = 0x8000000018c001e3}, {pmd = 0x8000000018e001e3}...}
```