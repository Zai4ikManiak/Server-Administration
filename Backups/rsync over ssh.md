
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


***
### [Backup Server] Lock the access.

1. If the connection through ssh key is working you can lock the password for the user.

```
passwd -l #USER
```

2. asd

***
