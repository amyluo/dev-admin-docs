#Inotify Watches Limit
Inotify requires a "watch handle" to be set for each directory in the project. Unfortunately, the default limit of watch handles may not be enough for reasonably sized projects, and reaching the limit will force IntelliJ platform to fall back to recursive scans of directory trees.

To prevent this situation it is recommended to increase the watches limit (to, say, 512K):

##1. Add the following line to either `/etc/sysctl.conf` file or a new *.conf file (e.g. `99-jetbrains.conf`) under `/etc/sysctl.d/` directory:

```
fs.inotify.max_user_watches = 524288
```

##2. Then run this command to apply the change:

```
$ sudo sysctl -p --system
```

And don't forget to restart your IDE.

**Note:** the watches limit is per-account setting. If there are other programs running under the same account which also use Inotify the limit should be raised high enough to suit needs of all of them.
