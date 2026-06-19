# RHCSA Linux System Administration Preparation

![Linux](https://img.shields.io/badge/Linux-RHCSA-blue)
![Status](https://img.shields.io/badge/Status-Learning-green)
![Progress](https://img.shields.io/badge/RHCSA%20Progress-Day%2013-orange)

This repository documents my **hands-on learning journey** while preparing for the **Red Hat Certified System Administrator (RHCSA)** certification.

---

# Section 1: Linux Fundamentals

This section covers the core Linux commands and concepts.

## Topics Covered

- Linux command basics
- Text processing commands
- File comparison
- File compression
- File management
- Linux labs
- Linux exercises

📂 Location

```text
section-1-linux-fundamentals/
```

---

# Section 2: System Administration

This section covers advanced Linux system administration topics.

## Topics Covered

- Linux file editor (`vi` / `vim`)
- `sed` command
- User account management
- Password aging
- Sudo & privilege management
- User monitoring & communication
- File permissions & special permissions
- Directory services & authentication
- System utility commands
- Process management (`ps`, `top`, `kill`, signals)
- Service management (`systemctl`)
- Job scheduling (`cron`, `at`)
- System maintenance commands (`shutdown`, `reboot`, `halt`)
- Log monitoring
- System information (`uname`, `dmidecode`)
- Hostname configuration
- Environment variables
- Terminal commands & control keys
- tmux (terminal multiplexer)
- Practice labs (real-world tasks)

📂 Location

```text
section-2-system-administration/
```

---

# Section 3: Networking, Services & System Update

This section covers networking, remote access, file transfer, web services, DNS, package management, system updates, security, monitoring, automation and performance tuning.

## Topics Covered

### Networking

- Client-Server Relationship
- Enable Internet on Linux VM
- Network Components
- Network Files and Commands
- NIC Information (`ethtool`)
- NIC / Port Bonding
- New Network Utilities
  - `nmtui`
  - `nmcli`
  - `nm-connection-editor`
  - GNOME Settings
- The `ss` Command
- `curl` and `ping`
- Tracing Network Traffic (`traceroute`)
- DHCP Server

### Remote Access

- SSH and Telnet
- Configure and Secure SSH
- SSH Key Authentication
- Access Remote Server Without Password
- OpenVPN

### File Transfer

- FTP (File Transfer Protocol)
- SCP (Secure Copy Protocol)
- rsync (Remote Synchronization)
- Downloading Files using `wget`

### Package Management & Updates

- RPM Package Management
- YUM Package Management
- System Updates and Repositories
- System Upgrade and Patch Management
- Create Local Repository (YUM Server)
- Advanced Package Management
- Rollback Patches and Updates

### DNS & Time Services

- DNS Installation and Configuration (BIND)
- Hostname or IP Lookup (`nslookup`, `dig`)
- Network Time Protocol (NTP)
- Chronyd (New Version of NTP)
- `timedatectl`

### Mail & Web Services

- Mail Transfer Agent (Postfix)
- Sendmail
- Apache HTTP Server
- Nginx Web Server
- Reverse Proxy Configuration
- Cockpit Web-Based Administration

### Security, Monitoring, Automation & Performance

- Proxy Server (Squid)
- Centralized Logging (rsyslog)
- Installing, Configuring and Managing Nagios
- OpenLDAP Installation and Configuration
- Firewall Management (`firewalld`)
- Securing Linux Machine (OS Hardening)
- Run Containers using Podman
- Installing, Configuring and Managing Docker
- Installing, Configuring and Managing Ansible
- Installing, Configuring and Managing OpenVPN
- Installing and Configuring a Clustered Environment
- Kickstart (Automate Linux Installation)
- Tune System Performance
  - `tuned`
  - `nice`
  - `renice`

### Labs & Exercises

- Network Diagnostics and Configuration Console
- File Transfer and Synchronization Toolkit
- DNS Lab
- Nginx Reverse Proxy Lab
- Admin Console for Logs, Traffic and Processes
- Networking, DNS, Apache, Sendmail and Chronyd Exercise

📂 Location

```text
section-3-networking-services-system-update/
```

---

# Learning Progress

| Day | Topic | Status |
|------|--------|--------|
| Day 1 | Text Processing Commands | ✅ Completed |
| Day 2 | File Utilities & Compression | ✅ Completed |
| Day 3 | Linux Basics & Command Differences | ✅ Completed |
| Day 4 | Linux Labs | ✅ Completed |
| Day 5 | Linux Command Practice Exercise | ✅ Completed |
| Day 6 | File Editor, sed, User Management | ✅ Completed |
| Day 7 | Process Management, Services, Scheduling | ✅ Completed |
| Day 8 | System Configuration, Monitoring, tmux & Practice Lab | ✅ Completed |
| Day 9 | Networking Basics, SSH, SSH Keys & NetworkManager Utilities | ✅ Completed |
| Day 10 | FTP, SCP, rsync, wget, RPM, YUM, Repositories & Patch Management | ✅ Completed |
| Day 11 | DNS, NTP, Chronyd, timedatectl, Postfix, Apache, Nginx & Cockpit | ✅ Completed |
| Day 12 | Squid, Rsyslog, Nagios, OpenLDAP, Firewall, OS Hardening, Traceroute & Performance Tuning | ✅ Completed |
| Day 13 | DHCP, Podman, Docker, Ansible, OpenVPN, Clustering, Kickstart & Enterprise Services | ✅ Completed |

---

# Repository Structure

```text
RHCSA-Linux-System-Administration/
│
├── section-1-linux-fundamentals/
│
├── section-2-system-administration/
│
└── section-3-networking-services-system-update/
    ├── networking/
    ├── remote-access/
    ├── file-transfer/
    ├── services/
    ├── system-update/
    ├── system-utilities/
    ├── exercises/
    └── labs/
```

---

# Tools Used

- Linux Terminal
- Bash
- Git
- GitHub
- VirtualBox / VMware
- Podman
- Docker
- Ansible

---

# Learning Goal

- Build strong Linux command-line skills
- Master Linux system administration
- Learn Linux networking and services
- Understand DNS and web technologies
- Master package management and repositories
- Learn Linux security, monitoring and performance tuning
- Learn automation using Ansible and Kickstart
- Understand containerization with Podman and Docker
- Prepare for RHCSA certification

---

# Author

**Piyush Vinde**

GitHub:

```text
https://github.com/piyushvinde10
```

---

⭐ This repository tracks my **RHCSA learning journey (Section-wise and Day-wise)**.