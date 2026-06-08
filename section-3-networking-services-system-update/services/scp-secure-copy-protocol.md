# SCP - Secure Copy Protocol

## Overview

SCP (Secure Copy Protocol) is a command-line utility used to securely transfer files and directories between Linux systems.

SCP uses SSH (Secure Shell) for authentication and encryption, making it a secure alternative to FTP.

---

# What is SCP?

SCP stands for **Secure Copy Protocol**.

It allows users to:

- Copy files from local to remote systems
- Copy files from remote to local systems
- Copy files between remote systems
- Transfer directories securely

SCP uses SSH encryption during file transfer.

---

# SCP Architecture

```text
Local Machine
      |
      | SSH (Port 22)
      |
      v
Remote Machine
```

All data transferred using SCP is encrypted.

---

# Default Port

```text
22/TCP
```

SCP uses the same port as SSH.

---

# Prerequisites

Before using SCP:

- SSH server must be running on the remote host.
- User account must exist on the remote host.
- Network connectivity must be available.

Verify SSH service:

```bash
systemctl status sshd
```

---

# Basic Syntax

```bash
scp [options] source destination
```

---

# Copy File from Local to Remote

```bash
scp file.txt user@192.168.1.100:/home/user
```

Example:

```bash
scp report.txt root@192.168.1.100:/root
```

---

# Copy File from Remote to Local

```bash
scp user@192.168.1.100:/home/user/file.txt .
```

Example:

```bash
scp root@192.168.1.100:/root/report.txt .
```

---

# Copy Directory from Local to Remote

Use `-r` option:

```bash
scp -r project/ user@192.168.1.100:/home/user
```

---

# Copy Directory from Remote to Local

```bash
scp -r user@192.168.1.100:/home/user/project .
```

---

# Copy Between Two Remote Servers

```bash
scp user1@server1:/tmp/file.txt user2@server2:/tmp
```

---

# Specify Custom SSH Port

If SSH uses a custom port:

```bash
scp -P 2222 file.txt user@192.168.1.100:/home/user
```

> Note: SCP uses uppercase `-P` for port.

---

# Preserve File Permissions

Use `-p` option:

```bash
scp -p file.txt user@192.168.1.100:/home/user
```

Preserves:

- File permissions
- Modification time
- Access time

---

# Enable Compression

Use `-C` option:

```bash
scp -C largefile.iso user@192.168.1.100:/tmp
```

Useful for large file transfers.

---

# Limit Transfer Speed

```bash
scp -l 1000 file.txt user@192.168.1.100:/tmp
```

Limits bandwidth usage.

---

# Verbose Mode

Display detailed transfer information:

```bash
scp -v file.txt user@192.168.1.100:/tmp
```

---

# Common Examples

## Transfer Log File

```bash
scp /var/log/messages user@192.168.1.100:/tmp
```

---

## Transfer Backup Directory

```bash
scp -r backup/ user@192.168.1.100:/backup
```

---

## Download Configuration File

```bash
scp user@192.168.1.100:/etc/hosts .
```

---

# Verify SSH Connectivity

Before SCP transfer:

```bash
ssh user@192.168.1.100
```

If SSH works, SCP should also work.

---

# Common Troubleshooting

## Check SSH Service

```bash
systemctl status sshd
```

---

## Verify Port 22

```bash
ss -tulnp | grep 22
```

---

## Test Connectivity

```bash
ping 192.168.1.100
```

---

## Check Firewall

```bash
firewall-cmd --list-services
```

Verify SSH service is allowed.

---

## Debug SCP Transfer

```bash
scp -v file.txt user@192.168.1.100:/tmp
```

---

# SCP vs FTP vs SFTP

| Feature | SCP | FTP | SFTP |
|----------|----------|----------|----------|
| Encryption | Yes | No | Yes |
| Port | 22 | 21 | 22 |
| Uses SSH | Yes | No | Yes |
| Secure | Yes | No | Yes |
| Directory Transfer | Yes | Yes | Yes |

---

# Security Benefits

- Encrypted communication
- Secure authentication
- No plain-text passwords
- Uses SSH infrastructure
- Supports SSH key authentication

---

# Useful Commands

## Upload File

```bash
scp file.txt user@host:/destination
```

---

## Download File

```bash
scp user@host:/source/file.txt .
```

---

## Upload Directory

```bash
scp -r directory user@host:/destination
```

---

## Custom Port

```bash
scp -P 2222 file.txt user@host:/destination
```

---

## Verbose Mode

```bash
scp -v file.txt user@host:/destination
```

---

# RHCSA Notes

SCP is commonly used by Linux administrators to:

- Transfer configuration files
- Copy backups
- Move log files
- Deploy application files
- Transfer scripts securely

Understanding SCP is important for RHCSA and real-world Linux administration.

---

# Summary

| Command | Purpose |
|----------|----------|
| scp file user@host:/path | Upload file |
| scp user@host:/file . | Download file |
| scp -r directory user@host:/path | Upload directory |
| scp -P 2222 file user@host:/path | Use custom port |
| scp -v file user@host:/path | Verbose mode |

---

# Conclusion

SCP (Secure Copy Protocol) is a secure and reliable method for transferring files between Linux systems. It uses SSH encryption, making it much safer than FTP. SCP is widely used in system administration, automation, DevOps, and RHCSA environments.