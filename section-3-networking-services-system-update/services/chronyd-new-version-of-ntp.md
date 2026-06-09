# chronyd (New Version of NTP)

## Overview

`chronyd` is the daemon used by **Chrony**, a modern implementation of the Network Time Protocol (NTP).

Chrony is designed to synchronize system clocks more accurately and efficiently than the traditional `ntpd` service.

Modern Red Hat Enterprise Linux (RHEL), Rocky Linux, AlmaLinux, and CentOS systems use Chrony as the default time synchronization service.

---

# What is Chrony?

Chrony is a suite of programs used to synchronize system time.

Main components:

| Component | Purpose |
|------------|----------|
| chronyd | Background daemon |
| chronyc | Command-line management tool |

---

# Why Chrony Replaced NTP?

Chrony offers several advantages over traditional NTP:

- Faster synchronization
- Better performance on virtual machines
- Handles unstable network connections
- Works well with intermittent internet access
- Improved clock accuracy
- Lower resource consumption

---

# Chrony Architecture

```text
Time Server
      |
      |
      v
   chronyd
      |
      |
      v
 System Clock
```

---

# NTP vs Chrony

| Feature | NTP (ntpd) | Chrony (chronyd) |
|----------|------------|------------|
| Synchronization Speed | Slow | Fast |
| Accuracy | Good | Better |
| Virtual Machine Support | Limited | Excellent |
| Offline Operation | Poor | Excellent |
| Default in RHEL 8/9 | No | Yes |

---

# Install Chrony

Install package:

```bash
dnf install chrony -y
```

Verify installation:

```bash
rpm -qa | grep chrony
```

---

# Start Chrony Service

Start service:

```bash
systemctl start chronyd
```

Enable service at boot:

```bash
systemctl enable chronyd
```

Verify status:

```bash
systemctl status chronyd
```

---

# Check Time Synchronization Status

```bash
timedatectl
```

Example Output:

```text
System clock synchronized: yes
NTP service: active
```

---

# Chrony Configuration File

Configuration file:

```text
/etc/chrony.conf
```

View file:

```bash
cat /etc/chrony.conf
```

Edit file:

```bash
vi /etc/chrony.conf
```

---

# Configure NTP Servers

Example:

```conf
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst
```

---

# Meaning of iburst

```text
iburst = Initial Burst
```

Allows faster synchronization during startup.

---

# Restart Chrony

After configuration changes:

```bash
systemctl restart chronyd
```

---

# Verify Time Sources

Display configured NTP servers:

```bash
chronyc sources
```

Example:

```text
MS Name/IP address
^* time.google.com
```

---

# Display Synchronization Details

```bash
chronyc tracking
```

Example:

```text
Reference ID    : time.google.com
Leap status     : Normal
System time     : synchronized
```

---

# Show Source Statistics

```bash
chronyc sourcestats
```

---

# Force Immediate Time Synchronization

```bash
chronyc makestep
```

Useful when system time is significantly incorrect.

---

# Display Current Date and Time

```bash
date
```

Example:

```text
Tue Jan 20 10:15:20 IST 2026
```

---

# Configure Time Zone

Display current timezone:

```bash
timedatectl
```

List available time zones:

```bash
timedatectl list-timezones
```

Set timezone:

```bash
timedatectl set-timezone Asia/Kolkata
```

Verify:

```bash
timedatectl
```

---

# Enable NTP Synchronization

```bash
timedatectl set-ntp true
```

Verify:

```bash
timedatectl
```

---

# Disable NTP Synchronization

```bash
timedatectl set-ntp false
```

---

# Configure Chrony Server

Edit configuration:

```bash
vi /etc/chrony.conf
```

Allow clients:

```conf
allow 192.168.1.0/24
```

Restart service:

```bash
systemctl restart chronyd
```

---

# Configure Chrony Client

Edit configuration:

```bash
vi /etc/chrony.conf
```

Add:

```conf
server 192.168.1.100 iburst
```

Restart service:

```bash
systemctl restart chronyd
```

---

# Verify Listening Port

Chrony uses:

```text
UDP Port 123
```

Check:

```bash
ss -ulnp | grep 123
```

Expected Output:

```text
udp LISTEN *:123
```

---

# Firewall Configuration

Allow NTP service:

```bash
firewall-cmd --permanent --add-service=ntp
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-services
```

---

# Troubleshooting

## Verify Service Status

```bash
systemctl status chronyd
```

---

## Verify Sources

```bash
chronyc sources -v
```

---

## Verify Synchronization

```bash
chronyc tracking
```

---

## Check Logs

```bash
journalctl -u chronyd
```

---

## Verify Port

```bash
ss -ulnp | grep 123
```

---

# Useful Commands

## Service Status

```bash
systemctl status chronyd
```

---

## Display Sources

```bash
chronyc sources
```

---

## Display Tracking Information

```bash
chronyc tracking
```

---

## Force Sync

```bash
chronyc makestep
```

---

## Show Statistics

```bash
chronyc sourcestats
```

---

## Display Time Settings

```bash
timedatectl
```

---

# RHCSA Notes

Important commands:

```bash
dnf install chrony
```

```bash
systemctl start chronyd
```

```bash
chronyc sources
```

```bash
chronyc tracking
```

```bash
chronyc makestep
```

```bash
timedatectl
```

Chrony is the default time synchronization solution in modern Red Hat Enterprise Linux systems and is frequently used in RHCSA labs and production environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install chrony | Install Chrony |
| systemctl start chronyd | Start Chrony service |
| chronyc sources | Display time sources |
| chronyc tracking | Display sync status |
| chronyc makestep | Force synchronization |
| timedatectl | Display time information |
| timedatectl set-ntp true | Enable NTP sync |

---

# Conclusion

Chronyd is the modern replacement for traditional NTP services and provides accurate, efficient, and reliable time synchronization. It is optimized for modern Linux systems, virtual environments, and enterprise infrastructures. Understanding Chrony installation, configuration, troubleshooting, and administration is an important RHCSA skill.