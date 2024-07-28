# 物理内存

## 整体流程

物理内存管理最上层的数据结构是node

以 vng 启动的 `--numa 2G,cpus=0-1 --numa 2G,cpus=2-3` 虚拟机为例：
```shell
root@virtme-ng:~# lscpu 
Architecture:             x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          46 bits physical, 48 bits virtual
  Byte Order:             Little Endian
CPU(s):                   4
  On-line CPU(s) list:    0-3
Vendor ID:                GenuineIntel
  BIOS Vendor ID:         QEMU
  Model name:             13th Gen Intel(R) Core(TM) i9-13900H
    BIOS Model name:      pc-i440fx-noble  CPU @ 2.0GHz
    BIOS CPU family:      1
    CPU family:           6
    Model:                186
    Thread(s) per core:   1
    Core(s) per socket:   4
    Socket(s):            1
NUMA:                     
  NUMA node(s):           2
  NUMA node0 CPU(s):      0,1
  NUMA node1 CPU(s):      2,3
```

在 `/sys/devices/system/node/node{}/` 目录下能查询到更详细的信息：
```shell
root@virtme-ng:~# ls -la /sys/devices/system/node/node1/
total 0
drwxr-xr-x 4 root root    0 Jul  6 14:37 .
drwxr-xr-x 5 root root    0 Jul  6 14:37 ..
--w------- 1 root root 4096 Jul  6 14:38 compact
lrwxrwxrwx 1 root root    0 Jul  6 14:38 cpu2 -> ../../cpu/cpu2
lrwxrwxrwx 1 root root    0 Jul  6 14:38 cpu3 -> ../../cpu/cpu3
-r--r--r-- 1 root root 4096 Jul  6 14:38 cpulist
-r--r--r-- 1 root root 4096 Jul  6 14:32 cpumap
-r--r--r-- 1 root root 4096 Jul  6 14:38 distance
drwxr-xr-x 3 root root    0 Jul  6 14:38 hugepages
-r--r--r-- 1 root root 4096 Jul  6 14:38 meminfo
-r--r--r-- 1 root root 4096 Jul  6 14:38 numastat
drwxr-xr-x 2 root root    0 Jul  6 14:38 power
lrwxrwxrwx 1 root root    0 Jul  6 11:38 subsystem -> ../../../../bus/node
-rw-r--r-- 1 root root 4096 Jul  6 11:38 uevent
-r--r--r-- 1 root root 4096 Jul  6 14:38 vmstat
```



NUMA初始化调用链
```palin
-> start_kernel // init/main.c
  |-> setup_arch //arch/x86/kernel/setup.c
    |-> e820__memory_setup // arch/x86/kernel/e820.c
    |-> trim_bios_range //arch/x86/kernel/setup.c
    |-> e820__end_of_ram_pfn // arch/x86/kernel/e820.c
	|-> e820__memblock_setup // arch/x86/kernel/e820.c
    |-> initmem_init // arch/x86/mm/numa_64.c
      |-> x86_numa_init // arch/x86/mm/numa.c
        |-> numa_init(x86_acpi_numa_init)
          |-> x86_acpi_numa_init // arch/x86/mm/srat.c
            |-> acpi_numa_init
              |-> acpi_parse_memory_affinity
                |-> acpi_numa_memory_affinity_init
                  |-> numa_add_memblk // arch/x86/mm/numa.c
          |-> numa_cleanup_meminfo
          |-> numa_register_memblks
            |-> alloc_node_data
    |-> x86_init.paging.pagetable_init()
  |-> mm_core_init // mm/mm_init.c
    |-> mem_init // arch/x86/mm/init_64.c  after_bootmem=1
```


在e820_memory_setup方法中，内核从BIOS中获取了物理内存的地址空间
```log
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bffdffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bffe0000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feffc000-0x00000000feffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
```

