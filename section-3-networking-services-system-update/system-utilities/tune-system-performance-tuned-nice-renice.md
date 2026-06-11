# Tune System Performance (tuned, nice and renice)

## Overview

System performance tuning is the process of optimizing Linux resources such as CPU, memory, storage, and network performance.

Linux provides several tools to manage system performance:

- tuned
- nice
- renice

These tools help administrators optimize resource utilization and prioritize critical applications.

---

# What is Performance Tuning?

Performance tuning involves:

- Optimizing CPU usage
- Managing process priorities
- Improving system responsiveness
- Applying workload-specific configurations

Benefits:

- Better application performance
- Reduced resource contention
- Improved system stability
- Efficient hardware utilization

---

# tuned

## What is tuned?

`tuned` is a Linux performance tuning daemon that automatically adjusts system settings according to predefined profiles.

Package:

```text
tuned
```

Service:

```text
tuned
```

---

# Install tuned

```bash
dnf install tuned -y
```

Verify installation:

```bash
rpm -qa | grep tuned
```

---

# Start tuned Service

```bash
systemctl start tuned
```

Enable at boot:

```bash
systemctl enable tuned
```

Check status:

```bash
systemctl status tuned
```

---

# Display Active Profile

```bash
tuned-adm active
```

Example:

```text
Current active profile: balanced
```

---

# List Available Profiles

```bash
tuned-adm list
```

Example:

```text
Available profiles:
- balanced
- throughput-performance
- powersave
- virtual-guest
- virtual-host
```

---

# Common tuned Profiles

| Profile | Purpose |
|----------|----------|
| balanced | Default profile |
| throughput-performance | Maximum performance |
| powersave | Save power |
| virtual-guest | Virtual machines |
| virtual-host | Virtualization hosts |
| latency-performance | Low latency workloads |

---

# Apply a Profile

Example:

```bash
tuned-adm profile throughput-performance
```

Verify:

```bash
tuned-adm active
```

---

# Recommend Profile

```bash
tuned-adm recommend
```

Example:

```text
virtual-guest
```

---

# Disable tuned

```bash
systemctl stop tuned
```

```bash
systemctl disable tuned
```

---

# nice Command

## What is nice?

The `nice` command starts a process with a specific CPU scheduling priority.

Range:

```text
-20 to 19
```

Priority:

```text
-20 = Highest Priority
19  = Lowest Priority
```

Default:

```text
0
```

---

# View Process Priority

```bash
ps -el
```

or

```bash
top
```

Look for:

```text
NI (Nice Value)
```

---

# Start Process with Nice Value

Example:

```bash
nice -n 10 tar -cvf backup.tar /home
```

---

# Start High Priority Process

```bash
nice -n -10 command
```

Example:

```bash
nice -n -10 backup_script.sh
```

Root privileges required.

---

# Display Nice Value

```bash
ps -eo pid,ni,cmd
```

Example Output:

```text
PID NI CMD
1234 10 tar
```

---

# renice Command

## What is renice?

`renice` changes the priority of a running process.

Unlike `nice`, it works on already running processes.

---

# Find Process ID

```bash
ps -ef
```

or

```bash
pgrep process_name
```

---

# Change Priority

Syntax:

```bash
renice priority PID
```

Example:

```bash
renice 10 1234
```

Output:

```text
1234 (process ID) old priority 0, new priority 10
```

---

# Increase Process Priority

Example:

```bash
renice -5 1234
```

Root privileges required.

---

# Change Multiple Processes

```bash
renice 5 1234 5678 9101
```

---

# Verify Priority

```bash
ps -eo pid,ni,cmd
```

or

```bash
top
```

---

# Example Workflow

Start process:

```bash
nice -n 15 dd if=/dev/zero of=testfile bs=1M count=1000
```

Find PID:

```bash
ps -ef | grep dd
```

Change priority:

```bash
renice 5 PID
```

Verify:

```bash
top
```

---

# Useful Commands

## Check tuned Status

```bash
systemctl status tuned
```

---

## List Profiles

```bash
tuned-adm list
```

---

## Active Profile

```bash
tuned-adm active
```

---

## Apply Profile

```bash
tuned-adm profile balanced
```

---

## Start Process with Priority

```bash
nice -n 10 command
```

---

## Modify Running Process

```bash
renice 5 PID
```

---

## View Priorities

```bash
ps -eo pid,ni,cmd
```

---

# Troubleshooting

## Verify tuned Service

```bash
systemctl status tuned
```

---

## Verify Active Profile

```bash
tuned-adm active
```

---

## Check Process Priority

```bash
top
```

---

## Check Nice Values

```bash
ps -eo pid,ni,cmd
```

---

# RHCSA Notes

Important commands:

```bash
dnf install tuned
```

```bash
systemctl start tuned
```

```bash
tuned-adm list
```

```bash
tuned-adm active
```

```bash
nice -n 10 command
```

```bash
renice 5 PID
```

```bash
top
```

Performance tuning is commonly tested in RHCSA labs and is important for Linux server optimization.

---

# Summary

| Command | Purpose |
|----------|----------|
| tuned-adm list | List tuning profiles |
| tuned-adm active | Show active profile |
| tuned-adm profile profile_name | Apply profile |
| nice -n value command | Start process with priority |
| renice value PID | Change running process priority |
| top | Monitor process priorities |

---

# Conclusion

Linux performance tuning helps optimize system resources and improve application responsiveness. The `tuned` service provides automatic system optimization through predefined profiles, while `nice` and `renice` allow administrators to control CPU scheduling priorities. Understanding these tools is valuable for RHCSA preparation and real-world Linux administration.