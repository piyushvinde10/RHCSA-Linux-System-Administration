# System Upgrade and Patch Management

## Overview

System Upgrade and Patch Management are critical Linux administration tasks used to keep systems secure, stable, and up to date.

Regular updates help:

- Fix security vulnerabilities
- Improve system performance
- Resolve software bugs
- Add new features
- Maintain compliance and stability

In Red Hat-based systems, upgrades and patches are commonly managed using:

- RPM
- YUM
- DNF

---

# What is a Patch?

A patch is a software update released by a vendor to fix:

- Security issues
- Software bugs
- Performance problems
- Compatibility issues

Example:

```text
Kernel Security Patch
OpenSSL Vulnerability Fix
Apache Bug Fix
```

---

# What is a System Upgrade?

A system upgrade updates installed packages or the operating system to newer versions.

Types:

- Package Upgrade
- Minor Release Upgrade
- Major Release Upgrade

---

# Importance of Patch Management

Benefits include:

- Improved security
- Better performance
- Reduced downtime
- Compliance with organizational policies
- Protection against vulnerabilities

---

# Check Current OS Version

```bash
cat /etc/redhat-release
```

or

```bash
hostnamectl
```

---

# Check Installed Kernel Version

```bash
uname -r
```

Example:

```text
5.14.0-427.el9.x86_64
```

---

# Check Available Updates

Using YUM:

```bash
yum check-update
```

Using DNF:

```bash
dnf check-update
```

---

# List Installed Packages

```bash
rpm -qa
```

---

# Update a Specific Package

Using YUM:

```bash
sudo yum update httpd
```

Using DNF:

```bash
sudo dnf update httpd
```

---

# Update All Packages

Using YUM:

```bash
sudo yum update -y
```

Using DNF:

```bash
sudo dnf update -y
```

---

# Apply Security Updates Only

```bash
sudo yum update --security
```

or

```bash
sudo dnf update --security
```

---

# Download Updates Without Installing

```bash
sudo yum update --downloadonly
```

---

# View Package Information

```bash
yum info package_name
```

Example:

```bash
yum info httpd
```

---

# View Package Changelog

```bash
rpm -q --changelog package_name
```

Example:

```bash
rpm -q --changelog kernel
```

---

# Verify Package Integrity

```bash
rpm -V package_name
```

Example:

```bash
rpm -V bash
```

---

# Check Enabled Repositories

```bash
yum repolist
```

or

```bash
dnf repolist
```

---

# Clean Package Cache

```bash
yum clean all
```

or

```bash
dnf clean all
```

---

# Rebuild Metadata Cache

```bash
yum makecache
```

or

```bash
dnf makecache
```

---

# Upgrade Kernel

Update system:

```bash
sudo yum update kernel
```

Verify installed kernels:

```bash
rpm -qa | grep kernel
```

---

# Reboot After Kernel Upgrade

```bash
sudo reboot
```

Verify new kernel:

```bash
uname -r
```

---

# Automated Updates

Install update utility:

```bash
sudo yum install dnf-automatic -y
```

Enable service:

```bash
sudo systemctl enable --now dnf-automatic.timer
```

Verify status:

```bash
systemctl status dnf-automatic.timer
```

---

# Patch Management Process

## Step 1: Assess Updates

```bash
yum check-update
```

---

## Step 2: Review Packages

```bash
yum list updates
```

---

## Step 3: Backup Critical Data

Example:

```bash
rsync -av /etc /backup/
```

---

## Step 4: Apply Updates

```bash
sudo yum update -y
```

---

## Step 5: Reboot if Required

```bash
sudo reboot
```

---

## Step 6: Verify System Health

```bash
systemctl --failed
```

---

# Common Troubleshooting

## Verify Repository Access

```bash
yum repolist
```

---

## Verify Internet Connectivity

```bash
ping google.com
```

---

## Verify DNS Resolution

```bash
host google.com
```

---

## Clean Repository Cache

```bash
yum clean all
```

---

## Check Package Database

```bash
rpm -qa | wc -l
```

---

# Best Practices

- Apply security patches regularly.
- Test updates in non-production environments.
- Take backups before upgrades.
- Review release notes.
- Monitor update logs.
- Schedule maintenance windows.
- Reboot after kernel updates.

---

# Useful Commands

## Check Updates

```bash
yum check-update
```

## Update System

```bash
yum update -y
```

## Update Security Packages

```bash
yum update --security
```

## Check Kernel Version

```bash
uname -r
```

## Verify Repositories

```bash
yum repolist
```

---

# Summary

| Command | Purpose |
|----------|----------|
| yum check-update | Check updates |
| yum update | Update packages |
| yum update --security | Apply security patches |
| yum repolist | Display repositories |
| rpm -qa | List installed packages |
| uname -r | Display kernel version |
| reboot | Restart system |

---

# RHCSA Notes

For RHCSA preparation, you should be able to:

- Check available updates
- Manage repositories
- Install and remove packages
- Apply patches
- Upgrade packages
- Verify package integrity
- Manage kernel updates

These tasks are common in enterprise Linux environments.

---

# Conclusion

System Upgrade and Patch Management are essential administrative tasks that keep Linux systems secure, reliable, and compliant. Understanding package updates, repository management, kernel upgrades, and security patching is a fundamental RHCSA skill and a critical responsibility for Linux administrators.