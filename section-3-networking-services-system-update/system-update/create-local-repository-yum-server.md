# Create Local Repository (YUM Server)

## Overview

A Local Repository (YUM Server) is used to provide software packages to Linux systems without requiring internet access.

Benefits:

- Faster package installation
- Reduced internet usage
- Centralized package management
- Useful in enterprise environments
- Required in many RHCSA practice labs

---

# What is a Local Repository?

A Local Repository is a directory containing RPM packages and repository metadata.

Example:

```text
Client System
      |
      |
      v
YUM Repository Server
      |
      ├── RPM Packages
      └── repodata/
```

Clients use the repository to install and update packages.

---

# Lab Environment

## Repository Server

```text
IP Address : 192.168.1.100
Hostname   : yum-server
```

## Client System

```text
IP Address : 192.168.1.101
Hostname   : yum-client
```

---

# Prerequisites

Install required packages:

```bash
yum install httpd createrepo -y
```

Verify installation:

```bash
rpm -qa | grep httpd
rpm -qa | grep createrepo
```

---

# Step 1: Create Repository Directory

Create directory:

```bash
mkdir -p /var/www/html/localrepo
```

Verify:

```bash
ls -ld /var/www/html/localrepo
```

---

# Step 2: Copy RPM Packages

Example:

```bash
cp *.rpm /var/www/html/localrepo/
```

Or copy packages from DVD:

```bash
cp -rv /mnt/BaseOS/Packages/* /var/www/html/localrepo/
```

Verify:

```bash
ls /var/www/html/localrepo
```

---

# Step 3: Create Repository Metadata

Generate metadata:

```bash
createrepo /var/www/html/localrepo
```

Example Output:

```text
Spawning worker...
Saving Primary metadata
Saving file lists metadata
```

Verify:

```bash
ls /var/www/html/localrepo
```

Expected:

```text
Packages
repodata
```

---

# Step 4: Start Apache Service

Start service:

```bash
systemctl start httpd
```

Enable at boot:

```bash
systemctl enable httpd
```

Check status:

```bash
systemctl status httpd
```

---

# Step 5: Configure Firewall

Allow HTTP service:

```bash
firewall-cmd --permanent --add-service=http
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-services
```

Expected:

```text
http https
```

---

# Step 6: Verify Repository Server

From repository server:

```bash
curl http://localhost/localrepo
```

or

```bash
curl http://192.168.1.100/localrepo
```

---

# Step 7: Configure Repository on Client

Create repository file:

```bash
vi /etc/yum.repos.d/local.repo
```

Add:

```ini
[localrepo]
name=Local YUM Repository
baseurl=http://192.168.1.100/localrepo
enabled=1
gpgcheck=0
```

Save and exit.

---

# Step 8: Clean Existing Cache

```bash
yum clean all
```

---

# Step 9: Rebuild Repository Cache

```bash
yum makecache
```

---

# Step 10: Verify Repository

Display repositories:

```bash
yum repolist
```

Expected:

```text
repo id       repo name
localrepo     Local YUM Repository
```

---

# Step 11: Install Package from Repository

Example:

```bash
yum install httpd -y
```

or

```bash
yum install vim -y
```

Verify:

```bash
rpm -qa | grep vim
```

---

# Create Repository Using DVD

Mount DVD:

```bash
mount /dev/sr0 /mnt
```

Create repo file:

```bash
vi /etc/yum.repos.d/dvd.repo
```

Add:

```ini
[dvd]
name=RHEL DVD Repository
baseurl=file:///mnt
enabled=1
gpgcheck=0
```

Verify:

```bash
yum repolist
```

---

# Update Repository Metadata

After adding new RPM packages:

```bash
createrepo --update /var/www/html/localrepo
```

---

# Troubleshooting

## Check Apache Status

```bash
systemctl status httpd
```

---

## Check Port 80

```bash
ss -tulnp | grep 80
```

---

## Verify Firewall

```bash
firewall-cmd --list-all
```

---

## Verify Repository URL

```bash
curl http://192.168.1.100/localrepo
```

---

## Verify Repository Configuration

```bash
cat /etc/yum.repos.d/local.repo
```

---

# Useful Commands

## List Repositories

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

## Install Package

```bash
yum install package_name
```

---

## Create Metadata

```bash
createrepo /path/to/repository
```

---

# Repository Structure

```text
localrepo/
│
├── package1.rpm
├── package2.rpm
├── package3.rpm
│
└── repodata/
    ├── primary.xml.gz
    ├── filelists.xml.gz
    └── repomd.xml
```

---

# RHCSA Notes

Important commands:

```bash
createrepo /repo
```

```bash
yum repolist
```

```bash
yum makecache
```

```bash
yum clean all
```

```bash
yum install package
```

Local repositories are commonly used in RHCSA labs and enterprise environments where systems do not have internet access.

---

# Summary

| Command | Purpose |
|----------|----------|
| createrepo /repo | Create repository metadata |
| yum repolist | Display repositories |
| yum makecache | Build repository cache |
| yum clean all | Clean cache |
| yum install package | Install package |
| systemctl start httpd | Start web server |
| firewall-cmd --add-service=http | Allow HTTP |

---

# Conclusion

A Local Repository (YUM Server) allows Linux systems to install and update packages without internet access. By combining RPM packages, repository metadata, and an HTTP server, administrators can build centralized package management solutions commonly used in RHCSA labs and enterprise Linux environments.