物理内存地址是不连续的，并且并不是所有地址段都是可用的。
可以算一下示例中的内存空间639KB+(1KB+64KB)+3144576KB+(128KB+16KB+16KB)+1048576KB，加起来总共4194016KB，而内核实际管理的是物理内存只有usable段，具体来说也就是`E820_TYPE_RAM`、`E820_TYPE_RESERVED_KERN`和`E820_TYPE_SOFT_RESERVED`三种类型。

物理地址的信息还可以从`/sys/firmware/memmap/`目录下查看
```
[0x0-0x9fbff] System RAM
[0x9fc00-0x9ffff] Reserved
[0xf0000-0xfffff] Reserved
[0x100000-0xbffdffff] System RAM
[0xbffe0000-0xbfffffff] Reserved
[0xfeffc000-0xfeffffff] Reserved
[0xfffc0000-0xffffffff] Reserved
[0x100000000-0x13fffffff] System RAM
```

以上是内核获取的RAM地址信息，对于某些I/O设备内核也会将它们映射到内存地址空间，也就是Memory Mapped IO，可以从 `/proc/iomem` 查看
```
00000000-00000fff : Reserved
00001000-0009fbff : System RAM
0009fc00-0009ffff : Reserved
000a0000-000bffff : PCI Bus 0000:00
000c0000-000c0dff : Video ROM
000f0000-000fffff : Reserved
  000f0000-000fffff : System ROM
00100000-bffdffff : System RAM
  01000000-021fffff : Kernel code
  02200000-02860fff : Kernel rodata
  02a00000-02cacf3f : Kernel data
  03482000-035fffff : Kernel bss
bffe0000-bfffffff : Reserved
c0000000-febfffff : PCI Bus 0000:00
  feb00000-feb7ffff : 0000:00:04.0
  feb80000-feb80fff : 0000:00:02.0
  feb81000-feb8100f : 0000:00:03.0
  feb82000-feb82fff : 0000:00:04.0
fec00000-fec003ff : IOAPIC 0
fed00000-fed003ff : HPET 0
  fed00000-fed003ff : PNP0103:00
feffc000-feffffff : Reserved
fffc0000-ffffffff : Reserved
100000000-13fffffff : System RAM
380000000000-38007fffffff : PCI Bus 0000:00
  380000000000-380000003fff : 0000:00:02.0
    380000000000-380000003fff : virtio-pci-modern
  380000004000-380000007fff : 0000:00:04.0
    380000004000-380000007fff : virtio-pci-modern
```

从`/proc/iomen`看到的内存空间与`/sys/firmware/memmap/`下看到的略有区别，这是由于内核在trim_bios_range方法中移除了BIOS管理的空间
```log
[    0.000114] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000115] e820: remove [mem 0x000a0000-0x000fffff] usable
```


接下来的日志引出了内存页，pfn全称page frame number，默认每4KB一个页帧。按照示例中的0x13fffffff计算，最大的页帧号为0x140000，从max_arch_pfn可见地址线为46位。除了`max_pfn`内核还计算了32位空间内最大的`max_low_pfn`，计算的逻辑在e820__end_of_ram_pfn方法中。
```log
[    0.000118] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000135] MTRR map: 4 entries (3 fixed + 1 variable; max 19), built from 8 variable MTRRs
[    0.000136] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000158] last_pfn = 0xbffe0 max_arch_pfn = 0x400000000
```

RAM地址空间是通过e820获取的，numa的信息是通过SRAT获取的，也就是System Resource Affinity Table
```log
[    0.003957] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.003958] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.003958] SRAT: PXM 1 -> APIC 0x02 -> Node 1
[    0.003959] SRAT: PXM 1 -> APIC 0x03 -> Node 1
[    0.003959] ACPI: SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.003960] ACPI: SRAT: Node 0 PXM 0 [mem 0x00100000-0x7fffffff]
[    0.003961] ACPI: SRAT: Node 1 PXM 1 [mem 0x80000000-0xbfffffff]
[    0.003961] ACPI: SRAT: Node 1 PXM 1 [mem 0x100000000-0x13fffffff]
```

