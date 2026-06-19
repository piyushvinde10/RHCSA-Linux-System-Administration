# Installing, Configuring and Managing OpenVPN

## Overview

OpenVPN is an open-source Virtual Private Network (VPN) solution used to create secure encrypted connections between clients and servers.

OpenVPN provides:

- Secure Remote Access
- Site-to-Site Connectivity
- Data Encryption
- Authentication
- Secure Communication over Public Networks

---

# What is VPN?

VPN stands for:

```text
Virtual Private Network
```

A VPN creates a secure tunnel between client and server.

Architecture:

```text
Client
   |
Encrypted Tunnel
   |
OpenVPN Server
   |
Private Network
```

---

# OpenVPN Components

| Component | Purpose |
|------------|----------|
| OpenVPN Server | VPN Server |
| OpenVPN Client | VPN Client |
| Easy-RSA | Certificate Management |
| CA Certificate | Certificate Authority |
| Server Certificate | Server Authentication |
| Client Certificate | Client Authentication |

---

# Install OpenVPN and Easy-RSA

Install EPEL Repository:

```bash
dnf install epel-release -y
```

Check existing installation:

```bash
rpm -qa | grep openvpn
```

Install packages:

```bash
dnf install openvpn easy-rsa -y
```

---

# Setup Easy-RSA

Copy Easy-RSA files:

```bash
cp -rv /usr/share/easy-rsa/3.1.6/* /etc/openvpn/
```

Move to OpenVPN directory:

```bash
cd /etc/openvpn/
```

Initialize PKI:

```bash
./easyrsa init-pki
```

---

# Create Certificate Authority (CA)

```bash
./easyrsa build-ca nopass
```

---

# Generate Server Certificate

Create request:

```bash
./easyrsa gen-req server nopass
```

Sign certificate:

```bash
./easyrsa sign-req server server
```

---

# Generate Client Certificate

Create request:

```bash
./easyrsa gen-req client nopass
```

Sign certificate:

```bash
./easyrsa sign-req client client
```

---

# Generate Diffie-Hellman Parameters

```bash
./easyrsa gen-dh
```

---

# Generate TLS Authentication Key

```bash
openvpn --genkey secret ta.key
```

---

# Move Certificates and Keys

```bash
mv pki/ca.crt pki/dh.pem /etc/openvpn/
```

```bash
mv pki/issued/server.crt /etc/openvpn/
```

```bash
mv pki/private/server.key /etc/openvpn/
```

---

# Configure OpenVPN Server

Copy sample configuration:

```bash
cp -rv \
/usr/share/doc/openvpn/sample/sample-config-files/server.conf \
/etc/openvpn/server/
```

Edit configuration:

```bash
vi /etc/openvpn/server/server.conf
```

---

# Enable IP Forwarding

Edit:

```bash
vi /etc/sysctl.conf
```

Add:

```conf
net.ipv4.ip_forward = 1
```

Apply changes:

```bash
sysctl -p
```

Verify:

```bash
sysctl net.ipv4.ip_forward
```

Expected:

```text
net.ipv4.ip_forward = 1
```

---

# Secure Certificates and Keys

```bash
chmod 600 \
/etc/openvpn/server/server.conf \
/etc/openvpn/*.key \
/etc/openvpn/*.crt
```

---

# Configure Firewall

Allow OpenVPN:

```bash
firewall-cmd --add-service=openvpn --permanent
```

Enable masquerading:

```bash
firewall-cmd --add-masquerade --permanent
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-all
```

---

# Start OpenVPN Server

Start service:

```bash
systemctl start openvpn-server@server.service
```

Enable at boot:

```bash
systemctl enable openvpn-server@server.service
```

Verify status:

```bash
systemctl status openvpn-server@server.service
```

---

# OpenVPN Client Setup

Install OpenVPN:

```bash
dnf install openvpn -y
```

Move to directory:

```bash
cd /etc/openvpn/
```

---

# Copy Client Certificates

```bash
scp \
/etc/openvpn/ca.crt \
/etc/openvpn/ta.key \
/etc/openvpn/pki/issued/client.crt \
/etc/openvpn/pki/private/client.key \
root@CLIENT-IP:/etc/openvpn/
```

Example:

```bash
root@192.168.100.178:/etc/openvpn/
```

---

# Configure Client

Copy sample configuration:

```bash
cp \
/usr/share/doc/openvpn/sample/sample-config-files/client.conf \
/etc/openvpn/client/
```

Edit:

```bash
vi /etc/openvpn/client/client.conf
```

Update:

```conf
remote 192.168.100.167 1194
```

Replace with your VPN server IP.

---

# Secure Client Files

```bash
chmod 600 \
/etc/openvpn/*.key \
/etc/openvpn/*.crt \
/etc/openvpn/client/client.conf
```

---

# Connect Client

Start VPN:

```bash
openvpn --config /etc/openvpn/client/client.conf
```

---

# Verify OpenVPN Port

Default Port:

```text
1194/UDP
```

Check:

```bash
ss -tulnp | grep 1194
```

---

# OpenVPN Service Management

Start:

```bash
systemctl start openvpn-server@server.service
```

Stop:

```bash
systemctl stop openvpn-server@server.service
```

Restart:

```bash
systemctl restart openvpn-server@server.service
```

Status:

```bash
systemctl status openvpn-server@server.service
```

---

# Useful Commands

## Check Version

```bash
openvpn --version
```

---

## Verify Service

```bash
systemctl status openvpn-server@server.service
```

---

## Verify Port

```bash
ss -tulnp | grep 1194
```

---

## Verify Firewall

```bash
firewall-cmd --list-all
```

---

## Verify IP Forwarding

```bash
sysctl net.ipv4.ip_forward
```

---

# Troubleshooting

## Check Service Logs

```bash
journalctl -u openvpn-server@server.service
```

---

## Verify Port

```bash
ss -tulnp | grep 1194
```

---

## Verify Firewall

```bash
firewall-cmd --list-all
```

---

## Verify Configuration

```bash
cat /etc/openvpn/server/server.conf
```

---

## Test Connectivity

```bash
ping VPN_SERVER_IP
```

---

# RHCSA Notes

Important commands:

```bash
dnf install openvpn easy-rsa
```

```bash
./easyrsa init-pki
```

```bash
./easyrsa build-ca
```

```bash
sysctl -p
```

```bash
systemctl start openvpn-server@server.service
```

```bash
openvpn --config client.conf
```

OpenVPN is widely used for secure remote access and encrypted communication in enterprise Linux environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install openvpn easy-rsa | Install OpenVPN |
| ./easyrsa init-pki | Initialize PKI |
| ./easyrsa build-ca | Create CA |
| sysctl -p | Enable IP forwarding |
| systemctl start openvpn-server | Start VPN Server |
| openvpn --config client.conf | Connect VPN Client |

---

# Conclusion

OpenVPN is a secure and reliable VPN solution used to establish encrypted communication channels between clients and servers. Understanding OpenVPN installation, certificate management, firewall configuration, client setup, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.