# Network Components

## Overview

Network components are the hardware and software elements that enable communication between devices in a network.

Understanding these components is essential for Linux System Administration and RHCSA certification.

---

## Network Interface Card (NIC)

A Network Interface Card (NIC) is a hardware component that allows a computer to connect to a network.

### Functions

- Provides network connectivity
- Sends and receives data packets
- Has a unique MAC address

### Check NIC Information

```bash
ip link show
```

---

## IP Address

An IP Address is a unique identifier assigned to a device on a network.

### Types

- IPv4
- IPv6

### Example IPv4 Address

```text
192.168.1.10
```

### Check IP Address

```bash
ip addr
```

---

## MAC Address

A MAC (Media Access Control) Address is a unique physical address assigned to a network interface.

### Example

```text
08:00:27:ab:cd:ef
```

### Display MAC Address

```bash
ip link
```

---

## Switch

A Switch is a networking device that connects multiple devices within the same network.

### Functions

- Transfers data between devices
- Uses MAC addresses for communication
- Reduces network collisions

### Example

```text
PC1 ----|
PC2 ----|---- Switch
PC3 ----|
```

---

## Router

A Router connects different networks and forwards data between them.

### Functions

- Connects LAN to WAN
- Routes packets
- Provides internet access

### Example

```text
LAN ---> Router ---> Internet
```

### View Default Gateway

```bash
ip route
```

---

## Gateway

A Gateway is the device through which network traffic exits the local network.

### Example

```text
Default Gateway: 192.168.1.1
```

### Check Gateway

```bash
ip route
```

---

## DNS Server

DNS (Domain Name System) translates domain names into IP addresses.

### Example

```text
google.com -> 142.250.x.x
```

### Check DNS Configuration

```bash
cat /etc/resolv.conf
```

---

## DHCP Server

DHCP (Dynamic Host Configuration Protocol) automatically assigns:

- IP Address
- Subnet Mask
- Gateway
- DNS Server

### Obtain IP Address

```bash
dhclient
```

---

## Firewall

A Firewall controls incoming and outgoing network traffic.

### Check Firewall Status

```bash
sudo firewall-cmd --state
```

### List Firewall Rules

```bash
sudo firewall-cmd --list-all
```

---

## Subnet Mask

A Subnet Mask separates the network portion and host portion of an IP address.

### Example

```text
255.255.255.0
```

or

```text
/24
```

---

## Network Topology

Network Topology refers to the physical or logical arrangement of devices.

### Common Types

- Star Topology
- Bus Topology
- Ring Topology
- Mesh Topology

### Star Topology

```text
      PC1
       |
PC2 -- Switch -- PC3
       |
      PC4
```

---

## Linux Commands for Network Information

### Display IP Address

```bash
ip addr
```

### Display Network Interfaces

```bash
ip link
```

### Display Routing Table

```bash
ip route
```

### Test Connectivity

```bash
ping google.com
```

### Display Open Ports

```bash
ss -tulnp
```

### DNS Lookup

```bash
nslookup google.com
```

---

## Network Communication Flow

```text
Client
   |
   | Request
   v
Switch
   |
   v
Router
   |
   v
Internet
   |
   v
Server

Server
   |
   | Response
   v
Client
```

---

## Summary

The main network components include:

- Network Interface Card (NIC)
- IP Address
- MAC Address
- Switch
- Router
- Gateway
- DNS Server
- DHCP Server
- Firewall
- Subnet Mask

Understanding these components helps Linux administrators configure, troubleshoot, and manage network connectivity effectively.