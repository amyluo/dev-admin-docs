##Show file system information: `df`
```
# human readable format, print sizes in powers of 1024 (1023M)
$ df -h

# print sizes in powers of 1000 (1.1G)
# df -s

# only listing local file systems
$ df -l

# print file system type
$ df -T
```

##Show CPU `lscpu`
```
$ lscp
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               142
Model name:          Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
Stepping:            9
CPU MHz:             800.001
CPU max MHz:         3100.0000
CPU min MHz:         400.0000
BogoMIPS:            5424.00
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            3072K
NUMA node0 CPU(s):   0-3
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp flush_l1d
```

##List hardware `lshw`
```
$ lshw
```

##Hardware Information `hwinfo`
```
$hwinfo --short
```

##Show USB devices `lsusb`
```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 06cb:00a2 Synaptics, Inc. 
Bus 001 Device 004: ID 13d3:56a6 IMC Networks 
Bus 001 Device 006: ID 0bda:b023 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

##Show PCI devices `lspci`
```
$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1d.2 PCI bridge: Intel Corporation Device 9d1a (rev f1)
00:1d.3 PCI bridge: Intel Corporation Device 9d1b (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 Non-Volatile memory controller: Lenovo Device 0003
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b822
06:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
```
##List block devices `lsblk`
```
$lsblk
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
nvme0n1               259:0    0 238.5G  0 disk  
├─nvme0n1p1           259:1    0   512M  0 part  /boot/efi
├─nvme0n1p2           259:2    0   732M  0 part  /boot
└─nvme0n1p3           259:3    0 237.3G  0 part  
  └─nvme0n1p3_crypt   253:0    0 237.3G  0 crypt 
    ├─mint--vg-root   253:1    0 229.5G  0 lvm   /
    └─mint--vg-swap_1 253:2    0   7.8G  0 lvm   [SWAP]

```

##Show input devices `xinput`
```
$ xinput
⎡ Virtual core pointer                    	id=2	[master pointer  (3)]
⎜   ↳ Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
⎜   ↳ Logitech Anywhere MX                    	id=9	[slave  pointer  (2)]
⎜   ↳ Logitech K750                           	id=10	[slave  pointer  (2)]
⎜   ↳ SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
⎜   ↳ TPPS/2 Elan TrackPoint                  	id=14	[slave  pointer  (2)]
⎣ Virtual core keyboard                   	id=3	[master keyboard (2)]
    ↳ Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    ↳ Power Button                            	id=6	[slave  keyboard (3)]
    ↳ Video Bus                               	id=7	[slave  keyboard (3)]
    ↳ Sleep Button                            	id=8	[slave  keyboard (3)]
    ↳ Integrated Camera: Integrated C         	id=11	[slave  keyboard (3)]
    ↳ AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    ↳ ThinkPad Extra Buttons                  	id=15	[slave  keyboard (3)]
    ↳ Logitech K750                           	id=16	[slave  keyboard (3)]

# show single device info
$ xinput list-props 9
Device 'Logitech Anywhere MX':
	Device Enabled (143):	1
	Coordinate Transformation Matrix (145):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Natural Scrolling Enabled (278):	0
	libinput Natural Scrolling Enabled Default (279):	0
	libinput Scroll Methods Available (280):	0, 0, 1
	libinput Scroll Method Enabled (281):	0, 0, 0
	libinput Scroll Method Enabled Default (282):	0, 0, 0
	libinput Button Scrolling Button (283):	2
	libinput Button Scrolling Button Default (284):	2
	libinput Middle Emulation Enabled (285):	0
	libinput Middle Emulation Enabled Default (286):	0
	libinput Accel Speed (287):	-1.000000
	libinput Accel Speed Default (288):	0.000000
	libinput Accel Profiles Available (289):	1, 1
	libinput Accel Profile Enabled (290):	1, 0
	libinput Accel Profile Enabled Default (291):	1, 0
	libinput Left Handed Enabled (292):	0
	libinput Left Handed Enabled Default (293):	0
	libinput Send Events Modes Available (263):	1, 0
	libinput Send Events Mode Enabled (264):	0, 0
	libinput Send Events Mode Enabled Default (265):	0, 0
	Device Node (266):	"/dev/input/event6"
	Device Product ID (267):	1133, 4119
	libinput Drag Lock Buttons (294):	<no items>
	libinput Horizontal Scroll Enabled (295):	1

# set device property
$ xinput set-prop <device> <property> <val>

# disable device
$ xinput disable <device>
# enable device
$ xinput enable <device>
```

##Check RAM `free`
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           7.6G        3.4G        384M        286M        3.8G        3.6G
Swap:          7.8G          0B        7.8G
```

##Use /proc files
```
# cpu information
$ cat /proc/cpuinfo

# memory information
$ cate /proc/meminfo

# Linux/kernel information
$ cat /proc/version

# SCSI/Sata devices
$ cat /proc/scsi/scsi

# Partitions
$ cat /proc/partitions
```

##Information about sata devices
```
$ sudo hdparm -i /dev/sda
/dev/sda:

 Model=ST3500418AS, FwRev=CC38, SerialNo=9VMJXV1N
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
```