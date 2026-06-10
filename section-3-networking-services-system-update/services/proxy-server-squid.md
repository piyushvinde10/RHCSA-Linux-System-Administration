# Proxy Server in Linux (Squid)

## Overview

A Proxy Server acts as an intermediary between clients and the internet.

Instead of clients connecting directly to websites, requests are sent through the proxy server.

Squid is the most popular proxy server used in Linux environments.

Benefits:

- Improved security
- Web content filtering
- Bandwidth optimization
- Access control
- Web caching
- User activity monitoring

---

# What is a Proxy Server?

A proxy server sits between the client and the destination server.

Architecture:

```text
Client
   |
   |
   v
Proxy Server (Squid)
   |
   |
   v
Internet
```

---

# Why Use a Proxy Server?

- Hide client IP addresses
- Control internet access
- Block websites
- Monitor web activity
- Improve performance using cache
- Reduce internet bandwidth usage

---

# Types of Proxy Servers

## Forward Proxy

Used by clients to access the internet.

```text
Client → Proxy → Internet
```

---

## Reverse Proxy

Used to protect backend servers.

```text
Client → Reverse Proxy → Web Server
```

Example:

- Nginx
- Apache
- HAProxy

---

# What is Squid?

Squid is an open-source proxy and caching server.

Features:

- HTTP Proxy
- HTTPS Proxy
- FTP Proxy
- Access Control Lists (ACL)
- Web Caching
- Authentication
- Traffic Logging

---

# Squid Default Port

```text
3128/TCP
```

Verify:

```bash
ss -tulnp | grep 3128
```

---

# Install Squid

Install package:

```bash
dnf install squid -y
```

Verify installation:

```bash
rpm -qa | grep squid
```

---

# Start Squid Service

Start service:

```bash
systemctl start squid
```

Enable service:

```bash
systemctl enable squid
```

Verify status:

```bash
systemctl status squid
```

---

# Squid Configuration File

Location:

```text
/etc/squid/squid.conf
```

View:

```bash
cat /etc/squid/squid.conf
```

Edit:

```bash
vi /etc/squid/squid.conf
```

---

# Basic Configuration

Allow local network:

```conf
acl localnet src 192.168.1.0/24
http_access allow localnet
```

Deny all others:

```conf
http_access deny all
```

---

# Configure Proxy Port

Default:

```conf
http_port 3128
```

Custom port:

```conf
http_port 8080
```

---

# Restart Squid

After configuration changes:

```bash
systemctl restart squid
```

---

# Configure Firewall

Allow Squid port:

```bash
firewall-cmd --permanent --add-port=3128/tcp
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-ports
```

---

# Configure Client Browser

Proxy Settings:

```text
Proxy IP: 192.168.1.100
Port: 3128
```

---

# Test Proxy Server

Using curl:

```bash
curl -x http://192.168.1.100:3128 http://example.com
```

---

# Block Specific Website

Edit configuration:

```bash
vi /etc/squid/squid.conf
```

Create ACL:

```conf
acl blocked_sites dstdomain .facebook.com
http_access deny blocked_sites
```

Restart service:

```bash
systemctl restart squid
```

---

# Allow Specific Network

```conf
acl office_network src 192.168.1.0/24
http_access allow office_network
```

---

# Configure Logging

Access log:

```text
/var/log/squid/access.log
```

View logs:

```bash
tail -f /var/log/squid/access.log
```

Example:

```text
TCP_MISS/200 GET http://example.com
```

---

# Clear Squid Cache

Stop service:

```bash
systemctl stop squid
```

Clear cache:

```bash
rm -rf /var/spool/squid/*
```

Start service:

```bash
systemctl start squid
```

---

# Verify Listening Port

```bash
ss -tulnp | grep squid
```

Expected Output:

```text
LISTEN 0 128 *:3128
```

---

# Squid Directory Structure

```text
/etc/squid/
│
├── squid.conf
│
/var/log/squid/
│
├── access.log
├── cache.log
└── store.log
```

---

# Squid Service Management

Start:

```bash
systemctl start squid
```

Stop:

```bash
systemctl stop squid
```

Restart:

```bash
systemctl restart squid
```

Enable:

```bash
systemctl enable squid
```

Status:

```bash
systemctl status squid
```

---

# Troubleshooting

## Verify Service

```bash
systemctl status squid
```

---

## Verify Port

```bash
ss -tulnp | grep 3128
```

---

## Verify Firewall

```bash
firewall-cmd --list-ports
```

---

## Check Logs

```bash
tail -f /var/log/squid/access.log
```

```bash
tail -f /var/log/squid/cache.log
```

---

## Verify Configuration

```bash
squid -k parse
```

Expected Output:

```text
Configuration file parsed successfully
```

---

# Useful Commands

## Install Squid

```bash
dnf install squid -y
```

---

## Start Service

```bash
systemctl start squid
```

---

## Enable Service

```bash
systemctl enable squid
```

---

## Check Status

```bash
systemctl status squid
```

---

## Verify Configuration

```bash
squid -k parse
```

---

## View Logs

```bash
tail -f /var/log/squid/access.log
```

---

# RHCSA Notes

Important commands:

```bash
dnf install squid
```

```bash
systemctl start squid
```

```bash
systemctl enable squid
```

```bash
ss -tulnp | grep 3128
```

```bash
squid -k parse
```

```bash
tail -f /var/log/squid/access.log
```

Proxy servers are commonly used in enterprise environments for security, monitoring, and internet access control.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install squid | Install Squid |
| systemctl start squid | Start service |
| systemctl enable squid | Enable at boot |
| squid -k parse | Verify configuration |
| ss -tulnp | Verify proxy port |
| tail -f access.log | View proxy logs |

---

# Conclusion

Squid is a powerful Linux proxy server that provides web caching, internet access control, content filtering, and monitoring capabilities. Understanding Squid installation, configuration, ACLs, logging, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.