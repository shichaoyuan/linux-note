# 分页

Intel在Ice Lake处理器支持了[5级分页](https://en.wikipedia.org/wiki/Intel_5-level_paging)，但是绝大部分还是只支持4级分页。

Linux内核为了兼容各种硬件，在数据结构上是设计了5个级别：
1. PGD(Page Global Direcotry)，页全局目录
2. P4D(Page 4th Directory)，页四级目录
3. PUD(Page Upper Directory)，页上级目录
4. PMD(Page Middle Directory)，页中级目录
5. PT(Page Table)，页表

## mem_section

```shell
start_kenel
  -> setup_arch #arch/x86/kernel/setup.c
    -> x86_init.paging.pagetable_init 
      -> native_pagetable_init #arch/x86/include/asm/pgtable_types.h
        -> paging_init #arch/x86/mm/init_64.c
          -> sparse_init #mm/sparse.c
```

```c
// mm/sparse.c
/*
 * Permanent SPARSEMEM data:
 *
 * 1) mem_section	- memory sections, mem_map's for valid memory
 */
struct mem_section **mem_section;
EXPORT_SYMBOL(mem_section);
```

```c
// include/linux/mmzone.h
/*
在x86_64下，SECTION_SIZE_BITS为27，SUBSECTIONS_SHIFT为21，那么SUBSECTIONS_PER_SECTION为64(1<<6)。
每个SECTION为128MB(1<<27)，每个SUBSECTION为2MB(1<<21)。
*/
#define SUBSECTIONS_PER_SECTION (1UL << (SECTION_SIZE_BITS - SUBSECTION_SHIFT))

struct mem_section_usage {
	struct rcu_head rcu;
#ifdef CONFIG_SPARSEMEM_VMEMMAP
	DECLARE_BITMAP(subsection_map, SUBSECTIONS_PER_SECTION);
#endif
	/* See declaration of similar field in struct zone */
	unsigned long pageblock_flags[0];
};

struct mem_section {
	/*
	 * This is, logically, a pointer to an array of struct
	 * pages.  However, it is stored with some other magic.
	 * (see sparse.c::sparse_init_one_section())
	 *
	 * Additionally during early boot we encode node id of
	 * the location of the section here to guide allocation.
	 * (see sparse.c::memory_present())
	 *
	 * Making it a UL at least makes someone do a cast
	 * before using it wrong.
	 */
	unsigned long section_mem_map;

	struct mem_section_usage *usage;
	/*
	 * WARNING: mem_section must be a power-of-2 in size for the
	 * calculation and use of SECTION_ROOT_MASK to make sense.
	 */
};

```

`mem_section`是个二维的指针，第一维是在 mem_present 方法中分配的。
```c
//mm/sparse.c
/* Record a memory area against a node. */
static void __init memory_present(int nid, unsigned long start, unsigned long end)
{
	unsigned long pfn;

#ifdef CONFIG_SPARSEMEM_EXTREME
	if (unlikely(!mem_section)) {
		unsigned long size, align;

        // NR_SECTION_ROOTS 表示存储这些 struct mem_section 需要的页数
        // 2048 * 8 = 16K
		size = sizeof(struct mem_section *) * NR_SECTION_ROOTS;
		align = 1 << (INTERNODE_CACHE_SHIFT);
        // [    0.004018] memblock_alloc_try_nid: 16384 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init+0x3f8/0x490
        // [    0.004019] memblock_reserve: [0x000000013fff6000-0x000000013fff9fff] memblock_alloc_internal+0x4e/0xc0
		mem_section = memblock_alloc(size, align);
		if (!mem_section)
			panic("%s: Failed to allocate %lu bytes align=0x%lx\n",
			      __func__, size, align);
	}
#endif

	start &= PAGE_SECTION_MASK;
	mminit_validate_memmodel_limits(&start, &end);
	for (pfn = start; pfn < end; pfn += PAGES_PER_SECTION) {
		unsigned long section = pfn_to_section_nr(pfn);
		struct mem_section *ms;

		sparse_index_init(section, nid);
		set_section_nid(section, nid);

		ms = __nr_to_section(section);
		if (!ms->section_mem_map) {
			ms->section_mem_map = sparse_encode_early_nid(nid) |
							SECTION_IS_ONLINE;
			__section_mark_present(ms, section);
		}
	}
}
```

```c
// include/linux/mmzone.h

// 地址线46位，每个setion为128MB，也就是27为，那么也就是最多524288(1<<19)个section
#define NR_MEM_SECTIONS		(1UL << SECTIONS_SHIFT)

// SECTIONS_PER_ROOT 表示一个页可以存储的 struct mem_section 数量，
// 4K / 16 = 256
#ifdef CONFIG_SPARSEMEM_EXTREME
#define SECTIONS_PER_ROOT       (PAGE_SIZE / sizeof (struct mem_section))
#else

// NR_SECTION_ROOTS 表示存储下这些 struct mem_section 需要的页数量
// 2048
#define NR_SECTION_ROOTS	DIV_ROUND_UP(NR_MEM_SECTIONS, SECTIONS_PER_ROOT)
```

```c
// include/linux/page-flags-layout.h
#ifdef CONFIG_SPARSEMEM
#include <asm/sparsemem.h>
// 4级页表的情况MAX_PHYSMEM_BITS为46，SECTION_SIZE_BITS为27，那么SECTION_SHIFT为19
#define SECTIONS_SHIFT	(MAX_PHYSMEM_BITS - SECTION_SIZE_BITS)
#else
```