# DHCP Server (Dynamic Host Configuration Protocol)

## Overview

DHCP (Dynamic Host Configuration Protocol) is a network management protocol that automatically assigns IP addresses and other network settings to client devices.

DHCP eliminates the need to manually configure IP addresses for every device on a network.

DHCP provides:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server
- Lease Time

---

# What is DHCP?

DHCP dynamically assigns network configuration information to clients.

Architecture:

```text
+-------------+
| DHCP Server |
+-------------+
       |
       |
-------------------------
|           |           |
PC1         PC2       PC3
(Client)   (Client)  (Client)
```

---

# DHCP Process (DORA)

DHCP communication follows four steps:

```text
D - Discover
O - Offer
R - Request
A - Acknowledge
```

Workflow:

```text
Client  ---> DHCP Discover
Server  ---> DHCP Offer
Client  ---> DHCP Request
Server  ---> DHCP Acknowledge
```

---

# Install DHCP Server

Install package:

```bash
dnf install dhcp-server -y
```

Verify installation:

```bash
rpm -qa | grep dhcp
```

---

# DHCP Configuration File

Location:

```text
/etc/dhcp/dhcpd.conf
```

Edit:

```bash
vi /etc/dhcp/dhcpd.conf
```

---

# Basic DHCP Configuration

Example:

```conf
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.100.0 netmask 255.255.255.0 {

range 192.168.100.100 192.168.100.200;

option routers 192.168.100.1;

option subnet-mask 255.255.255.0;

option domain-name-servers 8.8.8.8, 8.8.4.4;

}
```

---

# Configuration Explanation

| Parameter | Description |
|------------|------------|
| range | IP Pool |
| routers | Gateway |
| subnet-mask | Network Mask |
| domain-name-servers | DNS Server |
| default-lease-time | Lease Duration |
| max-lease-time | Maximum Lease |

---

# Start DHCP Service

Start service:

```bash
systemctl start dhcpd
```

Enable at boot:

```bash
systemctl enable dhcpd
```

Verify status:

```bash
systemctl status dhcpd
```

---

# Configure Firewall

Allow DHCP service:

```bash
firewall-cmd --permanent --add-service=dhcp
```

Reload:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-services
```

---

# Verify DHCP Port

DHCP uses:

```text
UDP Port 67 (Server)
UDP Port 68 (Client)
```

Check:

```bash
ss -tulnp | grep dhcp
```

or

```bash
ss -tulnp | grep 67
```

---

# Reserve Static IP for a Client

Find MAC address:

```bash
ip link
```

Example:

```conf
host client1 {

hardware ethernet 08:00:27:12:34:56;

fixed-address 192.168.100.50;

}
```

Restart DHCP:

```bash
systemctl restart dhcpd
```

---

# DHCP Lease File

Location:

```text
/var/lib/dhcpd/dhcpd.leases
```

View leases:

```bash
cat /var/lib/dhcpd/dhcpd.leases
```

---

# Verify Client IP

On client machine:

```bash
ip addr
```

or

```bash
ip a
```

---

# Renew DHCP Lease

Client:

```bash
dhclient
```

Release current IP:

```bash
dhclient -r
```

Request new IP:

```bash
dhclient
```

---

# Check DHCP Logs

View logs:

```bash
journalctl -u dhcpd
```

Follow logs:

```bash
journalctl -fu dhcpd
```

---

# DHCP Service Management

Start:

```bash
systemctl start dhcpd
```

Stop:

```bash
systemctl stop dhcpd
```

Restart:

```bash
systemctl restart dhcpd
```

Enable:

```bash
systemctl enable dhcpd
```

Status:

```bash
systemctl status dhcpd
```

---

# Useful Commands

## Verify Package

```bash
rpm -qa | grep dhcp
```

---

## Check Service

```bash
systemctl status dhcpd
```

---

## View Configuration

```bash
cat /etc/dhcp/dhcpd.conf
```

---

## View Leases

```bash
cat /var/lib/dhcpd/dhcpd.leases
```

---

## Renew Client IP

```bash
dhclient
```

---

## Verify Listening Ports

```bash
ss -tulnp | grep 67
```

---

# Troubleshooting

## Verify Configuration

```bash
dhcpd -t
```

Expected:

```text
Configuration file is valid
```

---

## Check Service

```bash
systemctl status dhcpd
```

---

## Check Logs

```bash
journalctl -u dhcpd
```

---

## Verify Firewall

```bash
firewall-cmd --list-services
```

---

## Verify Network Interface

```bash
ip addr
```

---

# DHCP Directory Structure

```text
/etc/dhcp/
│
└── dhcpd.conf

/var/lib/dhcpd/
│
└── dhcpd.leases
```

---

# RHCSA Notes

Important commands:

```bash
dnf install dhcp-server
```

```bash
systemctl start dhcpd
```

```bash
systemctl enable dhcpd
```

```bash
dhcpd -t
```

```bash
journalctl -u dhcpd
```

```bash
dhclient
```

Understanding DHCP is important for Linux network administration and enterprise environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install dhcp-server | Install DHCP |
| systemctl start dhcpd | Start DHCP Service |
| systemctl enable dhcpd | Enable DHCP |
| dhcpd -t | Validate Configuration |
| dhclient | Request IP |
| journalctl -u dhcpd | View Logs |

---

# Conclusion

DHCP is a critical network service that automatically assigns IP addresses and network configuration information to clients. It simplifies network administration, reduces manual configuration errors, and improves scalability. Understanding DHCP installation, configuration, lease management, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.