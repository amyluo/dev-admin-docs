## `top` displays a list of processes, with the ones using the most CPU at the top.
```
$ top
top - 19:18:50 up  7:05,  1 user,  load average: 3.29, 3.15, 2.95
Tasks: 285 total,   2 running, 218 sleeping,   0 stopped,   1 zombie
%Cpu(s): 23.3 us,  3.9 sy,  0.0 ni, 72.1 id,  0.1 wa,  0.0 hi,  0.6 si,  0.0 st
KiB Mem :  7926036 total,   234916 free,  3611080 used,  4080040 buff/cache
KiB Swap:  8142844 total,  8142844 free,        0 used.  3710668 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                        
 2034 hluo      20   0 3550056 265276  77060 R  54.1  3.3  37:54.94 cinnamon                                                                                                                                       
  989 root      20   0  550344  80488  59996 S  22.1  1.0  17:59.20 Xorg                                                                                                                                           
19689 hluo      20   0 6022744 854960  79880 S  14.9 10.8   7:44.18 java                                                                                                                                           
23603 hluo      20   0  999496 312492  45068 S   8.9  3.9   0:28.80 mintinstall                                                                                                                                    
12538 hluo      20   0  551344  63408  35788 S   2.6  0.8   0:12.57 terminator                                                                                                                                     
21272 hluo      20   0  983008 163760  85056 S   2.3  2.1   0:43.16 chrome                                                                                                                                         
  212 root      -2   0       0      0      0 S   0.7  0.0   0:23.62 i915/signal:0                                                                                                                                  
 1843 hluo      20   0 2020032  15628  13160 S   0.7  0.2   0:48.59 winedevice.exe                                                                                                                                 
21695 root      20   0       0      0      0 D   0.7  0.0   0:05.92 kworker/u8:0                                                                                                                                   
  410 root      20   0       0      0      0 S   0.3  0.0   0:01.82 jbd2/dm-1-8                                                                                                                                    
  893 root      20   0  503264  10876   8596 S   0.3  0.1   0:17.49 udisksd               
```

##The `htop` command is an improved top.
```
$ sudo apt-get install htop
```

##The `ps` command lists running processes.
```
# lists all processes running on your system
$ ps -A
```

##The `pstree` command is another way of visualizing processes. It displays them in tree format.


##The `kill` command can kill a process, given its process ID.
```
$ kill PID
```

##Given a search term, `pgrep` returns the process IDs that match it.
```
$ pgrep firefox
```

##The `pkill` and `killall` commands can kill a process, given its name. 
```
$ pkill firefox
$ killall firefox
```

##The `renice` command changes the nice value of an already running process.
```
$ renice 19 PID
```

##The `xkill` command is a way of easily killing graphical programs.
```
Select the window whose client you wish to kill with button 1....
```