# Installing, Configuring and Managing Nagios

## Overview

Nagios is an open-source infrastructure monitoring tool used to monitor:

- Servers
- Network devices
- Applications
- Services
- System resources

Nagios helps administrators detect issues before they impact users.

---

# What is Nagios?

Nagios provides monitoring and alerting capabilities for Linux and network environments.

Features:

- Host Monitoring
- Service Monitoring
- Email Alerts
- Performance Monitoring
- Web Dashboard
- Network Monitoring

---

# Nagios Architecture

```text
             Nagios Server
                    |
     --------------------------------
     |              |              |
 Linux Server   Web Server    Network Device
```

---

# Lab Environment

| Host | IP Address |
|--------|------------|
| Nagios Server | 192.168.100.161 |
| Client Server | 192.168.100.162 |

---

# Step 1: Install Required Packages

```bash
dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget -y
```

Install OpenSSL development package:

```bash
dnf install openssl-devel -y
```

---

# Step 2: Create Nagios User and Group

Create user:

```bash
useradd nagios
```

Create group:

```bash
groupadd nagcmd
```

Add nagios user to group:

```bash
usermod -a -G nagcmd nagios
```

Add apache user:

```bash
usermod -a -G nagcmd apache
```

---

# Step 3: Download Nagios Core

Move to temporary directory:

```bash
cd /tmp
```

Download Nagios:

```bash
wget -O nagios-4.5.4.tar.gz https://go.nagios.org/l/975333/2024-08-14/6dqd8
```

Extract package:

```bash
tar xzf nagios-4.5.4.tar.gz
```

Move to extracted directory:

```bash
cd nagios-4.5.4
```

---

# Step 4: Configure Nagios

```bash
./configure --with-command-group=nagcmd
```

---

# Step 5: Install Nagios Core

Compile:

```bash
make all
```

Install binaries:

```bash
make install
```

Install command mode:

```bash
make install-commandmode
```

Install startup scripts:

```bash
make install-init
```

Install sample configuration:

```bash
make install-config
```

Install Apache configuration:

```bash
make install-webconf
```

---

# Step 6: Install Nagios Plugins

Move to temporary directory:

```bash
cd /tmp
```

Download plugins:

```bash
wget https://nagios-plugins.org/download/nagios-plugins-2.4.11.tar.gz
```

Extract package:

```bash
tar xzf nagios-plugins-2.4.11.tar.gz
```

Move into directory:

```bash
cd nagios-plugins-2.4.11
```

Configure:

```bash
./configure --with-nagios-user=nagios --with-nagios-group=nagios
```

Compile:

```bash
make
```

Install:

```bash
make install
```

---

# Step 7: Disable Firewall (Lab Setup)

Stop firewall:

```bash
systemctl stop firewalld
```

Disable firewall:

```bash
systemctl disable firewalld
```

Verify:

```bash
systemctl status firewalld
```

---

# Step 8: Create Nagios Web Login

Create Nagios admin account:

```bash
htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
```

Enter password when prompted.

---

# Step 9: Start Services

Start Apache:

```bash
systemctl start httpd
```

Enable Apache:

```bash
systemctl enable httpd
```

Start Nagios:

```bash
systemctl start nagios
```

Enable Nagios:

```bash
systemctl enable nagios
```

Verify:

```bash
systemctl status nagios
```

---

# Step 10: Configure Hosts

Move to object directory:

```bash
cd /usr/local/nagios/etc/objects/
```

List files:

```bash
ls -ltr
```

Edit host configuration:

```bash
vi hosts.cfg
```

Add:

```cfg
define host {
 use linux-server
 host_name CentosServer
 alias My First Server
 address 192.168.100.162
 max_check_attempts 5
 check_period 24x7
 notification_interval 30
 notification_period 24x7
}
```

---

# Configure Ping Service

Add:

```cfg
define service {
 use generic-service
 host_name CentosServer
 service_description PING
 check_command check_ping!100.0,20%!500.0,60%
 max_check_attempts 5
 normal_check_interval 5
 retry_check_interval 1
 check_period 24x7
 notification_interval 30
 notification_period 24x7
}
```

---

# Step 11: Update Nagios Configuration

Edit:

```bash
cd /usr/local/nagios/etc/
```

```bash
vi nagios.cfg
```

Add:

```cfg
cfg_file=/usr/local/nagios/etc/objects/hosts.cfg
```

---

# Step 12: Verify Configuration

```bash
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
```

Expected:

```text
Things look okay - No serious problems were detected.
```

---

# Step 13: Restart Nagios

```bash
systemctl restart nagios
```

Verify:

```bash
systemctl status nagios
```

---

# Access Nagios Web Interface

Open browser:

```text
http://192.168.100.161/nagios
```

Login:

```text
Username: nagiosadmin
Password: ********
```

---

# Important Nagios Directories

```text
/usr/local/nagios/
│
├── bin/
├── etc/
├── libexec/
├── share/
├── var/
└── sbin/
```

---

# Nagios Service Management

Start:

```bash
systemctl start nagios
```

Stop:

```bash
systemctl stop nagios
```

Restart:

```bash
systemctl restart nagios
```

Status:

```bash
systemctl status nagios
```

---

# Troubleshooting

Verify configuration:

```bash
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
```

Check Apache:

```bash
systemctl status httpd
```

Check Nagios:

```bash
systemctl status nagios
```

Check listening ports:

```bash
ss -tulnp | grep httpd
```

Check logs:

```bash
tail -f /usr/local/nagios/var/nagios.log
```

---

# Useful Commands

```bash
systemctl status nagios
```

```bash
systemctl restart nagios
```

```bash
systemctl status httpd
```

```bash
htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
```

```bash
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
```

---

# RHCSA Notes

Topics Learned:

- Nagios Installation
- Host Monitoring
- Service Monitoring
- Apache Integration
- Plugin Management
- Web Interface Configuration
- Monitoring Linux Servers

---

# Summary

| Component | Purpose |
|------------|----------|
| Nagios Core | Monitoring Engine |
| Plugins | Service Checks |
| Apache | Web Interface |
| Hosts.cfg | Host Definitions |
| Services | Monitoring Checks |
| nagios.cfg | Main Configuration |

---

# Conclusion

Nagios is a powerful monitoring solution used to monitor Linux servers, services, and network devices. It provides centralized monitoring, alerting, and reporting capabilities. Understanding Nagios installation, configuration, host monitoring, and service checks is valuable for Linux administration and enterprise monitoring environments.