相关的数据结构为
```c
//include/acpi/actbl3.h

/* 1: Memory Affinity */

struct acpi_srat_mem_affinity {
	struct acpi_subtable_header header;
	u32 proximity_domain;
	u16 reserved;		/* Reserved, must be zero */
	u64 base_address;
	u64 length;
	u32 reserved1;
	u32 flags;
	u64 reserved2;		/* Reserved, must be zero */
};

/* Flags */

#define ACPI_SRAT_MEM_ENABLED       (1)	/* 00: Use affinity structure */
#define ACPI_SRAT_MEM_HOT_PLUGGABLE (1<<1)	/* 01: Memory region is hot pluggable */
#define ACPI_SRAT_MEM_NON_VOLATILE  (1<<2)	/* 02: Memory region is non-volatile */
```

在acpi_numa_memory_affinity_init方法中，内核会调用numa_add_memblk方法将上述信息保存到`numa_meminfo`中
```c
// arch/x86/mm/numa.c
static struct numa_meminfo numa_meminfo __initdata_or_meminfo;
```

```c
// arch/x86/mm/numa_internal.h
struct numa_memblk {
	u64			start;
	u64			end;
	int			nid;
};

struct numa_meminfo {
	int			nr_blks;
	struct numa_memblk	blk[NR_NODE_MEMBLKS];
};
```

在numa_cleanup_meminfo方法中打印了每个node的地址空间
```log
[    0.003962] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0x7fffffff] -> [mem 0x00000000-0x7fffffff]
[    0.003963] NUMA: Node 1 [mem 0x80000000-0xbfffffff] + [mem 0x100000000-0x13fffffff] -> [mem 0x80000000-0x13fffffff]
```

在alloc_node_data方法中打印了pglist_data数据的地址，占用16KB空间，默认在各个node内存空间的末尾位置。
```log
[    0.003965] NODE_DATA(0) allocated [mem 0x7fffc000-0x7fffffff]
[    0.003978] NODE_DATA(1) allocated [mem 0x13fffa000-0x13fffdfff]
```

在x86_init.paging.pagetable_init()方法中，内核根据上述从BIOS获取的信息构建pglist_data数据结构，也就是page list data。


```c
// arch/x86/mm/init_64.c
void __init paging_init(void)
{
	sparse_init();

	/*
	 * clear the default setting with node 0
	 * note: don't use nodes_clear here, that is really clearing when
	 *	 numa support is not compiled in, and later node_set_state
	 *	 will not set it back.
	 */
	node_clear_state(0, N_MEMORY);
	node_clear_state(0, N_NORMAL_MEMORY);

	zone_sizes_init();
}
```


NUMA的信息将会被进一步划分，最终维护在pglist_data数据结构中。
```c
// arch/x86/mm/numa.c
struct pglist_data *node_data[MAX_NUMNODES] __read_mostly;
```

