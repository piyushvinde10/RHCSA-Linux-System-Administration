# Network Time Protocol (NTP)

## Overview

Network Time Protocol (NTP) is a networking protocol used to synchronize the system clock of computers over a network.

Accurate time synchronization is critical for:

- Log analysis
- Authentication services
- Database consistency
- Cluster environments
- Monitoring tools
- Security auditing

---

# What is NTP?

NTP stands for:

```text
Network Time Protocol
```

It synchronizes system time with a reliable time source called an NTP Server.

Example:

```text
Client System
      |
      |
      v
NTP Server
      |
      |
      v
Reference Clock
```

---

# Why Time Synchronization is Important?

Without synchronized time:

- Logs become inaccurate
- Kerberos authentication may fail
- Monitoring alerts become unreliable
- Distributed applications may malfunction

---

# NTP Port

| Protocol | Port |
|-----------|------|
| UDP | 123 |

NTP uses:

```text
UDP Port 123
```

---

# NTP Components

## NTP Server

Provides accurate time to clients.

Example:

```text
time.google.com
pool.ntp.org
```

---

## NTP Client

Receives time updates from NTP servers.

---

# Chrony

Modern RHEL distributions use:

```text
chronyd
```

instead of the older:

```text
ntpd
```

Package:

```text
chrony
```

Service:

```text
chronyd
```

---

# Install Chrony

Install package:

```bash
dnf install chrony -y
```

Verify:

```bash
rpm -qa | grep chrony
```

---

# Start Chrony Service

Start service:

```bash
systemctl start chronyd
```

Enable at boot:

```bash
systemctl enable chronyd
```

Check status:

```bash
systemctl status chronyd
```

---

# Chrony Configuration File

Location:

```text
/etc/chrony.conf
```

View configuration:

```bash
cat /etc/chrony.conf
```

Edit configuration:

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

# Restart Chrony

After making changes:

```bash
systemctl restart chronyd
```

---

# Verify NTP Sources

Display configured NTP servers:

```bash
chronyc sources
```

Example Output:

```text
MS Name/IP address
^* time.google.com
```

---

# Verify Synchronization Status

```bash
chronyc tracking
```

Example Output:

```text
Reference ID    : time.google.com
System time     : synchronized
```

---

# Check Current Date and Time

```bash
date
```

Example:

```text
Tue Jan 20 10:20:15 IST 2026
```

---

# Display Detailed Time Information

```bash
timedatectl
```

Example Output:

```text
Local time: Tue 2026-01-20
Universal time: Tue 2026-01-20
NTP service: active
System clock synchronized: yes
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

# Configure System Time Zone

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

# Open Firewall for NTP Server

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

# Configure NTP Server

Edit:

```bash
vi /etc/chrony.conf
```

Allow client network:

```conf
allow 192.168.1.0/24
```

Restart service:

```bash
systemctl restart chronyd
```

---

# Configure NTP Client

Edit:

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

# Verify NTP Connectivity

Check UDP port:

```bash
ss -ulnp | grep 123
```

Expected Output:

```text
udp LISTEN *:123
```

---

# Useful Chrony Commands

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

## Force Time Synchronization

```bash
chronyc makestep
```

---

## Display NTP Statistics

```bash
chronyc sourcestats
```

---

# Troubleshooting

## Verify Service Status

```bash
systemctl status chronyd
```

---

## Verify NTP Sources

```bash
chronyc sources -v
```

---

## Verify Synchronization

```bash
chronyc tracking
```

---

## Verify Firewall

```bash
firewall-cmd --list-services
```

---

## Check Logs

```bash
journalctl -u chronyd
```

---

# NTP vs Manual Time Setting

| Feature | NTP | Manual |
|----------|------|--------|
| Automatic | Yes | No |
| Accurate | Yes | No |
| Enterprise Use | Yes | No |
| Continuous Sync | Yes | No |

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
timedatectl
```

```bash
timedatectl set-ntp true
```

These commands are commonly used in RHCSA exams and enterprise Linux environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install chrony | Install Chrony |
| systemctl start chronyd | Start NTP service |
| chronyc sources | Show NTP sources |
| chronyc tracking | Show sync status |
| timedatectl | Display time settings |
| timedatectl set-ntp true | Enable NTP |
| timedatectl set-timezone | Set timezone |

---

# Conclusion

Network Time Protocol (NTP) ensures accurate and synchronized system time across networked systems. Modern Red Hat-based Linux distributions use Chrony for time synchronization. Understanding NTP installation, configuration, troubleshooting, and time management is an important RHCSA skill and a critical requirement in enterprise environments.