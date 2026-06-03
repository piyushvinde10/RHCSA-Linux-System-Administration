# NIC Information using ethtool

## Overview

`ethtool` is a Linux command-line utility used to display and modify Network Interface Card (NIC) settings.

It helps administrators troubleshoot network issues, verify link status, check speed and duplex settings, and gather hardware information about network interfaces.

---

# What is a NIC?

A **Network Interface Card (NIC)** is a hardware component that allows a system to communicate over a network.

Examples:

- ens160
- ens192
- eth0
- eno1

---

# Installing ethtool

## RHEL / CentOS / Rocky Linux

```bash
sudo yum install ethtool -y
```

## Verify Installation

```bash
ethtool --version
```

---

# Display NIC Information

## Syntax

```bash
ethtool <interface-name>
```

## Example

```bash
ethtool ens160
```

### Sample Output

```text
Settings for ens160:
    Supported ports: [ TP ]
    Supported link modes: 1000baseT/Full
    Speed: 1000Mb/s
    Duplex: Full
    Auto-negotiation: on
    Link detected: yes
```

---

# Important Fields

| Field | Description |
|---------|-------------|
| Speed | Current NIC speed |
| Duplex | Half or Full duplex |
| Auto-negotiation | Automatic speed negotiation |
| Link detected | Indicates network cable connection |
| Supported ports | Supported network media |

---

# Check Driver Information

Display NIC driver details:

```bash
ethtool -i ens160
```

### Sample Output

```text
driver: vmxnet3
version: 1.0.0
firmware-version:
```

---

# Display NIC Statistics

View packet statistics:

```bash
ethtool -S ens160
```

### Information Provided

- Packets transmitted
- Packets received
- Errors
- Dropped packets

---

# Check Link Status

Display whether the network cable is connected:

```bash
ethtool ens160 | grep "Link detected"
```

### Example Output

```text
Link detected: yes
```

---

# Display Speed Information

```bash
ethtool ens160 | grep Speed
```

### Example Output

```text
Speed: 1000Mb/s
```

---

# Display Duplex Information

```bash
ethtool ens160 | grep Duplex
```

### Example Output

```text
Duplex: Full
```

---

# Display All Network Interfaces

Before using ethtool, identify interface names:

```bash
ip link show
```

or

```bash
nmcli device status
```

---

# Common Troubleshooting Commands

## Verify Interface Status

```bash
ip addr
```

---

## Check Link Status

```bash
ethtool ens160
```

---

## Verify Driver Information

```bash
ethtool -i ens160
```

---

## Display Statistics

```bash
ethtool -S ens160
```

---

## Test Connectivity

```bash
ping 8.8.8.8
```

---

# Practical RHCSA Examples

## Check Network Card Speed

```bash
ethtool ens160 | grep Speed
```

## Verify Cable Connection

```bash
ethtool ens160 | grep "Link detected"
```

## View Driver Information

```bash
ethtool -i ens160
```

## View NIC Statistics

```bash
ethtool -S ens160
```

---

# Summary

| Command | Purpose |
|----------|----------|
| ethtool ens160 | Display NIC information |
| ethtool -i ens160 | Display driver details |
| ethtool -S ens160 | Display NIC statistics |
| ip link show | Display interfaces |
| ip addr | Display IP addresses |
| nmcli device status | Display network device status |

---

# Conclusion

The `ethtool` command is an essential Linux networking utility used to inspect and troubleshoot Network Interface Cards (NICs). It provides information about speed, duplex mode, link status, driver details, and interface statistics, making it a valuable tool for RHCSA preparation and real-world system administration.