```c
// include/linux/mmzone.h
/*
 * On NUMA machines, each NUMA node would have a pg_data_t to describe
 * it's memory layout. On UMA machines there is a single pglist_data which
 * describes the whole memory.
 *
 * Memory statistics and page replacement data structures are maintained on a
 * per-zone basis.
 */
typedef struct pglist_data {
	/*
	 * node_zones contains just the zones for THIS node. Not all of the
	 * zones may be populated, but it is the full list. It is referenced by
	 * this node's node_zonelists as well as other node's node_zonelists.
	 */
	struct zone node_zones[MAX_NR_ZONES];

	/*
	 * node_zonelists contains references to all zones in all nodes.
	 * Generally the first zones will be references to this node's
	 * node_zones.
	 */
	struct zonelist node_zonelists[MAX_ZONELISTS];

	int nr_zones; /* number of populated zones in this node */
#ifdef CONFIG_FLATMEM	/* means !SPARSEMEM */
	struct page *node_mem_map;
#ifdef CONFIG_PAGE_EXTENSION
	struct page_ext *node_page_ext;
#endif
#endif
#if defined(CONFIG_MEMORY_HOTPLUG) || defined(CONFIG_DEFERRED_STRUCT_PAGE_INIT)
	/*
	 * Must be held any time you expect node_start_pfn,
	 * node_present_pages, node_spanned_pages or nr_zones to stay constant.
	 * Also synchronizes pgdat->first_deferred_pfn during deferred page
	 * init.
	 *
	 * pgdat_resize_lock() and pgdat_resize_unlock() are provided to
	 * manipulate node_size_lock without checking for CONFIG_MEMORY_HOTPLUG
	 * or CONFIG_DEFERRED_STRUCT_PAGE_INIT.
	 *
	 * Nests above zone->lock and zone->span_seqlock
	 */
	spinlock_t node_size_lock;
#endif
	unsigned long node_start_pfn;
	unsigned long node_present_pages; /* total number of physical pages */
	unsigned long node_spanned_pages; /* total size of physical page
					     range, including holes */
	int node_id;
	wait_queue_head_t kswapd_wait;
	wait_queue_head_t pfmemalloc_wait;

	/* workqueues for throttling reclaim for different reasons. */
	wait_queue_head_t reclaim_wait[NR_VMSCAN_THROTTLE];

	atomic_t nr_writeback_throttled;/* nr of writeback-throttled tasks */
	unsigned long nr_reclaim_start;	/* nr pages written while throttled
					 * when throttling started. */
#ifdef CONFIG_MEMORY_HOTPLUG
	struct mutex kswapd_lock;
#endif
	struct task_struct *kswapd;	/* Protected by kswapd_lock */
	int kswapd_order;
	enum zone_type kswapd_highest_zoneidx;

	int kswapd_failures;		/* Number of 'reclaimed == 0' runs */

#ifdef CONFIG_COMPACTION
	int kcompactd_max_order;
	enum zone_type kcompactd_highest_zoneidx;
	wait_queue_head_t kcompactd_wait;
	struct task_struct *kcompactd;
	bool proactive_compact_trigger;
#endif
	/*
	 * This is a per-node reserve of pages that are not available
	 * to userspace allocations.
	 */
	unsigned long		totalreserve_pages;

#ifdef CONFIG_NUMA
	/*
	 * node reclaim becomes active if more unmapped pages exist.
	 */
	unsigned long		min_unmapped_pages;
	unsigned long		min_slab_pages;
#endif /* CONFIG_NUMA */

	/* Write-intensive fields used by page reclaim */
	CACHELINE_PADDING(_pad1_);

#ifdef CONFIG_DEFERRED_STRUCT_PAGE_INIT
	/*
	 * If memory initialisation on large machines is deferred then this
	 * is the first PFN that needs to be initialised.
	 */
	unsigned long first_deferred_pfn;
#endif /* CONFIG_DEFERRED_STRUCT_PAGE_INIT */

#ifdef CONFIG_TRANSPARENT_HUGEPAGE
	struct deferred_split deferred_split_queue;
#endif

#ifdef CONFIG_NUMA_BALANCING
	/* start time in ms of current promote rate limit period */
	unsigned int nbp_rl_start;
	/* number of promote candidate pages at start time of current rate limit period */
	unsigned long nbp_rl_nr_cand;
	/* promote threshold in ms */
	unsigned int nbp_threshold;
	/* start time in ms of current promote threshold adjustment period */
	unsigned int nbp_th_start;
	/*
	 * number of promote candidate pages at start time of current promote
	 * threshold adjustment period
	 */
	unsigned long nbp_th_nr_cand;
#endif
	/* Fields commonly accessed by the page reclaim scanner */

	/*
	 * NOTE: THIS IS UNUSED IF MEMCG IS ENABLED.
	 *
	 * Use mem_cgroup_lruvec() to look up lruvecs.
	 */
	struct lruvec		__lruvec;

	unsigned long		flags;

#ifdef CONFIG_LRU_GEN
	/* kswap mm walk data */
	struct lru_gen_mm_walk mm_walk;
	/* lru_gen_folio list */
	struct lru_gen_memcg memcg_lru;
#endif

	CACHELINE_PADDING(_pad2_);

	/* Per-node vmstats */
	struct per_cpu_nodestat __percpu *per_cpu_nodestats;
	atomic_long_t		vm_stat[NR_VM_NODE_STAT_ITEMS];
#ifdef CONFIG_NUMA
	struct memory_tier __rcu *memtier;
#endif
#ifdef CONFIG_MEMORY_FAILURE
	struct memory_failure_stats mf_stats;
#endif
} pg_data_t;

```

