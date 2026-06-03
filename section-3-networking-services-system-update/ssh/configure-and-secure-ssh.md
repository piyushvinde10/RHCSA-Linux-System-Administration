# Configure and Secure SSH

## Overview

SSH (Secure Shell) is a secure protocol used for remote administration of Linux systems.

Proper SSH configuration and security hardening help protect servers from unauthorized access and brute-force attacks.

---

# Install OpenSSH Server

## RHEL / CentOS / Rocky Linux

```bash
sudo yum install openssh-server -y
```

Verify installation:

```bash
rpm -qa | grep openssh
```

---

# Start and Enable SSH Service

Start SSH service:

```bash
sudo systemctl start sshd
```

Enable SSH at boot:

```bash
sudo systemctl enable sshd
```

Check service status:

```bash
sudo systemctl status sshd
```

---

# Verify SSH Port

Display listening ports:

```bash
ss -tulnp | grep ssh
```

or

```bash
ss -tulnp | grep 22
```

Example Output:

```text
LISTEN 0 128 *:22 *:* users:(("sshd"))
```

---

# SSH Configuration File

Main configuration file:

```text
/etc/ssh/sshd_config
```

View configuration:

```bash
cat /etc/ssh/sshd_config
```

Edit configuration:

```bash
sudo vi /etc/ssh/sshd_config
```

---

# Change Default SSH Port

Default Port:

```text
22
```

Change to:

```text
Port 2222
```

Example:

```bash
sudo vi /etc/ssh/sshd_config
```

Modify:

```text
Port 2222
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

Verify:

```bash
ss -tulnp | grep 2222
```

---

# Disable Root Login

Allowing direct root login is not recommended.

Edit:

```bash
sudo vi /etc/ssh/sshd_config
```

Set:

```text
PermitRootLogin no
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

---

# Allow Specific Users

Restrict SSH access to selected users.

Edit:

```bash
sudo vi /etc/ssh/sshd_config
```

Add:

```text
AllowUsers admin user1
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

---

# Disable Empty Passwords

Edit configuration:

```text
PermitEmptyPasswords no
```

---

# Limit Authentication Attempts

Reduce brute-force attacks.

Edit:

```text
MaxAuthTries 3
```

---

# Set Login Timeout

Automatically disconnect idle login attempts.

Edit:

```text
LoginGraceTime 60
```

---

# Configure SSH Key Authentication

## Generate SSH Key Pair

Client System:

```bash
ssh-keygen
```

Example Files:

```text
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

---

## Copy Public Key to Server

```bash
ssh-copy-id user@192.168.1.100
```

---

## Test Key Authentication

```bash
ssh user@192.168.1.100
```

No password should be required.

---

# Disable Password Authentication

After key authentication works:

Edit:

```bash
sudo vi /etc/ssh/sshd_config
```

Set:

```text
PasswordAuthentication no
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

---

# Configure Firewall for SSH

Allow SSH service:

```bash
sudo firewall-cmd --permanent --add-service=ssh
```

Reload firewall:

```bash
sudo firewall-cmd --reload
```

Verify:

```bash
sudo firewall-cmd --list-services
```

---

# Verify SSH Configuration

Check configuration syntax:

```bash
sudo sshd -t
```

No output indicates valid configuration.

---

# Useful SSH Commands

## Connect to Remote Server

```bash
ssh user@192.168.1.100
```

---

## Connect Using Custom Port

```bash
ssh -p 2222 user@192.168.1.100
```

---

## Secure File Transfer

```bash
scp file.txt user@192.168.1.100:/home/user
```

---

## Copy Directory

```bash
scp -r data/ user@192.168.1.100:/home/user
```

---

# Common Troubleshooting Commands

Check SSH Service:

```bash
systemctl status sshd
```

Check Listening Ports:

```bash
ss -tulnp
```

Check Firewall Rules:

```bash
firewall-cmd --list-all
```

Verify Connectivity:

```bash
ping 192.168.1.100
```

Test SSH Port:

```bash
telnet 192.168.1.100 22
```

---

# Recommended SSH Security Settings

```text
Port 2222
PermitRootLogin no
PasswordAuthentication no
PermitEmptyPasswords no
MaxAuthTries 3
LoginGraceTime 60
AllowUsers admin user1
```

---

# Security Best Practices

- Use SSH key authentication.
- Disable root login.
- Disable password authentication.
- Use a non-default SSH port.
- Limit allowed users.
- Keep OpenSSH updated.
- Monitor SSH logs regularly.

---

# Summary

| Setting | Purpose |
|----------|----------|
| Port | Change default SSH port |
| PermitRootLogin no | Disable root login |
| PasswordAuthentication no | Disable password login |
| AllowUsers | Restrict SSH users |
| MaxAuthTries | Limit login attempts |
| LoginGraceTime | Set login timeout |

---

# Conclusion

SSH is the preferred method for remote administration of Linux systems. Proper configuration and security hardening significantly reduce the risk of unauthorized access. Understanding SSH configuration, key authentication, firewall integration, and security best practices is essential for RHCSA certification and real-world Linux administration.