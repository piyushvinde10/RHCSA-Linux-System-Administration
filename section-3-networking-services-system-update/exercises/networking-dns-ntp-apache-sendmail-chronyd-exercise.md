# Exercise: Networking, DNS, NTP, Apache, Sendmail and Chronyd

## Objective

Perform common Linux networking, package management, web server, mail server, and time synchronization tasks.

---

# Task 1: Enable Internet on Linux VM

## Verify Network Interface

```bash
ip addr
```

or

```bash
nmcli device status
```

---

## Test Internet Connectivity

```bash
ping 8.8.8.8
```

```bash
ping google.com
```

Expected:

```text
Packets received successfully
```

---

# Task 2: Run Network Commands

## View IP Address

```bash
ip addr
```

---

## View Routing Table

```bash
ip route
```

---

## View Active Connections

```bash
ss -tulnp
```

---

## View Network Interfaces

```bash
nmcli device status
```

---

## View DNS Configuration

```bash
cat /etc/resolv.conf
```

---

# Task 3: Capture Network Traffic Using tcpdump

## Identify Interface

```bash
ip addr
```

Example Interface:

```text
ens160
```

---

## Capture Traffic

```bash
tcpdump -i ens160
```

Example:

```bash
tcpdump -i eth0
```

Press:

```text
Ctrl + C
```

to stop capturing.

---

# Task 4: Update Linux System

Update packages:

```bash
yum update -y
```

or

```bash
dnf update -y
```

Verify OS Version:

```bash
cat /etc/redhat-release
```

---

# Task 5: Install DNS Server (BIND)

## Install Package

```bash
yum install bind bind-utils -y
```

or

```bash
dnf install bind bind-utils -y
```

---

## View Configuration File

```bash
vi /etc/named.conf
```

Important Sections:

```conf
options {
    listen-on port 53;
    directory "/var/named";
};
```

---

## Verify Configuration

```bash
named-checkconf
```

---

## Start DNS Service

```bash
systemctl start named
```

```bash
systemctl enable named
```

---

## Verify Status

```bash
systemctl status named
```

---

# Task 6: Configure NTP Synchronization

## Install NTP

```bash
yum install ntp -y
```

---

## Edit Configuration

```bash
vi /etc/ntp.conf
```

Add:

```conf
server pool.ntp.org iburst
```

---

## Start NTP Service

```bash
systemctl start ntpd
```

```bash
systemctl enable ntpd
```

---

## Verify Synchronization

```bash
ntpq -p
```

---

# Task 7: Install Apache (HTTPD)

## Install Package

```bash
yum install httpd -y
```

---

## Start Service

```bash
systemctl start httpd
```

```bash
systemctl enable httpd
```

---

## Create First Web Page

```bash
echo "Welcome to My First Apache Web Server" \
> /var/www/html/index.html
```

---

## Test Web Page

```bash
curl http://localhost
```

Expected:

```text
Welcome to My First Apache Web Server
```

---

## Verify Service

```bash
systemctl status httpd
```

---

# Task 8: Install and Configure Sendmail

## Install Package

```bash
yum install sendmail sendmail-cf -y
```

---

## Start Service

```bash
systemctl start sendmail
```

```bash
systemctl enable sendmail
```

---

## Verify Status

```bash
systemctl status sendmail
```

---

## Verify Port

```bash
ss -tulnp | grep 25
```

Expected:

```text
SMTP Port 25 Listening
```

---

# Task 9: Install and Configure Chronyd

## Stop NTP Service

```bash
systemctl stop ntpd
```

```bash
systemctl disable ntpd
```

---

## Install Chrony

```bash
yum install chrony -y
```

---

## Edit Configuration

```bash
vi /etc/chrony.conf
```

Add:

```conf
server pool.ntp.org iburst
```

---

## Start Chronyd

```bash
systemctl start chronyd
```

```bash
systemctl enable chronyd
```

---

## Verify Status

```bash
systemctl status chronyd
```

---

## Verify Synchronization

```bash
chronyc sources
```

```bash
chronyc tracking
```

---

# Verification Checklist

```text
✓ Internet Connectivity Working
✓ Network Commands Executed
✓ tcpdump Captured Traffic
✓ Linux System Updated
✓ BIND Installed and Configured
✓ NTP Configured with pool.ntp.org
✓ Apache Installed and Web Page Created
✓ Sendmail Installed and Running
✓ Chronyd Installed and Synchronizing Time
```

---

# Skills Practiced

- Network Configuration
- Network Troubleshooting
- Packet Capture using tcpdump
- DNS Server Administration
- Time Synchronization
- Apache Web Server Management
- Mail Server Administration
- Linux Package Management
- Service Management

---

# Conclusion

This exercise provides hands-on experience with Linux networking, DNS, web services, mail services, time synchronization, packet analysis, and system updates. These are essential Linux administration skills and important topics for RHCSA preparation.