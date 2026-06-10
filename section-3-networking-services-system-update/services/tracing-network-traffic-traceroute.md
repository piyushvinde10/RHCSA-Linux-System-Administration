# Tracing Network Traffic (traceroute)

## Overview

`traceroute` is a network diagnostic tool used to trace the path packets take from a source system to a destination system.

It helps administrators:

- Identify network paths
- Troubleshoot routing issues
- Detect network delays
- Locate packet loss
- Analyze network hops

---

# What is traceroute?

Traceroute displays every router (hop) that a packet passes through before reaching its destination.

Example:

```text
Client
   |
Router 1
   |
Router 2
   |
ISP Router
   |
Destination Server
```

---

# How traceroute Works

Traceroute uses:

```text
TTL (Time To Live)
```

TTL starts with:

```text
1 → 2 → 3 → 4 ...
```

Each router decreases TTL by 1.

When TTL reaches 0:

```text
Router sends ICMP Time Exceeded message
```

Traceroute records that router and continues.

---

# Install traceroute

RHEL / Rocky Linux / AlmaLinux:

```bash
dnf install traceroute -y
```

Verify:

```bash
rpm -qa | grep traceroute
```

---

# Basic Syntax

```bash
traceroute hostname
```

Example:

```bash
traceroute google.com
```

---

# Trace Route to an IP Address

```bash
traceroute 8.8.8.8
```

Example Output:

```text
1  192.168.1.1
2  10.0.0.1
3  172.16.0.1
4  8.8.8.8
```

---

# Trace Route to a Domain

```bash
traceroute google.com
```

---

# Display Numeric Addresses Only

```bash
traceroute -n google.com
```

Example:

```text
1 192.168.1.1
2 10.0.0.1
3 8.8.8.8
```

This avoids DNS lookups.

---

# Specify Maximum Hops

Default:

```text
30 hops
```

Set custom hops:

```bash
traceroute -m 10 google.com
```

---

# Change Packet Size

```bash
traceroute google.com 1000
```

Example:

```text
Packet Size = 1000 Bytes
```

---

# Use ICMP Instead of UDP

```bash
traceroute -I google.com
```

Useful when firewalls block UDP traffic.

---

# Use TCP Probes

```bash
traceroute -T google.com
```

Useful for web server troubleshooting.

---

# Set Wait Time

```bash
traceroute -w 5 google.com
```

Wait:

```text
5 Seconds
```

for each response.

---

# Set Number of Queries Per Hop

```bash
traceroute -q 5 google.com
```

Sends:

```text
5 Probes Per Hop
```

---

# Save Output to File

```bash
traceroute google.com > route.txt
```

View:

```bash
cat route.txt
```

---

# Understanding Output

Example:

```text
1 192.168.1.1 1.2 ms 1.3 ms 1.5 ms
2 10.0.0.1 4.0 ms 3.9 ms 4.1 ms
3 8.8.8.8 10.2 ms 10.4 ms 10.1 ms
```

Meaning:

| Column | Description |
|----------|----------|
| 1 | Hop Number |
| 192.168.1.1 | Router IP |
| 1.2 ms | Response Time |

---

# Missing Hop Example

```text
5 * * *
```

Meaning:

- Router did not respond
- Firewall blocked probe
- Packet filtered

---

# Traceroute vs Ping

| Feature | ping | traceroute |
|----------|----------|----------|
| Connectivity Test | Yes | Yes |
| Shows Network Path | No | Yes |
| Measures Latency | Yes | Yes |
| Shows Intermediate Routers | No | Yes |

---

# Common Troubleshooting

## Check Internet Route

```bash
traceroute google.com
```

---

## Verify Gateway Reachability

```bash
traceroute 8.8.8.8
```

---

## Detect Routing Loops

```bash
traceroute destination_ip
```

---

## Identify Slow Network Hop

```bash
traceroute hostname
```

Look for:

```text
High Response Time
```

---

# Related Commands

## Ping

```bash
ping google.com
```

---

## DNS Lookup

```bash
nslookup google.com
```

---

## Route Table

```bash
ip route
```

---

## Socket Information

```bash
ss -tulnp
```

---

# Useful Commands

## Basic Trace

```bash
traceroute google.com
```

---

## Numeric Output

```bash
traceroute -n google.com
```

---

## ICMP Trace

```bash
traceroute -I google.com
```

---

## TCP Trace

```bash
traceroute -T google.com
```

---

## Limit Hops

```bash
traceroute -m 10 google.com
```

---

# RHCSA Notes

Important commands:

```bash
dnf install traceroute
```

```bash
traceroute google.com
```

```bash
traceroute -n google.com
```

```bash
traceroute -I google.com
```

```bash
ip route
```

Traceroute is commonly used in Linux administration to diagnose network routing issues and connectivity problems.

---

# Summary

| Command | Purpose |
|----------|----------|
| traceroute google.com | Trace network path |
| traceroute -n google.com | Numeric output |
| traceroute -I google.com | Use ICMP |
| traceroute -T google.com | Use TCP |
| traceroute -m 10 google.com | Limit hops |
| ip route | View routing table |

---

# Conclusion

Traceroute is a powerful network troubleshooting tool that displays the path packets take through a network. It helps identify routing issues, network delays, unreachable routers, and connectivity problems. Understanding traceroute is an important Linux networking skill and useful for RHCSA preparation and real-world system administration.