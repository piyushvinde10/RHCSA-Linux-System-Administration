# NIC Bonding (Port Bonding)

## Overview

NIC Bonding, also known as Port Bonding or Network Bonding, is a technique used to combine multiple Network Interface Cards (NICs) into a single logical interface.

Bonding improves:

- Network redundancy (fault tolerance)
- High availability
- Load balancing
- Network performance

In Linux, the bonded interface is usually named:

```text
bond0
```

---

## Why Use NIC Bonding?

### Benefits

- Provides backup network links
- Prevents network downtime
- Increases bandwidth
- Improves network reliability

### Example

Without Bonding:

```text
Server
  |
 ens160
```

If the cable or NIC fails, network connectivity is lost.

With Bonding:

```text
          ens160
         /
Server -- bond0
         \
          ens192
```

If one NIC fails, the other NIC continues to provide connectivity.

---

## Bonding Modes

Linux supports multiple bonding modes.

### Mode 0 - Balance Round Robin

```text
mode=0
```

- Load balancing
- Fault tolerance
- Traffic distributed across all interfaces

---

### Mode 1 - Active Backup

```text
mode=1
```

- One active NIC
- One standby NIC
- Most commonly used
- Provides fault tolerance

---

### Mode 2 - Balance XOR

```text
mode=2
```

- Load balancing
- Fault tolerance
- Uses MAC address hashing

---

### Mode 3 - Broadcast

```text
mode=3
```

- Sends traffic through all interfaces
- High redundancy

---

### Mode 4 - LACP (802.3ad)

```text
mode=4
```

- Dynamic Link Aggregation
- Requires switch support
- High performance

---

### Mode 5 - Balance TLB

```text
mode=5
```

- Transmit Load Balancing
- No switch configuration required

---

### Mode 6 - Balance ALB

```text
mode=6
```

- Adaptive Load Balancing
- No switch configuration required

---

## Check Available Interfaces

Display NICs:

```bash
ip link show
```

Example:

```text
ens160
ens192
```

---

## Create Bond Interface Using nmcli

### Create bond0

```bash
nmcli connection add type bond ifname bond0 mode active-backup
```

---

### Assign IP Address

```bash
nmcli connection modify bond0 ipv4.addresses 192.168.1.100/24
nmcli connection modify bond0 ipv4.gateway 192.168.1.1
nmcli connection modify bond0 ipv4.method manual
```

---

### Add Slave Interfaces

```bash
nmcli connection add type ethernet slave-type bond ifname ens160 master bond0
```

```bash
nmcli connection add type ethernet slave-type bond ifname ens192 master bond0
```

---

### Activate Bond

```bash
nmcli connection up bond0
```

---

## Verify Bonding

Display bond information:

```bash
cat /proc/net/bonding/bond0
```

Example Output:

```text
Bonding Mode: fault-tolerance (active-backup)

Primary Slave: ens160

Currently Active Slave: ens160
```

---

## Display Network Connections

```bash
nmcli connection show
```

---

## Display Interface Information

```bash
ip addr show bond0
```

---

## Check Bond Status

```bash
cat /proc/net/bonding/bond0
```

---

## Test Bond Failover

### Check Active Interface

```bash
cat /proc/net/bonding/bond0
```

### Bring Down Active Interface

```bash
ip link set ens160 down
```

### Verify Backup Interface Becomes Active

```bash
cat /proc/net/bonding/bond0
```

---

## Common Troubleshooting Commands

Display Interfaces:

```bash
ip link
```

Display IP Address:

```bash
ip addr
```

Display Connections:

```bash
nmcli connection show
```

Display Bond Information:

```bash
cat /proc/net/bonding/bond0
```

Check Connectivity:

```bash
ping 8.8.8.8
```

---

## Summary

| Command | Purpose |
|----------|----------|
| ip link show | Display interfaces |
| nmcli connection show | Display connections |
| nmcli connection add | Create bond |
| nmcli connection up bond0 | Activate bond |
| ip addr show bond0 | Display bond IP |
| cat /proc/net/bonding/bond0 | Display bond status |

---

## Conclusion

NIC Bonding combines multiple network interfaces into a single logical interface to provide redundancy, fault tolerance, and increased availability.

For RHCSA and enterprise Linux environments, Active-Backup (Mode 1) is the most commonly used bonding mode because it provides simple and reliable network failover.