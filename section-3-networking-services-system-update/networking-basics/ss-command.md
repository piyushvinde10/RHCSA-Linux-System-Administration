# The ss Command

## Overview

The `ss` (Socket Statistics) command is a Linux utility used to display network socket information.

It is the modern replacement for the `netstat` command and provides faster and more detailed network information.

System administrators use `ss` to:

- View listening ports
- Check active network connections
- Troubleshoot network issues
- Identify services using ports
- Monitor TCP and UDP sockets

---

# Why Use ss?

Advantages of `ss`:

- Faster than netstat
- Displays more detailed information
- Shows process information
- Built into modern Linux distributions

---

# Basic Syntax

```bash
ss [options]
```

---

# Display All Connections

```bash
ss
```

Example Output:

```text
State      Recv-Q Send-Q Local Address:Port
ESTAB      0      0      192.168.1.10:ssh
```

---

# Display TCP Connections

```bash
ss -t
```

Example:

```text
State      Local Address:Port
ESTAB      192.168.1.10:ssh
```

---

# Display UDP Connections

```bash
ss -u
```

---

# Display Listening Ports

```bash
ss -l
```

Example:

```text
LISTEN 0 128 *:22
LISTEN 0 128 *:80
```

---

# Display TCP Listening Ports

```bash
ss -lt
```

---

# Display UDP Listening Ports

```bash
ss -lu
```

---

# Display Listening Ports with Process Information

```bash
ss -tulnp
```

### Option Explanation

| Option | Description |
|----------|-------------|
| -t | TCP sockets |
| -u | UDP sockets |
| -l | Listening sockets |
| -n | Numeric addresses |
| -p | Process information |

Example:

```text
LISTEN 0 128 *:22 users:(("sshd",pid=1012))
LISTEN 0 128 *:80 users:(("httpd",pid=2045))
```

---

# Find Process Using a Specific Port

Example: Port 22

```bash
ss -tulnp | grep 22
```

Output:

```text
LISTEN 0 128 *:22 users:(("sshd",pid=1012))
```

---

# Display Established Connections

```bash
ss -t state established
```

---

# Display SSH Connections

```bash
ss -tn | grep :22
```

---

# Display HTTP Connections

```bash
ss -tn | grep :80
```

---

# Display HTTPS Connections

```bash
ss -tn | grep :443
```

---

# Display Routing Information

```bash
ip route
```

> Routing information is managed using the `ip` command rather than `ss`.

---

# Display Socket Statistics

```bash
ss -s
```

Example Output:

```text
Total: 300
TCP:   50
UDP:   10
RAW:   0
```

---

# Display IPv4 Connections

```bash
ss -4
```

---

# Display IPv6 Connections

```bash
ss -6
```

---

# Display Connections for a Specific Process

Example: SSHD

```bash
ss -tp | grep sshd
```

---

# Common Troubleshooting Examples

## Verify SSH Service

```bash
ss -tulnp | grep ssh
```

---

## Verify Apache Service

```bash
ss -tulnp | grep httpd
```

---

## Verify HTTPS Service

```bash
ss -tulnp | grep 443
```

---

## Check Open Ports

```bash
ss -tuln
```

---

## Check Active Connections

```bash
ss -ant
```

---

# ss vs netstat

| Feature | ss | netstat |
|----------|----------|----------|
| Speed | Fast | Slower |
| Modern Utility | Yes | Legacy |
| Process Information | Yes | Yes |
| Default on New Systems | Yes | No |
| Recommended | Yes | No |

---

# Useful Examples

## Display All Listening Services

```bash
ss -l
```

---

## Display Listening TCP Services

```bash
ss -lt
```

---

## Display Listening UDP Services

```bash
ss -lu
```

---

## Display Ports and Processes

```bash
ss -tulnp
```

---

## Display Summary Statistics

```bash
ss -s
```

---

# Common Option Reference

| Option | Description |
|----------|-------------|
| -t | TCP sockets |
| -u | UDP sockets |
| -l | Listening sockets |
| -n | Numeric output |
| -p | Show process information |
| -a | Show all sockets |
| -s | Summary statistics |
| -4 | IPv4 sockets |
| -6 | IPv6 sockets |

---

# RHCSA Notes

The `ss` command is frequently used in RHCSA and Linux administration to:

- Verify service ports
- Troubleshoot connectivity issues
- Check listening services
- Confirm firewall and network configurations

A commonly used command is:

```bash
ss -tulnp
```

This displays all listening TCP and UDP ports along with associated processes.

---

# Summary

| Command | Purpose |
|----------|----------|
| ss | Display socket information |
| ss -t | TCP connections |
| ss -u | UDP connections |
| ss -l | Listening ports |
| ss -tulnp | Ports with process information |
| ss -s | Socket statistics |
| ss -4 | IPv4 connections |
| ss -6 | IPv6 connections |

---

# Conclusion

The `ss` command is a powerful networking utility used to inspect sockets, active connections, and listening services. It is the preferred replacement for `netstat` and an essential tool for troubleshooting and monitoring Linux network services.