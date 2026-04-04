# Lab 4: Create a System Health & Monitoring Report

This lab focuses on monitoring system performance, managing processes, checking logs, and summarizing system health.

---

# Task 1: Manage and Monitor Processes

## Objectives

- Start a process
- Move process to background
- Bring process to foreground
- Check running processes
- Set process priority

---

## 1. Start a Process

```
sleep 100
```

---

## 2. Run Process in Background

```
sleep 100 &
```

---

## 3. Move Running Process to Background

```
Ctrl + Z
bg
```

---

## 4. Bring Process to Foreground

```
fg %1
```

---

## 5. Check Running Processes

```
ps
ps aux
top
```

---

## 6. View Background Jobs

```
jobs
```

---

## 7. Set Process Priority

```
nice -n 5 sleep 100
```

---

# Task 2: Check System Usage & Resources

## Objectives

- Monitor system resources
- Check disk, memory, and CPU usage

---

## 1. Disk Usage

```
df -h
```

---

## 2. Memory Usage

```
free -m
```

---

## 3. Running Processes

```
top
```

---

# Task 3: Review System Logs

## Objectives

- View system log files
- Analyze logs

---

## 1. List Log Files

```
ll /var/log
```

---

## 2. View Log Content

### Boot Logs

```
head /var/log/boot.log
tail /var/log/boot.log
```

---

### Mail Logs

```
head /var/log/maillog
cat /var/log/maillog
```

---

### System Messages

```
head /var/log/messages
tail /var/log/messages
```

---

### Security Logs

```
head /var/log/secure
tail /var/log/secure
```

---

# Task 4: Summarize System Health Information

## Objectives

- Check logged-in users
- Monitor active sessions
- View login history

---

## 1. Check Logged-in Users

```
who
```

---

## 2. View User Activity

```
w
```

---

## 3. View Login History

```
last
```

---

# Summary

| Area | Command |
|------|--------|
| Process Management | `ps`, `top`, `jobs`, `fg`, `bg` |
| Disk Usage | `df -h` |
| Memory Usage | `free -m` |
| Logs | `/var/log/*` |
| Users | `who`, `w`, `last` |

---

# Key Learning

- Process control (foreground/background)
- System resource monitoring
- Log analysis
- User session tracking

---

# RHCSA Note

This lab covers important RHCSA topics:

- Process management
- System monitoring
- Log analysis
- User activity tracking

These are **real-world Linux system administrator skills**. :contentReference[oaicite:0]{index=0}