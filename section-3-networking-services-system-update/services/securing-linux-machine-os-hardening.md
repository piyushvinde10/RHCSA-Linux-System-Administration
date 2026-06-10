# Securing Linux Machine (OS Hardening)

## Overview

Operating System (OS) Hardening is the process of securing a Linux system by reducing vulnerabilities, minimizing attack surfaces, and implementing security best practices.

The goal is to protect the system from:

- Unauthorized access
- Malware attacks
- Data breaches
- Privilege escalation
- Network attacks

OS hardening is a critical responsibility for Linux administrators.

---

# What is OS Hardening?

OS Hardening involves:

- Removing unnecessary services
- Securing user accounts
- Applying updates and patches
- Configuring firewalls
- Enforcing strong authentication
- Monitoring system activity

---

# OS Hardening Checklist

```text
✓ Update System
✓ Secure User Accounts
✓ Configure Firewall
✓ Secure SSH
✓ Enable SELinux
✓ Configure Logging
✓ Remove Unused Services
✓ Enforce Password Policies
✓ Monitor System Activity
```

---

# Step 1: Keep System Updated

Check updates:

```bash
dnf check-update
```

Update system:

```bash
dnf update -y
```

Verify OS version:

```bash
cat /etc/redhat-release
```

---

# Step 2: Remove Unnecessary Packages

List installed packages:

```bash
rpm -qa
```

Remove unused package:

```bash
dnf remove package_name
```

Example:

```bash
dnf remove telnet -y
```

---

# Step 3: Disable Unused Services

List services:

```bash
systemctl list-unit-files --type=service
```

Disable service:

```bash
systemctl disable service_name
```

Stop service:

```bash
systemctl stop service_name
```

Example:

```bash
systemctl disable telnet.socket
```

---

# Step 4: Secure SSH

Edit SSH configuration:

```bash
vi /etc/ssh/sshd_config
```

Recommended settings:

```conf
PermitRootLogin no
PasswordAuthentication no
MaxAuthTries 3
Protocol 2
```

Restart SSH:

```bash
systemctl restart sshd
```

Verify:

```bash
systemctl status sshd
```

---

# Step 5: Configure SSH Key Authentication

Generate key:

```bash
ssh-keygen
```

Copy key:

```bash
ssh-copy-id user@server
```

Login:

```bash
ssh user@server
```

---

# Step 6: Configure Firewall

Start firewall:

```bash
systemctl start firewalld
```

Enable firewall:

```bash
systemctl enable firewalld
```

Verify:

```bash
systemctl status firewalld
```

List rules:

```bash
firewall-cmd --list-all
```

Allow SSH:

```bash
firewall-cmd --permanent --add-service=ssh
```

Reload:

```bash
firewall-cmd --reload
```

---

# Step 7: Enable SELinux

Check status:

```bash
getenforce
```

or

```bash
sestatus
```

Enable enforcing mode:

```bash
setenforce 1
```

Permanent configuration:

```bash
vi /etc/selinux/config
```

Set:

```conf
SELINUX=enforcing
```

---

# Step 8: Secure User Accounts

List users:

```bash
cat /etc/passwd
```

Lock account:

```bash
usermod -L username
```

Unlock account:

```bash
usermod -U username
```

Delete unused account:

```bash
userdel username
```

---

# Step 9: Enforce Password Policy

Edit:

```bash
vi /etc/login.defs
```

Example:

```conf
PASS_MAX_DAYS   90
PASS_MIN_DAYS   7
PASS_WARN_AGE   14
```

Verify:

```bash
chage -l username
```

---

# Step 10: Configure Password Complexity

Edit:

```bash
vi /etc/security/pwquality.conf
```

Example:

```conf
minlen = 8
minclass = 3
```

Requirements:

- Uppercase
- Lowercase
- Number
- Special character

---

# Step 11: Secure File Permissions

Find world-writable files:

```bash
find / -type f -perm -002
```

Find SUID files:

```bash
find / -perm -4000
```

Find SGID files:

```bash
find / -perm -2000
```

---

# Step 12: Monitor Failed Login Attempts

View authentication logs:

```bash
tail -f /var/log/secure
```

Search failed logins:

```bash
grep "Failed" /var/log/secure
```

---

# Step 13: Configure Automatic Screen Lock

Example timeout:

```bash
export TMOUT=600
```

Add to:

```bash
/etc/profile
```

Logout after:

```text
10 minutes
```

---

# Step 14: Enable Audit Logging

Install:

```bash
dnf install audit -y
```

Start service:

```bash
systemctl start auditd
```

Enable service:

```bash
systemctl enable auditd
```

Verify:

```bash
systemctl status auditd
```

---

# Step 15: Configure System Logging

Verify rsyslog:

```bash
systemctl status rsyslog
```

View logs:

```bash
tail -f /var/log/messages
```

---

# Step 16: Disable USB Storage (Optional)

Create rule:

```bash
echo "blacklist usb-storage" \
> /etc/modprobe.d/disable-usb.conf
```

Rebuild initramfs:

```bash
dracut -f
```

---

# Step 17: Verify Open Ports

Display listening ports:

```bash
ss -tulnp
```

Check specific ports:

```bash
ss -tulnp | grep 22
```

---

# Step 18: Check Running Processes

Display processes:

```bash
ps -ef
```

Interactive view:

```bash
top
```

---

# Security Verification Commands

## Check SELinux

```bash
getenforce
```

---

## Check Firewall

```bash
firewall-cmd --list-all
```

---

## Check SSH

```bash
systemctl status sshd
```

---

## Check Open Ports

```bash
ss -tulnp
```

---

## Check Users

```bash
cat /etc/passwd
```

---

# Useful Security Commands

## Security Updates

```bash
dnf update -y
```

---

## View Login History

```bash
last
```

---

## View Failed Logins

```bash
lastb
```

---

## Check File Permissions

```bash
ls -l
```

---

## Verify Services

```bash
systemctl list-units --type=service
```

---

# OS Hardening Best Practices

- Keep systems updated.
- Use SSH keys instead of passwords.
- Disable root login.
- Enable SELinux.
- Enable firewall.
- Remove unused services.
- Monitor logs regularly.
- Use strong passwords.
- Limit user privileges.
- Perform regular security audits.

---

# RHCSA Notes

Important commands:

```bash
dnf update
```

```bash
sestatus
```

```bash
getenforce
```

```bash
firewall-cmd --list-all
```

```bash
ss -tulnp
```

```bash
systemctl status sshd
```

```bash
last
```

```bash
lastb
```

These commands are commonly used for Linux security auditing and system hardening.

---

# Summary

| Task | Command |
|--------|----------|
| Update System | dnf update |
| Check SELinux | sestatus |
| Check Firewall | firewall-cmd --list-all |
| Check Open Ports | ss -tulnp |
| View Login History | last |
| Check Failed Logins | lastb |
| Audit Service | systemctl status auditd |

---

# Conclusion

OS Hardening is the process of securing a Linux system by minimizing vulnerabilities and enforcing security controls. Proper hardening includes patch management, firewall configuration, SELinux enforcement, secure authentication, logging, auditing, and continuous monitoring. These practices are essential for RHCSA preparation and real-world Linux administration.