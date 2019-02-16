##1. Configure SSH Daemon
```
$ sudo apt install ssh

$ sudo nano /etc/ssh/sshd_config
```

And append the following to the end of hte file
```
Match group sftp
ChrootDirectory /home
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp
```
Restart SSH server to apply new changes
```
$ sudo service ssh restart
```

##2. Create SFTP user account
```
$ sudo addgroup sftp
Adding group `sftp' (GID 1001) ...
Done.

$ sudo useradd -m sftpuser -g sftp

$ sudo passwd sftpuser
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

$ sudo chmod 700 /home/sftpuser/
```

##3. User login via SFTP
```
$ sftp -P 22 sftpuser@ubuntu-sftp
The authenticity of host 'ubuntu-sftp (10.1.1.4)' can't be established.
ECDSA key fingerprint is SHA256:8SSv/iz6OGaF8m0TLcJNtRSitfTm59dOVa57WnRfUx8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ubuntu-sftp' (ECDSA) to the list of known hosts.
sftpuser@ubuntu-sftp's password: 
Connected to ubuntu-sftp.

sftp>
```