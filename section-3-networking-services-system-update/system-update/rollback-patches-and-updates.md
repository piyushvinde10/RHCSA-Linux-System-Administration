# Rollback Patches and Updates

## Overview

Patch rollback is the process of reverting software updates or package changes when an update causes issues such as:

- Application failures
- System instability
- Compatibility problems
- Performance degradation

Rollback helps restore the system to a previously working state.

---

# Why Rollback Updates?

Common reasons include:

- Faulty package updates
- Failed application startup
- Kernel upgrade issues
- Dependency conflicts
- Security patch incompatibility

---

# Prerequisites

Before applying updates:

- Create system backups
- Take VM snapshots
- Record installed package versions
- Test updates in non-production environments

---

# View YUM Transaction History

Display package transaction history:

```bash
yum history
```

Example Output:

```text
ID     | Command Line
--------------------------------
15     | update
14     | install httpd
13     | update kernel
```

---

# View Transaction Details

Display detailed transaction information:

```bash
yum history info 15
```

Example:

```text
Transaction ID : 15
Packages Altered:
Updated httpd
Updated openssl
```

---

# Undo a Transaction

Rollback a specific transaction:

```bash
yum history undo 15
```

Example:

```bash
yum history undo 10
```

This reverts packages changed during transaction 10.

---

# Redo a Transaction

Reapply a transaction:

```bash
yum history redo 15
```

---

# Rollback Multiple Transactions

Rollback to a previous transaction state:

```bash
yum history rollback 10
```

This reverts all changes after transaction ID 10.

---

# Verify Installed Package Version

Check package version:

```bash
rpm -qi httpd
```

Example:

```text
Version : 2.4.57
```

---

# Downgrade a Package

Install an older package version:

```bash
yum downgrade package_name
```

Example:

```bash
yum downgrade httpd
```

---

# Install Specific Package Version

List available versions:

```bash
yum --showduplicates list httpd
```

Install version:

```bash
yum install httpd-2.4.53
```

---

# Rollback Kernel Updates

List installed kernels:

```bash
rpm -qa | grep kernel
```

Example:

```text
kernel-5.14.0-427
kernel-5.14.0-410
```

---

# Display Current Kernel

```bash
uname -r
```

---

# Select Older Kernel at Boot

1. Reboot system:

```bash
reboot
```

2. At GRUB menu select:

```text
Advanced Options
```

3. Choose older kernel version.

---

# Set Default Kernel

Display kernels:

```bash
grubby --info=ALL
```

Set default kernel:

```bash
grubby --set-default /boot/vmlinuz-5.14.0-410
```

Verify:

```bash
grubby --default-kernel
```

---

# Backup Before Patching

Backup important files:

```bash
rsync -av /etc /backup/etc
```

Backup application data:

```bash
rsync -av /var/www /backup/www
```

---

# VM Snapshot Rollback

If using VMware or VirtualBox:

1. Take snapshot before update.
2. Apply updates.
3. Restore snapshot if update fails.

Example:

```text
Snapshot Name:
Pre-Patch-Backup
```

---

# Verify Package Integrity

Check installed package:

```bash
rpm -V package_name
```

Example:

```bash
rpm -V bash
```

---

# Check Failed Services After Update

```bash
systemctl --failed
```

---

# Check System Logs

Review recent logs:

```bash
journalctl -xe
```

Check boot logs:

```bash
journalctl -b
```

---

# Troubleshooting Failed Updates

## Verify Repositories

```bash
yum repolist
```

---

## Clean Cache

```bash
yum clean all
```

---

## Rebuild Cache

```bash
yum makecache
```

---

## Verify Package Database

```bash
rpm --rebuilddb
```

---

# Best Practices

- Always take backups before updates.
- Use VM snapshots in lab environments.
- Review package changes before updating.
- Test updates in staging systems.
- Keep previous kernel versions.
- Document rollback procedures.

---

# Useful Commands

## View History

```bash
yum history
```

---

## Transaction Details

```bash
yum history info ID
```

---

## Undo Update

```bash
yum history undo ID
```

---

## Rollback Updates

```bash
yum history rollback ID
```

---

## Downgrade Package

```bash
yum downgrade package_name
```

---

## Display Current Kernel

```bash
uname -r
```

---

# Rollback Workflow

```text
Check History
      ↓
Identify Update
      ↓
Take Backup
      ↓
Rollback Transaction
      ↓
Verify Services
      ↓
Check Logs
      ↓
Confirm System Health
```

---

# RHCSA Notes

Important commands:

```bash
yum history
```

```bash
yum history undo ID
```

```bash
yum history rollback ID
```

```bash
yum downgrade package
```

```bash
uname -r
```

```bash
rpm -qa | grep kernel
```

Understanding rollback procedures is important for enterprise Linux administration and helps minimize downtime after failed updates.

---

# Summary

| Command | Purpose |
|----------|----------|
| yum history | View transaction history |
| yum history info ID | Transaction details |
| yum history undo ID | Undo transaction |
| yum history rollback ID | Rollback updates |
| yum downgrade package | Install older version |
| uname -r | Display current kernel |
| rpm -qa | List installed packages |

---

# Conclusion

Rollback Patches and Updates is an essential Linux administration skill that helps recover systems from problematic updates. Using YUM history, package downgrades, kernel selection, backups, and snapshots allows administrators to safely revert changes and restore system stability.