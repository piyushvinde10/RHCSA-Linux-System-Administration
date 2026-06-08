# FTP - File Transfer Protocol

## Overview

FTP (File Transfer Protocol) is a standard network protocol used to transfer files between a client and a server over a TCP/IP network.

FTP allows users to:

- Upload files to a server
- Download files from a server
- Manage remote files and directories

FTP is widely used for file sharing and data transfer, although secure alternatives such as SFTP and SCP are preferred today.

---

# What is FTP?

FTP is a client-server protocol that enables file transfer between systems.

### Architecture

```text
FTP Client  <-------->  FTP Server
```

Examples:

- FileZilla
- ftp command
- lftp
- WinSCP

---

# FTP Ports

FTP uses two connections:

| Port | Purpose |
|--------|----------|
| 21 | Control Connection |
| 20 | Data Connection |

---

# FTP Modes

## Active Mode

```text
Client ---> Server (Port 21)
Server ---> Client (Port 20)
```

The server initiates the data connection.

---

## Passive Mode

```text
Client ---> Server (Port 21)
Client ---> Server (Random Port)
```

The client initiates both connections.

Passive mode is commonly used because it works better with firewalls.

---

# Install FTP Server

## Install vsftpd

```bash
sudo yum install vsftpd -y
```

Verify Installation:

```bash
rpm -qa | grep vsftpd
```

---

# Start FTP Service

```bash
sudo systemctl start vsftpd
```

---

# Enable FTP at Boot

```bash
sudo systemctl enable vsftpd
```

---

# Check FTP Status

```bash
sudo systemctl status vsftpd
```

---

# FTP Configuration File

Main configuration file:

```text
/etc/vsftpd/vsftpd.conf
```

View Configuration:

```bash
cat /etc/vsftpd/vsftpd.conf
```

Edit Configuration:

```bash
sudo vi /etc/vsftpd/vsftpd.conf
```

---

# Allow FTP Through Firewall

```bash
sudo firewall-cmd --permanent --add-service=ftp
```

Reload Firewall:

```bash
sudo firewall-cmd --reload
```

Verify:

```bash
sudo firewall-cmd --list-services
```

---

# Connect to FTP Server

## Using Hostname

```bash
ftp ftp.example.com
```

## Using IP Address

```bash
ftp 192.168.1.100
```

Example:

```text
Name: user
Password:
ftp>
```

---

# Common FTP Commands

## Display Current Directory

```bash
pwd
```

---

## List Files

```bash
ls
```

---

## Change Directory

```bash
cd directory_name
```

---

## Upload File

```bash
put file.txt
```

---

## Download File

```bash
get file.txt
```

---

## Upload Multiple Files

```bash
mput *.txt
```

---

## Download Multiple Files

```bash
mget *.txt
```

---

## Exit FTP

```bash
bye
```

or

```bash
quit
```

---

# Verify FTP Port

Check Port 21:

```bash
ss -tulnp | grep 21
```

Example:

```text
LISTEN 0 32 *:21
```

---

# Test FTP Connectivity

Using Telnet:

```bash
telnet 192.168.1.100 21
```

Expected Output:

```text
220 (vsFTPd 3.x.x)
```

---

# FTP Directory

Default FTP directory:

```text
/var/ftp/
```

List Files:

```bash
ls -l /var/ftp
```

---

# FTP Service Management

Start Service:

```bash
sudo systemctl start vsftpd
```

Stop Service:

```bash
sudo systemctl stop vsftpd
```

Restart Service:

```bash
sudo systemctl restart vsftpd
```

Check Status:

```bash
sudo systemctl status vsftpd
```

---

# FTP vs SFTP

| Feature | FTP | SFTP |
|----------|----------|----------|
| Security | No Encryption | Encrypted |
| Port | 21 | 22 |
| Authentication | Username/Password | SSH Authentication |
| Data Protection | No | Yes |
| Recommended | No | Yes |

---

# Common Troubleshooting

## Verify Service

```bash
systemctl status vsftpd
```

---

## Verify Listening Port

```bash
ss -tulnp | grep 21
```

---

## Verify Firewall

```bash
firewall-cmd --list-services
```

---

## Check FTP Logs

```bash
tail -f /var/log/messages
```

---

## Test Connectivity

```bash
ftp localhost
```

---

# Security Best Practices

- Disable anonymous access.
- Use strong passwords.
- Restrict user access.
- Use passive mode when required.
- Prefer SFTP over FTP.
- Monitor FTP logs regularly.

---

# Summary

| Command | Purpose |
|----------|----------|
| ftp server | Connect to FTP server |
| put file | Upload file |
| get file | Download file |
| ls | List files |
| pwd | Display current directory |
| bye | Exit FTP |
| systemctl status vsftpd | Check FTP service |
| ss -tulnp | Verify FTP port |

---

# Conclusion

FTP is a protocol used to transfer files between systems over a network. While FTP remains important for understanding networking concepts, secure alternatives such as SFTP and SCP are preferred in modern Linux environments. Understanding FTP installation, configuration, commands, and troubleshooting is valuable for RHCSA preparation and Linux administration.