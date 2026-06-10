# Firewall Management in Linux

## Overview

A Firewall is a security system that monitors and controls incoming and outgoing network traffic based on predefined rules.

Firewalls help protect Linux systems from:

- Unauthorized access
- Network attacks
- Malware
- Port scanning
- Unauthorized services

Modern Red Hat-based Linux distributions use:

```text
firewalld
```

as the default firewall management service.

---

# What is a Firewall?

A firewall acts as a barrier between a trusted internal network and untrusted external networks.

Architecture:

```text
Internet
    |
    |
Firewall
    |
    |
Linux Server
```

---

# Firewall Components

| Component | Purpose |
|------------|----------|
| firewalld | Firewall Service |
| firewall-cmd | Command-Line Tool |
| Zones | Security Levels |
| Services | Predefined Rules |
| Ports | Network Access Rules |

---

# Check Firewall Status

Verify service:

```bash
systemctl status firewalld
```

Example Output:

```text
active (running)
```

---

# Start Firewall

```bash
systemctl start firewalld
```

---

# Stop Firewall

```bash
systemctl stop firewalld
```

---

# Enable Firewall at Boot

```bash
systemctl enable firewalld
```

---

# Disable Firewall at Boot

```bash
systemctl disable firewalld
```

---

# Restart Firewall

```bash
systemctl restart firewalld
```

---

# Reload Firewall Rules

```bash
firewall-cmd --reload
```

---

# Check Firewall State

```bash
firewall-cmd --state
```

Expected:

```text
running
```

---

# Display Active Zones

```bash
firewall-cmd --get-active-zones
```

---

# List All Firewall Rules

```bash
firewall-cmd --list-all
```

---

# Firewall Zones

Display available zones:

```bash
firewall-cmd --get-zones
```

Example:

```text
public
home
internal
trusted
work
```

---

# Display Default Zone

```bash
firewall-cmd --get-default-zone
```

---

# Change Default Zone

Example:

```bash
firewall-cmd --set-default-zone=home
```

---

# Allow a Service

Example: Allow SSH

```bash
firewall-cmd --permanent --add-service=ssh
```

Reload:

```bash
firewall-cmd --reload
```

---

# Allow HTTP Service

```bash
firewall-cmd --permanent --add-service=http
```

Reload:

```bash
firewall-cmd --reload
```

---

# Allow HTTPS Service

```bash
firewall-cmd --permanent --add-service=https
```

Reload:

```bash
firewall-cmd --reload
```

---

# Remove a Service

Example:

```bash
firewall-cmd --permanent --remove-service=http
```

Reload:

```bash
firewall-cmd --reload
```

---

# Open a Port

Example:

```bash
firewall-cmd --permanent --add-port=8080/tcp
```

Reload:

```bash
firewall-cmd --reload
```

---

# Open Multiple Ports

```bash
firewall-cmd --permanent --add-port=80/tcp
```

```bash
firewall-cmd --permanent --add-port=443/tcp
```

Reload:

```bash
firewall-cmd --reload
```

---

# Remove a Port

```bash
firewall-cmd --permanent --remove-port=8080/tcp
```

Reload:

```bash
firewall-cmd --reload
```

---

# List Open Ports

```bash
firewall-cmd --list-ports
```

---

# List Allowed Services

```bash
firewall-cmd --list-services
```

---

# Allow Specific IP Address

Example:

```bash
firewall-cmd --permanent \
--add-rich-rule='rule family="ipv4" source address="192.168.1.100" accept'
```

Reload:

```bash
firewall-cmd --reload
```

---

# Block Specific IP Address

```bash
firewall-cmd --permanent \
--add-rich-rule='rule family="ipv4" source address="192.168.1.100" drop'
```

Reload:

```bash
firewall-cmd --reload
```

---

# Verify Listening Ports

```bash
ss -tulnp
```

Example:

```bash
ss -tulnp | grep 80
```

---

# Firewall Configuration Files

Main directory:

```text
/etc/firewalld/
```

Zone files:

```text
/etc/firewalld/zones/
```

---

# Common Services

| Service | Port |
|-----------|------|
| SSH | 22 |
| HTTP | 80 |
| HTTPS | 443 |
| DNS | 53 |
| SMTP | 25 |
| NTP | 123 |
| LDAP | 389 |
| Cockpit | 9090 |

---

# Useful Commands

## Display Configuration

```bash
firewall-cmd --list-all
```

---

## Display Zones

```bash
firewall-cmd --get-zones
```

---

## Display Services

```bash
firewall-cmd --list-services
```

---

## Display Ports

```bash
firewall-cmd --list-ports
```

---

## Reload Rules

```bash
firewall-cmd --reload
```

---

# Troubleshooting

## Verify Firewall Service

```bash
systemctl status firewalld
```

---

## Verify Port Access

```bash
ss -tulnp
```

---

## Verify Rules

```bash
firewall-cmd --list-all
```

---

## Check Logs

```bash
journalctl -u firewalld
```

---

# RHCSA Notes

Important commands:

```bash
systemctl status firewalld
```

```bash
firewall-cmd --list-all
```

```bash
firewall-cmd --add-service=http
```

```bash
firewall-cmd --add-port=8080/tcp
```

```bash
firewall-cmd --reload
```

```bash
firewall-cmd --get-active-zones
```

Firewall configuration is a common RHCSA exam topic and an essential Linux administration skill.

---

# Summary

| Command | Purpose |
|----------|----------|
| systemctl start firewalld | Start firewall |
| systemctl stop firewalld | Stop firewall |
| firewall-cmd --list-all | Display rules |
| firewall-cmd --add-service=http | Allow HTTP |
| firewall-cmd --add-port=8080/tcp | Open port |
| firewall-cmd --reload | Apply changes |
| firewall-cmd --get-active-zones | Show active zones |

---

# Conclusion

Firewalld is the default firewall management service in modern Red Hat-based Linux systems. It provides flexible and dynamic firewall management through zones, services, ports, and rich rules. Understanding firewalld configuration, troubleshooting, and security best practices is an important RHCSA skill and a critical part of Linux system administration.