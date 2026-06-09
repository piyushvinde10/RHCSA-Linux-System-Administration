# Linux Web-Based Administration (Cockpit)

## Overview

Cockpit is a web-based Linux administration tool that allows administrators to manage Linux servers through a graphical web interface.

Using Cockpit, administrators can:

- Monitor system performance
- Manage services
- Manage users
- Configure networking
- Manage storage
- Access logs
- Open a web terminal

Cockpit is included by default in many Red Hat-based Linux distributions.

---

# What is Cockpit?

Cockpit is a lightweight web management interface for Linux servers.

Architecture:

```text
Administrator
      |
      | HTTPS (Port 9090)
      |
      v
    Cockpit
      |
      v
Linux Server
```

---

# Features of Cockpit

- Web-based administration
- User management
- Service management
- System monitoring
- Storage management
- Networking configuration
- Journal log viewing
- Terminal access
- Package updates
- Multi-server management

---

# Cockpit Port

Default Port:

```text
9090/TCP
```

Access URL:

```text
https://SERVER-IP:9090
```

Example:

```text
https://192.168.1.100:9090
```

---

# Install Cockpit

Install package:

```bash
dnf install cockpit -y
```

Verify installation:

```bash
rpm -qa | grep cockpit
```

---

# Start Cockpit Service

Start service:

```bash
systemctl start cockpit.socket
```

Enable at boot:

```bash
systemctl enable cockpit.socket
```

Verify status:

```bash
systemctl status cockpit.socket
```

---

# Verify Listening Port

Check port:

```bash
ss -tulnp | grep 9090
```

Expected Output:

```text
LISTEN 0 128 *:9090
```

---

# Configure Firewall

Allow Cockpit service:

```bash
firewall-cmd --permanent --add-service=cockpit
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
cockpit
```

---

# Access Cockpit

Open browser:

```text
https://SERVER-IP:9090
```

Example:

```text
https://192.168.1.100:9090
```

Login using:

```text
Linux Username
Linux Password
```

---

# Cockpit Dashboard

The dashboard provides:

- CPU Usage
- Memory Usage
- Disk Usage
- Network Activity
- System Health

---

# User Management

Navigate:

```text
Accounts → Create User
```

Tasks:

- Create users
- Delete users
- Modify passwords
- Assign administrator privileges

---

# Service Management

Navigate:

```text
Services
```

Tasks:

- Start services
- Stop services
- Restart services
- Enable services
- Disable services

Example:

```text
httpd
nginx
sshd
chronyd
```

---

# Storage Management

Navigate:

```text
Storage
```

Manage:

- Disks
- Partitions
- LVM
- Mount points
- File systems

---

# Network Management

Navigate:

```text
Networking
```

Manage:

- IP Addresses
- Network Interfaces
- DNS Configuration
- Routing

---

# System Logs

Navigate:

```text
Logs
```

View:

- System Logs
- Service Logs
- Error Messages

Equivalent command:

```bash
journalctl
```

---

# Web Terminal

Navigate:

```text
Terminal
```

Provides direct command-line access from the browser.

Example:

```bash
pwd
```

```bash
hostname
```

```bash
df -h
```

---

# Software Updates

Navigate:

```text
Software Updates
```

Tasks:

- Check updates
- Install updates
- Reboot system

Equivalent commands:

```bash
dnf update
```

---

# Multi-Server Management

Add remote servers:

```text
Dashboard → Add New Host
```

Requirements:

- SSH Access
- Network Connectivity

---

# Cockpit Service Management

Start:

```bash
systemctl start cockpit.socket
```

Stop:

```bash
systemctl stop cockpit.socket
```

Restart:

```bash
systemctl restart cockpit.socket
```

Enable:

```bash
systemctl enable cockpit.socket
```

Status:

```bash
systemctl status cockpit.socket
```

---

# Verify Cockpit Package

```bash
rpm -qa | grep cockpit
```

---

# Troubleshooting

## Verify Service Status

```bash
systemctl status cockpit.socket
```

---

## Verify Port

```bash
ss -tulnp | grep 9090
```

---

## Verify Firewall

```bash
firewall-cmd --list-services
```

---

## Check Logs

```bash
journalctl -u cockpit
```

---

## Verify Connectivity

```bash
curl -k https://localhost:9090
```

---

# Useful Commands

## Install Cockpit

```bash
dnf install cockpit -y
```

---

## Start Service

```bash
systemctl start cockpit.socket
```

---

## Enable Service

```bash
systemctl enable cockpit.socket
```

---

## Check Status

```bash
systemctl status cockpit.socket
```

---

## Verify Port

```bash
ss -tulnp | grep 9090
```

---

# Cockpit Directory Structure

```text
/usr/share/cockpit/
/etc/cockpit/
/var/lib/cockpit/
```

---

# RHCSA Notes

Important commands:

```bash
dnf install cockpit
```

```bash
systemctl start cockpit.socket
```

```bash
systemctl enable cockpit.socket
```

```bash
systemctl status cockpit.socket
```

```bash
ss -tulnp | grep 9090
```

```bash
firewall-cmd --add-service=cockpit
```

Cockpit is commonly used in modern Linux administration because it provides a simple web-based interface for managing Linux servers.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install cockpit | Install Cockpit |
| systemctl start cockpit.socket | Start Cockpit |
| systemctl enable cockpit.socket | Enable at boot |
| systemctl status cockpit.socket | Check status |
| ss -tulnp | Verify port 9090 |
| firewall-cmd --add-service=cockpit | Allow Cockpit |

---

# Conclusion

Cockpit is a powerful web-based administration tool for Linux systems. It simplifies server management by providing a graphical interface for monitoring, networking, storage, services, user management, and troubleshooting. Understanding Cockpit installation, configuration, and administration is valuable for RHCSA preparation and real-world Linux system administration.