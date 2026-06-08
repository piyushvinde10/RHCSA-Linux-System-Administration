# rsync - Remote Synchronization

## Overview

`rsync` (Remote Synchronization) is a powerful Linux utility used to synchronize files and directories between systems.

It can:

- Copy files locally
- Transfer files remotely
- Synchronize directories
- Create backups
- Preserve file permissions and ownership

Unlike `scp`, rsync transfers only the changed portions of files, making it faster and more efficient.

---

# Features of rsync

- Fast file synchronization
- Incremental transfers
- Supports local and remote transfers
- Preserves permissions and ownership
- Compression support
- Backup creation
- Resume interrupted transfers

---

# Basic Syntax

```bash
rsync [options] source destination
```

---

# Install rsync

## RHEL / CentOS / Rocky Linux

```bash
sudo yum install rsync -y
```

## Verify Installation

```bash
rsync --version
```

---

# Local File Synchronization

## Copy a File

```bash
rsync file.txt /backup/
```

Example:

```bash
rsync report.txt /backup/
```

---

## Copy a Directory

```bash
rsync -r project/ /backup/
```

---

# Remote Synchronization

## Copy Local File to Remote Server

```bash
rsync file.txt user@192.168.1.100:/home/user/
```

---

## Copy Remote File to Local System

```bash
rsync user@192.168.1.100:/home/user/file.txt .
```

---

## Synchronize Directory to Remote Server

```bash
rsync -av project/ user@192.168.1.100:/backup/
```

---

## Synchronize Directory from Remote Server

```bash
rsync -av user@192.168.1.100:/backup/project/ .
```

---

# Common Options

## Archive Mode

```bash
rsync -a source destination
```

Preserves:

- Permissions
- Ownership
- Timestamps
- Symbolic Links

---

## Verbose Output

```bash
rsync -v source destination
```

Displays detailed transfer information.

---

## Compression

```bash
rsync -z source destination
```

Compresses data during transfer.

---

## Archive + Verbose + Compression

```bash
rsync -avz source destination
```

Most commonly used option.

---

# Dry Run

Preview changes without transferring files:

```bash
rsync -av --dry-run source destination
```

Useful before large synchronizations.

---

# Delete Removed Files

```bash
rsync -av --delete source destination
```

Deletes files on destination that no longer exist in source.

---

# Use Custom SSH Port

```bash
rsync -avz -e "ssh -p 2222" source user@host:/backup/
```

---

# Create Backup

```bash
rsync -av /data/ /backup/
```

Example:

```bash
rsync -av /home/piyush/ /backup/home-backup/
```

---

# Exclude Files

Exclude log files:

```bash
rsync -av --exclude="*.log" source destination
```

---

# Exclude Multiple Files

```bash
rsync -av \
--exclude="*.log" \
--exclude="*.tmp" \
source destination
```

---

# Synchronize Using SSH

```bash
rsync -avz -e ssh project/ user@192.168.1.100:/backup/
```

---

# Verify Synchronization

Compare source and destination:

```bash
diff -r source destination
```

---

# Common Examples

## Backup Home Directory

```bash
rsync -av /home/user/ /backup/user/
```

---

## Sync Website Files

```bash
rsync -avz website/ user@server:/var/www/html/
```

---

## Sync Configuration Files

```bash
rsync -av /etc/ user@backup-server:/backup/etc/
```

---

# Troubleshooting

## Verify SSH Connectivity

```bash
ssh user@192.168.1.100
```

---

## Test Network Connectivity

```bash
ping 192.168.1.100
```

---

## Debug Transfer

```bash
rsync -avvv source destination
```

---

## Check SSH Port

```bash
ss -tulnp | grep 22
```

---

# rsync vs SCP

| Feature | rsync | SCP |
|----------|----------|----------|
| Incremental Transfer | Yes | No |
| Compression | Yes | Limited |
| Synchronization | Yes | No |
| Resume Transfer | Yes | No |
| Uses SSH | Yes | Yes |
| Backup Support | Yes | No |

---

# Security Benefits

- Uses SSH encryption
- Supports SSH key authentication
- Secure remote transfers
- Efficient bandwidth usage

---

# RHCSA Notes

Commonly used options:

```bash
rsync -avz source destination
```

Meaning:

| Option | Description |
|----------|-------------|
| a | Archive Mode |
| v | Verbose |
| z | Compression |

---

# Useful Commands

## Copy File

```bash
rsync file.txt /backup/
```

## Copy Directory

```bash
rsync -av project/ /backup/
```

## Sync to Remote Server

```bash
rsync -avz project/ user@host:/backup/
```

## Dry Run

```bash
rsync -av --dry-run source destination
```

## Delete Removed Files

```bash
rsync -av --delete source destination
```

---

# Summary

| Command | Purpose |
|----------|----------|
| rsync file dest | Copy file |
| rsync -r dir dest | Copy directory |
| rsync -av source dest | Archive mode sync |
| rsync -avz source dest | Compressed sync |
| rsync --dry-run | Preview changes |
| rsync --delete | Remove extra files |

---

# Conclusion

`rsync` is one of the most important Linux file synchronization and backup tools. It provides fast, secure, and efficient file transfers by copying only changed data. Because of its flexibility and performance, rsync is widely used for backups, server synchronization, migrations, and system administration tasks.