# Kickstart (Automate Linux Installation)

## Overview

Kickstart is an automated installation method used in Red Hat-based Linux distributions such as:

- Red Hat Enterprise Linux (RHEL)
- CentOS
- Rocky Linux
- AlmaLinux

Kickstart allows administrators to automate Linux installations using a configuration file called:

```text
ks.cfg
```

This eliminates manual intervention during OS installation.

---

# What is Kickstart?

Kickstart is used to automate:

- Disk Partitioning
- Package Installation
- Network Configuration
- User Creation
- Security Configuration
- Post Installation Tasks

---

# Benefits of Kickstart

- Automated Installation
- Faster Deployment
- Consistent Configuration
- Reduced Human Errors
- Mass Server Provisioning
- Easy OS Standardization

---

# Kickstart Architecture

```text
            Kickstart File (ks.cfg)
                      |
                      |
                      v
      ----------------------------------
      |                                |
Linux Installer                  Installation Source
      |                                |
      ----------------------------------
                      |
                      v
              Automated OS Installation
```

---

# Kickstart File Location

Default location after installation:

```text
/root/anaconda-ks.cfg
```

View file:

```bash
cat /root/anaconda-ks.cfg
```

---

# Install Kickstart Tools

Install package:

```bash
dnf install pykickstart -y
```

Verify:

```bash
rpm -qa | grep kickstart
```

---

# Basic Kickstart File Structure

Example:

```kickstart
#version=RHEL9

lang en_US.UTF-8
keyboard us
timezone Asia/Kolkata

rootpw redhat123

reboot

network --bootproto=dhcp

firewall --enabled

selinux --enforcing

bootloader --location=mbr

clearpart --all --initlabel

autopart

%packages
@core
%end
```

---

# Kickstart Sections

## Installation Settings

```kickstart
lang en_US.UTF-8
keyboard us
timezone Asia/Kolkata
```

---

## Root Password

```kickstart
rootpw redhat123
```

Encrypted password:

```kickstart
rootpw --iscrypted HASHED_PASSWORD
```

---

## Network Configuration

DHCP:

```kickstart
network --bootproto=dhcp
```

Static IP:

```kickstart
network --bootproto=static \
--ip=192.168.1.100 \
--netmask=255.255.255.0 \
--gateway=192.168.1.1 \
--nameserver=8.8.8.8
```

---

## Firewall Configuration

Enable:

```kickstart
firewall --enabled
```

Disable:

```kickstart
firewall --disabled
```

---

## SELinux

Enable:

```kickstart
selinux --enforcing
```

Disable:

```kickstart
selinux --disabled
```

---

## Disk Partitioning

Automatic:

```kickstart
autopart
```

Manual:

```kickstart
clearpart --all --initlabel

part /boot --fstype=xfs --size=1024

part swap --size=2048

part / --fstype=xfs --grow --size=10240
```

---

## Package Selection

Minimal Installation:

```kickstart
%packages
@core
%end
```

Additional packages:

```kickstart
%packages
@core
vim
wget
net-tools
%end
```

---

# Create User

Example:

```kickstart
user --name=piyush \
--password=password123
```

---

# Reboot After Installation

```kickstart
reboot
```

---

# Post Installation Script

Run commands after installation:

```kickstart
%post

echo "Welcome to RHCSA Lab" \
> /etc/motd

dnf install wget -y

%end
```

---

# Validate Kickstart File

Verify syntax:

```bash
ksvalidator ks.cfg
```

Expected Output:

```text
No errors found
```

---

# Use Kickstart During Installation

Boot installer and select:

```text
Install Red Hat Enterprise Linux
```

Press:

```text
Tab
```

Add:

```text
inst.ks=http://192.168.1.100/ks.cfg
```

Example:

```text
linux inst.ks=http://192.168.1.100/ks.cfg
```

---

# Kickstart Sources

Kickstart file can be stored on:

- HTTP Server
- FTP Server
- NFS Server
- Local Disk
- USB Drive

Examples:

```text
inst.ks=http://server/ks.cfg
```

```text
inst.ks=ftp://server/ks.cfg
```

```text
inst.ks=nfs:server:/ks.cfg
```

---

# Example Complete Kickstart File

```kickstart
#version=RHEL9

lang en_US.UTF-8
keyboard us

timezone Asia/Kolkata

rootpw redhat123

network --bootproto=dhcp

firewall --enabled

selinux --enforcing

bootloader --location=mbr

clearpart --all --initlabel

autopart

reboot

%packages

@core
vim
wget
net-tools

%end

%post

echo "Kickstart Installation Complete" \
> /etc/motd

%end
```

---

# Useful Commands

## View Existing Kickstart File

```bash
cat /root/anaconda-ks.cfg
```

---

## Validate File

```bash
ksvalidator ks.cfg
```

---

## Install Kickstart Tools

```bash
dnf install pykickstart -y
```

---

## Edit Kickstart File

```bash
vi ks.cfg
```

---

# Troubleshooting

## Verify Kickstart Syntax

```bash
ksvalidator ks.cfg
```

---

## Check Installation Logs

```bash
cat /tmp/anaconda.log
```

---

## Verify Network Connectivity

```bash
ping server-ip
```

---

## Verify Web Server

```bash
curl http://server-ip/ks.cfg
```

---

# RHCSA Notes

Important commands:

```bash
cat /root/anaconda-ks.cfg
```

```bash
ksvalidator ks.cfg
```

```bash
dnf install pykickstart
```

```bash
vi ks.cfg
```

```bash
curl http://server-ip/ks.cfg
```

Kickstart is commonly used in enterprise environments for automated Linux deployments.

---

# Summary

| Command | Purpose |
|----------|----------|
| cat /root/anaconda-ks.cfg | View generated Kickstart |
| ksvalidator ks.cfg | Validate Kickstart file |
| dnf install pykickstart | Install validation tools |
| vi ks.cfg | Edit Kickstart file |
| inst.ks=http://server/ks.cfg | Use Kickstart during installation |

---

# Conclusion

Kickstart is an automated installation framework for Red Hat-based Linux systems. It enables administrators to deploy multiple Linux servers quickly and consistently using a predefined configuration file. Understanding Kickstart installation automation, package selection, partitioning, networking, and post-installation scripting is valuable for RHCSA preparation and enterprise Linux administration.