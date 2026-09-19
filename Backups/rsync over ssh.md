# rsync over SSH

This guide describes how to configure **rsync over SSH** for automated backups using:

* SSH key-based authentication
* A dedicated backup user
* `rrsync` to restrict SSH access to rsync only
* Source-IP restrictions
* A locked user password
* Normal filesystem permissions

The goal is to allow a source server to transfer backups to a backup server over SSH without providing the backup account with a normal interactive shell or arbitrary command execution.

---

# Overview

The setup consists of two servers:

```text
┌─────────────────────┐             ┌─────────────────────┐
│    Source Server    │             │    Backup Server    │
│                     │             │                     │
│  rsync              │    SSH      │  sshd               │
│  SSH client         │ ──────────► │  rrsync             │
│                     │             │  /srv/backup        │
└─────────────────────┘             └─────────────────────┘
```

The source server connects to the backup server using SSH.

The SSH public key is restricted so that the backup account can only execute `rrsync`. Direct shell access and arbitrary command execution are therefore prevented.

> **Note:** This configuration does **not** use `rsyncd` or an rsync daemon. The rsync process on the backup server is started by SSH when the source server connects.

***

## 1. Backup Server — Create the Backup User

Replace the following placeholders:

* `#USER` — backup username
* `/srv/backup` — backup directory

1.Create a dedicated user and backup directory:

```
mkdir -p /srv/backup
useradd -d /srv/backup -s /bin/bash -U #USER
chown -R #USER:#USER /srv/backup
```

2. At this stage, you can set a password temporarily for initial configuration:

```bash
passwd #USER
```

> [!IMPORTANT]
> The password will be locked later. The backup account will ultimately authenticate using the SSH key only.

***

## 2. Source Server — Generate an SSH Key

The source server must authenticate to the backup server using an SSH key.

1. Generate a dedicated key:

```bash
ssh-keygen
```

2. Copy the public key to the backup server:

```bash
ssh-copy-id #USER@BACKUP_SRV
```

***

## 3. Backup Server — Install `rrsync`

`rrsync` is a restricted wrapper for rsync over SSH.

It allows the SSH account to be used for rsync transfers without providing the remote client with unrestricted shell access.

1. If `rrsync` is not already installed, obtain it and place it at:

```text
/usr/local/bin/rrsync
```

2. Make sure it is executable:

```bash
chmod 755 /usr/local/bin/rrsync
```

You can also verify that it is executable by running:

```bash
/usr/local/bin/rrsync
```

***

## 4. Backup Server — Configure `authorized_keys`

1. Create the SSH directory and authorized_keys file:

```
mkdir -p /srv/backup/.ssh
touch /srv/backup/.ssh/authorized_keys

chown -R #USER:#USER /srv/backup/.ssh
chmod 700 /srv/backup/.ssh
chmod 600 /srv/backup/.ssh/authorized_keys
```

2. Add the source server's public key to:

```
/srv/backup/.ssh/authorized_keys
```

3. The key should be restricted using the following options:

```text
from="SOURCE_IP_ADDRESS",restrict,command="/usr/local/bin/rrsync /srv/backup" ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA...
```

For example:

```text
from="10.10.10.100",restrict,command="/usr/local/bin/rrsync /srv/backup" ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA...
```

### SSH key restrictions

| Restriction                | Purpose                                                                                                         |
| :--- | :--- |
| `from="SOURCE_IP_ADDRESS"` | Allows the key to be used only from the specified IP address                                                    |
| `restrict`                 | Disables unnecessary SSH features such as PTY allocation, agent forwarding, port forwarding, and X11 forwarding |
| `command="..."`            | Forces the connection to execute `rrsync` instead of allowing arbitrary commands                                |

Together, these restrictions significantly reduce what can be done with the SSH key if it is compromised.

***

## 5. Backup Server — Lock the User Password

Once SSH key authentication has been successfully configured and tested, lock the backup user's password:

```bash
passwd -l #USER
```

This prevents the account from being used for normal password authentication.

Verify the account status:

```bash
passwd -S #USER
```

The password should be reported as locked.

> [!IMPORTANT]
>  Test SSH key authentication before locking the password. Otherwise, you may make troubleshooting more difficult.

***

## 6. Source Server — Test the Configuration

1. Verify that the SSH key is accepted:

```bash
ssh -i ~/.ssh/backup_ed25519 #USER@#REMOTE_SERVER
```

An interactive shell should not be available.

2. Verify that arbitrary commands are rejected:

```bash
ssh -i ~/.ssh/backup_ed25519 -T #USER@#REMOTE_SERVER 'id'
```

The command should be rejected by rrsync, for example:

```text
/usr/local/bin/rrsync: SSH_ORIGINAL_COMMAND='id' is not rsync
```

3. Perform an rsync dry run:

```
rsync -av --dry-run \
    -e "ssh -i ~/.ssh/backup_ed25519" \
    /source/path/ \
    #USER@#REMOTE_SERVER:/srv/backup/
```

4. If the dry run succeeds, perform the actual transfer:

```
rsync -av \
    -e "ssh -i ~/.ssh/backup_ed25519" \
    /source/path/ \
    #USER@#REMOTE_SERVER:/srv/backup/
```

***

## 7. Security Checklist

Before putting the configuration into production, verify the following:

* [ ] A dedicated backup user is used.
* [ ] The backup user does not have root privileges.
* [ ] The backup directory is owned by the backup user.
* [ ] SSH key authentication works.
* [ ] The private key is protected.
* [ ] `rrsync` is installed and executable.
* [ ] The SSH key uses `command="/usr/local/bin/rrsync ..."`.
* [ ] The SSH key uses `restrict`.
* [ ] The SSH key uses `from="SOURCE_IP_ADDRESS"`.
* [ ] The backup user's password is locked.
* [ ] Interactive SSH access is not available.
* [ ] Arbitrary SSH commands are rejected.
* [ ] Port forwarding is disabled.
* [ ] The backup user has only the required filesystem permissions.
* [ ] An `rsync --dry-run` completes successfully.
* [ ] The actual backup transfer completes successfully.

***
