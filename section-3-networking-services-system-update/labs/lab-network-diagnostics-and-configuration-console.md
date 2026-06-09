# Lab: Build a Network Diagnostics and Configuration Console

## Objective

Build a lightweight network diagnostics toolkit that collects:

- System identity information
- IP addressing details
- Routing information
- DNS configuration
- HTTP connectivity checks
- Name resolution results
- TCP and UDP socket snapshots

All information will be stored in files for quick reference and troubleshooting.

---

# Scenario

You are a Linux administrator and need a small network console toolkit to:

- Verify network status
- Record system identity
- Check routing configuration
- Test internet connectivity
- Validate DNS resolution
- Capture socket information
- Generate a quick troubleshooting report

---

# Task 1: Create Workspace and Report File

## Create Workspace

```bash
mkdir -p ~/net_console/snapshots
```

---

## Create Blank Report

```bash
> ~/net_console/report.txt
```

---

## Verify Directory Structure

```bash
ls -R ~/net_console
```

Expected Output:

```text
net_console/
├── report.txt
└── snapshots/
```

---

# Task 2: Record Local Identity and Routes

## Save Hostname

```bash
hostname > ~/net_console/report.txt
```

---

## Save IP Address Information

```bash
ip addr >> ~/net_console/report.txt
```

---

## Save Routing Table

```bash
ip route > ~/net_console/snapshots/route.txt
```

---

## Save Kernel Routing Table

```bash
cat /proc/net/route >> ~/net_console/snapshots/route.txt
```

---

## Save DNS Resolver Configuration

```bash
cat /etc/resolv.conf > ~/net_console/snapshots/resolver.txt
```

---

## Verify Route File

```bash
cat ~/net_console/snapshots/route.txt
```

---

# Task 3: Test Connectivity and HTTP Reachability

## Download HTTP Headers

```bash
curl -I https://example.com \
> ~/net_console/snapshots/headers.txt
```

---

## Save HTTP Status Code

```bash
curl -s -o /dev/null \
-w "%{http_code}\n" \
https://example.com \
> ~/net_console/snapshots/status.txt
```

---

## Save Timing Information

```bash
curl -o /dev/null -s \
-w "Connect: %{time_connect}s\nTotal: %{time_total}s\n" \
https://example.com \
> ~/net_console/snapshots/timing.txt
```

---

## Append Status to Report

```bash
echo "HTTP Status:" >> ~/net_console/report.txt
cat ~/net_console/snapshots/status.txt >> ~/net_console/report.txt
```

---

## Verify Header File

```bash
cat ~/net_console/snapshots/headers.txt
```

---

# Task 4: Check Name Resolution and Open Sockets

## Resolve Domain Name

```bash
getent hosts example.com \
> ~/net_console/snapshots/dns.txt
```

---

## Save TCP Socket Table

```bash
cat /proc/net/tcp \
> ~/net_console/snapshots/tcp.txt
```

---

## Save UDP Socket Table

```bash
cat /proc/net/udp \
> ~/net_console/snapshots/udp.txt
```

---

## Count TCP Entries

```bash
wc -l ~/net_console/snapshots/tcp.txt
```

---

## Count UDP Entries

```bash
wc -l ~/net_console/snapshots/udp.txt
```

---

## Append Socket Counts to Report

```bash
echo "" >> ~/net_console/report.txt
echo "TCP Entries:" >> ~/net_console/report.txt
wc -l < ~/net_console/snapshots/tcp.txt >> ~/net_console/report.txt

echo "UDP Entries:" >> ~/net_console/report.txt
wc -l < ~/net_console/snapshots/udp.txt >> ~/net_console/report.txt
```

---

# Verify Generated Files

```bash
ls -lh ~/net_console/snapshots
```

Expected Files:

```text
route.txt
resolver.txt
headers.txt
status.txt
timing.txt
dns.txt
tcp.txt
udp.txt
```

---

# View Final Report

```bash
cat ~/net_console/report.txt
```

Example:

```text
server01

HTTP Status:
200

TCP Entries:
15

UDP Entries:
5
```

---

# Final Directory Structure

```text
net_console/
├── report.txt
│
└── snapshots/
    ├── route.txt
    ├── resolver.txt
    ├── headers.txt
    ├── status.txt
    ├── timing.txt
    ├── dns.txt
    ├── tcp.txt
    └── udp.txt
```

---

# Commands Used

| Command | Purpose |
|----------|----------|
| hostname | Display hostname |
| ip addr | Display IP addresses |
| ip route | Display routing table |
| cat /proc/net/route | Kernel routing table |
| cat /etc/resolv.conf | DNS configuration |
| curl | HTTP connectivity testing |
| getent hosts | DNS resolution |
| cat /proc/net/tcp | TCP sockets |
| cat /proc/net/udp | UDP sockets |
| wc -l | Count lines |

---

# Skills Practiced

- Hostname management
- IP address inspection
- Route verification
- DNS troubleshooting
- HTTP reachability testing
- Socket analysis
- File redirection
- Report generation

---

# Summary

This lab builds a lightweight Network Diagnostics and Configuration Console that collects network information and stores it in files for quick troubleshooting and analysis.

The toolkit provides:

- System identity
- Routing information
- DNS settings
- HTTP connectivity status
- TCP and UDP snapshots
- A consolidated report

These are common Linux administration tasks used in RHCSA preparation and real-world troubleshooting.