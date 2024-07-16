# 系统日志


```log
[    0.000000] Linux version 6.6.36 (yuan@yuan-t14p) (gcc (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #8 SMP PREEMPT_DYNAMIC Tue Jul 16 23:26:16 CST 2024
[    0.000000] Command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 memblock=debug nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
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
[    0.000000] kvm-clock: using sched offset of 197425080 cycles
[    0.000001] clocksource: kvm-clock: mask: 0xffffffffffffffff max_cycles: 0x1cd42e4dffb, max_idle_ns: 881590591483 ns
[    0.000002] tsc: Detected 2995.200 MHz processor
[    0.000118] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000119] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000139] MTRR map: 4 entries (3 fixed + 1 variable; max 19), built from 8 variable MTRRs
[    0.000141] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.003814] found SMP MP-table at [mem 0x000f5470-0x000f547f]
[    0.003815] memblock_reserve: [0x00000000000f5470-0x00000000000f547f] smp_scan_config+0xc5/0x150
[    0.003819] memblock_reserve: [0x00000000000f5480-0x00000000000f5557] smp_scan_config+0x135/0x150
[    0.003822] memblock_reserve: [0x0000000003600000-0x0000000003608fff] setup_arch+0xd94/0xf80
[    0.003824] memblock_add: [0x0000000000001000-0x000000000009fbff] e820__memblock_setup+0x6e/0xb0
[    0.003826] memblock_add: [0x0000000000100000-0x00000000bffdffff] e820__memblock_setup+0x6e/0xb0
[    0.003827] memblock_add: [0x0000000100000000-0x000000013fffffff] e820__memblock_setup+0x6e/0xb0
[    0.003829] MEMBLOCK configuration:
[    0.003829]  memory size = 0x00000000fff7ec00 reserved size = 0x000000000267a000
[    0.003829]  memory.cnt  = 0x3
[    0.003830]  memory[0x0]	[0x0000000000001000-0x000000000009efff], 0x000000000009e000 bytes flags: 0x0
[    0.003831]  memory[0x1]	[0x0000000000100000-0x00000000bffdffff], 0x00000000bfee0000 bytes flags: 0x0
[    0.003831]  memory[0x2]	[0x0000000100000000-0x000000013fffffff], 0x0000000040000000 bytes flags: 0x0
[    0.003832]  reserved.cnt  = 0x3
[    0.003832]  reserved[0x0]	[0x0000000000000000-0x000000000000ffff], 0x0000000000010000 bytes flags: 0x0
[    0.003833]  reserved[0x1]	[0x000000000009f000-0x00000000000fffff], 0x0000000000061000 bytes flags: 0x0
[    0.003833]  reserved[0x2]	[0x0000000001000000-0x0000000003608fff], 0x0000000002609000 bytes flags: 0x0
[    0.003834] memblock_phys_alloc_range: 28672 bytes align=0x1000 from=0x0000000000000000 max_addr=0x0000000000100000 reserve_real_mode+0x52/0x90
[    0.003836] memblock_reserve: [0x0000000000098000-0x000000000009efff] memblock_alloc_range_nid+0xdc/0x150
[    0.003837] memblock_reserve: [0x0000000000000000-0x00000000000fffff] setup_arch+0x74e/0xf80
[    0.003843] Using GB pages for direct mapping
[    0.003856] memblock_phys_alloc_range: 2097152 bytes align=0x200000 from=0x0000000000100000 max_addr=0x0000000140000000 init_mem_mapping+0x1a8/0x340
[    0.003858] memblock_reserve: [0x000000013fe00000-0x000000013fffffff] memblock_alloc_range_nid+0xdc/0x150
[    0.003859] memblock_phys_free: [0x000000013fe00000-0x000000013fffffff] init_mem_mapping+0x1b8/0x340
[    0.003903] memblock_phys_alloc_range: 4096 bytes align=0x1000 from=0x0000000120000000 max_addr=0x0000000140000000 alloc_low_pages+0x91/0x150
[    0.003904] memblock_reserve: [0x000000013ffff000-0x000000013fffffff] memblock_alloc_range_nid+0xdc/0x150
[    0.003931] memblock_phys_alloc_range: 4096 bytes align=0x1000 from=0x0000000120000000 max_addr=0x0000000140000000 alloc_low_pages+0x91/0x150
[    0.003932] memblock_reserve: [0x000000013fffe000-0x000000013fffefff] memblock_alloc_range_nid+0xdc/0x150
[    0.003953] ACPI: Early table checksum verification disabled
[    0.003955] ACPI: RSDP 0x00000000000F5270 000014 (v00 BOCHS )
[    0.003959] ACPI: RSDT 0x00000000BFFE1E95 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003975] ACPI: FACP 0x00000000BFFE1C21 000074 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003979] ACPI: DSDT 0x00000000BFFE0040 001BE1 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003981] ACPI: FACS 0x00000000BFFE0000 000040
[    0.003982] ACPI: APIC 0x00000000BFFE1C95 000090 (v03 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003984] ACPI: HPET 0x00000000BFFE1D25 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003985] ACPI: SRAT 0x00000000BFFE1D5D 000110 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003987] ACPI: WAET 0x00000000BFFE1E6D 000028 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003988] ACPI: Reserving FACP table memory at [mem 0xbffe1c21-0xbffe1c94]
[    0.003989] memblock_reserve: [0x00000000bffe1c21-0x00000000bffe1c94] acpi_reserve_initial_tables+0x45/0x70
[    0.003990] ACPI: Reserving DSDT table memory at [mem 0xbffe0040-0xbffe1c20]
[    0.003991] memblock_reserve: [0x00000000bffe0040-0x00000000bffe1c20] acpi_reserve_initial_tables+0x45/0x70
[    0.003992] ACPI: Reserving FACS table memory at [mem 0xbffe0000-0xbffe003f]
[    0.003992] memblock_reserve: [0x00000000bffe0000-0x00000000bffe003f] acpi_reserve_initial_tables+0x45/0x70
[    0.003993] ACPI: Reserving APIC table memory at [mem 0xbffe1c95-0xbffe1d24]
[    0.003993] memblock_reserve: [0x00000000bffe1c95-0x00000000bffe1d24] acpi_reserve_initial_tables+0x45/0x70
[    0.003994] ACPI: Reserving HPET table memory at [mem 0xbffe1d25-0xbffe1d5c]
[    0.003995] memblock_reserve: [0x00000000bffe1d25-0x00000000bffe1d5c] acpi_reserve_initial_tables+0x45/0x70
[    0.003996] ACPI: Reserving SRAT table memory at [mem 0xbffe1d5d-0xbffe1e6c]
[    0.003996] memblock_reserve: [0x00000000bffe1d5d-0x00000000bffe1e6c] acpi_reserve_initial_tables+0x45/0x70
[    0.003997] ACPI: Reserving WAET table memory at [mem 0xbffe1e6d-0xbffe1e94]
[    0.003997] memblock_reserve: [0x00000000bffe1e6d-0x00000000bffe1e94] acpi_reserve_initial_tables+0x45/0x70
[    0.004015] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.004016] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.004016] SRAT: PXM 1 -> APIC 0x02 -> Node 1
[    0.004016] SRAT: PXM 1 -> APIC 0x03 -> Node 1
[    0.004017] ACPI: SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.004018] ACPI: SRAT: Node 0 PXM 0 [mem 0x00100000-0x7fffffff]
[    0.004019] ACPI: SRAT: Node 1 PXM 1 [mem 0x80000000-0xbfffffff]
[    0.004019] ACPI: SRAT: Node 1 PXM 1 [mem 0x100000000-0x13fffffff]
[    0.004020] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0x7fffffff] -> [mem 0x00000000-0x7fffffff]
[    0.004021] NUMA: Node 1 [mem 0x80000000-0xbfffffff] + [mem 0x100000000-0x13fffffff] -> [mem 0x80000000-0x13fffffff]
[    0.004022] memblock_reserve: [0x000000007fffc000-0x000000007fffffff] memblock_alloc_range_nid+0xdc/0x150
[    0.004024] NODE_DATA(0) allocated [mem 0x7fffc000-0x7fffffff]
[    0.004038] memblock_reserve: [0x000000013fffa000-0x000000013fffdfff] memblock_alloc_range_nid+0xdc/0x150
[    0.004039] NODE_DATA(1) allocated [mem 0x13fffa000-0x13fffdfff]
[    0.004046] MEMBLOCK configuration:
[    0.004047]  memory size = 0x00000000fff7ec00 reserved size = 0x0000000002714e95
[    0.004051]  memory.cnt  = 0x4
[    0.004052]  memory[0x0]	[0x0000000000001000-0x000000000009efff], 0x000000000009e000 bytes on node 0 flags: 0x0
[    0.004053]  memory[0x1]	[0x0000000000100000-0x000000007fffffff], 0x000000007ff00000 bytes on node 0 flags: 0x0
[    0.004053]  memory[0x2]	[0x0000000080000000-0x00000000bffdffff], 0x000000003ffe0000 bytes on node 1 flags: 0x0
[    0.004054]  memory[0x3]	[0x0000000100000000-0x000000013fffffff], 0x0000000040000000 bytes on node 1 flags: 0x0
[    0.004054]  reserved.cnt  = 0x6
[    0.004055]  reserved[0x0]	[0x0000000000000000-0x00000000000fffff], 0x0000000000100000 bytes on node 0 flags: 0x0
[    0.004055]  reserved[0x1]	[0x0000000001000000-0x0000000003608fff], 0x0000000002609000 bytes on node 0 flags: 0x0
[    0.004056]  reserved[0x2]	[0x000000007fffc000-0x000000007fffffff], 0x0000000000004000 bytes flags: 0x0
[    0.004056]  reserved[0x3]	[0x00000000bffe0000-0x00000000bffe1e94], 0x0000000000001e95 bytes on node 1 flags: 0x0
[    0.004057]  reserved[0x4]	[0x000000013fffa000-0x000000013fffdfff], 0x0000000000004000 bytes flags: 0x0
[    0.004057]  reserved[0x5]	[0x000000013fffe000-0x000000013fffffff], 0x0000000000002000 bytes on node 1 flags: 0x0
[    0.004060] memblock_alloc_try_nid: 16384 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init+0x3f8/0x490
[    0.004061] memblock_reserve: [0x000000013fff6000-0x000000013fff9fff] memblock_alloc_range_nid+0xdc/0x150
[    0.004069] memblock_alloc_try_nid: 4096 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_index_alloc+0x3b/0x60
[    0.004071] memblock_reserve: [0x000000007fffb000-0x000000007fffbfff] memblock_alloc_range_nid+0xdc/0x150
[    0.004074] memblock_alloc_try_nid: 896 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init_nid+0x45/0x390
[    0.004075] memblock_reserve: [0x000000007fffac80-0x000000007fffafff] memblock_alloc_range_nid+0xdc/0x150
[    0.004078] memblock_alloc_exact_nid_raw: 33554432 bytes align=0x200000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 sparse_init_nid+0x9f/0x390
[    0.004079] memblock_reserve: [0x000000007de00000-0x000000007fdfffff] memblock_alloc_range_nid+0xdc/0x150
[    0.004081] memblock_alloc_try_nid_raw: 4096 bytes align=0x1000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 vmemmap_p4d_populate+0x5d/0xf0
[    0.004082] memblock_reserve: [0x000000007fff9000-0x000000007fff9fff] memblock_alloc_range_nid+0xdc/0x150
[    0.004085] memblock_alloc_try_nid_raw: 4096 bytes align=0x1000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 vmemmap_pud_populate+0x4a/0xd0
[    0.004086] memblock_reserve: [0x000000007fff8000-0x000000007fff8fff] memblock_alloc_range_nid+0xdc/0x150
[    0.004090] memblock_alloc_try_nid: 896 bytes align=0x40 nid=0 from=0x0000000000000000 max_addr=0x0000000000000000 sparse_init_nid+0x45/0x390
[    0.004091] memblock_reserve: [0x000000007fffa900-0x000000007fffac7f] memblock_alloc_range_nid+0xdc/0x150
[    0.004092] memblock_alloc_exact_nid_raw: 33554432 bytes align=0x200000 nid=1 from=0x0000000001000000 max_addr=0x0000000000000000 sparse_init_nid+0x9f/0x390
[    0.004093] memblock_reserve: [0x000000013de00000-0x000000013fdfffff] memblock_alloc_range_nid+0xdc/0x150
[    0.004095] Zone ranges:
[    0.004095]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.004096]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.004097]   Normal   [mem 0x0000000100000000-0x000000013fffffff]
[    0.004097] Movable zone start for each node
[    0.004097] Early memory node ranges
[    0.004098]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.004098]   node   0: [mem 0x0000000000100000-0x000000007fffffff]
[    0.004099]   node   1: [mem 0x0000000080000000-0x00000000bffdffff]
[    0.004099]   node   1: [mem 0x0000000100000000-0x000000013fffffff]
[    0.004100] Initmem setup node 0 [mem 0x0000000000001000-0x000000007fffffff]
[    0.004101] Initmem setup node 1 [mem 0x0000000080000000-0x000000013fffffff]
[    0.004108] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.004211] On node 0, zone DMA: 97 pages in unavailable ranges
[    0.032769] On node 1, zone Normal: 32 pages in unavailable ranges
[    0.032937] ACPI: PM-Timer IO Port: 0x608
[    0.032941] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.032965] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.032966] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.032967] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.032968] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.032968] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.032969] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.032971] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.032972] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.032972] memblock_alloc_try_nid: 73 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 acpi_parse_hpet+0x90/0x150
[    0.032976] memblock_reserve: [0x000000013fff5f80-0x000000013fff5fc8] memblock_alloc_range_nid+0xdc/0x150
[    0.032982] TSC deadline timer available
[    0.032982] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.032983] memblock_alloc_try_nid: 75 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 io_apic_init_mappings+0x42/0x210
[    0.032985] memblock_reserve: [0x000000013fff5f00-0x000000013fff5f4a] memblock_alloc_range_nid+0xdc/0x150
[    0.032994] kvm-guest: APIC: eoi() replaced with kvm_guest_apic_eoi_write()
[    0.033002] kvm-guest: KVM setup pv remote TLB flush
[    0.033003] kvm-guest: setup PV sched yield
[    0.033004] memblock_alloc_try_nid: 576 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 e820__reserve_resources+0x2d/0x200
[    0.033007] memblock_reserve: [0x000000013fff5cc0-0x000000013fff5eff] memblock_alloc_range_nid+0xdc/0x150
[    0.033009] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033011] memblock_reserve: [0x000000013fff5c40-0x000000013fff5ca7] memblock_alloc_range_nid+0xdc/0x150
[    0.033012] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033014] memblock_reserve: [0x000000013fff5bc0-0x000000013fff5c27] memblock_alloc_range_nid+0xdc/0x150
[    0.033015] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033016] memblock_reserve: [0x000000013fff5b40-0x000000013fff5ba7] memblock_alloc_range_nid+0xdc/0x150
[    0.033018] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033019] memblock_reserve: [0x000000013fff5ac0-0x000000013fff5b27] memblock_alloc_range_nid+0xdc/0x150
[    0.033020] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033022] memblock_reserve: [0x000000013fff5a40-0x000000013fff5aa7] memblock_alloc_range_nid+0xdc/0x150
[    0.033023] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033024] memblock_reserve: [0x000000013fff59c0-0x000000013fff5a27] memblock_alloc_range_nid+0xdc/0x150
[    0.033026] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033027] memblock_reserve: [0x000000013fff5940-0x000000013fff59a7] memblock_alloc_range_nid+0xdc/0x150
[    0.033028] memblock_alloc_try_nid: 104 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 firmware_map_add_early+0x2c/0xc0
[    0.033030] memblock_reserve: [0x000000013fff58c0-0x000000013fff5927] memblock_alloc_range_nid+0xdc/0x150
[    0.033035] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.033037] memblock_reserve: [0x000000013fff5880-0x000000013fff589f] memblock_alloc_range_nid+0xdc/0x150
[    0.033038] PM: hibernation: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.033039] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.033041] memblock_reserve: [0x000000013fff5840-0x000000013fff585f] memblock_alloc_range_nid+0xdc/0x150
[    0.033042] PM: hibernation: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.033042] PM: hibernation: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.033043] PM: hibernation: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.033043] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 register_nosave_region+0x4a/0xc0
[    0.033045] memblock_reserve: [0x000000013fff5800-0x000000013fff581f] memblock_alloc_range_nid+0xdc/0x150
[    0.033046] PM: hibernation: Registered nosave memory: [mem 0xbffe0000-0xbfffffff]
[    0.033046] PM: hibernation: Registered nosave memory: [mem 0xc0000000-0xfeffbfff]
[    0.033046] PM: hibernation: Registered nosave memory: [mem 0xfeffc000-0xfeffffff]
[    0.033047] PM: hibernation: Registered nosave memory: [mem 0xff000000-0xfffbffff]
[    0.033047] PM: hibernation: Registered nosave memory: [mem 0xfffc0000-0xffffffff]
[    0.033048] [mem 0xc0000000-0xfeffbfff] available for PCI devices
[    0.033048] Booting paravirtualized kernel on KVM
[    0.033049] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1910969940391419 ns
[    0.036572] memblock_alloc_try_nid: 716 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0xbb/0x690
[    0.036575] memblock_reserve: [0x000000013fff5500-0x000000013fff57cb] memblock_alloc_range_nid+0xdc/0x150
[    0.036577] memblock_alloc_try_nid: 716 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0xee/0x690
[    0.036579] memblock_reserve: [0x000000013fff5200-0x000000013fff54cb] memblock_alloc_range_nid+0xdc/0x150
[    0.036581] setup_percpu: NR_CPUS:64 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:2
[    0.036582] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_build_alloc_info+0x20f/0x520
[    0.036583] memblock_reserve: [0x000000013fff4000-0x000000013fff4fff] memblock_alloc_range_nid+0xdc/0x150
[    0.036590] memblock_alloc_try_nid: 4096 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0x71/0x610
[    0.036591] memblock_reserve: [0x000000013fff3000-0x000000013fff3fff] memblock_alloc_range_nid+0xdc/0x150
[    0.036595] memblock_alloc_try_nid: 2097152 bytes align=0x200000 nid=0 from=0x0000000001000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0xfd/0x610
[    0.036596] memblock_reserve: [0x000000007dc00000-0x000000007ddfffff] memblock_alloc_range_nid+0xdc/0x150
[    0.037477] memblock_alloc_try_nid: 2097152 bytes align=0x200000 nid=1 from=0x0000000001000000 max_addr=0x0000000000000000 pcpu_embed_first_chunk+0xfd/0x610
[    0.037480] memblock_reserve: [0x000000013dc00000-0x000000013ddfffff] memblock_alloc_range_nid+0xdc/0x150
[    0.038459] memblock_phys_free: [0x000000007dc36000-0x000000007dcfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.038471] memblock_phys_free: [0x000000007dd36000-0x000000007ddfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.038478] memblock_phys_free: [0x000000013dc36000-0x000000013dcfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.038484] memblock_phys_free: [0x000000013dd36000-0x000000013ddfffff] pcpu_embed_first_chunk+0x1d8/0x610
[    0.038486] percpu: Embedded 54 pages/cpu s183016 r8192 d29976 u1048576
[    0.038487] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0xc2/0x8a0
[    0.038489] memblock_reserve: [0x000000013fff51c0-0x000000013fff51cf] memblock_alloc_range_nid+0xdc/0x150
[    0.038490] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0xed/0x8a0
[    0.038491] memblock_reserve: [0x000000013fff5180-0x000000013fff518f] memblock_alloc_range_nid+0xdc/0x150
[    0.038493] memblock_alloc_try_nid: 16 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x11b/0x8a0
[    0.038494] memblock_reserve: [0x000000013fff5140-0x000000013fff514f] memblock_alloc_range_nid+0xdc/0x150
[    0.038496] memblock_alloc_try_nid: 32 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x14a/0x8a0
[    0.038497] memblock_reserve: [0x000000013fff5100-0x000000013fff511f] memblock_alloc_range_nid+0xdc/0x150
[    0.038499] pcpu-alloc: s183016 r8192 d29976 u1048576 alloc=1*2097152
[    0.038500] pcpu-alloc: [0] 0 1 [1] 2 3 
[    0.038502] memblock_alloc_try_nid: 352 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_setup_first_chunk+0x5de/0x8a0
[    0.038503] memblock_reserve: [0x000000013fff2e80-0x000000013fff2fdf] memblock_alloc_range_nid+0xdc/0x150
[    0.038510] memblock_alloc_try_nid: 136 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x76/0x270
[    0.038511] memblock_reserve: [0x000000013fff5040-0x000000013fff50c7] memblock_alloc_range_nid+0xdc/0x150
[    0.038513] memblock_alloc_try_nid: 384 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0xd6/0x270
[    0.038514] memblock_reserve: [0x000000013fff2d00-0x000000013fff2e7f] memblock_alloc_range_nid+0xdc/0x150
[    0.038516] memblock_alloc_try_nid: 392 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x105/0x270
[    0.038517] memblock_reserve: [0x000000013fff2b40-0x000000013fff2cc7] memblock_alloc_range_nid+0xdc/0x150
[    0.038519] memblock_alloc_try_nid: 96 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x131/0x270
[    0.038520] memblock_reserve: [0x000000013fff2ac0-0x000000013fff2b1f] memblock_alloc_range_nid+0xdc/0x150
[    0.038523] memblock_alloc_try_nid: 136 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x76/0x270
[    0.038524] memblock_reserve: [0x000000013fff2a00-0x000000013fff2a87] memblock_alloc_range_nid+0xdc/0x150
[    0.038526] memblock_alloc_try_nid: 1024 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0xd6/0x270
[    0.038527] memblock_reserve: [0x000000013fff2600-0x000000013fff29ff] memblock_alloc_range_nid+0xdc/0x150
[    0.038528] memblock_alloc_try_nid: 1032 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x105/0x270
[    0.038530] memblock_reserve: [0x000000013fff21c0-0x000000013fff25c7] memblock_alloc_range_nid+0xdc/0x150
[    0.038531] memblock_alloc_try_nid: 256 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 pcpu_alloc_first_chunk+0x131/0x270
[    0.038533] memblock_reserve: [0x000000013fff20c0-0x000000013fff21bf] memblock_alloc_range_nid+0xdc/0x150
[    0.038534] memblock_phys_free: [0x000000013fff4000-0x000000013fff4fff] pcpu_embed_first_chunk+0x284/0x610
[    0.038536] memblock_phys_free: [0x000000013fff3000-0x000000013fff3fff] pcpu_embed_first_chunk+0x291/0x610
[    0.038549] Kernel command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 memblock=debug nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.038629] memblock_alloc_try_nid: 456 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 start_kernel+0x495/0x690
[    0.038631] memblock_reserve: [0x000000013fff4e40-0x000000013fff5007] memblock_alloc_range_nid+0xdc/0x150
[    0.038634] Unknown kernel command line parameters "virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 virtme_stty_con=rows 43 cols 132 iutf8 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq", will be passed to user space.
[    0.038634] memblock_phys_free: [0x000000013fff4e40-0x000000013fff5007] start_kernel+0x525/0x690
[    0.038644] random: crng init done
[    0.038646] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.038648] memblock_reserve: [0x000000013fff4000-0x000000013fff4fff] memblock_alloc_range_nid+0xdc/0x150
[    0.038650] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.038651] memblock_reserve: [0x000000013fff3000-0x000000013fff3fff] memblock_alloc_range_nid+0xdc/0x150
[    0.038653] memblock_alloc_try_nid: 4096 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 spp_getpage+0x3e/0x70
[    0.038654] memblock_reserve: [0x000000013fff1000-0x000000013fff1fff] memblock_alloc_range_nid+0xdc/0x150
[    0.038695] Fallback order for Node 0: 0 1 
[    0.038696] Fallback order for Node 1: 1 0 
[    0.038697] Built 2 zonelists, mobility grouping on.  Total pages: 1031904
[    0.038698] Policy zone: Normal
[    0.038699] mem auto-init: stack:all(zero), heap alloc:off, heap free:off
[    0.038701] software IO TLB: area num 4.
[    0.038702] memblock_alloc_try_nid: 67108864 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x00000000ffffffff swiotlb_init_remap+0xd1/0x2f0
[    0.038704] memblock_reserve: [0x00000000bbfe0000-0x00000000bffdffff] memblock_alloc_range_nid+0xdc/0x150
[    0.067911] memblock_alloc_try_nid: 786432 bytes align=0x1000 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 swiotlb_init_remap+0x148/0x2f0
[    0.067914] memblock_reserve: [0x000000013ff31000-0x000000013fff0fff] memblock_alloc_range_nid+0xdc/0x150
[    0.068319] memblock_alloc_try_nid: 64 bytes align=0x40 nid=-1 from=0x0000000000000000 max_addr=0x0000000000000000 swiotlb_init_remap+0x172/0x2f0
[    0.068321] memblock_reserve: [0x000000013fff5000-0x000000013fff503f] memblock_alloc_range_nid+0xdc/0x150
[    0.076934] Memory: 4021152K/4193784K available (18432K kernel code, 2739K rwdata, 6532K rodata, 2644K init, 1528K bss, 172376K reserved, 0K cma-reserved)
[    0.076975] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=2
[    0.077687] Dynamic Preempt: voluntary
[    0.077740] rcu: Preemptible hierarchical RCU implementation.
[    0.077740] rcu: 	RCU event tracing is enabled.
[    0.077740] rcu: 	RCU restricting CPUs from NR_CPUS=64 to nr_cpu_ids=4.
[    0.077741] 	Trampoline variant of Tasks RCU enabled.
[    0.077742] rcu: RCU calculated value of scheduler-enlistment delay is 100 jiffies.
[    0.077742] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.078513] NR_IRQS: 4352, nr_irqs: 456, preallocated irqs: 16
[    0.078684] rcu: srcu_init: Setting srcu_struct sizes based on contention.
[    0.078762] Console: colour *CGA 80x25
[    0.078764] printk: console [tty0] enabled
[    0.078781] ACPI: Core revision 20230628
[    0.078848] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604467 ns
[    0.078907] APIC: Switch to symmetric I/O mode setup
[    0.078910] kvm-guest: APIC: send_IPI_mask() replaced with kvm_send_ipi_mask()
[    0.078934] kvm-guest: APIC: send_IPI_mask_allbutself() replaced with kvm_send_ipi_mask_allbutself()
[    0.078935] kvm-guest: setup PV IPIs
[    0.079526] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079537] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.079540] Calibrating delay loop (skipped) preset value.. 5990.40 BogoMIPS (lpj=2995200)
[    0.079608] x86/cpu: User Mode Instruction Prevention (UMIP) activated
[    0.079650] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.079651] Last level dTLB entries: 4KB 0, 2MB 0, 4MB 0, 1GB 0
[    0.079654] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.079658] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on vm exit
[    0.079658] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on syscall
[    0.079658] Spectre V2 : Mitigation: Enhanced / Automatic IBRS
[    0.079659] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.079659] Spectre V2 : Spectre v2 / PBRSB-eIBRS: Retire a single CALL on VMEXIT
[    0.079660] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.079662] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl
[    0.079662] Register File Data Sampling: Vulnerable: No microcode
[    0.079673] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.079674] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.079674] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.079675] x86/fpu: Supporting XSAVE feature 0x200: 'Protection Keys User registers'
[    0.079675] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.079676] x86/fpu: xstate_offset[9]:  832, xstate_sizes[9]:    8
[    0.079676] x86/fpu: Enabled xstate features 0x207, context size is 840 bytes, using 'compacted' format.
[    0.091140] Freeing SMP alternatives memory: 48K
[    0.091142] pid_max: default: 32768 minimum: 301
[    0.091152] LSM: initializing lsm=capability,selinux,integrity
[    0.091155] SELinux:  Initializing.
[    0.092955] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes, vmalloc hugepage)
[    0.093913] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes, vmalloc)
[    0.093943] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.093971] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.094215] smpboot: CPU0: 13th Gen Intel(R) Core(TM) i9-13900H (family: 0x6, model: 0xba, stepping: 0x2)
[    0.094353] RCU Tasks: Setting shift to 2 and lim to 1 rcu_task_cb_adjust=1.
[    0.094363] Performance Events: unsupported p6 CPU model 186 no PMU driver, software events only.
[    0.094385] signal: max sigframe size: 3632
[    0.094423] rcu: Hierarchical SRCU implementation.
[    0.094423] rcu: 	Max phase no-delay instances is 400.
[    0.094538] smp: Bringing up secondary CPUs ...
[    0.094538] smpboot: x86: Booting SMP configuration:
[    0.094538] .... node  #0, CPUs:      #1
[    0.094538] .... node  #1, CPUs:   #2 #3
[    0.095556] smp: Brought up 2 nodes, 4 CPUs
[    0.095557] smpboot: Max logical packages: 1
[    0.095557] smpboot: Total of 4 processors activated (23961.60 BogoMIPS)
[    0.095732] devtmpfs: initialized
[    0.095732] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
[    0.095732] futex hash table entries: 1024 (order: 4, 65536 bytes, vmalloc)
[    0.095732] PM: RTC time: 15:38:07, date: 2024-07-16
[    0.095781] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.095833] audit: initializing netlink subsys (disabled)
[    0.095847] audit: type=2000 audit(1721144288.237:1): state=initialized audit_enabled=0 res=1
[    0.095847] thermal_sys: Registered thermal governor 'step_wise'
[    0.095847] thermal_sys: Registered thermal governor 'user_space'
[    0.095847] cpuidle: using governor menu
[    0.096583] PCI: Using configuration type 1 for base access
[    0.096684] kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
[    0.096731] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
[    0.096731] HugeTLB: 28 KiB vmemmap can be freed for a 2.00 MiB page
[    0.096731] ACPI: Added _OSI(Module Device)
[    0.096731] ACPI: Added _OSI(Processor Device)
[    0.096731] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096731] ACPI: Added _OSI(Processor Aggregator Device)
[    0.096947] ACPI: 1 ACPI AML tables successfully acquired and loaded
[    0.099570] ACPI: _OSC evaluation for CPUs failed, trying _PDC
[    0.099631] ACPI: Interpreter enabled
[    0.099638] ACPI: PM: (supports S0 S3 S4 S5)
[    0.099639] ACPI: Using IOAPIC for interrupt routing
[    0.099646] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.099646] PCI: Using E820 reservations for host bridge windows
[    0.099697] ACPI: Enabled 2 GPEs in block 00 to 0F
[    0.100440] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.100443] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI HPX-Type3]
[    0.100444] acpi PNP0A03:00: _OSC: not requesting OS control; OS requires [ExtendedConfig ASPM ClockPM MSI]
[    0.100448] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended configuration space under this bridge
[    0.100493] PCI host bridge to bus 0000:00
[    0.100494] pci_bus 0000:00: Unknown NUMA node; performance will be reduced
[    0.100494] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.100495] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.100496] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.100496] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff window]
[    0.100497] pci_bus 0000:00: root bus resource [mem 0x380000000000-0x38007fffffff window]
[    0.100497] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.100518] pci 0000:00:00.0: [8086:1237] type 00 class 0x060000
[    0.100723] pci 0000:00:01.0: [8086:7000] type 00 class 0x060100
[    0.100986] pci 0000:00:01.1: [8086:7010] type 00 class 0x010180
[    0.102078] pci 0000:00:01.1: reg 0x20: [io  0xc060-0xc06f]
[    0.102504] pci 0000:00:01.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.102505] pci 0000:00:01.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.102505] pci 0000:00:01.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.102506] pci 0000:00:01.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.102583] pci 0000:00:01.3: [8086:7113] type 00 class 0x068000
[    0.102785] pci 0000:00:01.3: quirk: [io  0x0600-0x063f] claimed by PIIX4 ACPI
[    0.102789] pci 0000:00:01.3: quirk: [io  0x0700-0x070f] claimed by PIIX4 SMB
[    0.102959] pci 0000:00:02.0: [1af4:1009] type 00 class 0x000200
[    0.103540] pci 0000:00:02.0: reg 0x10: [io  0xc000-0xc03f]
[    0.104129] pci 0000:00:02.0: reg 0x14: [mem 0xfeb80000-0xfeb80fff]
[    0.105540] pci 0000:00:02.0: reg 0x20: [mem 0x380000000000-0x380000003fff 64bit pref]
[    0.106511] pci 0000:00:03.0: [8086:25ab] type 00 class 0x088000
[    0.106750] pci 0000:00:03.0: reg 0x10: [mem 0xfeb81000-0xfeb8100f]
[    0.110024] pci 0000:00:04.0: [1af4:1000] type 00 class 0x020000
[    0.110384] pci 0000:00:04.0: reg 0x10: [io  0xc040-0xc05f]
[    0.110744] pci 0000:00:04.0: reg 0x14: [mem 0xfeb82000-0xfeb82fff]
[    0.111745] pci 0000:00:04.0: reg 0x20: [mem 0x380000004000-0x380000007fff 64bit pref]
[    0.112187] pci 0000:00:04.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.112738] ACPI: PCI: Interrupt link LNKA configured for IRQ 10
[    0.112774] ACPI: PCI: Interrupt link LNKB configured for IRQ 10
[    0.112805] ACPI: PCI: Interrupt link LNKC configured for IRQ 11
[    0.112834] ACPI: PCI: Interrupt link LNKD configured for IRQ 11
[    0.112852] ACPI: PCI: Interrupt link LNKS configured for IRQ 9
[    0.112965] iommu: Default domain type: Translated
[    0.112966] iommu: DMA domain TLB invalidation policy: lazy mode
[    0.113006] SCSI subsystem initialized
[    0.113040] libata version 3.00 loaded.
[    0.113040] ACPI: bus type USB registered
[    0.113040] usbcore: registered new interface driver usbfs
[    0.113040] usbcore: registered new interface driver hub
[    0.113040] usbcore: registered new device driver usb
[    0.113040] pps_core: LinuxPPS API ver. 1 registered
[    0.113040] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.113040] PTP clock support registered
[    0.113556] Advanced Linux Sound Architecture Driver Initialized.
[    0.113753] NetLabel: Initializing
[    0.113753] NetLabel:  domain hash size = 128
[    0.113754] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.113764] NetLabel:  unlabeled traffic allowed by default
[    0.113791] PCI: Using ACPI for IRQ routing
[    0.113791] PCI: pci_cache_line_size set to 64 bytes
[    0.113791] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.113791] e820: reserve RAM buffer [mem 0xbffe0000-0xbfffffff]
[    0.113791] vgaarb: loaded
[    0.113791] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.113791] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.117138] clocksource: Switched to clocksource kvm-clock
[    0.117263] VFS: Disk quotas dquot_6.6.0
[    0.117268] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.117307] pnp: PnP ACPI init
[    0.117354] pnp 00:02: [dma 2]
[    0.117450] pnp: PnP ACPI: found 5 devices
[    0.124814] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.124877] NET: Registered PF_INET protocol family
[    0.125353] IP idents hash table entries: 65536 (order: 7, 524288 bytes, vmalloc)
[    0.125963] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes, vmalloc)
[    0.125995] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, vmalloc)
[    0.125998] TCP established hash table entries: 32768 (order: 6, 262144 bytes, vmalloc)
[    0.126219] TCP bind hash table entries: 32768 (order: 8, 1048576 bytes, vmalloc)
[    0.127035] TCP: Hash tables configured (established 32768 bind 32768)
[    0.127154] UDP hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.127207] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.127286] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    0.127490] RPC: Registered named UNIX socket transport module.
[    0.127491] RPC: Registered udp transport module.
[    0.127492] RPC: Registered tcp transport module.
[    0.127492] RPC: Registered tcp-with-tls transport module.
[    0.127493] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    0.127917] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.127920] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.127921] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.127922] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff window]
[    0.127923] pci_bus 0000:00: resource 8 [mem 0x380000000000-0x38007fffffff window]
[    0.127949] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.127958] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.128013] PCI: CLS 0 bytes, default 64
[    0.128054] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.128054] software IO TLB: mapped [mem 0x00000000bbfe0000-0x00000000bffe0000] (64MB)
[    0.131609] RAPL PMU: API unit is 2^-32 Joules, 0 fixed counters, 10737418240 ms ovfl timer
[    0.131624] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.145153] Initialise system trusted keyrings
[    0.145478] workingset: timestamp_bits=56 max_order=20 bucket_order=0
[    0.145801] NFS: Registering the id_resolver key type
[    0.145805] Key type id_resolver registered
[    0.145806] Key type id_legacy registered
[    0.145836] 9p: Installing v9fs 9p2000 file system support
[    0.151488] Key type asymmetric registered
[    0.151489] Asymmetric key parser 'x509' registered
[    0.151522] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.151528] io scheduler mq-deadline registered
[    0.151528] io scheduler kyber registered
[    0.151952] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.152126] ACPI: button: Power Button [PWRF]
[    0.157944] ACPI: \_SB_.LNKB: Enabled at IRQ 10
[    0.164938] ACPI: \_SB_.LNKD: Enabled at IRQ 11
[    0.165590] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.165729] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.165994] Non-volatile memory driver v1.3
[    0.165995] Linux agpgart interface v0.103
[    0.166033] ACPI: bus type drm_connector registered
[    0.167872] loop: module loaded
[    0.167926] ata_piix 0000:00:01.1: version 2.13
[    0.168598] scsi host0: ata_piix
[    0.168843] scsi host1: ata_piix
[    0.168880] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc060 irq 14
[    0.168881] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc068 irq 15
[    0.171267] e100: Intel(R) PRO/100 Network Driver
[    0.171269] e100: Copyright(c) 1999-2006 Intel Corporation
[    0.171274] e1000: Intel(R) PRO/1000 Network Driver
[    0.171274] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    0.171279] e1000e: Intel(R) PRO/1000 Network Driver
[    0.171279] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.171284] sky2: driver version 1.30
[    0.171390] usbcore: registered new interface driver usblp
[    0.171394] usbcore: registered new interface driver usb-storage
[    0.171418] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.172113] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.172116] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.172205] rtc_cmos 00:04: RTC can wake from S4
[    0.172685] rtc_cmos 00:04: registered as rtc0
[    0.172794] rtc_cmos 00:04: alarms up to one day, y3k, 242 bytes nvram, hpet irqs
[    0.172991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.173073] device-mapper: ioctl: 4.48.0-ioctl (2023-03-01) initialised: dm-devel@redhat.com
[    0.173082] intel_pstate: CPU model not supported
[    0.173091] hid: raw HID events driver (C) Jiri Kosina
[    0.173181] usbcore: registered new interface driver usbhid
[    0.173182] usbhid: USB HID core driver
[    0.174390] Initializing XFRM netlink socket
[    0.174406] NET: Registered PF_INET6 protocol family
[    0.174966] Segment Routing with IPv6
[    0.174970] In-situ OAM (IOAM) with IPv6
[    0.175006] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    0.175110] NET: Registered PF_PACKET protocol family
[    0.175134] 9pnet: Installing 9P2000 support
[    0.175917] Key type dns_resolver registered
[    0.176447] IPI shorthand broadcast: enabled
[    0.178566] sched_clock: Marking stable (178001979, -149230)->(178101806, -249057)
[    0.178957] registered taskstats version 1
[    0.178959] Loading compiled-in X.509 certificates
[    0.179487] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[    0.180778] PM:   Magic number: 0:381:639
[    0.180800] printk: console [netcon0] enabled
[    0.180801] netconsole: network logging started
[    0.180838] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    0.181014] kworker/u10:3 (67) used greatest stack depth: 14232 bytes left
[    0.181259] Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    0.181364] Loaded X.509 cert 'wens: 61c038651aabdcf94bd0ac7ff06c7248db18c600'
[    0.181375] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    0.181377] cfg80211: failed to load regulatory.db
[    0.181386] ALSA device list:
[    0.181387]   No soundcards found.
[    0.326542] ata2: found unknown device (class 0)
[    0.327499] ata2.00: ATAPI: QEMU DVD-ROM, 2.5+, max UDMA/100
[    0.329562] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     2.5+ PQ: 0 ANSI: 5
[    0.349256] sr 1:0:0:0: [sr0] scsi3-mmc drive: 4x/4x cd/rw xa/form2 tray
[    0.349274] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.357347] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.357920] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.358247] md: Skipping autodetection of RAID arrays. (raid=autodetect will force)
[    0.358375] 9pnet_virtio: no channels available for device 
[    0.360354] VFS: Mounted root (9p filesystem) readonly on device 0:18.
[    0.360693] devtmpfs: mounted
[    0.361366] Freeing unused kernel image (initmem) memory: 2644K
[    0.361371] Write protecting the kernel read-only data: 26624k
[    0.362493] Freeing unused kernel image (rodata/data gap) memory: 1660K
[    0.373711] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.373719] Run /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init as init process
[    0.373720]   with arguments:
[    0.373721]     /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.373722]   with environment:
[    0.373723]     HOME=/
[    0.373724]     TERM=xterm-256color
[    0.373724]     virtme_hostname=virtme-ng
[    0.373725]     nr_open=1048576
[    0.373726]     virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0
[    0.373727]     virtme_rw_overlay0=/etc
[    0.373727]     virtme_rw_overlay1=/lib
[    0.373728]     virtme_rw_overlay2=/home
[    0.373729]     virtme_rw_overlay3=/opt
[    0.373729]     virtme_rw_overlay4=/srv
[    0.373730]     virtme_rw_overlay5=/usr
[    0.373731]     virtme_rw_overlay6=/var
[    0.373731]     virtme_rw_overlay7=/tmp
[    0.373732]     virtme_console=ttyS0
[    0.373733]     virtme_stty_con=rows 43 cols 132 iutf8
[    0.373733]     biosdevname=0
[    0.373734]     virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq
[    0.392885] virtme-ng-init: mount devtmpfs -> /dev: EBUSY: Device or resource busy
[    0.456324] modprobe (73) used greatest stack depth: 13600 bytes left
[    0.456689] virtme-ng-init: mount virtme_rw_overlay0 -> /etc: ENODEV: No such device
[    0.507074] virtme-ng-init: mount virtme_rw_overlay1 -> /lib: ENODEV: No such device
[    0.549659] virtme-ng-init: mount virtme_rw_overlay2 -> /home: ENODEV: No such device
[    0.580631] virtme-ng-init: mount virtme_rw_overlay3 -> /opt: ENODEV: No such device
[    0.614931] virtme-ng-init: mount virtme_rw_overlay4 -> /srv: ENODEV: No such device
[    0.641971] virtme-ng-init: mount virtme_rw_overlay5 -> /usr: ENODEV: No such device
[    0.665083] virtme-ng-init: mount virtme_rw_overlay6 -> /var: ENODEV: No such device
[    0.685209] virtme-ng-init: mount virtme_rw_overlay7 -> /tmp: ENODEV: No such device
[    0.791624] systemd-tmpfile (81) used greatest stack depth: 13400 bytes left
[    0.791660] virtme-ng-init: Failed to opendir() '/proc/self/fd/5': Permission denied
[    0.797581] ip (83) used greatest stack depth: 12672 bytes left
[    0.797699] virtme-ng-init: setting up network device eth0
[    0.807590] virtme-ng-init: Starting systemd-udevd version 255.4-1ubuntu8.1
[    0.807593] virtme-ng-init: triggering udev coldplug
[    1.277186] virtme-ng-init: waiting for udev to settle
[    1.946666] virtme-ng-init: udev is done
[    4.331875] virtme-ng-init: udhcpc: started, v1.36.1
               udhcpc: broadcasting discover
               udhcpc: broadcasting discover
               udhcpc: broadcasting select for 192.168.122.76, server 192.168.122.1
               udhcpc: lease of 192.168.122.76 obtained from 192.168.122.1, lease time 3600
               mktemp: failed to create file via template '/tmp/tmp.XXXXXXXXXX': Read-only file system
               chmod: cannot access '': No such file or directory
               mount: /run/systemd/resolve/stub-resolv.conf: wrong fs type, bad option, bad superblock on , missing codepage or helper program, or other error.
                      dmesg(1) may have more information after failed mount system call.
[    4.349661] virtme-ng-init: initialization done
```