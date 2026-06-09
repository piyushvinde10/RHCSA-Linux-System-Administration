# Web Server (Apache - HTTP)

## Overview

Apache HTTP Server is one of the most widely used web servers in the world.

It is used to:

- Host websites
- Serve web pages
- Deliver web applications
- Handle HTTP and HTTPS requests

Apache is open-source, reliable, and commonly used in Linux environments.

---

# What is a Web Server?

A web server is software that receives requests from clients (web browsers) and sends web pages back to them.

Example:

```text
Client Browser
      |
      | HTTP Request
      |
      v
Apache Web Server
      |
      | HTTP Response
      |
      v
Web Page
```

---

# What is Apache?

Apache HTTP Server is:

```text
Open Source Web Server
```

Package Name:

```text
httpd
```

Service Name:

```text
httpd
```

Default Port:

```text
80/TCP
```

---

# HTTP Protocol

HTTP stands for:

```text
HyperText Transfer Protocol
```

Used for:

- Website communication
- Data transfer
- Web applications

Default Port:

```text
80
```

---

# HTTPS Protocol

HTTPS stands for:

```text
HyperText Transfer Protocol Secure
```

Default Port:

```text
443
```

Provides:

- Encryption
- Authentication
- Secure communication

---

# Install Apache

Install package:

```bash
dnf install httpd -y
```

Verify installation:

```bash
rpm -qa | grep httpd
```

---

# Start Apache Service

Start service:

```bash
systemctl start httpd
```

Enable service:

```bash
systemctl enable httpd
```

Verify status:

```bash
systemctl status httpd
```

---

# Verify Listening Port

Check HTTP port:

```bash
ss -tulnp | grep 80
```

Expected Output:

```text
LISTEN 0 511 *:80
```

---

# Apache Configuration Files

Main configuration file:

```text
/etc/httpd/conf/httpd.conf
```

Configuration directory:

```text
/etc/httpd/conf.d/
```

View configuration:

```bash
cat /etc/httpd/conf/httpd.conf
```

---

# Apache Document Root

Default web content location:

```text
/var/www/html
```

Create test page:

```bash
echo "Welcome to Apache Web Server" > /var/www/html/index.html
```

Verify:

```bash
cat /var/www/html/index.html
```

---

# Test Apache Locally

Using browser:

```text
http://localhost
```

Using curl:

```bash
curl http://localhost
```

Expected Output:

```text
Welcome to Apache Web Server
```

---

# Allow HTTP Through Firewall

Allow HTTP service:

```bash
firewall-cmd --permanent --add-service=http
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-services
```

Expected:

```text
http
```

---

# Configure HTTPS

Install SSL module:

```bash
dnf install mod_ssl -y
```

Verify:

```bash
rpm -qa | grep mod_ssl
```

Restart Apache:

```bash
systemctl restart httpd
```

Check HTTPS port:

```bash
ss -tulnp | grep 443
```

---

# Apache Directory Structure

```text
/etc/httpd/
│
├── conf/
│   └── httpd.conf
│
├── conf.d/
│
├── logs/
│
└── modules/
```

---

# Apache Log Files

Access log:

```text
/var/log/httpd/access_log
```

Error log:

```text
/var/log/httpd/error_log
```

View logs:

```bash
tail -f /var/log/httpd/access_log
```

```bash
tail -f /var/log/httpd/error_log
```

---

# Apache Service Management

Start service:

```bash
systemctl start httpd
```

Stop service:

```bash
systemctl stop httpd
```

Restart service:

```bash
systemctl restart httpd
```

Reload configuration:

```bash
systemctl reload httpd
```

Check status:

```bash
systemctl status httpd
```

---

# Verify Apache Configuration

Check syntax:

```bash
httpd -t
```

Expected Output:

```text
Syntax OK
```

---

# Virtual Hosts

Virtual Hosts allow multiple websites on a single server.

Example:

```conf
<VirtualHost *:80>
    ServerName site1.example.com
    DocumentRoot /var/www/site1
</VirtualHost>
```

---

# Common Troubleshooting

## Check Service Status

```bash
systemctl status httpd
```

---

## Verify Port 80

```bash
ss -tulnp | grep 80
```

---

## Verify Firewall

```bash
firewall-cmd --list-services
```

---

## Check Configuration

```bash
httpd -t
```

---

## Check Logs

```bash
tail -f /var/log/httpd/error_log
```

---

# Useful Commands

## Install Apache

```bash
dnf install httpd -y
```

---

## Start Service

```bash
systemctl start httpd
```

---

## Enable Service

```bash
systemctl enable httpd
```

---

## Check Status

```bash
systemctl status httpd
```

---

## Verify Configuration

```bash
httpd -t
```

---

## Test Website

```bash
curl http://localhost
```

---

# RHCSA Notes

Important commands:

```bash
dnf install httpd
```

```bash
systemctl start httpd
```

```bash
systemctl enable httpd
```

```bash
httpd -t
```

```bash
ss -tulnp | grep 80
```

```bash
curl http://localhost
```

```bash
firewall-cmd --add-service=http
```

Apache web server configuration and troubleshooting are common Linux administration tasks and important RHCSA skills.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install httpd | Install Apache |
| systemctl start httpd | Start Apache |
| systemctl enable httpd | Enable at boot |
| httpd -t | Verify configuration |
| curl http://localhost | Test website |
| ss -tulnp | Verify listening port |
| firewall-cmd --add-service=http | Allow HTTP traffic |

---

# Conclusion

Apache HTTP Server is one of the most popular web servers used in Linux environments. It allows administrators to host websites, manage web applications, and provide HTTP/HTTPS services. Understanding Apache installation, configuration, logs, firewall settings, and troubleshooting is an essential RHCSA and Linux administration skill.