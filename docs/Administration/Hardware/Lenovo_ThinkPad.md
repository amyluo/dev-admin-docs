## How to disable TrackPoint in Linux Mint / Ubuntu
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