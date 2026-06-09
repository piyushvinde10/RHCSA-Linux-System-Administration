# Installing, Configuring and Managing Nginx

## Overview

Nginx is a high-performance web server, reverse proxy server, and load balancer.

Features:

- Web Hosting
- Reverse Proxy
- Load Balancing
- SSL/TLS Support
- Static Content Serving
- High Performance

---

# Lab Environment

| Server | IP Address |
|----------|------------|
| MyFirstLinuxOS | 192.168.100.161 |
| CentOS Server | 192.168.100.162 |

---

# Step 1: Install Nginx

Verify installation:

```bash
rpm -qa | grep nginx
```

Install package:

```bash
dnf install nginx -y
```

---

# Step 2: Start and Enable Nginx

Start service:

```bash
systemctl start nginx
```

Enable at boot:

```bash
systemctl enable nginx
```

Verify status:

```bash
systemctl status nginx
```

---

# Step 3: Disable Firewall (Lab Environment)

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

# Step 4: Configure Nginx on Server 1

Main configuration file:

```bash
vi /etc/nginx/nginx.conf
```

Create virtual host:

```bash
vi /etc/nginx/conf.d/myfirstlinuxos.conf
```

Configuration:

```nginx
server {
    listen 80;
    server_name 192.168.100.161;

    root /var/www/myfirstlinuxos/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

---

# Step 5: Create Website Content

Create directory:

```bash
mkdir -p /var/www/myfirstlinuxos/html/
```

Move to directory:

```bash
cd /var/www/myfirstlinuxos/html/
```

Create page:

```bash
vi index.html
```

Add content:

```html
<h1>Hello from MyFirstLinuxOS</h1>
```

---

# Step 6: Test Configuration

Verify syntax:

```bash
nginx -t
```

Expected Output:

```text
syntax is ok
test is successful
```

Restart service:

```bash
systemctl restart nginx
```

Access website:

```text
http://192.168.100.161
```

Expected:

```text
Hello from MyFirstLinuxOS
```

---

# Step 7: Configure Nginx on Server 2

Install:

```bash
dnf install nginx -y
```

Start service:

```bash
systemctl start nginx
```

Enable service:

```bash
systemctl enable nginx
```

Disable firewall:

```bash
systemctl stop firewalld
```

```bash
systemctl disable firewalld
```

Create virtual host:

```bash
vi /etc/nginx/conf.d/centosserver.conf
```

Configuration:

```nginx
server {
    listen 80;
    server_name 192.168.100.162;

    root /var/www/centosserver/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

---

# Create Website Content

Create directory:

```bash
mkdir -p /var/www/centosserver/html
```

Move to directory:

```bash
cd /var/www/centosserver/html/
```

Create page:

```bash
vi index.html
```

Add content:

```html
<h1>Hello from CentOS Server</h1>
```

---

# Verify Configuration

```bash
nginx -t
```

Restart service:

```bash
systemctl restart nginx
```

Access website:

```text
http://192.168.100.162
```

Expected:

```text
Hello from CentOS Server
```

---

# Step 8: Configure Reverse Proxy

On Server 1:

```bash
vi /etc/nginx/conf.d/reverseproxy.conf
```

Configuration:

```nginx
server {
    listen 80;
    server_name 192.168.100.161;

    location / {
        proxy_pass http://192.168.100.162;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

---

# Reverse Proxy Explanation

```text
Client
   |
   v
Server 1 (Nginx Reverse Proxy)
   |
   v
Server 2 (Backend Web Server)
```

Benefits:

- Hide backend servers
- Load balancing
- SSL termination
- Improved security

---

# Step 9: Final Testing

Verify syntax:

```bash
nginx -t
```

Restart Nginx:

```bash
systemctl restart nginx
```

Access website:

```text
http://192.168.100.161
```

Nginx forwards the request to:

```text
http://192.168.100.162
```

---

# Nginx Service Management

Start:

```bash
systemctl start nginx
```

Stop:

```bash
systemctl stop nginx
```

Restart:

```bash
systemctl restart nginx
```

Reload:

```bash
systemctl reload nginx
```

Status:

```bash
systemctl status nginx
```

---

# Verify Listening Port

```bash
ss -tulnp | grep nginx
```

Expected:

```text
LISTEN 0 511 *:80
```

---

# Verify Installed Package

```bash
rpm -qa | grep nginx
```

---

# Troubleshooting

Check service:

```bash
systemctl status nginx
```

Check syntax:

```bash
nginx -t
```

Check logs:

```bash
tail -f /var/log/nginx/error.log
```

Check port:

```bash
ss -tulnp | grep 80
```

---

# Useful Commands

```bash
dnf install nginx -y
```

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

```bash
nginx -t
```

```bash
systemctl restart nginx
```

```bash
ss -tulnp | grep nginx
```

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install nginx | Install Nginx |
| systemctl start nginx | Start service |
| systemctl enable nginx | Enable at boot |
| nginx -t | Verify configuration |
| systemctl restart nginx | Restart service |
| ss -tulnp | Check listening ports |

---

# Conclusion

Nginx is a powerful web server and reverse proxy solution widely used in Linux environments. This lab demonstrated Nginx installation, website hosting, virtual host configuration, reverse proxy setup, service management, and troubleshooting. These skills are valuable for RHCSA preparation and real-world Linux administration.