# Client-Server Relationship

## Overview

The Client-Server model is a networking architecture where a **client** requests services or resources, and a **server** provides those services or resources.

This model forms the foundation of most network communications and internet-based applications.

---

## Client

A **Client** is a system, device, or application that sends requests to a server.

### Examples

- Web Browser (Chrome, Firefox)
- SSH Client
- FTP Client
- curl
- wget

### Client Responsibilities

- Initiates communication
- Sends requests
- Receives responses
- Displays results to the user

---

## Server

A **Server** is a system or application that receives requests from clients and provides the requested services.

### Examples

- Apache HTTP Server
- Nginx Web Server
- SSH Server (sshd)
- FTP Server
- DNS Server

### Server Responsibilities

- Listens for incoming requests
- Processes requests
- Provides services and resources
- Sends responses back to clients

---

## Communication Process

The communication between a client and server follows these steps:

1. Client sends a request.
2. Server receives the request.
3. Server processes the request.
4. Server sends a response.
5. Client receives and displays the response.

### Diagram

```text
Client  ---- Request ---->  Server
Client  <--- Response ----  Server
```

---

## Example: Web Browsing

When a user enters a website URL:

```text
Browser (Client)
       |
       | HTTP Request
       v
Apache/Nginx (Server)
       |
       | HTTP Response
       v
Browser (Client)
```

The browser requests a webpage, and the web server sends the webpage content back to the browser.

---

## Example: SSH Connection

### Client Machine

```bash
ssh user@192.168.1.10
```

### Server Machine

```bash
systemctl status sshd
```

The SSH client requests a remote connection, and the SSH server authenticates the user before granting access.

---

## Common Client-Server Services

| Service | Client | Server | Port |
|----------|----------|----------|----------|
| SSH | ssh | sshd | 22 |
| HTTP | Browser | Apache/Nginx | 80 |
| HTTPS | Browser | Apache/Nginx | 443 |
| FTP | ftp | vsftpd | 21 |
| DNS | dig, nslookup | DNS Server | 53 |

---

## Useful Linux Commands

### Check Network Connectivity

```bash
ping google.com
```

### Display Open Ports

```bash
ss -tulnp
```

### Test Web Service

```bash
curl http://localhost
```

### Check Service Status

```bash
systemctl status httpd
```

### Display Host Information

```bash
hostnamectl
```

---

## Importance in RHCSA

Understanding the Client-Server model helps in:

- Configuring network services
- Managing SSH access
- Troubleshooting connectivity issues
- Managing web servers
- Monitoring services
- Configuring firewalls

---

## Key Points

- A client requests services.
- A server provides services.
- Communication occurs through network protocols.
- Most Linux networking tasks are based on the Client-Server architecture.

---

## Conclusion

The Client-Server model is one of the most important concepts in Linux networking. Understanding how clients and servers communicate is essential for system administration, troubleshooting, and RHCSA certification preparation.