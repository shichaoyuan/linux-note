# 系统日志


```log
[    0.000000] Linux version 6.6.36 (yuan@yuan-t14p) (gcc (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #2 SMP PREEMPT_DYNAMIC Fri Jul  5 23:42:24 CST 2024
[    0.000000] Command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
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
[    0.000000] kvm-clock: using sched offset of 190466222 cycles
[    0.000001] clocksource: kvm-clock: mask: 0xffffffffffffffff max_cycles: 0x1cd42e4dffb, max_idle_ns: 881590591483 ns
[    0.000002] tsc: Detected 2995.200 MHz processor
[    0.000114] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000115] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000118] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000135] MTRR map: 4 entries (3 fixed + 1 variable; max 19), built from 8 variable MTRRs
[    0.000136] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000158] last_pfn = 0xbffe0 max_arch_pfn = 0x400000000
[    0.003810] found SMP MP-table at [mem 0x000f5470-0x000f547f]
[    0.003819] Using GB pages for direct mapping
[    0.003915] ACPI: Early table checksum verification disabled
[    0.003916] ACPI: RSDP 0x00000000000F5270 000014 (v00 BOCHS )
[    0.003920] ACPI: RSDT 0x00000000BFFE1E95 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003924] ACPI: FACP 0x00000000BFFE1C21 000074 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003928] ACPI: DSDT 0x00000000BFFE0040 001BE1 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003930] ACPI: FACS 0x00000000BFFE0000 000040
[    0.003931] ACPI: APIC 0x00000000BFFE1C95 000090 (v03 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003933] ACPI: HPET 0x00000000BFFE1D25 000038 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003934] ACPI: SRAT 0x00000000BFFE1D5D 000110 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003936] ACPI: WAET 0x00000000BFFE1E6D 000028 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
[    0.003937] ACPI: Reserving FACP table memory at [mem 0xbffe1c21-0xbffe1c94]
[    0.003938] ACPI: Reserving DSDT table memory at [mem 0xbffe0040-0xbffe1c20]
[    0.003938] ACPI: Reserving FACS table memory at [mem 0xbffe0000-0xbffe003f]
[    0.003938] ACPI: Reserving APIC table memory at [mem 0xbffe1c95-0xbffe1d24]
[    0.003939] ACPI: Reserving HPET table memory at [mem 0xbffe1d25-0xbffe1d5c]
[    0.003939] ACPI: Reserving SRAT table memory at [mem 0xbffe1d5d-0xbffe1e6c]
[    0.003939] ACPI: Reserving WAET table memory at [mem 0xbffe1e6d-0xbffe1e94]
[    0.003957] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.003958] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.003958] SRAT: PXM 1 -> APIC 0x02 -> Node 1
[    0.003959] SRAT: PXM 1 -> APIC 0x03 -> Node 1
[    0.003959] ACPI: SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.003960] ACPI: SRAT: Node 0 PXM 0 [mem 0x00100000-0x7fffffff]
[    0.003961] ACPI: SRAT: Node 1 PXM 1 [mem 0x80000000-0xbfffffff]
[    0.003961] ACPI: SRAT: Node 1 PXM 1 [mem 0x100000000-0x13fffffff]
[    0.003962] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0x7fffffff] -> [mem 0x00000000-0x7fffffff]
[    0.003963] NUMA: Node 1 [mem 0x80000000-0xbfffffff] + [mem 0x100000000-0x13fffffff] -> [mem 0x80000000-0x13fffffff]
[    0.003965] NODE_DATA(0) allocated [mem 0x7fffc000-0x7fffffff]
[    0.003978] NODE_DATA(1) allocated [mem 0x13fffa000-0x13fffdfff]
[    0.004003] Zone ranges:
[    0.004003]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.004004]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.004005]   Normal   [mem 0x0000000100000000-0x000000013fffffff]
[    0.004005] Movable zone start for each node
[    0.004006] Early memory node ranges
[    0.004006]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.004006]   node   0: [mem 0x0000000000100000-0x000000007fffffff]
[    0.004007]   node   1: [mem 0x0000000080000000-0x00000000bffdffff]
[    0.004007]   node   1: [mem 0x0000000100000000-0x000000013fffffff]
[    0.004008] Initmem setup node 0 [mem 0x0000000000001000-0x000000007fffffff]
[    0.004009] Initmem setup node 1 [mem 0x0000000080000000-0x000000013fffffff]
[    0.004015] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.004118] On node 0, zone DMA: 97 pages in unavailable ranges
[    0.030308] On node 1, zone Normal: 32 pages in unavailable ranges
[    0.030472] ACPI: PM-Timer IO Port: 0x608
[    0.030477] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.030501] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.030503] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.030503] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.030504] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.030505] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.030505] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.030507] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.030508] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.030512] TSC deadline timer available
[    0.030512] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.030522] kvm-guest: APIC: eoi() replaced with kvm_guest_apic_eoi_write()
[    0.030529] kvm-guest: KVM setup pv remote TLB flush
[    0.030531] kvm-guest: setup PV sched yield
[    0.030535] PM: hibernation: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.030535] PM: hibernation: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.030536] PM: hibernation: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.030536] PM: hibernation: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.030536] PM: hibernation: Registered nosave memory: [mem 0xbffe0000-0xbfffffff]
[    0.030537] PM: hibernation: Registered nosave memory: [mem 0xc0000000-0xfeffbfff]
[    0.030537] PM: hibernation: Registered nosave memory: [mem 0xfeffc000-0xfeffffff]
[    0.030537] PM: hibernation: Registered nosave memory: [mem 0xff000000-0xfffbffff]
[    0.030538] PM: hibernation: Registered nosave memory: [mem 0xfffc0000-0xffffffff]
[    0.030538] [mem 0xc0000000-0xfeffbfff] available for PCI devices
[    0.030539] Booting paravirtualized kernel on KVM
[    0.030540] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1910969940391419 ns
[    0.033760] setup_percpu: NR_CPUS:64 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:2
[    0.035395] percpu: Embedded 54 pages/cpu s183016 r8192 d29976 u1048576
[    0.035397] pcpu-alloc: s183016 r8192 d29976 u1048576 alloc=1*2097152
[    0.035398] pcpu-alloc: [0] 0 1 [1] 2 3 
[    0.035417] Kernel command line: virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 psmouse.proto=exps "virtme_stty_con=rows 43 cols 132 iutf8" TERM=xterm-256color virtme.dhcp net.ifnames=0 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq rootfstype=9p rootflags=version=9p2000.L,trans=virtio,access=any raid=noautodetect ro quiet loglevel=0 nokaslr init=/usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.035490] Unknown kernel command line parameters "virtme_hostname=virtme-ng nr_open=1048576 virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0 virtme_rw_overlay0=/etc virtme_rw_overlay1=/lib virtme_rw_overlay2=/home virtme_rw_overlay3=/opt virtme_rw_overlay4=/srv virtme_rw_overlay5=/usr virtme_rw_overlay6=/var virtme_rw_overlay7=/tmp virtme_console=ttyS0 virtme_stty_con=rows 43 cols 132 iutf8 biosdevname=0 virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq", will be passed to user space.
[    0.035499] random: crng init done
[    0.035538] Fallback order for Node 0: 0 1 
[    0.035540] Fallback order for Node 1: 1 0 
[    0.035541] Built 2 zonelists, mobility grouping on.  Total pages: 1031904
[    0.035541] Policy zone: Normal
[    0.035542] mem auto-init: stack:all(zero), heap alloc:off, heap free:off
[    0.035544] software IO TLB: area num 4.
[    0.070040] Memory: 4021152K/4193784K available (18432K kernel code, 2739K rwdata, 6532K rodata, 2644K init, 1528K bss, 172376K reserved, 0K cma-reserved)
[    0.070074] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=2
[    0.070751] Dynamic Preempt: voluntary
[    0.070781] rcu: Preemptible hierarchical RCU implementation.
[    0.070782] rcu: 	RCU event tracing is enabled.
[    0.070782] rcu: 	RCU restricting CPUs from NR_CPUS=64 to nr_cpu_ids=4.
[    0.070783] 	Trampoline variant of Tasks RCU enabled.
[    0.070783] rcu: RCU calculated value of scheduler-enlistment delay is 100 jiffies.
[    0.070784] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.071479] NR_IRQS: 4352, nr_irqs: 456, preallocated irqs: 16
[    0.071652] rcu: srcu_init: Setting srcu_struct sizes based on contention.
[    0.071734] Console: colour *CGA 80x25
[    0.071735] printk: console [tty0] enabled
[    0.071746] ACPI: Core revision 20230628
[    0.071813] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604467 ns
[    0.071866] APIC: Switch to symmetric I/O mode setup
[    0.071869] kvm-guest: APIC: send_IPI_mask() replaced with kvm_send_ipi_mask()
[    0.071873] kvm-guest: APIC: send_IPI_mask_allbutself() replaced with kvm_send_ipi_mask_allbutself()
[    0.071874] kvm-guest: setup PV IPIs
[    0.072424] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072435] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.072438] Calibrating delay loop (skipped) preset value.. 5990.40 BogoMIPS (lpj=2995200)
[    0.072505] x86/cpu: User Mode Instruction Prevention (UMIP) activated
[    0.072547] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.072548] Last level dTLB entries: 4KB 0, 2MB 0, 4MB 0, 1GB 0
[    0.072552] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.072555] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on vm exit
[    0.072556] Spectre V2 : Spectre BHI mitigation: SW BHB clearing on syscall
[    0.072556] Spectre V2 : Mitigation: Enhanced / Automatic IBRS
[    0.072556] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.072556] Spectre V2 : Spectre v2 / PBRSB-eIBRS: Retire a single CALL on VMEXIT
[    0.072558] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.072559] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl
[    0.072559] Register File Data Sampling: Vulnerable: No microcode
[    0.072570] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.072571] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.072571] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.072571] x86/fpu: Supporting XSAVE feature 0x200: 'Protection Keys User registers'
[    0.072572] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.072572] x86/fpu: xstate_offset[9]:  832, xstate_sizes[9]:    8
[    0.072573] x86/fpu: Enabled xstate features 0x207, context size is 840 bytes, using 'compacted' format.
[    0.083062] Freeing SMP alternatives memory: 48K
[    0.083064] pid_max: default: 32768 minimum: 301
[    0.083074] LSM: initializing lsm=capability,selinux,integrity
[    0.083076] SELinux:  Initializing.
[    0.084812] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes, vmalloc hugepage)
[    0.085673] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes, vmalloc)
[    0.085703] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.085731] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes, vmalloc)
[    0.086007] smpboot: CPU0: 13th Gen Intel(R) Core(TM) i9-13900H (family: 0x6, model: 0xba, stepping: 0x2)
[    0.086141] RCU Tasks: Setting shift to 2 and lim to 1 rcu_task_cb_adjust=1.
[    0.086151] Performance Events: unsupported p6 CPU model 186 no PMU driver, software events only.
[    0.086172] signal: max sigframe size: 3632
[    0.086186] rcu: Hierarchical SRCU implementation.
[    0.086187] rcu: 	Max phase no-delay instances is 400.
[    0.086348] smp: Bringing up secondary CPUs ...
[    0.086429] smpboot: x86: Booting SMP configuration:
[    0.086430] .... node  #0, CPUs:      #1
[    0.086437] .... node  #1, CPUs:   #2 #3
[    0.086511] smp: Brought up 2 nodes, 4 CPUs
[    0.086513] smpboot: Max logical packages: 1
[    0.086514] smpboot: Total of 4 processors activated (23961.60 BogoMIPS)
[    0.087535] devtmpfs: initialized
[    0.087573] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
[    0.087573] futex hash table entries: 1024 (order: 4, 65536 bytes, vmalloc)
[    0.087573] PM: RTC time: 15:07:49, date: 2024-07-10
[    0.087752] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.087804] audit: initializing netlink subsys (disabled)
[    0.087818] audit: type=2000 audit(1720624069.472:1): state=initialized audit_enabled=0 res=1
[    0.087818] thermal_sys: Registered thermal governor 'step_wise'
[    0.087818] thermal_sys: Registered thermal governor 'user_space'
[    0.087818] cpuidle: using governor menu
[    0.087818] PCI: Using configuration type 1 for base access
[    0.088466] kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
[    0.088518] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
[    0.088518] HugeTLB: 28 KiB vmemmap can be freed for a 2.00 MiB page
[    0.088675] ACPI: Added _OSI(Module Device)
[    0.088675] ACPI: Added _OSI(Processor Device)
[    0.088675] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.088675] ACPI: Added _OSI(Processor Aggregator Device)
[    0.088675] ACPI: 1 ACPI AML tables successfully acquired and loaded
[    0.091477] ACPI: _OSC evaluation for CPUs failed, trying _PDC
[    0.091510] ACPI: Interpreter enabled
[    0.091515] ACPI: PM: (supports S0 S3 S4 S5)
[    0.091515] ACPI: Using IOAPIC for interrupt routing
[    0.091520] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.091521] PCI: Using E820 reservations for host bridge windows
[    0.091555] ACPI: Enabled 2 GPEs in block 00 to 0F
[    0.092143] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.092145] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI HPX-Type3]
[    0.092146] acpi PNP0A03:00: _OSC: not requesting OS control; OS requires [ExtendedConfig ASPM ClockPM MSI]
[    0.092149] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended configuration space under this bridge
[    0.092200] PCI host bridge to bus 0000:00
[    0.092200] pci_bus 0000:00: Unknown NUMA node; performance will be reduced
[    0.092201] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.092202] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.092203] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.092203] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff window]
[    0.092204] pci_bus 0000:00: root bus resource [mem 0x380000000000-0x38007fffffff window]
[    0.092204] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.092224] pci 0000:00:00.0: [8086:1237] type 00 class 0x060000
[    0.092422] pci 0000:00:01.0: [8086:7000] type 00 class 0x060100
[    0.092684] pci 0000:00:01.1: [8086:7010] type 00 class 0x010180
[    0.093641] pci 0000:00:01.1: reg 0x20: [io  0xc060-0xc06f]
[    0.094046] pci 0000:00:01.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.094047] pci 0000:00:01.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.094047] pci 0000:00:01.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.094048] pci 0000:00:01.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.094123] pci 0000:00:01.3: [8086:7113] type 00 class 0x068000
[    0.094321] pci 0000:00:01.3: quirk: [io  0x0600-0x063f] claimed by PIIX4 ACPI
[    0.094325] pci 0000:00:01.3: quirk: [io  0x0700-0x070f] claimed by PIIX4 SMB
[    0.094482] pci 0000:00:02.0: [1af4:1009] type 00 class 0x000200
[    0.095045] pci 0000:00:02.0: reg 0x10: [io  0xc000-0xc03f]
[    0.095438] pci 0000:00:02.0: reg 0x14: [mem 0xfeb80000-0xfeb80fff]
[    0.096966] pci 0000:00:02.0: reg 0x20: [mem 0x380000000000-0x380000003fff 64bit pref]
[    0.097815] pci 0000:00:03.0: [8086:25ab] type 00 class 0x088000
[    0.098076] pci 0000:00:03.0: reg 0x10: [mem 0xfeb81000-0xfeb8100f]
[    0.100655] pci 0000:00:04.0: [1af4:1000] type 00 class 0x020000
[    0.100988] pci 0000:00:04.0: reg 0x10: [io  0xc040-0xc05f]
[    0.101312] pci 0000:00:04.0: reg 0x14: [mem 0xfeb82000-0xfeb82fff]
[    0.102309] pci 0000:00:04.0: reg 0x20: [mem 0x380000004000-0x380000007fff 64bit pref]
[    0.102619] pci 0000:00:04.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.103091] ACPI: PCI: Interrupt link LNKA configured for IRQ 10
[    0.103125] ACPI: PCI: Interrupt link LNKB configured for IRQ 10
[    0.103154] ACPI: PCI: Interrupt link LNKC configured for IRQ 11
[    0.103193] ACPI: PCI: Interrupt link LNKD configured for IRQ 11
[    0.103228] ACPI: PCI: Interrupt link LNKS configured for IRQ 9
[    0.103337] iommu: Default domain type: Translated
[    0.103338] iommu: DMA domain TLB invalidation policy: lazy mode
[    0.103377] SCSI subsystem initialized
[    0.103445] libata version 3.00 loaded.
[    0.103452] ACPI: bus type USB registered
[    0.103452] usbcore: registered new interface driver usbfs
[    0.103452] usbcore: registered new interface driver hub
[    0.103452] usbcore: registered new device driver usb
[    0.103453] pps_core: LinuxPPS API ver. 1 registered
[    0.103454] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.103455] PTP clock support registered
[    0.103471] Advanced Linux Sound Architecture Driver Initialized.
[    0.103606] NetLabel: Initializing
[    0.103607] NetLabel:  domain hash size = 128
[    0.103607] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.103614] NetLabel:  unlabeled traffic allowed by default
[    0.103636] PCI: Using ACPI for IRQ routing
[    0.103636] PCI: pci_cache_line_size set to 64 bytes
[    0.103689] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.103690] e820: reserve RAM buffer [mem 0xbffe0000-0xbfffffff]
[    0.103700] vgaarb: loaded
[    0.103723] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.103725] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.106626] clocksource: Switched to clocksource kvm-clock
[    0.106726] VFS: Disk quotas dquot_6.6.0
[    0.106736] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.106762] pnp: PnP ACPI init
[    0.106805] pnp 00:02: [dma 2]
[    0.106882] pnp: PnP ACPI: found 5 devices
[    0.111762] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.111774] NET: Registered PF_INET protocol family
[    0.112006] IP idents hash table entries: 65536 (order: 7, 524288 bytes, vmalloc)
[    0.112390] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes, vmalloc)
[    0.112409] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, vmalloc)
[    0.112411] TCP established hash table entries: 32768 (order: 6, 262144 bytes, vmalloc)
[    0.112530] TCP bind hash table entries: 32768 (order: 8, 1048576 bytes, vmalloc)
[    0.112969] TCP: Hash tables configured (established 32768 bind 32768)
[    0.113028] UDP hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.113058] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes, vmalloc)
[    0.113107] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    0.113229] RPC: Registered named UNIX socket transport module.
[    0.113230] RPC: Registered udp transport module.
[    0.113230] RPC: Registered tcp transport module.
[    0.113231] RPC: Registered tcp-with-tls transport module.
[    0.113231] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    0.113429] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.113430] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.113430] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.113431] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff window]
[    0.113432] pci_bus 0000:00: resource 8 [mem 0x380000000000-0x38007fffffff window]
[    0.113444] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.113449] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.113476] PCI: CLS 0 bytes, default 64
[    0.113505] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.113505] software IO TLB: mapped [mem 0x00000000bbfe0000-0x00000000bffe0000] (64MB)
[    0.116408] RAPL PMU: API unit is 2^-32 Joules, 0 fixed counters, 10737418240 ms ovfl timer
[    0.116416] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b2c8ec87c7, max_idle_ns: 440795278598 ns
[    0.134555] Initialise system trusted keyrings
[    0.134824] workingset: timestamp_bits=56 max_order=20 bucket_order=0
[    0.135114] NFS: Registering the id_resolver key type
[    0.135121] Key type id_resolver registered
[    0.135121] Key type id_legacy registered
[    0.135145] 9p: Installing v9fs 9p2000 file system support
[    0.139404] Key type asymmetric registered
[    0.139405] Asymmetric key parser 'x509' registered
[    0.139414] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.139424] io scheduler mq-deadline registered
[    0.139424] io scheduler kyber registered
[    0.139926] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.140109] ACPI: button: Power Button [PWRF]
[    0.150302] ACPI: \_SB_.LNKB: Enabled at IRQ 10
[    0.158730] ACPI: \_SB_.LNKD: Enabled at IRQ 11
[    0.159268] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.159370] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.159595] Non-volatile memory driver v1.3
[    0.159596] Linux agpgart interface v0.103
[    0.159625] ACPI: bus type drm_connector registered
[    0.161208] loop: module loaded
[    0.161253] ata_piix 0000:00:01.1: version 2.13
[    0.161802] scsi host0: ata_piix
[    0.162188] scsi host1: ata_piix
[    0.162215] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc060 irq 14
[    0.162216] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc068 irq 15
[    0.163314] e100: Intel(R) PRO/100 Network Driver
[    0.163315] e100: Copyright(c) 1999-2006 Intel Corporation
[    0.163318] e1000: Intel(R) PRO/1000 Network Driver
[    0.163319] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    0.163321] e1000e: Intel(R) PRO/1000 Network Driver
[    0.163322] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.163324] sky2: driver version 1.30
[    0.163381] usbcore: registered new interface driver usblp
[    0.163383] usbcore: registered new interface driver usb-storage
[    0.163398] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.163869] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.163871] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.163948] rtc_cmos 00:04: RTC can wake from S4
[    0.164351] rtc_cmos 00:04: registered as rtc0
[    0.164406] rtc_cmos 00:04: alarms up to one day, y3k, 242 bytes nvram, hpet irqs
[    0.164462] device-mapper: ioctl: 4.48.0-ioctl (2023-03-01) initialised: dm-devel@redhat.com
[    0.164465] intel_pstate: CPU model not supported
[    0.164473] hid: raw HID events driver (C) Jiri Kosina
[    0.164537] usbcore: registered new interface driver usbhid
[    0.164537] usbhid: USB HID core driver
[    0.164664] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.165401] Initializing XFRM netlink socket
[    0.165409] NET: Registered PF_INET6 protocol family
[    0.165693] Segment Routing with IPv6
[    0.165705] In-situ OAM (IOAM) with IPv6
[    0.165720] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    0.165816] NET: Registered PF_PACKET protocol family
[    0.165831] 9pnet: Installing 9P2000 support
[    0.166223] Key type dns_resolver registered
[    0.166887] IPI shorthand broadcast: enabled
[    0.168366] sched_clock: Marking stable (168003170, -219210)->(168899243, -1115283)
[    0.168586] registered taskstats version 1
[    0.168590] Loading compiled-in X.509 certificates
[    0.168704] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[    0.169772] PM:   Magic number: 0:413:133
[    0.169797] acpi device:08: hash matches
[    0.169802] printk: console [netcon0] enabled
[    0.169803] netconsole: network logging started
[    0.169830] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    0.170272] kworker/u10:3 (66) used greatest stack depth: 14384 bytes left
[    0.170683] Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    0.170775] Loaded X.509 cert 'wens: 61c038651aabdcf94bd0ac7ff06c7248db18c600'
[    0.170794] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    0.170796] cfg80211: failed to load regulatory.db
[    0.170805] ALSA device list:
[    0.170806]   No soundcards found.
[    0.320362] ata2: found unknown device (class 0)
[    0.321774] ata2.00: ATAPI: QEMU DVD-ROM, 2.5+, max UDMA/100
[    0.325261] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     2.5+ PQ: 0 ANSI: 5
[    0.347190] sr 1:0:0:0: [sr0] scsi3-mmc drive: 4x/4x cd/rw xa/form2 tray
[    0.347200] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.355534] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.355899] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.356309] md: Skipping autodetection of RAID arrays. (raid=autodetect will force)
[    0.356404] 9pnet_virtio: no channels available for device 
[    0.358679] VFS: Mounted root (9p filesystem) readonly on device 0:18.
[    0.359512] devtmpfs: mounted
[    0.360202] Freeing unused kernel image (initmem) memory: 2644K
[    0.360207] Write protecting the kernel read-only data: 26624k
[    0.361257] Freeing unused kernel image (rodata/data gap) memory: 1660K
[    0.372992] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.373001] Run /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init as init process
[    0.373002]   with arguments:
[    0.373003]     /usr/lib/python3/dist-packages/virtme/guest/bin/virtme-ng-init
[    0.373004]   with environment:
[    0.373005]     HOME=/
[    0.373006]     TERM=xterm-256color
[    0.373006]     virtme_hostname=virtme-ng
[    0.373007]     nr_open=1048576
[    0.373008]     virtme_link_mods=/home/yuan/learn_linux/linux-6.6.36/buildq/.virtme_mods/lib/modules/0.0.0
[    0.373009]     virtme_rw_overlay0=/etc
[    0.373010]     virtme_rw_overlay1=/lib
[    0.373010]     virtme_rw_overlay2=/home
[    0.373011]     virtme_rw_overlay3=/opt
[    0.373012]     virtme_rw_overlay4=/srv
[    0.373012]     virtme_rw_overlay5=/usr
[    0.373013]     virtme_rw_overlay6=/var
[    0.373014]     virtme_rw_overlay7=/tmp
[    0.373015]     virtme_console=ttyS0
[    0.373015]     virtme_stty_con=rows 43 cols 132 iutf8
[    0.373016]     biosdevname=0
[    0.373017]     virtme_chdir=home/yuan/learn_linux/linux-6.6.36/buildq
[    0.410908] virtme-ng-init: mount devtmpfs -> /dev: EBUSY: Device or resource busy
[    0.470423] modprobe (74) used greatest stack depth: 13600 bytes left
[    0.470557] virtme-ng-init: mount virtme_rw_overlay0 -> /etc: ENODEV: No such device
[    0.519778] virtme-ng-init: mount virtme_rw_overlay1 -> /lib: ENODEV: No such device
[    0.566207] virtme-ng-init: mount virtme_rw_overlay2 -> /home: ENODEV: No such device
[    0.630409] virtme-ng-init: mount virtme_rw_overlay3 -> /opt: ENODEV: No such device
[    0.690487] virtme-ng-init: mount virtme_rw_overlay4 -> /srv: ENODEV: No such device
[    0.734853] virtme-ng-init: mount virtme_rw_overlay5 -> /usr: ENODEV: No such device
[    0.784164] virtme-ng-init: mount virtme_rw_overlay6 -> /var: ENODEV: No such device
[    0.822635] virtme-ng-init: mount virtme_rw_overlay7 -> /tmp: ENODEV: No such device
[    1.058439] systemd-tmpfile (82) used greatest stack depth: 13400 bytes left
[    1.058510] virtme-ng-init: Failed to opendir() '/proc/self/fd/5': Permission denied
[    1.074340] ip (84) used greatest stack depth: 12672 bytes left
[    1.074413] virtme-ng-init: setting up network device eth0
[    1.078702] virtme-ng-init: Starting systemd-udevd version 255.4-1ubuntu8.1
[    1.078705] virtme-ng-init: triggering udev coldplug
[    1.804914] virtme-ng-init: waiting for udev to settle
[    2.521835] virtme-ng-init: udev is done
[    7.740995] virtme-ng-init: udhcpc: started, v1.36.1
               udhcpc: broadcasting discover
               udhcpc: broadcasting discover
               udhcpc: broadcasting discover
               udhcpc: broadcasting select for 192.168.122.76, server 192.168.122.1
               udhcpc: lease of 192.168.122.76 obtained from 192.168.122.1, lease time 3600
               mktemp: failed to create file via template '/tmp/tmp.XXXXXXXXXX': Read-only file system
               chmod: cannot access '': No such file or directory
               mount: /run/systemd/resolve/stub-resolv.conf: wrong fs type, bad option, bad superblock on , missing codepage or helper program, or other error.
                      dmesg(1) may have more information after failed mount system call.
[    7.763107] virtme-ng-init: initialization done

```