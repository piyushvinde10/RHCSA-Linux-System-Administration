# System Updates and Repositories (RPM & YUM)

## Overview

Linux systems use package management tools to install, update, remove, and manage software packages.

In Red Hat Enterprise Linux (RHEL) and RHCSA environments, the primary package management tools are:

- RPM (Red Hat Package Manager)
- YUM (Yellowdog Updater Modified)

These tools help administrators manage software packages and system updates efficiently.

---

# What is RPM?

RPM (Red Hat Package Manager) is a package management utility used to:

- Install software
- Verify packages
- Query package information
- Remove packages

RPM works directly with `.rpm` files.

---

# RPM Package Format

```text
package-name-version-release.arch.rpm
```

Example:

```text
httpd-2.4.57-5.el9.x86_64.rpm
```

---

# RPM Commands

## Install Package

```bash
sudo rpm -ivh package.rpm
```

Options:

| Option | Description |
|----------|-------------|
| i | Install |
| v | Verbose |
| h | Show Progress |

Example:

```bash
sudo rpm -ivh httpd.rpm
```

---

## Upgrade Package

```bash
sudo rpm -Uvh package.rpm
```

---

## Remove Package

```bash
sudo rpm -e package_name
```

Example:

```bash
sudo rpm -e httpd
```

---

## Verify Installed Package

```bash
rpm -V package_name
```

Example:

```bash
rpm -V bash
```

---

## List Installed Packages

```bash
rpm -qa
```

---

## Search Installed Package

```bash
rpm -qa | grep httpd
```

---

## Display Package Information

```bash
rpm -qi package_name
```

Example:

```bash
rpm -qi bash
```

---

## List Files Installed by Package

```bash
rpm -ql package_name
```

Example:

```bash
rpm -ql httpd
```

---

# What is YUM?

YUM (Yellowdog Updater Modified) is a package management tool that automatically resolves dependencies.

YUM works with repositories to install and update packages.

---

# Benefits of YUM

- Dependency resolution
- Repository management
- Software updates
- Package search
- Easier package installation

---

# YUM Repositories

Repository configuration files are stored in:

```text
/etc/yum.repos.d/
```

List repositories:

```bash
ls /etc/yum.repos.d/
```

---

# YUM Commands

## List Repositories

```bash
yum repolist
```

---

## Install Package

```bash
sudo yum install package_name -y
```

Example:

```bash
sudo yum install httpd -y
```

---

## Remove Package

```bash
sudo yum remove package_name -y
```

Example:

```bash
sudo yum remove httpd -y
```

---

## Search Package

```bash
yum search package_name
```

Example:

```bash
yum search nginx
```

---

## Display Package Information

```bash
yum info package_name
```

Example:

```bash
yum info httpd
```

---

## List Installed Packages

```bash
yum list installed
```

---

## Check Available Updates

```bash
yum check-update
```

---

## Update Specific Package

```bash
sudo yum update package_name
```

Example:

```bash
sudo yum update httpd
```

---

## Update Entire System

```bash
sudo yum update -y
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

# Repository Configuration

## Create Custom Repository

Repository file:

```text
/etc/yum.repos.d/custom.repo
```

Example:

```ini
[local-repo]
name=Local Repository
baseurl=http://repo.example.com
enabled=1
gpgcheck=0
```

---

## Verify Repository

```bash
yum repolist
```

---

# Common System Update Tasks

## Check Available Updates

```bash
yum check-update
```

---

## Update Entire System

```bash
sudo yum update -y
```

---

## Update Security Packages

```bash
sudo yum update --security
```

---

## Verify Installed Kernel

```bash
uname -r
```

---

## Reboot After Kernel Update

```bash
sudo reboot
```

---

# Troubleshooting YUM

## Clean Cache

```bash
yum clean all
```

---

## Rebuild Repository Metadata

```bash
yum makecache
```

---

## Verify Network Connectivity

```bash
ping google.com
```

---

## Verify Repository Access

```bash
yum repolist
```

---

# RPM vs YUM

| Feature | RPM | YUM |
|----------|----------|----------|
| Dependency Resolution | No | Yes |
| Repository Support | No | Yes |
| Package Installation | Yes | Yes |
| System Updates | No | Yes |
| Package Queries | Yes | Yes |

---

# Common RHCSA Commands

## Install Package

```bash
yum install package_name -y
```

---

## Remove Package

```bash
yum remove package_name -y
```

---

## Search Package

```bash
yum search package_name
```

---

## Update System

```bash
yum update -y
```

---

## List Installed Packages

```bash
rpm -qa
```

---

# Summary

| Command | Purpose |
|----------|----------|
| rpm -ivh package.rpm | Install RPM |
| rpm -e package | Remove RPM |
| rpm -qa | List installed packages |
| yum install package | Install package |
| yum remove package | Remove package |
| yum update | Update package/system |
| yum repolist | List repositories |
| yum check-update | Check updates |

---

# Conclusion

RPM and YUM are essential package management tools in Red Hat-based Linux distributions. RPM manages individual package files, while YUM provides repository-based package installation and automatic dependency resolution. Understanding RPM, YUM, repositories, and system updates is a key RHCSA skill for managing Linux systems efficiently.