##1. Installing Samba
```
$ sudo apt update
$ sudo apt install samba

# check installation
$ whereis samba
samba: /usr/sbin/samba /usr/lib/samba /etc/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz
```

##2. Setting up Samb
```
$ mkdir /home/<username>/sambashare/

$ sudo nano /etc/samba/smb.conf
```
At the bottom of the file, add the following lines
```
[sambashare]
    comment = Samba on Ubuntu
    path = /home/<username>/sambashare
    read only = no
    browsable = yes
```

##3. Restart Samba
```
$ sudo service smbd restart
```

##4. Setting up User Accounts and Connecting to Share
```
$ sudo smbpasswd -a <username>
```
