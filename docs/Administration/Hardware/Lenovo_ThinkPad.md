##How to disable TrackPoint in Linux Mint / Ubuntu
```
$ xinput list
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
    ↳ AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    ↳ ThinkPad Extra Buttons                  	id=15	[slave  keyboard (3)]
    ↳ Logitech K750                           	id=16	[slave  keyboard (3)]
    ↳ Integrated Camera: Integrated C         	id=11	[slave  keyboard (3)]


$ xinput set-prop "TPPS/2 Elan TrackPoint" "Device Enabled" 0

# Using device id
$ xinput set-prop 14 "Device Enabled" 0

$ xinput list-props 14
Device 'TPPS/2 Elan TrackPoint':
	Device Enabled (143):	0
	Coordinate Transformation Matrix (145):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Natural Scrolling Enabled (278):	0
	libinput Natural Scrolling Enabled Default (279):	0
	libinput Scroll Methods Available (280):	0, 0, 1
	libinput Scroll Method Enabled (281):	0, 0, 1
	libinput Scroll Method Enabled Default (282):	0, 0, 1
	libinput Button Scrolling Button (283):	2
	libinput Button Scrolling Button Default (284):	2
	libinput Middle Emulation Enabled (285):	0
	libinput Middle Emulation Enabled Default (286):	0
	libinput Accel Speed (287):	1.000000
	libinput Accel Speed Default (288):	0.000000
	libinput Accel Profiles Available (289):	1, 1
	libinput Accel Profile Enabled (290):	1, 0
	libinput Accel Profile Enabled Default (291):	1, 0
	libinput Left Handed Enabled (292):	0
	libinput Left Handed Enabled Default (293):	0
	libinput Send Events Modes Available (263):	1, 0
	libinput Send Events Mode Enabled (264):	0, 0
	libinput Send Events Mode Enabled Default (265):	0, 0
	Device Node (266):	"/dev/input/event8"
	Device Product ID (267):	2, 10
	libinput Drag Lock Buttons (294):	<no items>
	libinput Horizontal Scroll Enabled (295):	1
```

##Install wireless driver for Realtek Device b822 (r8822be) on ThinkPad E580 model# 20KS-003QUS
```
# check network hardware:
$ inxi -Fx
System:    Host: N/A Kernel: 4.15.0-45-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.8.9 (Gtk 3.22.30-1ubuntu1) Distro: Linux Mint 19 Tara
Machine:   Device: laptop System: LENOVO product: 20KS003QUS v: ThinkPad E580 serial: N/A
           Mobo: LENOVO model: 20KS003QUS v: SDK0J40697 WIN serial: N/A
           UEFI: LENOVO v: R0PET42W (1.19 ) date: 06/14/2018
Battery    BAT0: charge: 45.6 Wh 96.1% condition: 47.5/45.7 Wh (104%) model: SMP 01AV447 status: N/A
CPU:       Dual core Intel Core i5-7200U (-MT-MCP-) arch: Kaby Lake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10848
           clock speeds: max: 3100 MHz 1: 2524 MHz 2: 2237 MHz 3: 2414 MHz 4: 2459 MHz
Graphics:  Card: Intel HD Graphics 620 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@59.98hz, 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           version: 4.5 Mesa 18.2.2 Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: 8c:16:45:db:13:fa
           Card-2: Realtek Device b822 driver: r8822be port: c000 bus-ID: 05:00.0
           IF: wlp5s0 state: up speed: N/A duplex: N/A mac: d8:9c:67:18:48:67
......


# install necessary software
$ sudo apt install git dkms
$ git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
$ sudo dkms add ./rtlwifi_new
$ sudo dkms install rtlwifi_new/0.6
```
Now reboot. It may requite disable Secure Boot in BIOS.
