# Network Files and Commands

## Overview

Linux provides various network configuration files and commands to manage, monitor, and troubleshoot network connectivity.

This document covers important network files and commonly used networking commands for RHCSA preparation.

---

# Important Network Files

## 1. /etc/hosts

Maps hostnames to IP addresses locally.

### Example

```text
127.0.0.1 localhost
192.168.1.10 server1
```

### View File

```bash
cat /etc/hosts
```

---

## 2. /etc/resolv.conf

Stores DNS server information.

### Example

```text
nameserver 8.8.8.8
nameserver 8.8.4.4
```

### View File

```bash
cat /etc/resolv.conf
```

---

## 3. /etc/hostname

Stores the system hostname.

### Example

```text
server1
```

### View File

```bash
cat /etc/hostname
```

---

## 4. Network Interface Configuration Files

RHEL-based systems store network configurations under:

```text
/etc/NetworkManager/system-connections/
```

### List Files

```bash
ls /etc/NetworkManager/system-connections/
```

---

# Network Commands

## ping

The ping command tests network connectivity between systems.

### Syntax

```bash
ping <hostname-or-ip>
```

### Example

```bash
ping google.com
```

### Send 4 Packets

```bash
ping -c 4 google.com
```

### Uses

- Check network connectivity
- Verify remote host availability
- Troubleshoot network issues

---

## ifup

The ifup command activates a network interface.

### Syntax

```bash
ifup <interface>
```

### Example

```bash
ifup ens160
```

### Uses

- Enable network interface
- Bring interface online

> Note: Modern RHEL versions use NetworkManager and nmcli instead of ifup.

---

## ifdown

The ifdown command deactivates a network interface.

### Syntax

```bash
ifdown <interface>
```

### Example

```bash
ifdown ens160
```

### Uses

- Disable network interface
- Bring interface offline

> Note: Modern RHEL versions use NetworkManager and nmcli instead of ifdown.

---

## netstat

Displays network connections, routing tables, interface statistics, and listening ports.

### Display All Connections

```bash
netstat -a
```

### Display Listening Ports

```bash
netstat -tuln
```

### Display Routing Table

```bash
netstat -r
```

### Uses

- Check open ports
- Verify services are listening
- Troubleshoot network issues

> Modern systems use the ss command instead of netstat.

### Alternative

```bash
ss -tulnp
```

---

## tcpdump

Captures and analyzes network packets.

### Syntax

```bash
tcpdump [options]
```

### Capture All Packets

```bash
sudo tcpdump
```

### Capture on Specific Interface

```bash
sudo tcpdump -i ens160
```

### Capture ICMP Packets

```bash
sudo tcpdump icmp
```

### Capture and Save to File

```bash
sudo tcpdump -w capture.pcap
```

### Read Saved Capture

```bash
sudo tcpdump -r capture.pcap
```

### Uses

- Network troubleshooting
- Packet analysis
- Security investigations
- Traffic monitoring

---

# Additional Useful Network Commands

## Display IP Address

```bash
ip addr
```

---

## Display Routing Table

```bash
ip route
```

---

## Display Network Interfaces

```bash
ip link
```

---

## Display DNS Information

```bash
cat /etc/resolv.conf
```

---

## Display Hostname

```bash
hostnamectl
```

---

# Common Troubleshooting Workflow

## Step 1: Check Interface Status

```bash
ip addr
```

## Step 2: Verify Connectivity

```bash
ping 8.8.8.8
```

## Step 3: Verify DNS Resolution

```bash
ping google.com
```

## Step 4: Check Open Ports

```bash
ss -tulnp
```

## Step 5: Capture Traffic

```bash
sudo tcpdump -i ens160
```

---

# Summary

| Command | Purpose |
|----------|----------|
| ping | Test network connectivity |
| ifup | Enable network interface |
| ifdown | Disable network interface |
| netstat | Display network information |
| tcpdump | Capture and analyze packets |
| ip addr | Display IP addresses |
| ip route | Display routing table |
| ss | Display active connections |

Understanding these files and commands is essential for Linux networking, troubleshooting, and RHCSA certification preparation.