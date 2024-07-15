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


