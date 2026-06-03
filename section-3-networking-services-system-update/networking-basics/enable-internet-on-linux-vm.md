# Enable Internet on Linux Virtual Machine

## Objective

This guide explains how to enable internet connectivity on a Linux Virtual Machine (VM) using VirtualBox or VMware.

---

## Step 1: Configure VM Network Adapter

### VirtualBox

1. Power off the VM.
2. Open **Settings → Network**.
3. Enable **Adapter 1**.
4. Select **NAT** or **Bridged Adapter**.
5. Start the VM.

### VMware

1. Power off the VM.
2. Open **Virtual Machine Settings**.
3. Select **Network Adapter**.
4. Choose **NAT** or **Bridged**.
5. Start the VM.

---

## Step 2: Check Network Interface

Display available network interfaces:

```bash
ip addr
```

or

```bash
nmcli device status
```

Example Output:

```text
ens160    connected
lo        unmanaged
```

---

## Step 3: Enable Network Interface

Bring the interface up:

```bash
sudo nmcli connection up ens160
```

or

```bash
sudo ip link set ens160 up
```

---

## Step 4: Obtain an IP Address

Request an IP address from the DHCP server:

```bash
sudo dhclient ens160
```

Verify the IP address:

```bash
ip addr show ens160
```

---

## Step 5: Verify Default Gateway

Check routing information:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev ens160
```

---

## Step 6: Verify DNS Configuration

Check DNS servers:

```bash
cat /etc/resolv.conf
```

Example:

```text
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

## Step 7: Test Connectivity

### Test Local Network

```bash
ping -c 4 192.168.1.1
```

### Test Internet Connectivity

```bash
ping -c 4 8.8.8.8
```

### Test DNS Resolution

```bash
ping -c 4 google.com
```

---

## Step 8: Restart Network Service

Restart NetworkManager:

```bash
sudo systemctl restart NetworkManager
```

Verify service status:

```bash
sudo systemctl status NetworkManager
```

---

## Useful Troubleshooting Commands

Display IP Address:

```bash
ip addr
```

Display Routing Table:

```bash
ip route
```

Display DNS Configuration:

```bash
cat /etc/resolv.conf
```

Display Network Connections:

```bash
nmcli connection show
```

Display Network Devices:

```bash
nmcli device status
```

---

## Common Issues

### No IP Address

```bash
sudo dhclient <interface-name>
```

### Interface Down

```bash
sudo ip link set <interface-name> up
```

### DNS Not Working

Add public DNS servers:

```text
nameserver 8.8.8.8
nameserver 8.8.4.4
```

### Incorrect VM Network Mode

Ensure the adapter is configured as:

- NAT
- Bridged Adapter

---

## Summary

To enable internet access on a Linux VM:

1. Configure the VM network adapter.
2. Verify the network interface.
3. Obtain an IP address.
4. Verify routing information.
5. Check DNS configuration.
6. Test connectivity.
7. Restart NetworkManager if required.

These are common RHCSA networking tasks and troubleshooting steps.