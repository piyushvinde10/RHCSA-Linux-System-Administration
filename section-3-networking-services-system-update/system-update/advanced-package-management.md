# Advanced Package Management

## Overview

Advanced Package Management involves managing software packages, dependencies, repositories, package groups, and package verification on Linux systems.

In Red Hat-based distributions, package management is performed using:

- RPM (Red Hat Package Manager)
- YUM (Yellowdog Updater Modified)
- DNF (Dandified YUM)

These tools help administrators install, update, remove, verify, and troubleshoot software packages efficiently.

---

# Package Management Architecture

```text
Application
     |
     v
YUM / DNF
     |
     v
RPM Database
     |
     v
Installed Packages
```

---

# Verify Installed Packages

List all installed packages:

```bash
rpm -qa
```

Count installed packages:

```bash
rpm -qa | wc -l
```

Search package:

```bash
rpm -qa | grep httpd
```

---

# Display Package Information

```bash
rpm -qi package_name
```

Example:

```bash
rpm -qi bash
```

Output:

```text
Name        : bash
Version     : 5.1
Release     : 2.el9
```

---

# List Files Installed by Package

```bash
rpm -ql package_name
```

Example:

```bash
rpm -ql httpd
```

---

# Find Package Owning a File

```bash
rpm -qf /etc/passwd
```

Example Output:

```text
setup-2.13.7-10.el9.noarch
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

Checks:

- File size
- Permissions
- Ownership
- Checksums
- Timestamps

---

# Package Dependencies

Display dependencies:

```bash
rpm -qR package_name
```

Example:

```bash
rpm -qR httpd
```

---

# Install Package with Dependencies

```bash
yum install package_name -y
```

Example:

```bash
yum install httpd -y
```

---

# Download Package Without Installing

```bash
yum install --downloadonly package_name
```

Example:

```bash
yum install --downloadonly vim
```

---

# Reinstall Package

```bash
yum reinstall package_name -y
```

Example:

```bash
yum reinstall bash -y
```

---

# Remove Package

```bash
yum remove package_name -y
```

Example:

```bash
yum remove httpd -y
```

---

# Package Groups

Package groups install multiple related packages.

List groups:

```bash
yum grouplist
```

---

## Install Group

```bash
yum groupinstall "Development Tools" -y
```

---

## Remove Group

```bash
yum groupremove "Development Tools" -y
```

---

# Package History

Display transaction history:

```bash
yum history
```

Example:

```text
ID | Command Line
1  | install httpd
2  | update
```

---

# Undo Package Transaction

```bash
yum history undo ID
```

Example:

```bash
yum history undo 5
```

---

# View Repository Information

List repositories:

```bash
yum repolist
```

Display repository details:

```bash
yum repoinfo
```

---

# Enable Repository

```bash
yum-config-manager --enable repository_name
```

Example:

```bash
yum-config-manager --enable appstream
```

---

# Disable Repository

```bash
yum-config-manager --disable repository_name
```

---

# Clean Repository Cache

```bash
yum clean all
```

---

# Rebuild Repository Cache

```bash
yum makecache
```

---

# Check Available Updates

```bash
yum check-update
```

---

# Update Specific Package

```bash
yum update package_name
```

Example:

```bash
yum update httpd
```

---

# Update Entire System

```bash
yum update -y
```

---

# Security Updates

Install security patches:

```bash
yum update --security
```

---

# Lock Package Version

Install plugin:

```bash
yum install yum-plugin-versionlock -y
```

Lock package:

```bash
yum versionlock add package_name
```

Example:

```bash
yum versionlock add kernel
```

---

# Remove Version Lock

```bash
yum versionlock delete kernel
```

---

# Check Package Changelog

```bash
rpm -q --changelog package_name
```

Example:

```bash
rpm -q --changelog kernel
```

---

# Manage Local RPM Packages

Install RPM:

```bash
rpm -ivh package.rpm
```

Upgrade RPM:

```bash
rpm -Uvh package.rpm
```

Remove RPM:

```bash
rpm -e package_name
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

## Clean Cache

```bash
yum clean all
```

---

## Rebuild Metadata

```bash
yum makecache
```

---

## Verify Package Database

```bash
rpm --rebuilddb
```

---

# Useful Commands

## Search Package

```bash
yum search package_name
```

---

## Package Information

```bash
yum info package_name
```

---

## List Installed Packages

```bash
yum list installed
```

---

## List Available Packages

```bash
yum list available
```

---

# RPM vs YUM vs DNF

| Feature | RPM | YUM | DNF |
|----------|----------|----------|----------|
| Dependency Resolution | No | Yes | Yes |
| Repository Support | No | Yes | Yes |
| Package History | No | Yes | Yes |
| Faster Performance | No | No | Yes |
| Modern Tool | No | Limited | Yes |

---

# RHCSA Notes

Important commands:

```bash
rpm -qa
```

```bash
rpm -qi package
```

```bash
rpm -ql package
```

```bash
yum install package
```

```bash
yum update
```

```bash
yum history
```

```bash
yum repolist
```

These commands are frequently used in RHCSA labs and enterprise Linux administration.

---

# Summary

| Command | Purpose |
|----------|----------|
| rpm -qa | List installed packages |
| rpm -qi package | Package information |
| rpm -ql package | List package files |
| rpm -qf file | Find package owning file |
| yum install package | Install package |
| yum remove package | Remove package |
| yum update | Update packages |
| yum history | View transactions |
| yum repolist | List repositories |

---

# Conclusion

Advanced Package Management enables administrators to efficiently install, update, verify, troubleshoot, and secure software packages. Understanding RPM, YUM, DNF, repositories, package groups, and dependency management is essential for RHCSA certification and real-world Linux administration.