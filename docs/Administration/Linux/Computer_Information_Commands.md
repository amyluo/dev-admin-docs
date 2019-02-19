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

##Command line system information script `inxi` for console and IRC
- Using below command in most scenarios
```
$ inxi -Fx
```

- Complete help
```
$ inxi -h
inxi supports the following options. You can combine them, or list them one by one. Examples: inxi -v4 -c6 OR
inxi -bDc 6. If you start inxi with no arguments, it will show the short form.
 
The following options if used without -F, -b, or -v will show just option line(s): A, B, C, D, G, I, M, N, P, R,
S, f, i, m, n, o, p, l, u, r, s, t - you can use these alone or together to show just the line(s) you want to
see. If you use them with -v [level], -b or -F, it will show the full output for that line along with the output
for the chosen verbosity level.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Output Control Options:
-A     Audio/sound card information.
-b     Basic output, short form. Like inxi -v 2, only minus hard disk names .
-B     Battery info, shows charge, condition, plus extra information (if battery present).
-c     Color schemes. Scheme number is required. Color selectors run a color selector option prior to inxi
       starting which lets you set the config file value for the selection.
       Supported color schemes: 0-42 Example: inxi -c 11
       Color selectors for each type display (NOTE: irc and global only show safe color set):
         94  Console, out of X
         95  Terminal, running in X - like xTerm
         96  Gui IRC, running in X - like Xchat, Quassel, Konversation etc.
         97  Console IRC running in X - like irssi in xTerm
         98  Console IRC not in  X
         99  Global - Overrides/removes all settings. Setting specific removes global.
-C     CPU output, including per CPU clockspeed and max CPU speed (if available).
-d     Optical drive data (and floppy disks, if present). Same as -Dd. See also -x and -xx.
-D     Full hard Disk info, not only model, ie: /dev/sda ST380817AS 80.0GB. See also -x and -xx. Disk total used
       percentage includes swap partition size(s).
-f     All cpu flags, triggers -C. Not shown with -F to avoid spamming. ARM cpus show 'features'.
-F     Full output for inxi. Includes all Upper Case line letters, plus -s and -n. Does not show extra verbose
       options like -d -f -l -m -o -p -r -t -u -x
-G     Graphic card information (card, display server type/version, resolution, renderer, OpenGL version).
-i     Wan IP address, and shows local interfaces (requires ifconfig network tool). Same as -Nni. Not shown with
       -F for user security reasons, you shouldn't paste your local/wan IP.
-I     Information: processes, uptime, memory, irc client (or shell type), inxi version.
-l     Partition labels. Default: short partition -P. For full -p output, use: -pl (or -plu).
-m     Memory (RAM) data. Physical system memory array(s), capacity, how many devices (slots) supported, and
       individual memory devices (sticks of memory etc). For devices, shows device locator, size, speed, type
       (like: DDR3). If neither -I nor -tm are selected, also shows ram used/total. Also see -x, -xx, -xxx
-M     Machine data. Device type (desktop, server, laptop, VM etc.), Motherboard, Bios, and if present, System
       Builder (Like Lenovo). Shows UEFI/BIOS/UEFI [Legacy]. Older systems/kernels without the required /sys data
       can use dmidecode instead, run as root. Dmidecode can be forced with -! 33
-n     Advanced Network card information. Same as -Nn. Shows interface, speed, mac id, state, etc.
-N     Network card information. With -x, shows PCI BusID, Port number.
-o     Unmounted partition information (includes UUID and LABEL if available). Shows file system type if you have
       file installed, if you are root OR if you have added to /etc/sudoers (sudo v. 1.7 or newer)
       Example: <username> ALL = NOPASSWD: /usr/bin/file  
-p     Full partition information (-P plus all other detected partitions).
-P     Basic partition information (shows what -v 4 would show, but without extra data). Shows, if detected: /
       /boot /home /opt /tmp /usr /var /var/log /var/tmp . Use -p to see all mounted partitions.
-r     Distro repository data. Supported repo types: APK; APT; PACMAN; PISI; PORTAGE; PORTS (BSDs); SLACKPKG;
       URPMQ; YUM; ZYPP.
-R     RAID data. Shows RAID devices, states, levels, and components, and extra data with -x/-xx. md-raid: If
       device is resyncing, shows resync progress line as well.
-s     Sensors output (if sensors installed/configured): mobo/cpu/gpu temp; detected fan speeds. Gpu temp only
       for Fglrx/Nvidia drivers. Nvidia shows screen number for > 1 screens.
-S     System information: host name, kernel, desktop environment (if in X), distro
-t     Processes. Requires extra options: c (cpu) m (memory) cm (cpu+memory). If followed by numbers 1-20, shows
       that number of processes for each type (default: 5; if in irc, max: 5): -t cm10
       Make sure to have no space between letters and numbers (-t cm10 - right, -t cm 10 - wrong).
-u     Partition UUIDs. Default: short partition -P. For full -p output, use: -pu (or -plu).
-v     Script verbosity levels. Verbosity level number is required. Should not be used with -b or -F
       Supported levels: 0-7 Example: inxi -v 4
         0   Short output, same as: inxi
         1   Basic verbose, -S + basic CPU + -G + basic Disk + -I.
         2   Networking card (-N), Machine (-M) data, if present, Battery (-B), basic hard disk data (names
             only), and, if present, basic raid (devices only, and if inactive, notes that). similar to: inxi -b
         3   Advanced CPU (-C), battery, network (-n) data, and switches on -x advanced data option.
         4   Partition size/filled data (-P) for (if present): /, /home, /var/, /boot. Shows full disk data (-D).
         5   Audio card (-A); sensors (-s), memory/ram (-m), partition label (-l) and UUID (-u), short form of
             optical drives, standard raid data (-R).
         6   Full partition (-p), unmounted partition (-o), optical drive (-d), full raid; triggers -xx.
         7   Network IP data (-i); triggers -xxx.
-w     Local weather data/time. To check an alternate location, see: -W <location>. For extra weather data
       options see -x, -xx, and -xxx.
-W     <location> Supported options for <location>: postal code; city, state/country; latitude, longitude. Only
       use if you want the weather somewhere other than the machine running inxi. Use only ascii characters,
       replace spaces in city/state/country names with '+'. Example: inxi -W new+york,ny
-x     Adds the following extra data (only works with verbose or line output, not short form):
         -B  Vendor/model, status (if available)
         -C  CPU Flags, Bogomips on Cpu;CPU microarchitecture / revision if found, like: (Sandy Bridge rev.2)
         -d  Extra optical drive data; adds rev version to optical drive.
         -D  Hdd temp with disk data if you have hddtemp installed, if you are root OR if you have added to
             /etc/sudoers (sudo v. 1.7 or newer) Example: <username> ALL = NOPASSWD: /usr/sbin/hddtemp
         -G  Direct rendering status for Graphics (in X).
         -G  (for single gpu, nvidia driver) screen number gpu is running on.
         -i  For IPv6, show additional IP v6 scope addresses: Global, Site, Temporary, Unknown.
         -I  System GCC, default. With -xx, also show other installed GCC versions. If running in console, not in
             IRC client, shows shell version number, if detected. Init/RC Type and runlevel (if available).
         -m  Part number; Max memory module size (if available).
      -N -A  Version/port(s)/driver version (if available) for Network/Audio;
   -N -A -G  Network, audio, graphics, shows PCI Bus ID/Usb ID number of card.
         -R  md-raid: Shows component raid id. Adds second RAID Info line: raid level; report on drives (like
             5/5); blocks; chunk size; bitmap (if present). Resync line, shows blocks synced/total blocks.
             zfs-raid: Shows raid array full size; available size; portion allocated to RAID
         -S  Desktop toolkit if available (GNOME/XFCE/KDE only); Kernel gcc version
         -t  Memory use output to cpu (-xt c), and cpu use to memory (-xt m).
      -w -W  Wind speed and time zone (-w only).
-xx    Show extra, extra data (only works with verbose or line output, not short form):
         -A  Chip vendor:product ID for each audio device.
         -B  serial number, voltage (if available).
         -C  Minimum CPU speed, if available.
         -D  Disk serial number; Firmware rev. if available.
         -G  Chip vendor:product ID for each video card; (mir/wayland only) compositor (alpha test); OpenGL
             compatibility version, if free drivers and available.
         -I  Other detected installed gcc versions (if present). System default runlevel. Adds parent program (or
             tty) for shell info if not in IRC (like Konsole or Gterm). Adds Init/RC (if found) version number.
         -m  Manufacturer, Serial Number, single/double bank (if found).
         -M  Chassis information, bios rom size (dmidecode only), if data for either is available.
         -N  Chip vendor:product ID for each nic.
         -R  md-raid: Superblock (if present); algorythm, U data. Adds system info line (kernel support,read
             ahead, raid events). If present, adds unused device line. Resync line, shows progress bar.
         -S  Display manager (dm) in desktop output, if in X (like kdm, gdm3, lightdm).
      -w -W  Humidity, barometric pressure.
   -@ 11-14  Automatically uploads debugger data tar.gz file to ftp.techpatterns.com. EG: inxi -xx@14
-xxx   Show extra, extra, extra data (only works with verbose or line output, not short form):
         -B  chemistry, cycles, location (if available).
         -m  Width of memory bus, data and total (if present and greater than data); Detail, if present, for
             Type; module voltage, if available.
         -S  Panel/shell information in desktop output, if in X (like gnome-shell, cinnamon, mate-panel).
      -w -W  Location (uses -z/irc filter), weather observation time, wind chill, heat index, dew point (shows
             extra lines for data where relevant).
-y     Required extra option: integer, 80 or greater. Set the output line width max. Overrides IRC/Terminal
       settings or actual widths. If used with -h, put -y option first. Example: inxi -y 130
-z     Security filters for IP/Mac addresses, location, user home directory name. Default on for irc clients.
-Z     Absolute override for output filters. Useful for debugging networking issues in irc for example.
 
Additional Options:
-h --help      This help menu.
-H             This help menu, plus developer options. Do not use dev options in normal operation!
--recommends   Checks inxi application dependencies + recommends, and directories, then shows what package(s) you
               need to install to add support for that feature.
-V --version   inxi version information. Prints information then exits.
 
Debugging Options:
-%     Overrides defective or corrupted data.
-@     Triggers debugger output. Requires debugging level 1-14 (8-10 - logging of data). Less than 8 just
       triggers inxi debugger output on screen.
         1-7 On screen debugger output
         8   Basic logging
         9   Full file/sys info logging
         10  Color logging.
       The following create a tar.gz file of system data, plus collecting the inxi output to file. To
       automatically upload debugger data tar.gz file to ftp.techpatterns.com: inxi -xx@ <11-14>
       For alternate ftp upload locations: Example: inxi -! ftp.yourserver.com/incoming -xx@ 14
         11  With data file of tree traverse read of /sys.
         12  With xorg conf and log data, xrandr, xprop, xdpyinfo, glxinfo etc.
         13  With data from dev, disks, partitions, etc., plus /sys tree traverse data file.
         14  Everything, full data collection.
 
Advanced Options:
-! 31  Turns off hostname in output. Useful if showing output from servers etc.
-! 32  Turns on hostname in output. Overrides global B_SHOW_HOST='false'
-! 33  Forces use of dmidecode data instead of /sys where relevant (-M).
-! 34  Skips SSL certificate checks for all downloader activies (wget/fetch/curl only). Must go before other
       options. 
-! 40  Will try to get display data out of X. Default gets it from display :0. If you use this format: -! 40:1 it
       would get it from display 1 instead, or any display you specify as long as there is no space between -! 40
       and the :[display-number].
-! 41  Bypass curl as a downloader option.
-! 42  Bypass fetch as a downloader option.
-! 43  Bypass wget as a downloader option.
-! 44  Bypass curl, fetch, and wget as a downloader options. Forces Perl if HTTP::Tiny present.
```