在此期间已经有分配内存的动作了，例如alloc_node_data，此时管理内存的数据结构是 memblock。

## memblock


### 数据结构

定义在 `include/linux/memblock.h`

```c
/**
 * struct memblock_region - represents a memory region
 * @base: base address of the region
 * @size: size of the region
 * @flags: memory region attributes
 * @nid: NUMA node id
 */
struct memblock_region {
	phys_addr_t base;
	phys_addr_t size;
	enum memblock_flags flags;
#ifdef CONFIG_NUMA
	int nid;
#endif
};

/**
 * struct memblock_type - collection of memory regions of certain type
 * @cnt: number of regions
 * @max: size of the allocated array
 * @total_size: size of all regions
 * @regions: array of regions
 * @name: the memory type symbolic name
 */
struct memblock_type {
	unsigned long cnt;
	unsigned long max;
	phys_addr_t total_size;
	struct memblock_region *regions;
	char *name;
};

/**
 * struct memblock - memblock allocator metadata
 * @bottom_up: is bottom up direction?
 * @current_limit: physical address of the current allocation limit
 * @memory: usable memory regions
 * @reserved: reserved memory regions
 */
struct memblock {
	bool bottom_up;  /* is bottom up direction? */
	phys_addr_t current_limit;
	struct memblock_type memory;
	struct memblock_type reserved;
};
```

全局对象在 `mm/memblock.c`
```c
static struct memblock_region memblock_memory_init_regions[INIT_MEMBLOCK_MEMORY_REGIONS] __initdata_memblock;
static struct memblock_region memblock_reserved_init_regions[INIT_MEMBLOCK_RESERVED_REGIONS] __initdata_memblock;

struct memblock memblock __initdata_memblock = {
	.memory.regions		= memblock_memory_init_regions,
	.memory.cnt		= 1,	/* empty dummy entry */
	.memory.max		= INIT_MEMBLOCK_MEMORY_REGIONS,
	.memory.name		= "memory",

	.reserved.regions	= memblock_reserved_init_regions,
	.reserved.cnt		= 1,	/* empty dummy entry */
	.reserved.max		= INIT_MEMBLOCK_RESERVED_REGIONS,
	.reserved.name		= "reserved",

	.bottom_up		= false,
	.current_limit		= MEMBLOCK_ALLOC_ANYWHERE,
};

/*
 * keep a pointer to &memblock.memory in the text section to use it in
 * __next_mem_range() and its helpers.
 *  For architectures that do not keep memblock data after init, this
 * pointer will be reset to NULL at memblock_discard()
 */
static __refdata struct memblock_type *memblock_memory = &memblock.memory;
```

### 操作记录

e820__memblock_setup方法中，将从e820获取的物理地址段添加到了`memblock`中

