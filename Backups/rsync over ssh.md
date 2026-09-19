
### [Backup Server] User and Rsync Config.

1. Create the user and group:

```
mkdir /path/to/home/dir ;
useradd -d /path/to/home/dir -s /bin/bash -U #USER ;
passwd #USER ;
chown -R #USER:#USER /path/to/home/dir ;
```

2. Edit */etc/rsync.conf*
    - `[#USER]` -> The name of the block.
    - `auth user` -> The name of the created user.
    - `uid/gid` -> The UID and the GUID.
        - <ins>Limit privileges</ins>: reduces damage if the service is compromised.
        - <ins>Control file ownership</ins>: the files will be owned by the user and group.
        - <ins>Control permissions</ins>: the deamon can read/write only what that account is allowed to access.
        - <ins>Avoid unintended root access</ins>
    - `path` -> Path to home directory.
    - `host allow` -> The IP address of the server that is allowed to connect through rsync.
    - `fake super` -> Preserve file metadata that requires root privileges.

```
[#USER]
    auth users = 
    uid = 
    gid = 
    path = 
    host allow = 
    fake super = yes
```

***
### [Source Server] SSH key and connection.

1. *Generate*, *upload*, and *test* the ssh key to remote server.
    - The server **must be accessed through SSH key**, overwise the tunnel will fail.

```
ssh-key-gen ;
ssh-copy-id #USER@#REMOTE_SERVER ;
ssh #USER@#REMOTE_SERVER ;
```

***
### [Backup Server] rrsync

A general restricted wrapper around rsync, mainly used for SSH access where you don't want the remote user to get a general shell.
This is handy cause we leave the shell for #USER as /bin/bash, and we will have to restrict it further.

1. Download it.
2. Upload it to */usr/local/bin/rrsync*, if it was not installed there.
    - This will enable the package use for any user.

***
### [Backup Server] Lock the access.

1. If the connection through ssh key is working you can lock the password for #USER.

```
passwd -l #USER
```

2. Add the below text at the begining of /path/to/home/dir.ssh/authorized_keys.

```
from="SOURCE_IP_ADDRESS",restrict,command="/usr/local/bin/rrsync /path/to/home/dir" 
```

***

### [Source Server] Test rync.

1. Check if ssh connection through to the server.

```
ssh #USER@#REMOTE_SERVER

#It should return:
PTY allocation request failed on channel 0
/usr/local/bin/rrsync: Not invoked via sshd
Use 'command="/usr/local/bin/rrsync [-ro|-wo] SUBDIR"'
	in front of lines in /cloud/backup/fabrikhome//.ssh/authorized_keys
Connection to 10.10.10.201 closed.

ssh -T #USER@#REMOTE_SERVER 'echo HELLO'
ssh fabrikhome@10.10.10.201 'id'
ssh fabrikhome@10.10.10.201 'touch /tmp/test.txt'

# Any command should return:
/usr/local/bin/rrsync: SSH_ORIGINAL_COMMAND='echo HELLO' is not rsync
```

2. Test rsync connection to backup server.

```
rsync -av --dry-run /root fabrikhome@10.10.10.201:/etc/
```
