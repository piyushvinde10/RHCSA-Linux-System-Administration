# New Network Utilities (nmtui, nmcli, nm-connection-editor and GNOME Settings)

## Overview

Modern Linux distributions use **NetworkManager** to manage network configurations.

NetworkManager provides multiple tools to configure and manage networking:

- nmtui
- nmcli
- nm-connection-editor
- GNOME Settings

These tools simplify network administration and are commonly used in RHCSA environments.

---

# NetworkManager

NetworkManager is a service that manages network devices and connections.

## Check NetworkManager Status

```bash
systemctl status NetworkManager
```

## Start NetworkManager

```bash
sudo systemctl start NetworkManager
```

## Enable NetworkManager at Boot

```bash
sudo systemctl enable NetworkManager
```

---

# nmtui (Network Manager Text User Interface)

## Overview

`nmtui` is a text-based interface used to configure network settings from the terminal.

It is useful on servers without a graphical interface.

---

## Launch nmtui

```bash
nmtui
```

### Main Menu

```text
+-------------------------+
| Edit a connection       |
| Activate a connection   |
| Set system hostname     |
| Quit                    |
+-------------------------+
```

---

## Common Tasks

### Configure Static IP

1. Run:

```bash
nmtui
```

2. Select:

```text
Edit a connection
```

3. Choose network interface.

4. Configure:
   - IP Address
   - Gateway
   - DNS Server

5. Save changes.

---

## Activate Connection

```text
Activate a connection
```

---

# nmcli (Network Manager Command Line Interface)

## Overview

`nmcli` is a command-line utility used to manage NetworkManager.

It is one of the most important networking tools for RHCSA.

---

## Display Network Devices

```bash
nmcli device status
```

Example:

```text
DEVICE   TYPE      STATE      CONNECTION
ens160   ethernet  connected  ens160
```

---

## Display Connections

```bash
nmcli connection show
```

---

## Display IP Address

```bash
nmcli device show
```

---

## Bring Connection Up

```bash
nmcli connection up ens160
```

---

## Bring Connection Down

```bash
nmcli connection down ens160
```

---

## Configure Static IP

```bash
nmcli connection modify ens160 \
ipv4.addresses 192.168.1.100/24 \
ipv4.gateway 192.168.1.1 \
ipv4.dns 8.8.8.8 \
ipv4.method manual
```

Activate configuration:

```bash
nmcli connection up ens160
```

---

## Configure DHCP

```bash
nmcli connection modify ens160 ipv4.method auto
```

Restart connection:

```bash
nmcli connection up ens160
```

---

# nm-connection-editor

## Overview

`nm-connection-editor` is a graphical network configuration tool.

It provides an advanced GUI for managing network settings.

---

## Launch Tool

```bash
nm-connection-editor
```

---

## Features

- Configure Static IP
- Configure DHCP
- Configure DNS
- Configure Routes
- Configure VLANs
- Configure Bonding
- Configure Teaming

---

## Typical Workflow

1. Launch:

```bash
nm-connection-editor
```

2. Select Network Interface.

3. Edit:
   - IPv4 Settings
   - IPv6 Settings
   - DNS
   - Routes

4. Save configuration.

---

# GNOME Settings

## Overview

GNOME Settings provides a simple graphical interface for network configuration.

Best suited for desktop environments.

---

## Open Network Settings

```text
Settings → Network
```

---

## Features

- Configure Wired Connections
- Configure Wi-Fi
- Set Static IP
- Configure DNS
- Configure Proxy Settings

---

## Configure Static IP

1. Open:

```text
Settings → Network
```

2. Select Network Interface.

3. Click Settings.

4. Navigate to:

```text
IPv4
```

5. Select:

```text
Manual
```

6. Enter:
   - IP Address
   - Netmask
   - Gateway
   - DNS

7. Apply configuration.

---

# Useful NetworkManager Commands

## Display Interfaces

```bash
ip link show
```

---

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

## Display Active Connections

```bash
nmcli connection show --active
```

---

## Restart NetworkManager

```bash
sudo systemctl restart NetworkManager
```

---

## Check Connectivity

```bash
ping google.com
```

---

# Comparison of Network Utilities

| Tool | Interface Type | Environment |
|--------|---------------|-------------|
| nmtui | Text-based UI | Terminal |
| nmcli | Command Line | Terminal |
| nm-connection-editor | Graphical UI | Desktop |
| GNOME Settings | Graphical UI | Desktop |

---

# RHCSA Notes

For RHCSA exam preparation:

- Learn nmcli thoroughly.
- Understand nmtui navigation.
- Practice static and dynamic IP configuration.
- Verify settings using ip and nmcli commands.

The RHCSA exam commonly uses NetworkManager-based networking tasks.

---

# Summary

| Utility | Purpose |
|-----------|----------|
| nmtui | Text-based network configuration |
| nmcli | Command-line network management |
| nm-connection-editor | Advanced GUI network editor |
| GNOME Settings | Desktop network configuration |
| NetworkManager | Network management service |

These tools are essential for configuring and troubleshooting networking on modern Linux systems.