```log
[    0.000000] memblock_reserve: [0x0000000001000000-0x00000000035fffff] setup_arch+0x275/0xf80
[    0.000000] memblock_reserve: [0x0000000000000000-0x000000000000ffff] setup_arch+0x281/0xf80
[    0.000000] memblock_reserve: [0x000000000009f000-0x00000000000fffff] setup_arch+0x3a1/0xf80
...
[    0.003805] memblock_reserve: [0x00000000000f5470-0x00000000000f547f] smp_scan_config+0xc5/0x150
[    0.003808] memblock_reserve: [0x00000000000f5480-0x00000000000f5557] smp_scan_config+0x135/0x150
[    0.003811] memblock_reserve: [0x0000000003600000-0x0000000003608fff] setup_arch+0xd94/0xf80
[    0.003813] memblock_add: [0x0000000000001000-0x000000000009fbff] e820__memblock_setup+0x6e/0xb0
[    0.003815] memblock_add: [0x0000000000100000-0x00000000bffdffff] e820__memblock_setup+0x6e/0xb0
[    0.003816] memblock_add: [0x0000000100000000-0x000000013fffffff] e820__memblock_setup+0x6e/0xb0
[    0.003818] MEMBLOCK configuration:
[    0.003818]  memory size = 0x00000000fff7ec00 reserved size = 0x000000000267a000
[    0.003818]  memory.cnt  = 0x3
[    0.003819]  memory[0x0]	[0x0000000000001000-0x000000000009efff], 0x000000000009e000 bytes flags: 0x0
[    0.003820]  memory[0x1]	[0x0000000000100000-0x00000000bffdffff], 0x00000000bfee0000 bytes flags: 0x0
[    0.003820]  memory[0x2]	[0x0000000100000000-0x000000013fffffff], 0x0000000040000000 bytes flags: 0x0
[    0.003821]  reserved.cnt  = 0x3
[    0.003821]  reserved[0x0]	[0x0000000000000000-0x000000000000ffff], 0x0000000000010000 bytes flags: 0x0
[    0.003822]  reserved[0x1]	[0x000000000009f000-0x00000000000fffff], 0x0000000000061000 bytes flags: 0x0
[    0.003822]  reserved[0x2]	[0x0000000001000000-0x0000000003608fff], 0x0000000002609000 bytes flags: 0x0
```

[0x0000000001000000-0x00000000035fffff] 这一段是kernel二进制的地址空间。

能加入到`memblock_memory`的只有`E820_TYPE_RAM`、`E820_TYPE_RESERVED_KERN`这两种类型的地址段。

dump的信息与add的记录略有区别，原因是地址按照PAGE_SIZE(0x1000)进行了对齐。

添加memblock段的函数最终调的都是`memblock_add_range`：
```c
static int __init_memblock memblock_add_range(struct memblock_type *type,
				phys_addr_t base, phys_addr_t size,
				int nid, enum memblock_flags flags)
{
	bool insert = false;
	phys_addr_t obase = base;
	phys_addr_t end = base + memblock_cap_size(base, &size);
	int idx, nr_new, start_rgn = -1, end_rgn;
	struct memblock_region *rgn;

	if (!size)
		return 0;

	/* special case for empty array */
	if (type->regions[0].size == 0) { // 初始为空的状态，直接赋值给第一个regions
		WARN_ON(type->cnt != 1 || type->total_size);
		type->regions[0].base = base;
		type->regions[0].size = size;
		type->regions[0].flags = flags;
		memblock_set_region_node(&type->regions[0], nid);
		type->total_size = size;
		return 0;
	}

	/*
	 * The worst case is when new range overlaps all existing regions,
	 * then we'll need type->cnt + 1 empty regions in @type. So if
	 * type->cnt * 2 + 1 is less than or equal to type->max, we know
	 * that there is enough empty regions in @type, and we can insert
	 * regions directly.
	 */
	if (type->cnt * 2 + 1 <= type->max)
		insert = true;

repeat:
	/*
	 * The following is executed twice.  Once with %false @insert and
	 * then with %true.  The first counts the number of regions needed
	 * to accommodate the new area.  The second actually inserts them.
	 */
	base = obase;
	nr_new = 0;

	for_each_memblock_type(idx, type, rgn) {
		phys_addr_t rbase = rgn->base;
		phys_addr_t rend = rbase + rgn->size;

		if (rbase >= end) // 此时应该插入在此rgn前面，所以可以退出循环
			break;
		if (rend <= base)
			continue;
		/*
		 * @rgn overlaps.  If it separates the lower part of new
		 * area, insert that portion.
		 */
		if (rbase > base) { //如果有重叠
#ifdef CONFIG_NUMA
			WARN_ON(nid != memblock_get_region_node(rgn));
#endif
			WARN_ON(flags != rgn->flags);
			nr_new++;
			if (insert) {
				if (start_rgn == -1)
					start_rgn = idx;
				end_rgn = idx + 1;
				// 将不重叠的前半部分插入进来
				memblock_insert_region(type, idx++, base,
						       rbase - base, nid,
						       flags);
			}
		}
		/* area below @rend is dealt with, forget about it */
		base = min(rend, end);
	}

	/* insert the remaining portion */
	if (base < end) {
		nr_new++;
		if (insert) {
			if (start_rgn == -1)
				start_rgn = idx;
			end_rgn = idx + 1;
			memblock_insert_region(type, idx, base, end - base,
					       nid, flags);
		}
	}

	if (!nr_new)
		return 0;

	/*
	 * If this was the first round, resize array and repeat for actual
	 * insertions; otherwise, merge and return.
	 */
	if (!insert) {
		while (type->cnt + nr_new > type->max)
			if (memblock_double_array(type, obase, size) < 0)
				return -ENOMEM;
		insert = true;
		goto repeat;
	} else {
		// 合并连续的rgn
		memblock_merge_regions(type, start_rgn, end_rgn);
		return 0;
	}
}
```

