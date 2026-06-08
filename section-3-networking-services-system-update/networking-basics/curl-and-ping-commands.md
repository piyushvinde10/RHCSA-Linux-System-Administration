# curl and ping Commands

## Overview

The `curl` and `ping` commands are essential networking tools used by Linux administrators for testing connectivity, troubleshooting network issues, and verifying service availability.

---

# ping Command

## What is ping?

The `ping` command is used to test network connectivity between two systems.

It sends ICMP (Internet Control Message Protocol) Echo Request packets to a target host and waits for a reply.

---

## Basic Syntax

```bash
ping <hostname-or-ip>
```

### Example

```bash
ping google.com
```

---

## Send Limited Packets

By default, ping runs continuously.

Send only 4 packets:

```bash
ping -c 4 google.com
```

Example Output:

```text
64 bytes from google.com: icmp_seq=1 ttl=115 time=25 ms
64 bytes from google.com: icmp_seq=2 ttl=115 time=23 ms
```

---

## Ping an IP Address

```bash
ping 8.8.8.8
```

---

## Ping Localhost

```bash
ping localhost
```

or

```bash
ping 127.0.0.1
```

---

## Display Summary Only

```bash
ping -c 5 google.com
```

Example:

```text
5 packets transmitted, 5 received, 0% packet loss
```

---

## Common Uses of ping

- Verify network connectivity
- Check if a host is reachable
- Test DNS resolution
- Troubleshoot network issues
- Measure network latency

---

# curl Command

## What is curl?

`curl` (Client URL) is a command-line tool used to transfer data from or to a server using various protocols.

Supported protocols include:

- HTTP
- HTTPS
- FTP
- SFTP
- SCP
- SMTP

---

## Basic Syntax

```bash
curl <URL>
```

### Example

```bash
curl https://www.google.com
```

This displays the webpage source code.

---

## Display HTTP Headers

```bash
curl -I https://www.google.com
```

Example Output:

```text
HTTP/2 200
content-type: text/html
server: gws
```

---

## Download a File

```bash
curl -O https://example.com/file.txt
```

---

## Save Output to a Custom File

```bash
curl -o webpage.html https://example.com
```

---

## Check Website Response

```bash
curl -I https://github.com
```

Expected Output:

```text
HTTP/2 200
```

---

## Test Local Web Server

```bash
curl http://localhost
```

Useful for testing Apache or Nginx services.

---

## Display Public IP Address

```bash
curl ifconfig.me
```

Example Output:

```text
203.0.113.10
```

---

## Follow Redirects

```bash
curl -L http://google.com
```

---

## Display Detailed Information

```bash
curl -v https://www.google.com
```

---

# ping vs curl

| Feature | ping | curl |
|----------|----------|----------|
| Purpose | Test connectivity | Transfer data |
| Protocol | ICMP | HTTP/HTTPS/FTP |
| Tests Service Availability | No | Yes |
| Measures Latency | Yes | No |
| Downloads Files | No | Yes |
| Checks HTTP Response | No | Yes |

---

# Practical Examples

## Check Internet Connectivity

```bash
ping 8.8.8.8
```

---

## Verify DNS Resolution

```bash
ping google.com
```

---

## Verify Web Server Availability

```bash
curl http://localhost
```

---

## Check HTTP Response Code

```bash
curl -I https://github.com
```

---

## Download a File

```bash
curl -O https://example.com/file.txt
```

---

# Common Troubleshooting Workflow

## Step 1: Test Network Connectivity

```bash
ping 8.8.8.8
```

If successful, the network is working.

---

## Step 2: Test DNS Resolution

```bash
ping google.com
```

If IP works but hostname fails, DNS may be misconfigured.

---

## Step 3: Test Web Service

```bash
curl http://localhost
```

or

```bash
curl -I http://localhost
```

Verify that the web server is responding.

---

# Summary

| Command | Purpose |
|----------|----------|
| ping host | Test connectivity |
| ping -c 4 host | Send 4 packets |
| curl URL | Retrieve webpage content |
| curl -I URL | Display HTTP headers |
| curl -O URL | Download file |
| curl -o file URL | Save output to file |
| curl -v URL | Verbose output |

---

# Conclusion

The `ping` command is primarily used to verify network connectivity and measure latency, while the `curl` command is used to communicate with web services, retrieve content, download files, and troubleshoot HTTP/HTTPS applications. Both tools are essential for Linux administration, networking, and RHCSA preparation.