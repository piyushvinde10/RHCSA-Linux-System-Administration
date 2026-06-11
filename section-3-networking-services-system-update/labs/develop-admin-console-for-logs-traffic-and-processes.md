# Lab: Develop an Admin Console for Logs, Traffic, and Processes

## Objective

Build a simple Linux administration console that:

- Collects log snapshots
- Verifies DNS and web connectivity
- Captures process information
- Demonstrates process priority management
- Creates a reusable troubleshooting toolkit

---

# Lab Environment

```text
Home Directory
└── admin_console
    ├── report.txt
    └── snapshots
```

---

# Task 1: Create Your Workspace and Report File

## Create Directory Structure

Create the workspace:

```bash
mkdir -p ~/admin_console/snapshots
```

Create an empty report file:

```bash
touch ~/admin_console/report.txt
```

Verify:

```bash
ls -R ~/admin_console
```

Expected Output:

```text
admin_console
├── report.txt
└── snapshots
```

---

# Task 2: Read Key Logs and Create a Summary

## Navigate to Log Directory

```bash
cd /var/log
```

List log files:

```bash
ls
```

---

## Capture Beginning of Authentication Log

```bash
head /var/log/secure > ~/admin_console/snapshots/auth_head.txt
```

or

```bash
head /var/log/auth.log > ~/admin_console/snapshots/auth_head.txt
```

---

## Capture End of Authentication Log

```bash
tail /var/log/secure > ~/admin_console/snapshots/auth_tail.txt
```

or

```bash
tail /var/log/auth.log > ~/admin_console/snapshots/auth_tail.txt
```

---

## Write Summary to Report

```bash
echo "Authentication log snapshots captured successfully." \
>> ~/admin_console/report.txt
```

Verify:

```bash
cat ~/admin_console/report.txt
```

---

# Task 3: Check DNS, Remote IP, and HTTP Reachability

## Resolve example.com

```bash
getent hosts example.com
```

Save output:

```bash
getent hosts example.com \
> ~/admin_console/snapshots/dns.txt
```

Verify:

```bash
cat ~/admin_console/snapshots/dns.txt
```

---

## Capture HTTP Headers

```bash
curl -I https://example.com \
> ~/admin_console/snapshots/http_headers.txt
```

---

## Capture HTTP Status Code

```bash
curl -s -o /dev/null \
-w "%{http_code}\n" https://example.com \
> ~/admin_console/snapshots/http_status.txt
```

---

## Capture Remote IP

```bash
curl -s https://ifconfig.me
```

Save:

```bash
curl -s https://ifconfig.me \
> ~/admin_console/snapshots/public_ip.txt
```

---

## Append Summary to Report

```bash
echo "DNS resolution and HTTP connectivity verified." \
>> ~/admin_console/report.txt
```

---

# Task 4: Inspect Processes and Demonstrate Priority Management

## Capture Process Snapshot

```bash
ps -eo pid,ppid,ni,cmd --sort=-ni \
> ~/admin_console/snapshots/ps_top.txt
```

Verify:

```bash
head ~/admin_console/snapshots/ps_top.txt
```

---

## Start a Background Process

Run sleep with lower priority:

```bash
nice -n 10 sleep 300 &
```

Check process:

```bash
ps -ef | grep sleep
```

---

## Identify Process ID

```bash
pgrep sleep
```

Example Output:

```text
12345
```

---

## Change Process Priority

```bash
renice 5 12345
```

Example Output:

```text
12345 (process ID) old priority 10, new priority 5
```

---

## Verify Priority

```bash
ps -o pid,ni,cmd -p 12345
```

---

## Record Action in Report

```bash
echo "Process priority modified using nice and renice." \
>> ~/admin_console/report.txt
```

---

# Verify Final Report

```bash
cat ~/admin_console/report.txt
```

Example Output:

```text
Authentication log snapshots captured successfully.
DNS resolution and HTTP connectivity verified.
Process priority modified using nice and renice.
```

---

# Final Directory Structure

```text
~/admin_console
│
├── report.txt
│
└── snapshots
    ├── auth_head.txt
    ├── auth_tail.txt
    ├── dns.txt
    ├── http_headers.txt
    ├── http_status.txt
    ├── public_ip.txt
    └── ps_top.txt
```

---

# Commands Used

## Directory Management

```bash
mkdir
```

```bash
touch
```

```bash
ls
```

---

## Log Analysis

```bash
head
```

```bash
tail
```

---

## DNS and Networking

```bash
getent hosts
```

```bash
curl
```

---

## Process Management

```bash
ps
```

```bash
nice
```

```bash
renice
```

```bash
pgrep
```

---

# RHCSA Skills Practiced

- Log Monitoring
- DNS Resolution
- HTTP Connectivity Testing
- Process Inspection
- Process Priority Management
- Report Generation
- Linux Troubleshooting

---

# Conclusion

This lab demonstrates how to build a lightweight Linux administration console for logs, network diagnostics, and process management. The toolkit can be reused for daily monitoring and troubleshooting tasks in real-world Linux environments.