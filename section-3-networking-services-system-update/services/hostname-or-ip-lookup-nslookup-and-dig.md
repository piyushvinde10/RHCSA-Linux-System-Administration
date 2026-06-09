# Hostname or IP Lookup (nslookup and dig)

## Overview

DNS lookup tools help administrators verify hostname-to-IP and IP-to-hostname resolution.

The two most commonly used DNS troubleshooting tools are:

- `nslookup`
- `dig`

These tools are used to:

- Verify DNS records
- Troubleshoot name resolution issues
- Query DNS servers
- Check forward and reverse lookups

---

# What is DNS Lookup?

DNS lookup is the process of converting:

```text
Hostname → IP Address
```

Example:

```text
google.com → 142.250.193.78
```

and

```text
IP Address → Hostname
```

Example:

```text
8.8.8.8 → dns.google
```

---

# nslookup Command

`nslookup` stands for:

```text
Name Server Lookup
```

It is used to query DNS servers and retrieve DNS records.

---

# Basic Syntax

```bash
nslookup hostname
```

Example:

```bash
nslookup google.com
```

Output:

```text
Name: google.com
Address: 142.250.193.78
```

---

# Lookup a Hostname

```bash
nslookup github.com
```

---

# Reverse Lookup

Find hostname from IP address:

```bash
nslookup 8.8.8.8
```

Output:

```text
8.8.8.8.in-addr.arpa
name = dns.google
```

---

# Query Specific DNS Server

```bash
nslookup google.com 8.8.8.8
```

Example:

```bash
nslookup github.com 1.1.1.1
```

---

# Interactive Mode

Start interactive mode:

```bash
nslookup
```

Example:

```text
> google.com
> github.com
> exit
```

---

# dig Command

`dig` stands for:

```text
Domain Information Groper
```

It is an advanced DNS troubleshooting tool included in the bind-utils package.

---

# Install dig

```bash
dnf install bind-utils -y
```

Verify:

```bash
which dig
```

---

# Basic Syntax

```bash
dig hostname
```

Example:

```bash
dig google.com
```

---

# Lookup A Record

```bash
dig google.com
```

Example Output:

```text
ANSWER SECTION:
google.com. 300 IN A 142.250.193.78
```

---

# Reverse Lookup

```bash
dig -x 8.8.8.8
```

Output:

```text
ANSWER SECTION:
8.8.8.8.in-addr.arpa PTR dns.google.
```

---

# Query Specific DNS Server

```bash
dig @8.8.8.8 google.com
```

Example:

```bash
dig @1.1.1.1 github.com
```

---

# Short Output

```bash
dig +short google.com
```

Output:

```text
142.250.193.78
```

---

# Lookup MX Records

```bash
dig google.com MX
```

Output:

```text
google.com. IN MX 10 smtp.google.com.
```

---

# Lookup NS Records

```bash
dig google.com NS
```

---

# Lookup CNAME Records

```bash
dig www.github.com CNAME
```

---

# Lookup All Records

```bash
dig google.com ANY
```

---

# Compare nslookup and dig

| Feature | nslookup | dig |
|----------|-----------|------|
| Simple Output | Yes | No |
| Detailed Output | Limited | Yes |
| DNS Troubleshooting | Basic | Advanced |
| Reverse Lookup | Yes | Yes |
| Query Specific Server | Yes | Yes |
| Preferred by Admins | No | Yes |

---

# Common DNS Records

| Record | Purpose |
|----------|----------|
| A | Hostname → IPv4 |
| AAAA | Hostname → IPv6 |
| PTR | IP → Hostname |
| MX | Mail Server |
| NS | Name Server |
| CNAME | Alias Record |
| TXT | Text Information |

---

# DNS Troubleshooting Examples

## Verify DNS Resolution

```bash
nslookup google.com
```

or

```bash
dig google.com
```

---

## Verify Reverse Lookup

```bash
nslookup 8.8.8.8
```

or

```bash
dig -x 8.8.8.8
```

---

## Check DNS Server Response

```bash
dig @8.8.8.8 google.com
```

---

## Check Mail Records

```bash
dig google.com MX
```

---

## Check Name Servers

```bash
dig google.com NS
```

---

# Verify DNS Configuration

Check configured DNS server:

```bash
cat /etc/resolv.conf
```

Example:

```text
nameserver 8.8.8.8
```

---

# Useful Commands

## Hostname Lookup

```bash
nslookup hostname
```

```bash
dig hostname
```

---

## Reverse Lookup

```bash
nslookup IP
```

```bash
dig -x IP
```

---

## Short Output

```bash
dig +short hostname
```

---

## Query DNS Server

```bash
dig @DNS_SERVER hostname
```

---

# RHCSA Notes

Important commands:

```bash
nslookup hostname
```

```bash
dig hostname
```

```bash
dig +short hostname
```

```bash
dig -x IP
```

```bash
cat /etc/resolv.conf
```

These commands are frequently used for DNS troubleshooting and network diagnostics in Linux environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| nslookup google.com | Hostname lookup |
| nslookup 8.8.8.8 | Reverse lookup |
| dig google.com | Detailed DNS query |
| dig -x 8.8.8.8 | Reverse DNS lookup |
| dig +short google.com | Short output |
| dig google.com MX | Mail server records |
| dig google.com NS | Name server records |

---

# Conclusion

`nslookup` and `dig` are essential DNS troubleshooting tools used by Linux administrators. They help verify hostname resolution, reverse lookups, DNS records, and DNS server responses. Understanding these commands is important for RHCSA preparation and real-world Linux network administration.