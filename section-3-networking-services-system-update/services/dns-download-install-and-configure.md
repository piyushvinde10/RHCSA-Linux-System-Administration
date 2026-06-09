# DNS - Download, Install and Configure (Domain Name System)

## Overview

DNS (Domain Name System) translates hostnames into IP addresses and IP addresses into hostnames.

Examples:

```text
google.com        → 142.250.193.78
192.168.1.10      → server.lab.local
```

DNS eliminates the need to remember IP addresses and allows users to access systems using hostnames.

---

# What is DNS?

DNS is a distributed database that stores:

- Hostname to IP mappings
- IP to Hostname mappings
- Mail server information
- Alias records

Common Record Types:

| Record | Purpose |
|----------|----------|
| A | Hostname → IP Address |
| PTR | IP Address → Hostname |
| CNAME | Hostname Alias |
| MX | Mail Server |
| NS | Name Server |
| SOA | Start of Authority |

---

# DNS Components

## BIND

BIND stands for:

```text
Berkeley Internet Name Domain
```

Main DNS service:

```text
named
```

Package name:

```text
bind
```

Utilities:

```text
named
rndc
dig
nslookup
host
```

---

# DNS Ports

| Protocol | Port |
|-----------|------|
| UDP | 53 |
| TCP | 53 |

DNS queries typically use UDP port 53.

---

# DNS Configuration Files

| File | Purpose |
|--------|---------|
| /etc/named.conf | Main configuration file |
| /var/named | Zone files |
| /etc/rndc.conf | Remote DNS administration |

---

# DNS Server Types

## Primary DNS Server

Stores original zone files.

---

## Secondary DNS Server

Receives zone transfers from primary server.

---

## Caching DNS Server

Caches DNS responses to improve performance.

---

## Forwarding DNS Server

Forwards DNS requests to another DNS server.

---

# Install DNS Server

Install BIND packages:

```bash
dnf install bind bind-utils -y
```

Verify:

```bash
rpm -qa | grep bind
```

---

# Configure DNS Server

Edit configuration file:

```bash
vi /etc/named.conf
```

Modify:

```conf
listen-on port 53 { 127.0.0.1; 192.168.1.100; };
```

---

## Add Forward Zone

```conf
zone "lab.local" IN {
        type master;
        file "forward.lab";
        allow-update { none; };
};
```

---

## Add Reverse Zone

```conf
zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "reverse.lab";
        allow-update { none; };
};
```

---

# Create Zone Files

Move to zone directory:

```bash
cd /var/named
```

Create files:

```bash
touch forward.lab
touch reverse.lab
```

---

# Configure Forward Zone

Edit:

```bash
vi /var/named/forward.lab
```

Example:

```dns
$TTL 86400

@ IN SOA masterdns.lab.local. root.lab.local. (
        2026010101
        3600
        1800
        604800
        86400 )

@           IN NS masterdns.lab.local.

@           IN A 192.168.1.100

masterdns   IN A 192.168.1.100
clienta     IN A 192.168.1.101
clientb     IN A 192.168.1.102
```

---

# Configure Reverse Zone

Edit:

```bash
vi /var/named/reverse.lab
```

Example:

```dns
$TTL 86400

@ IN SOA masterdns.lab.local. root.lab.local. (
        2026010101
        3600
        1800
        604800
        86400 )

@ IN NS masterdns.lab.local.

100 IN PTR masterdns.lab.local.
101 IN PTR clienta.lab.local.
102 IN PTR clientb.lab.local.
```

---

# Configure Permissions

```bash
chgrp named -R /var/named
chown root:named /etc/named.conf
```

Restore SELinux contexts:

```bash
restorecon -rv /var/named
restorecon /etc/named.conf
```

---

# Verify DNS Configuration

Check syntax:

```bash
named-checkconf /etc/named.conf
```

Check forward zone:

```bash
named-checkzone lab.local /var/named/forward.lab
```

Check reverse zone:

```bash
named-checkzone lab.local /var/named/reverse.lab
```

---

# Start DNS Service

Start service:

```bash
systemctl start named
```

Enable at boot:

```bash
systemctl enable named
```

Verify:

```bash
systemctl status named
```

---

# Configure DNS Client

Edit network configuration:

```bash
vi /etc/resolv.conf
```

Add:

```text
nameserver 192.168.1.100
```

---

# Restart Network

```bash
systemctl restart NetworkManager
```

---

# Test DNS Server

Using dig:

```bash
dig masterdns.lab.local
```

---

Using nslookup:

```bash
nslookup masterdns.lab.local
```

```bash
nslookup clienta.lab.local
```

```bash
nslookup 192.168.1.101
```

---

Using host:

```bash
host masterdns.lab.local
```

---

# DNS Resource Records

## A Record

Hostname to IP mapping.

Example:

```dns
server1 IN A 192.168.1.10
```

---

## PTR Record

IP to hostname mapping.

Example:

```dns
10 IN PTR server1.lab.local.
```

---

## CNAME Record

Alias record.

Example:

```dns
www IN CNAME server1
```

---

## MX Record

Mail server record.

Example:

```dns
@ IN MX 10 mail.lab.local.
```

---

## NS Record

Name server record.

Example:

```dns
@ IN NS masterdns.lab.local.
```

---

## SOA Record

Start of Authority record.

Contains:

- Serial number
- Refresh interval
- Retry interval
- Expire time
- TTL

---

# DNS Administration using rndc

Check DNS status:

```bash
rndc status
```

Reload configuration:

```bash
rndc reload
```

Reload specific zone:

```bash
rndc reload lab.local
```

Reload new zones:

```bash
rndc reconfig
```

---

# Troubleshooting

Check DNS service:

```bash
systemctl status named
```

Check listening port:

```bash
ss -tulnp | grep 53
```

Check logs:

```bash
journalctl -u named
```

Verify resolver:

```bash
cat /etc/resolv.conf
```

---

# Useful Commands

```bash
dig hostname
```

```bash
nslookup hostname
```

```bash
host hostname
```

```bash
named-checkconf
```

```bash
named-checkzone
```

```bash
rndc status
```

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install bind bind-utils | Install DNS |
| systemctl start named | Start DNS service |
| named-checkconf | Check DNS configuration |
| named-checkzone | Check zone files |
| dig hostname | DNS lookup |
| nslookup hostname | DNS lookup |
| host hostname | DNS lookup |
| rndc reload | Reload DNS |

---

# Conclusion

DNS is a critical network service that translates hostnames into IP addresses and vice versa. Understanding BIND installation, zone files, resource records, forward and reverse lookups, and DNS troubleshooting is essential for RHCSA and Linux system administration.