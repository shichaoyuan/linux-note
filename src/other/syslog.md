# 系统日志


```log
[    0.000000] Linux version 6.6.41-dirty (yuan@yuan-t14p) (gcc (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #2 SMP PREEMPT_DYNAMIC Mon Jul 22 22:10:58 CST 2024
[    0.000000] Command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-stable/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-stable/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 memblock=debug nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.000000] memblock_reserve: [0x0000000001000000-0x00000000035fffff] setup_arch+0x275/0xf80
[    0.000000] memblock_reserve: [0x0000000000000000-0x000000000000ffff] setup_arch+0x281/0xf80
[    0.000000] memblock_reserve: [0x000000000009f000-0x00000000000fffff] setup_arch+0x3a1/0xf80
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bffdffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bffe0000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feffc000-0x00000000feffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] APIC: Static calls initialized
[    0.000000] SMBIOS 3.0.0 present.
[    0.000000] DMI: QEMU Ubuntu 24.04 PC (i440FX + PIIX, 1996), BIOS 1.16.3-debian-1.16.3-2 04/01/2014
[    0.000000] Hypervisor detected: KVM
[    0.000000] kvm-clock: Using msrs 4b564d01 and 4b564d00
[    0.000000] kvm-clock: using sched offset of 206775474 cycles
[    0.000001] clocksource: kvm-clock: mask: 0xffffffffffffffff max_cycles: 0x1cd42e4dffb, max_idle_ns: 881590591483 ns
[    0.000002] tsc: Detected 2995.200 MHz processor
[    0.000116] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000117] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000119] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000138] MTRR map: 4 entries (3 fixed + 1 variable; max 19), built from 8 variable MTRRs
[    0.000139] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000163] last_pfn = 0xbffe0 max_arch_pfn = 0x400000000
[    0.003805] found SMP MP-table at [mem 0x000f5470-0x000f547f]
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
[    0.003823] memblock_phys_alloc_range: 28672 bytes align=0x1000 from=0x0000000000000000 max_addr=0x0000000000100000 reserve_real_mode+0x52/0x90
[    0.003825] memblock_reserve: [0x0000000000098000-0x000000000009efff] memblock_phys_alloc_range+0x5e/0x70
[    0.003827] memblock_reserve: [0x0000000000000000-0x00000000000fffff] setup_arch+0x74e/0xf80
[    0.003832] Using GB pages for direct mapping
[    0.003843] memblock_phys_alloc_range: 2097152 bytes align=0x200000 from=0x0000000000100000 max_addr=0x0000000140000000 init_mem_mapping+0x1a8/0x340
[    0.003845] memblock_reserve: [0x000000013fe00000-0x000000013fffffff] memblock_phys_alloc_range+0x5e/0x70
[    0.003846] memblock_phys_free: [0x000000013fe00000-0x000000013fffffff] init_mem_mapping+0x1b8/0x340
[    0.003883] memblock_phys_alloc_range: 4096 bytes align=0x1000 from=0x0000000120000000 max_addr=0x0000000140000000 alloc_low_pages+0x91/0x150
[    0.003885] memblock_reserve: [0x000000013ffff000-0x000000013fffffff] memblock_phys_alloc_range+0x5e/0x70
[    0.003909] memblock_phys_alloc_range: 4096 bytes align=0x1000 from=0x0000000120000000 max_addr=0x0000000140000000 alloc_low_pages+0x91/0x150
[    0.003910] memblock_reserve: [0x000000013fffe000-0x000000013fffefff] memblock_phys_alloc_range+0x5e/0x70
[    0.003928] ACPI: Early table checksum verification disabled
[    0.003931] ACPI: RSDP 0x00000000000F5270 000014 (v00 BOCHS )
[    0.003935] ACPI: RSDT 0x00000000BFFE1E95 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003939] ACPI: FACP 0x00000000BFFE1C21 000074 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003943] ACPI: DSDT 0x00000000BFFE0040 001BE1 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003944] ACPI: FACS 0x00000000BFFE0000 000040
[    0.003946] ACPI: APIC 0x00000000BFFE1C95 000090 (v03 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003947] ACPI: HPET 0x00000000BFFE1D25 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003949] ACPI: SRAT 0x00000000BFFE1D5D 000110 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003950] ACPI: WAET 0x00000000BFFE1E6D 000028 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003951] ACPI: Reserving FACP table memory at [mem 0xbffe1c21-0xbffe1c94]
[    0.003952] memblock_reserve: [0x00000000bffe1c21-0x00000000bffe1c94] acpi_reserve_initial_tables+0x45/0x70
[    0.003954] ACPI: Reserving DSDT table memory at [mem 0xbffe0040-0xbffe1c20]
[    0.003954] memblock_reserve: [0x00000000bffe0040-0x00000000bffe1c20] acpi_reserve_initial_tables+0x45/0x70
[    0.003955] ACPI: Reserving FACS table memory at [mem 0xbffe0000-0xbffe003f]
[    0.003956] memblock_reserve: [0x00000000bffe0000-0x00000000bffe003f] acpi_reserve_initial_tables+0x45/0x70
[    0.003957] ACPI: Reserving APIC table memory at [mem 0xbffe1c95-0xbffe1d24]
[    0.003957] memblock_reserve: [0x00000000bffe1c95-0x00000000bffe1d24] acpi_reserve_initial_tables+0x45/0x70
[    0.003958] ACPI: Reserving HPET table memory at [mem 0xbffe1d25-0xbffe1d5c]
[    0.003958] memblock_reserve: [0x00000000bffe1d25-0x00000000bffe1d5c] acpi_reserve_initial_tables+0x45/0x70
[    0.003959] ACPI: Reserving SRAT table memory at [mem 0xbffe1d5d-0xbffe1e6c]
[    0.003960] memblock_reserve: [0x00000000bffe1d5d-0x00000000bffe1e6c] acpi_reserve_initial_tables+0x45/0x70
[    0.003961] ACPI: Reserving WAET table memory at [mem 0xbffe1e6d-0xbffe1e94]
[    0.003961] memblock_reserve: [0x00000000bffe1e6d-0x00000000bffe1e94] acpi_reserve_initial_tables+0x45/0x70
[    0.003980] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.003980] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.003981] SRAT: PXM 1 -> APIC 0x02 -> Node 1
[    0.003981] SRAT: PXM 1 -> APIC 0x03 -> Node 1
[    0.003982] ACPI: SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.003983] ACPI: SRAT: Node 0 PXM 0 [mem 0x00100000-0x7fffffff]
[    0.003983] ACPI: SRAT: Node 1 PXM 1 [mem 0x80000000-0xbfffffff]
[    0.003984] ACPI: SRAT: Node 1 PXM 1 [mem 0x100000000-0x13fffffff]
[    0.003985] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0x7fffffff] -> [mem 0x00000000-0x7fffffff]
[    0.003986] NUMA: Node 1 [mem 0x80000000-0xbfffffff] + [mem 0x100000000-0x13fffffff] -> [mem 0x80000000-0x13fffffff]
[    0.003987] memblock_reserve: [0x000000007fffc000-0x000000007fffffff] numa_init+0x365/0x690
[    0.003989] NODE_DATA(0) allocated [mem 0x7fffc000-0x7fffffff]
[    0.003999] memblock_reserve: [0x000000013fffa000-0x000000013fffdfff] numa_init+0x365/0x690
[    0.004001] NODE_DATA(1) allocated [mem 0x13fffa000-0x13fffdfff]
[    0.004008] MEMBLOCK configuration:
[    0.004009]  memory size = 0x00000000fff7ec00 reserved size = 0x0000000002714e95
[    0.004009]  memory.cnt  = 0x4
[    0.004009]  memory[0x0]	[0x0000000000001000-0x000000000009efff], 0x000000000009e000 bytes on node 0 flags: 0x0
[    0.004010]  memory[0x1]	[0x0000000000100000-0x000000007fffffff], 0x000000007ff00000 bytes on node 0 flags: 0x0
[    0.004011]  memory[0x2]	[0x0000000080000000-0x00000000bffdffff], 0x000000003ffe0000 bytes on node 1 flags: 0x0
[    0.004011]  memory[0x3]	[0x0000000100000000-0x000000013fffffff], 0x0000000040000000 bytes on node 1 flags: 0x0
[    0.004012]  reserved.cnt  = 0x6
[    0.004012]  reserved[0x0]	[0x0000000000000000-0x00000000000fffff], 0x0000000000100000 bytes on node 0 flags: 0x0
[    0.004013]  reserved[0x1]	[0x0000000001000000-0x0000000003608fff], 0x0000000002609000 bytes on node 0 flags: 0x0
[    0.004013]  reserved[0x2]	[0x000000007fffc000-0x000000007fffffff], 0x0000000000004000 bytes flags: 0x0
[    0.004014]  reserved[0x3]	[0x00000000bffe0000-0x00000000bffe1e94], 0x0000000000001e95 bytes on node 1 flags: 0x0
[    0.004014]  reserved[0x4]	[0x000000013fffa000-0x000000013fffdfff], 0x0000000000004000 bytes flags: 0x0
[    0.004015]  reserved[0x5]	[0x000000013fffe000-0x000000013fffffff], 0x0000000000002000 bytes on node 1 flags: 0x0
[    0.004018] memblock_alloc_try_nid: 16384 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init+0x3f8/0x490
[    0.004019] memblock_reserve: [0x000000013fff6000-0x000000013fff9fff] memblock_alloc_internal+0x4e/0xc0
[    0.004028] memblock_alloc_try_nid: 4096 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_index_alloc+0x3b/0x60
[    0.004029] memblock_reserve: [0x000000007fffb000-0x000000007fffbfff] memblock_alloc_internal+0x4e/0xc0
[    0.004034] memblock_alloc_try_nid: 896 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init_nid+0x45/0x390
[    0.004035] memblock_reserve: [0x000000007fffac80-0x000000007fffafff] memblock_alloc_internal+0x4e/0xc0
[    0.004038] memblock_alloc_exact_nid_raw: 33554432 bytes align=0x200000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 sparse_init_nid+0x9f/0x390
[    0.004039] memblock_reserve: [0x000000007de00000-0x000000007fdfffff] memblock_alloc_internal+0x4e/0xc0
[    0.004041] memblock_alloc_try_nid_raw: 4096 bytes align=0x1000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 vmemmap_p4d_populate+0x5d/0xf0
[    0.004043] memblock_reserve: [0x000000007fff9000-0x000000007fff9fff] memblock_alloc_internal+0x4e/0xc0
[    0.004046] memblock_alloc_try_nid_raw: 4096 bytes align=0x1000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 vmemmap_pud_populate+0x4a/0xd0
[    0.004047] memblock_reserve: [0x000000007fff8000-0x000000007fff8fff] memblock_alloc_internal+0x4e/0xc0
[    0.004050] memblock_alloc_try_nid: 896 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init_nid+0x45/0x390
[    0.004051] memblock_reserve: [0x000000007fffa900-0x000000007fffac7f] memblock_alloc_internal+0x4e/0xc0
[    0.004053] memblock_alloc_exact_nid_raw: 33554432 bytes align=0x200000 nid=1 from=0x0000000001000000 max_addr=0x0000000000000000 sparse_init_nid+0x9f/0x390
[    0.004053] memblock_reserve: [0x000000013de00000-0x000000013fdfffff] memblock_alloc_internal+0x4e/0xc0
[    0.004055] Zone ranges:
[    0.004056]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.004056]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.004057]   Normal   [mem 0x0000000100000000-0x000000013fffffff]
[    0.004058] Movable zone start for each node
[    0.004058] Early memory node ranges
[    0.004058]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.004059]   node   0: [mem 0x0000000000100000-0x000000007fffffff]
[    0.004059]   node   1: [mem 0x0000000080000000-0x00000000bffdffff]
[    0.004059]   node   1: [mem 0x0000000100000000-0x000000013fffffff]
[    0.004060] Initmem setup node 0 [mem 0x0000000000001000-0x000000007fffffff]
[    0.004061] Initmem setup node 1 [mem 0x0000000080000000-0x000000013fffffff]
[    0.004069] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.004180] On node 0, zone DMA: 97 pages in unavailable ranges
[    0.032510] On node 1, zone Normal: 32 pages in unavailable ranges
[    0.032686] ACPI: PM-Timer IO Port: 0x608
[    0.032690] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.032714] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.032715] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.032716] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.032717] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.032718] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.032718] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.032720] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.032725] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.032726] memblock_alloc_try_nid: 73 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 acpi_parse_hpet+0x90/0x150
[    0.032729] memblock_reserve: [0x000000013fff5f80-0x000000013fff5fc8] memblock_alloc_internal+0x4e/0xc0
[    0.032734] TSC deadline timer available
[    0.032734] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.032735] memblock_alloc_try_nid: 75 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 io_apic_init_mappings+0x42/0x210
[    0.032737] memblock_reserve: [0x000000013fff5f00-0x000000013fff5f4a] memblock_alloc_internal+0x4e/0xc0
[    0.032746] kvm-guest: APIC: eoi() replaced with kvm_guest_apic_eoi_write()
[    0.032752] kvm-guest: KVM setup pv remote TLB flush
[    0.032754] kvm-guest: setup PV sched yield
[    0.032755] memblock_alloc_try_nid: 576 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 e820__reserve_resources+0x2d/0x200
[    0.032757] memblock_reserve: [0x000000013fff5cc0-0x000000013fff5eff] memblock_alloc_internal+0x4e/0xc0
[    0.032759] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032761] memblock_reserve: [0x000000013fff5c40-0x000000013fff5ca7] memblock_alloc_internal+0x4e/0xc0
[    0.032763] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032764] memblock_reserve: [0x000000013fff5bc0-0x000000013fff5c27] memblock_alloc_internal+0x4e/0xc0
[    0.032766] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032767] memblock_reserve: [0x000000013fff5b40-0x000000013fff5ba7] memblock_alloc_internal+0x4e/0xc0
[    0.032768] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032770] memblock_reserve: [0x000000013fff5ac0-0x000000013fff5b27] memblock_alloc_internal+0x4e/0xc0
[    0.032771] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032772] memblock_reserve: [0x000000013fff5a40-0x000000013fff5aa7] memblock_alloc_internal+0x4e/0xc0
[    0.032773] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032775] memblock_reserve: [0x000000013fff59c0-0x000000013fff5a27] memblock_alloc_internal+0x4e/0xc0
[    0.032776] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032777] memblock_reserve: [0x000000013fff5940-0x000000013fff59a7] memblock_alloc_internal+0x4e/0xc0
[    0.032779] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.032780] memblock_reserve: [0x000000013fff58c0-0x000000013fff5927] memblock_alloc_internal+0x4e/0xc0
[    0.032781] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.032783] memblock_reserve: [0x000000013fff5880-0x000000013fff589f] memblock_alloc_internal+0x4e/0xc0
[    0.032784] PM: hibernation: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.032785] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.032787] memblock_reserve: [0x000000013fff5840-0x000000013fff585f] memblock_alloc_internal+0x4e/0xc0
[    0.032788] PM: hibernation: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.032788] PM: hibernation: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.032789] PM: hibernation: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.032789] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.032790] memblock_reserve: [0x000000013fff5800-0x000000013fff581f] memblock_alloc_internal+0x4e/0xc0
[    0.032792] PM: hibernation: Registered nosave memory: [mem 0xbffe0000-0xbfffffff]
[    0.032792] PM: hibernation: Registered nosave memory: [mem 0xc0000000-0xfeffbfff]
[    0.032792] PM: hibernation: Registered nosave memory: [mem 0xfeffc000-0xfeffffff]
[    0.032792] PM: hibernation: Registered nosave memory: [mem 0xff000000-0xfffbffff]
[    0.032793] PM: hibernation: Registered nosave memory: [mem 0xfffc0000-0xffffffff]
[    0.032794] [mem 0xc0000000-0xfeffbfff] available for PCI devices
[    0.032794] Booting paravirtualized kernel on KVM
[    0.032795] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1910969940391419 ns
[    0.035993] memblock_alloc_try_nid: 716 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0xbb/0x690
[    0.035995] memblock_reserve: [0x000000013fff5500-0x000000013fff57cb] memblock_alloc_internal+0x4e/0xc0
[    0.035997] memblock_alloc_try_nid: 716 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0xee/0x690
[    0.035999] memblock_reserve: [0x000000013fff5200-0x000000013fff54cb] memblock_alloc_internal+0x4e/0xc0
[    0.036000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:2
[    0.036001] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_build_alloc_info+0x20f/0x520
[    0.036003] memblock_reserve: [0x000000013fff4000-0x000000013fff4fff] memblock_alloc_internal+0x4e/0xc0
[    0.036009] memblock_alloc_try_nid: 4096 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0x71/0x610
[    0.036011] memblock_reserve: [0x000000013fff3000-0x000000013fff3fff] memblock_alloc_internal+0x4e/0xc0
[    0.036014] memblock_alloc_try_nid: 2097152 bytes align=0x200000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0xfd/0x610
[    0.036016] memblock_reserve: [0x000000007dc00000-0x000000007ddfffff] memblock_alloc_internal+0x4e/0xc0
[    0.036917] memblock_alloc_try_nid: 2097152 bytes align=0x200000 nid=1 from=0x0000000001000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0xfd/0x610
[    0.036920] memblock_reserve: [0x000000013dc00000-0x000000013ddfffff] memblock_alloc_internal+0x4e/0xc0
[    0.037789] memblock_phys_free: [0x000000007dc36000-0x000000007dcfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.037797] memblock_phys_free: [0x000000007dd36000-0x000000007ddfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.037803] memblock_phys_free: [0x000000013dc36000-0x000000013dcfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.037809] memblock_phys_free: [0x000000013dd36000-0x000000013ddfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.037810] percpu: Embedded 54 pages/cpu s183016 r8192 d29976 u1048576
[    0.037811] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0xc2/0x8a0
[    0.037812] memblock_reserve: [0x000000013fff51c0-0x000000013fff51cf] memblock_alloc_internal+0x4e/0xc0
[    0.037814] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0xed/0x8a0
[    0.037815] memblock_reserve: [0x000000013fff5180-0x000000013fff518f] memblock_alloc_internal+0x4e/0xc0
[    0.037816] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x11b/0x8a0
[    0.037818] memblock_reserve: [0x000000013fff5140-0x000000013fff514f] memblock_alloc_internal+0x4e/0xc0
[    0.037819] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x14a/0x8a0
[    0.037820] memblock_reserve: [0x000000013fff5100-0x000000013fff511f] memblock_alloc_internal+0x4e/0xc0
[    0.037822] pcpu-alloc: s183016 r8192 d29976 u1048576 alloc=1*2097152
[    0.037823] pcpu-alloc: [0] 0 1 [1] 2 3 
[    0.037825] memblock_alloc_try_nid: 352 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x5de/0x8a0
[    0.037826] memblock_reserve: [0x000000013fff2e80-0x000000013fff2fdf] memblock_alloc_internal+0x4e/0xc0
[    0.037831] memblock_alloc_try_nid: 136 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x76/0x270
[    0.037833] memblock_reserve: [0x000000013fff5040-0x000000013fff50c7] memblock_alloc_internal+0x4e/0xc0
[    0.037834] memblock_alloc_try_nid: 384 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0xd6/0x270
[    0.037835] memblock_reserve: [0x000000013fff2d00-0x000000013fff2e7f] memblock_alloc_internal+0x4e/0xc0
[    0.037837] memblock_alloc_try_nid: 392 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x105/0x270
[    0.037838] memblock_reserve: [0x000000013fff2b40-0x000000013fff2cc7] memblock_alloc_internal+0x4e/0xc0
[    0.037839] memblock_alloc_try_nid: 96 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x131/0x270
[    0.037841] memblock_reserve: [0x000000013fff2ac0-0x000000013fff2b1f] memblock_alloc_internal+0x4e/0xc0
[    0.037843] memblock_alloc_try_nid: 136 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x76/0x270
[    0.037845] memblock_reserve: [0x000000013fff2a00-0x000000013fff2a87] memblock_alloc_internal+0x4e/0xc0
[    0.037846] memblock_alloc_try_nid: 1024 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0xd6/0x270
[    0.037847] memblock_reserve: [0x000000013fff2600-0x000000013fff29ff] memblock_alloc_internal+0x4e/0xc0
[    0.037848] memblock_alloc_try_nid: 1032 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x105/0x270
[    0.037850] memblock_reserve: [0x000000013fff21c0-0x000000013fff25c7] memblock_alloc_internal+0x4e/0xc0
[    0.037851] memblock_alloc_try_nid: 256 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x131/0x270
[    0.037852] memblock_reserve: [0x000000013fff20c0-0x000000013fff21bf] memblock_alloc_internal+0x4e/0xc0
[    0.037854] memblock_phys_free: [0x000000013fff4000-0x000000013fff4fff] pcpu_embed_first_chunk+0x284/0x610
[    0.037855] memblock_phys_free: [0x000000013fff3000-0x000000013fff3fff] pcpu_embed_first_chunk+0x291/0x610
[    0.037867] Kernel command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-stable/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-stable/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 memblock=debug nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.037943] memblock_alloc_try_nid: 456 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0x495/0x690
[    0.037945] memblock_reserve: [0x000000013fff4e40-0x000000013fff5007] memblock_alloc_internal+0x4e/0xc0
[    0.037947] Unknown kernel command line parameters "virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-stable/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 virtme_stty_con=rows 43 cols 132 iutf8 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-stable/buildq", will be passed to user space.
[    0.037948] memblock_phys_free: [0x000000013fff4e40-0x000000013fff5007] start_kernel+0x525/0x690
[    0.037957] random: crng init done
[    0.037959] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.037961] memblock_reserve: [0x000000013fff4000-0x000000013fff4fff] memblock_alloc_internal+0x4e/0xc0
[    0.037962] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.037963] memblock_reserve: [0x000000013fff3000-0x000000013fff3fff] memblock_alloc_internal+0x4e/0xc0
[    0.037965] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.037966] memblock_reserve: [0x000000013fff1000-0x000000013fff1fff] memblock_alloc_internal+0x4e/0xc0
[    0.038005] Fallback order for Node 0: 0 1 
[    0.038006] Fallback order for Node 1: 1 0 
[    0.038007] Built 2 zonelists, mobility grouping on.  Total pages: 1031904
[    0.038008] Policy zone: Normal
[    0.038008] mem auto-init: stack:all(zero), heap alloc:off, heap free:off
[    0.038010] software IO TLB: area num 4.
[    0.038011] memblock_alloc_try_nid: 67108864 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x00000000ffffffff swiotlb_init_remap+0xd1/0x2f0
[    0.038012] memblock_reserve: [0x00000000bbfe0000-0x00000000bffdffff] memblock_alloc_internal+0x4e/0xc0
[    0.066005] memblock_alloc_try_nid: 786432 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 swiotlb_init_remap+0x148/0x2f0
[    0.066008] memblock_reserve: [0x000000013ff31000-0x000000013fff0fff] memblock_alloc_internal+0x4e/0xc0
[    0.066334] memblock_alloc_try_nid: 64 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 swiotlb_init_remap+0x172/0x2f0
[    0.066336] memblock_reserve: [0x000000013fff5000-0x000000013fff503f] memblock_alloc_internal+0x4e/0xc0
[    0.074369] Memory: 4021152K/4193784K available (18432K kernel code, 2739K rwdata, 6532K rodata, 2644K init, 1528K bss, 172376K reserved, 0K cma-reserved)
[    0.074399] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=2
[    0.075056] Dynamic Preempt: voluntary
[    0.075087] rcu: Preemptible hierarchical RCU implementation.
[    0.075087] rcu: 	RCU event tracing is enabled.
[    0.075088] rcu: 	RCU restricting CPUs from NR_CPUS=64 to nr_cpu_ids=4.
[    0.075088] 	Trampoline variant of Tasks RCU enabled.
[    0.075089] rcu: RCU calculated value of scheduler-enlistment delay is 100 jiffies.
[    0.075089] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.075795] NR_IRQS: 4352, nr_irqs: 456, preallocated irqs: 16
[    0.075964] rcu: srcu_init: Setting srcu_struct sizes based on contention.
[    0.076042] Console: colour *CGA 80x25
[    0.076043] printk: console [tty0] enabled
[    0.076060] ACPI: Core revision 20230628
[    0.076131] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604467 ns
[    0.076187] APIC: Switch to symmetric I/O mode setup
[    0.076191] kvm-guest: APIC: send_IPI_mask() replaced with kvm_send_ipi_mask()
[    0.076194] kvm-guest: APIC: send_IPI_mask_allbutself() replaced with kvm_send_ipi_mask_allbutself()
[    0.076195] kvm-guest: setup PV IPIs
[    0.076809] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076821] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.076824] Calibrating delay loop (skipped) preset value.. 5990.40 BogoMIPS (lpj=2995200)
[    0.076894] x86/cpu: User Mode Instruction Prevention (UMIP) activated
[    0.076938] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.076939] Last level dTLB entries: 4KB 0, 2MB 0, 4MB 0, 1GB 0
[    0.076943] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.076946] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on vm exit
[    0.076947] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on syscall
[    0.076947] Spectre V2 : Mitigation: Enhanced / Automatic IBRS
[    0.076947] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.076947] Spectre V2 : Spectre v2 / PBRSB-eIBRS: Retire a single CALL on VMEXIT
[    0.076948] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.076950] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl
[    0.076950] Register File Data Sampling: Vulnerable: No microcode
[    0.076962] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.076962] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.076963] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.076963] x86/fpu: Supporting XSAVE feature 0x200: 'Protection Keys User registers'
[    0.076964] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.076964] x86/fpu: xstate_offset[9]:  832, xstate_sizes[9]:    8
[    0.076965] x86/fpu: Enabled xstate features 0x207, context size is 840 bytes, using 'compacted' format.
[    0.087437] Freeing SMP alternatives memory: 48K
[    0.087439] pid_max: default: 32768 minimum: 301
[    0.087449] LSM: initializing lsm=capability,selinux,integrity
[    0.087451] SELinux:  Initializing.
[    0.089361] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes, vmalloc hugepage)
[    0.090319] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes, vmalloc)
[    0.090351] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.090380] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.090644] smpboot: CPU0: 13th Gen Intel(R) Core(TM) i9-13900H (family: 0x6, model: 0xba, stepping: 0x2)
[    0.090783] RCU Tasks: Setting shift to 2 and lim to 1 rcu_task_cb_adjust=1.
[    0.090795] Performance Events: unsupported p6 CPU model 186 no PMU driver, software events only.
[    0.090814] signal: max sigframe size: 3632
[    0.090822] rcu: Hierarchical SRCU implementation.
[    0.090822] rcu: 	Max phase no-delay instances is 400.
[    0.090822] smp: Bringing up secondary CPUs ...
[    0.090822] smpboot: x86: Booting SMP configuration:
[    0.090822] .... node  #0, CPUs:      #1
[    0.090822] .... node  #1, CPUs:   #2 #3
[    0.091002] smp: Brought up 2 nodes, 4 CPUs
[    0.091003] smpboot: Max logical packages: 1
[    0.091004] smpboot: Total of 4 processors activated (23961.60 BogoMIPS)
[    0.091824] devtmpfs: initialized
[    0.091924] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
[    0.091924] futex hash table entries: 1024 (order: 4, 65536 bytes, vmalloc)
[    0.091940] PM: RTC time: 14:12:08, date: 2024-07-22
[    0.092009] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.092063] audit: initializing netlink subsys (disabled)
[    0.092081] audit: type=2000 audit(1721657528.975:1): state=initialized audit_enabled=0 res=1
[    0.092081] thermal_sys: Registered thermal governor 'step_wise'
[    0.092081] thermal_sys: Registered thermal governor 'user_space'
[    0.092081] cpuidle: using governor menu
[    0.092081] PCI: Using configuration type 1 for base access
[    0.092125] kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
[    0.092991] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
[    0.092991] HugeTLB: 28 KiB vmemmap can be freed for a 2.00 MiB page
[    0.093457] ACPI: Added _OSI(Module Device)
[    0.093457] ACPI: Added _OSI(Processor Device)
[    0.093457] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.093457] ACPI: Added _OSI(Processor Aggregator Device)
[    0.093457] ACPI: 1 ACPI AML tables successfully acquired and loaded
[    0.094885] ACPI: _OSC evaluation for CPUs failed, trying _PDC
[    0.094885] ACPI: Interpreter enabled
[    0.094885] ACPI: PM: (supports S0 S3 S4 S5)
[    0.094885] ACPI: Using IOAPIC for interrupt routing
[    0.094888] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.094889] PCI: Using E820 reservations for host bridge windows
[    0.094953] ACPI: Enabled 2 GPEs in block 00 to 0F
[    0.095841] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.095844] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI HPX-Type3]
[    0.095845] acpi PNP0A03:00: _OSC: not requesting OS control; OS requires [ExtendedConfig ASPM ClockPM MSI]
[    0.095849] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended configuration space under this bridge
[    0.095903] PCI host bridge to bus 0000:00
[    0.095903] pci_bus 0000:00: Unknown NUMA node; performance will be reduced
[    0.095904] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.095905] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.095906] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.095906] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff window]
[    0.095907] pci_bus 0000:00: root bus resource [mem 0x380000000000-0x38007fffffff window]
[    0.095907] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.095928] pci 0000:00:00.0: [8086:1237] type 00 class 0x060000
[    0.096141] pci 0000:00:01.0: [8086:7000] type 00 class 0x060100
[    0.096401] pci 0000:00:01.1: [8086:7010] type 00 class 0x010180
[    0.097772] pci 0000:00:01.1: reg 0x20: [io  0xc060-0xc06f]
[    0.098244] pci 0000:00:01.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.098245] pci 0000:00:01.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.098245] pci 0000:00:01.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.098246] pci 0000:00:01.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.098324] pci 0000:00:01.3: [8086:7113] type 00 class 0x068000
[    0.098524] pci 0000:00:01.3: quirk: [io  0x0600-0x063f] claimed by PIIX4 ACPI
[    0.098528] pci 0000:00:01.3: quirk: [io  0x0700-0x070f] claimed by PIIX4 SMB
[    0.098668] pci 0000:00:02.0: [1af4:1009] type 00 class 0x000200
[    0.099202] pci 0000:00:02.0: reg 0x10: [io  0xc000-0xc03f]
[    0.099824] pci 0000:00:02.0: reg 0x14: [mem 0xfeb80000-0xfeb80fff]
[    0.101824] pci 0000:00:02.0: reg 0x20: [mem 0x380000000000-0x380000003fff 64bit pref]
[    0.102899] pci 0000:00:03.0: [8086:25ab] type 00 class 0x088000
[    0.103166] pci 0000:00:03.0: reg 0x10: [mem 0xfeb81000-0xfeb8100f]
[    0.104523] pci 0000:00:04.0: [1af4:1000] type 00 class 0x020000
[    0.105824] pci 0000:00:04.0: reg 0x10: [io  0xc040-0xc05f]
[    0.106202] pci 0000:00:04.0: reg 0x14: [mem 0xfeb82000-0xfeb82fff]
[    0.107442] pci 0000:00:04.0: reg 0x20: [mem 0x380000004000-0x380000007fff 64bit pref]
[    0.107790] pci 0000:00:04.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.108319] ACPI: PCI: Interrupt link LNKA configured for IRQ 10
[    0.108357] ACPI: PCI: Interrupt link LNKB configured for IRQ 10
[    0.108388] ACPI: PCI: Interrupt link LNKC configured for IRQ 11
[    0.108421] ACPI: PCI: Interrupt link LNKD configured for IRQ 11
[    0.108438] ACPI: PCI: Interrupt link LNKS configured for IRQ 9
[    0.108563] iommu: Default domain type: Translated
[    0.108564] iommu: DMA domain TLB invalidation policy: lazy mode
[    0.108607] SCSI subsystem initialized
[    0.108852] libata version 3.00 loaded.
[    0.108852] ACPI: bus type USB registered
[    0.108858] usbcore: registered new interface driver usbfs
[    0.108860] usbcore: registered new interface driver hub
[    0.108867] usbcore: registered new device driver usb
[    0.108875] pps_core: LinuxPPS API ver. 1 registered
[    0.108876] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.108877] PTP clock support registered
[    0.108894] Advanced Linux Sound Architecture Driver Initialized.
[    0.108927] NetLabel: Initializing
[    0.108927] NetLabel:  domain hash size = 128
[    0.108928] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.108934] NetLabel:  unlabeled traffic allowed by default
[    0.108942] PCI: Using ACPI for IRQ routing
[    0.108942] PCI: pci_cache_line_size set to 64 bytes
[    0.108942] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.108942] e820: reserve RAM buffer [mem 0xbffe0000-0xbfffffff]
[    0.108942] vgaarb: loaded
[    0.108942] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.108942] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.112905] clocksource: Switched to clocksource kvm-clock
[    0.113014] VFS: Disk quotas dquot_6.6.0
[    0.113019] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.113044] pnp: PnP ACPI init
[    0.113075] pnp 00:02: [dma 2]
[    0.113150] pnp: PnP ACPI: found 5 devices
[    0.119306] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.119321] NET: Registered PF_INET protocol family
[    0.119569] IP idents hash table entries: 65536 (order: 7, 524288 bytes, vmalloc)
[    0.119978] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes, vmalloc)
[    0.119996] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, vmalloc)
[    0.119998] TCP established hash table entries: 32768 (order: 6, 262144 bytes, vmalloc)
[    0.120127] TCP bind hash table entries: 32768 (order: 8, 1048576 bytes, vmalloc)
[    0.120582] TCP: Hash tables configured (established 32768 bind 32768)
[    0.120644] UDP hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.120676] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.120718] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    0.121050] RPC: Registered named UNIX socket transport module.
[    0.121051] RPC: Registered udp transport module.
[    0.121052] RPC: Registered tcp transport module.
[    0.121052] RPC: Registered tcp-with-tls transport module.
[    0.121052] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    0.121329] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.121331] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.121332] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.121332] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff window]
[    0.121333] pci_bus 0000:00: resource 8 [mem 0x380000000000-0x38007fffffff window]
[    0.121352] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.121358] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.121403] PCI: CLS 0 bytes, default 64
[    0.121426] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.121427] software IO TLB: mapped [mem 0x00000000bbfe0000-0x00000000bffe0000] (64MB)
[    0.124537] RAPL PMU: API unit is 2^-32 Joules, 0 fixed counters, 10737418240 ms ovfl timer
[    0.124544] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.138984] Initialise system trusted keyrings
[    0.139348] workingset: timestamp_bits=56 max_order=20 bucket_order=0
[    0.139643] NFS: Registering the id_resolver key type
[    0.139646] Key type id_resolver registered
[    0.139647] Key type id_legacy registered
[    0.139851] 9p: Installing v9fs 9p2000 file system support
[    0.143076] Key type asymmetric registered
[    0.143077] Asymmetric key parser 'x509' registered
[    0.143091] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.143095] io scheduler mq-deadline registered
[    0.143096] io scheduler kyber registered
[    0.143382] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.143431] ACPI: button: Power Button [PWRF]
[    0.149435] ACPI: \_SB_.LNKB: Enabled at IRQ 10
[    0.156080] ACPI: \_SB_.LNKD: Enabled at IRQ 11
[    0.156631] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.156714] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.157067] Non-volatile memory driver v1.3
[    0.157068] Linux agpgart interface v0.103
[    0.157094] ACPI: bus type drm_connector registered
[    0.158475] loop: module loaded
[    0.158519] ata_piix 0000:00:01.1: version 2.13
[    0.159032] scsi host0: ata_piix
[    0.159171] scsi host1: ata_piix
[    0.159188] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc060 irq 14
[    0.159189] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc068 irq 15
[    0.161302] e100: Intel(R) PRO/100 Network Driver
[    0.161303] e100: Copyright(c) 1999-2006 Intel Corporation
[    0.161323] e1000: Intel(R) PRO/1000 Network Driver
[    0.161323] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    0.161330] e1000e: Intel(R) PRO/1000 Network Driver
[    0.161330] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.161333] sky2: driver version 1.30
[    0.161645] usbcore: registered new interface driver usblp
[    0.161648] usbcore: registered new interface driver usb-storage
[    0.161660] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.162168] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.162172] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.162297] rtc_cmos 00:04: RTC can wake from S4
[    0.162597] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.162684] rtc_cmos 00:04: registered as rtc0
[    0.162729] rtc_cmos 00:04: alarms up to one day, y3k, 242 bytes nvram, hpet irqs
[    0.162925] device-mapper: ioctl: 4.48.0-ioctl (2023-03-01) initialised: dm-devel@redhat.com
[    0.162940] intel_pstate: CPU model not supported
[    0.162947] hid: raw HID events driver (C) Jiri Kosina
[    0.162997] usbcore: registered new interface driver usbhid
[    0.162998] usbhid: USB HID core driver
[    0.163422] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[    0.163642] Initializing XFRM netlink socket
[    0.163648] NET: Registered PF_INET6 protocol family
[    0.164118] Segment Routing with IPv6
[    0.164128] In-situ OAM (IOAM) with IPv6
[    0.164145] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    0.164202] NET: Registered PF_PACKET protocol family
[    0.164215] 9pnet: Installing 9P2000 support
[    0.164842] Key type dns_resolver registered
[    0.165202] IPI shorthand broadcast: enabled
[    0.166319] sched_clock: Marking stable (166001050, -145614)->(166885961, -1030525)
[    0.166533] registered taskstats version 1
[    0.166534] Loading compiled-in X.509 certificates
[    0.167199] PM:   Magic number: 0:313:233
[    0.167217] printk: console [netcon0] enabled
[    0.167218] netconsole: network logging started
[    0.167237] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    0.167555] kworker/u9:1 (68) used greatest stack depth: 14768 bytes left
[    0.167738] Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    0.167798] Loaded X.509 cert 'wens: 61c038651aabdcf94bd0ac7ff06c7248db18c600'
[    0.167808] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    0.167809] cfg80211: failed to load regulatory.db
[    0.167814] ALSA device list:
[    0.167815]   No soundcards found.
[    0.315827] ata2: found unknown device (class 0)
[    0.317324] ata2.00: ATAPI: QEMU DVD-ROM, 2.5+, max UDMA/100
[    0.320177] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     2.5+ PQ: 0 ANSI: 5
[    0.339220] sr 1:0:0:0: [sr0] scsi3-mmc drive: 4x/4x cd/rw xa/form2 tray
[    0.339232] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.347038] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.347545] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.347902] md: Skipping autodetection of RAID arrays. (raid=autodetect will force)
[    0.347976] 9pnet_virtio: no channels available for device 
[    0.349450] VFS: Mounted root (9p filesystem) readonly on device 0:18.
[    0.350302] devtmpfs: mounted
[    0.351048] Freeing unused kernel image (initmem) memory: 2644K
[    0.351053] Write protecting the kernel read-only data: 26624k
[    0.351981] Freeing unused kernel image (rodata/data gap) memory: 1660K
[    0.364397] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.364406] Run /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init as init process
[    0.364407]   with arguments:
[    0.364408]     /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.364409]   with environment:
[    0.364409]     HOME=/
[    0.364410]     TERM=xterm-256color
[    0.364411]     virtme_hostname=virtme-ng
[    0.364411]     nr_open=1048576
[    0.364412]     virtme_link_mods=/home/yuan/learn_linux/linux-stable/buildq/.virtme_mods/lib/modules/0.0.0
[    0.364413]     virtme_rw_overlay0=/etc
[    0.364413]     virtme_rw_overlay1=/lib
[    0.364414]     virtme_rw_overlay2=/home
[    0.364415]     virtme_rw_overlay3=/opt
[    0.364415]     virtme_rw_overlay4=/srv
[    0.364416]     virtme_rw_overlay5=/usr
[    0.364417]     virtme_rw_overlay6=/var
[    0.364417]     virtme_rw_overlay7=/tmp
[    0.364418]     virtme_console=ttyS0
[    0.364418]     virtme_stty_con=rows 43 cols 132 iutf8
[    0.364419]     biosdevname=0
[    0.364420]     virtme_chdir=home/yuan/learn_linux/linux-stable/buildq
[    0.414415] virtme-ng-init: mount devtmpfs -> /dev: EBUSY: Device or resource busy
[    0.495996] modprobe (72) used greatest stack depth: 13600 bytes left
[    0.496279] virtme-ng-init: mount virtme_rw_overlay0 -> /etc: ENODEV: No such device
[    0.551239] virtme-ng-init: mount virtme_rw_overlay1 -> /lib: ENODEV: No such device
[    0.611729] virtme-ng-init: mount virtme_rw_overlay2 -> /home: ENODEV: No such device
[    0.658748] virtme-ng-init: mount virtme_rw_overlay3 -> /opt: ENODEV: No such device
[    0.699707] virtme-ng-init: mount virtme_rw_overlay4 -> /srv: ENODEV: No such device
[    0.726684] virtme-ng-init: mount virtme_rw_overlay5 -> /usr: ENODEV: No such device
[    0.748339] virtme-ng-init: mount virtme_rw_overlay6 -> /var: ENODEV: No such device
[    0.769398] virtme-ng-init: mount virtme_rw_overlay7 -> /tmp: ENODEV: No such device
[    0.943445] systemd-tmpfile (80) used greatest stack depth: 13400 bytes left
[    0.943456] virtme-ng-init: Failed to opendir() '/proc/self/fd/5': Permission denied
[    0.959863] ip (82) used greatest stack depth: 12880 bytes left
[    0.959955] virtme-ng-init: setting up network device eth0
[    0.962931] virtme-ng-init: Starting systemd-udevd version 255.4-1ubuntu8.2
[    0.962934] virtme-ng-init: triggering udev coldplug
[    1.920780] virtme-ng-init: waiting for udev to settle
[    2.727629] virtme-ng-init: udev is done
[    7.571086] virtme-ng-init: udhcpc: started, v1.36.1
               udhcpc: broadcasting discover
               udhcpc: broadcasting discover
               udhcpc: broadcasting discover
               udhcpc: broadcasting select for 192.168.122.76, server 192.168.122.1
               udhcpc: lease of 192.168.122.76 obtained from 192.168.122.1, lease time 3600
               mktemp: failed to create file via template '/tmp/tmp.XXXXXXXXXX': Read-only file system
               chmod: cannot access '': No such file or directory
               mount: /run/systemd/resolve/stub-resolv.conf: wrong fs type, bad option, bad superblock on , missing codepage or helper program, or other error.
                      dmesg(1) may have more information after failed mount system call.
[    7.584795] virtme-ng-init: initialization done
```