### memblock分配的数据

```log
[    0.003843] memblock_phys_alloc_range: 2097152 bytes align=0x200000 from=0x0000000000100000 max_addr=0x0000000140000000 init_mem_mapping+0x1a8/0x340
[    0.003845] memblock_reserve: [0x000000013fe00000-0x000000013fffffff] memblock_phys_alloc_range+0x5e/0x70
[    0.003846] memblock_phys_free: [0x000000013fe00000-0x000000013fffffff] init_mem_mapping+0x1b8/0x340
```

```c
// arch/x86/mm/init.c
void __init init_mem_mapping(void)
{
	unsigned long end;

	pti_check_boottime_disable();
	probe_page_size_mask();
	setup_pcid();

#ifdef CONFIG_X86_64
	end = max_pfn << PAGE_SHIFT;
#else
	end = max_low_pfn << PAGE_SHIFT;
#endif

	/* the ISA range is always mapped regardless of memory holes */
	init_memory_mapping(0, ISA_END_ADDRESS, PAGE_KERNEL);

	/* Init the trampoline, possibly with KASLR memory offset */
	init_trampoline();

	/*
	 * If the allocation is in bottom-up direction, we setup direct mapping
	 * in bottom-up, otherwise we setup direct mapping in top-down.
	 */
	if (memblock_bottom_up()) {
		unsigned long kernel_end = __pa_symbol(_end);

		/*
		 * we need two separate calls here. This is because we want to
		 * allocate page tables above the kernel. So we first map
		 * [kernel_end, end) to make memory above the kernel be mapped
		 * as soon as possible. And then use page tables allocated above
		 * the kernel to map [ISA_END_ADDRESS, kernel_end).
		 */
		memory_map_bottom_up(kernel_end, end);
		memory_map_bottom_up(ISA_END_ADDRESS, kernel_end);
	} else {
		memory_map_top_down(ISA_END_ADDRESS, end);
	}

#ifdef CONFIG_X86_64
	if (max_pfn > max_low_pfn) {
		/* can we preserve max_low_pfn ?*/
		max_low_pfn = max_pfn;
	}
#else
	early_ioremap_page_table_range_init();
#endif

	load_cr3(swapper_pg_dir);
	__flush_tlb_all();

	x86_init.hyper.init_mem_mapping();

	early_memtest(0, max_pfn_mapped << PAGE_SHIFT);
}
```

默认从top分配PMD，占用2MB空间。