# Lab: Build a Simple Network Troubleshooting Toolkit

## Objective

Build a small network troubleshooting toolkit in your home directory that can:

- Perform quick connectivity checks
- Save network snapshots
- Verify HTTP/HTTPS access
- Inspect sockets
- Capture SSH client information

---

# Scenario

You are a Linux administrator and need a lightweight toolkit for basic network troubleshooting.

Tasks include:

- Creating a workspace
- Testing web connectivity
- Capturing socket information
- Verifying outbound HTTPS access
- Checking SSH client configuration

---

# Task 1: Set Up Workspace and Verify HTTP Reachability

## Create Workspace

```bash
mkdir -p ~/net_lab
cd ~/net_lab
```

---

## Create Report File

```bash
touch report.txt
```

---

## Record HTTP Headers

```bash
curl -I https://example.com > headers.txt
```

---

## Record HTTP Status Code

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://example.com > status.txt
```

---

## Perform Host Lookup

```bash
host example.com > host_lookup.txt
```

---

## Save Directory Listing

```bash
ls -lh > file_list.txt
```

---

## Append Results to Report

```bash
echo "=== HTTP Reachability Check ===" >> report.txt
cat status.txt >> report.txt
```

---

# Task 2: Save Lightweight Socket Snapshot

## Capture TCP and UDP Socket Information

```bash
ss -tuna > ss.out
```

---

## View First Few Lines

```bash
head ss.out
```

---

## Append Snapshot Summary

```bash
echo "" >> report.txt
echo "=== Socket Snapshot ===" >> report.txt
head -10 ss.out >> report.txt
```

---

# Task 3: Check External Reachability Using curl

## Save HTTP Headers

```bash
curl -I https://example.com > curl_headers.txt
```

---

## Save Status Code

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://example.com > curl_status.txt
```

---

## Save Timing Information

```bash
curl -o /dev/null -s -w "Connect: %{time_connect}s\nTotal: %{time_total}s\n" https://example.com > curl_timing.txt
```

---

## Append Status to Report

```bash
echo "" >> report.txt
echo "=== HTTPS Reachability ===" >> report.txt
cat curl_status.txt >> report.txt
```

---

# Task 4: Verify SSH Client and Capture Configuration

## Check SSH Version

```bash
ssh -V
```

Example:

```text
OpenSSH_8.7p1
```

---

## Save SSH Version

```bash
ssh -V 2>> report.txt
```

---

## Capture Effective SSH Configuration

```bash
ssh -G localhost > ssh_config.txt
```

---

## Verify Configuration File

```bash
head ssh_config.txt
```

---

## Append SSH Information

```bash
echo "" >> report.txt
echo "=== SSH Configuration ===" >> report.txt
head -10 ssh_config.txt >> report.txt
```

---

# Verify Generated Files

```bash
ls -lh ~/net_lab
```

Expected Files:

```text
report.txt
headers.txt
status.txt
host_lookup.txt
file_list.txt
ss.out
curl_headers.txt
curl_status.txt
curl_timing.txt
ssh_config.txt
```

---

# View Final Report

```bash
cat report.txt
```

---

# Skills Practiced

- Directory creation
- File management
- curl command
- host lookup
- ss command
- SSH client configuration
- Output redirection
- Report generation
- Network troubleshooting

---

# Summary

This lab creates a lightweight network troubleshooting toolkit that collects:

- HTTP reachability information
- DNS lookup results
- Socket statistics
- HTTPS status codes
- Timing metrics
- SSH client configuration

These commands are commonly used in Linux administration, troubleshooting, and RHCSA environments.