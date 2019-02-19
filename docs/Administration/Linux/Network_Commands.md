##Tool for enabling and disabling wireless devices `rfkill`
```
# list all
$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

# unblock device
$ rfkill unblock 4
$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
$ rfkill -h

Usage:
 rfkill [options] command [identifier ...]

Tool for enabling and disabling wireless devices.

Options:
 -J, --json             use JSON output format
 -n, --noheadings       don't print headings
 -o, --output <list>    define which output columns to use
 -r, --raw              use the raw output format

 -h, --help             display this help
 -V, --version          display version

Available output columns:
 DEVICE      kernel device name
 ID          device identifier value
 TYPE        device type name that can be used as identifier
 TYPE-DESC   device type description
 SOFT        status of software block
 HARD        status of hardware block

Commands:
 help
 event
 list   [identifier]
 block   identifier
 unblock identifier
```