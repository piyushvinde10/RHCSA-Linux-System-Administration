# Log Monitoring in Linux

Log monitoring is used to **analyze system activity, errors, and events**.

Most log files are stored in:

```
/var/log
```

---

# 1. List Log Files

To view all log files:

```
cd /var/log
ll
```

This directory contains important logs like:

- boot logs
- cron logs
- system logs
- security logs

---

# 2. Cron Job Logs

To view cron-related logs:

```
more cron
```

This shows:

- Scheduled jobs execution
- Cron service activity

---

# 3. Boot Process Logs

To view system boot logs:

```
more boot
```

Shows:

- System startup process
- Services started during boot

---

# 4. Mail Logs

To check mail server logs:

```
more maillog
```

Used for:

- Mail service activity
- Email troubleshooting

---

# 5. System Messages Log

To view system messages:

```
more messages
```

Shows:

- System events
- Service logs
- General system activity

---

# 6. Security Logs

To check security-related logs:

```
more secure
```

Shows:

- Login attempts
- Sudo usage
- Authentication logs

---

# Useful Commands for Logs

## View First Lines

```
head filename
```

---

## View Last Lines

```
tail filename
```

---

## Scroll Through Logs

```
more filename
```

---

# Summary

| Log Type | Command |
|--------|--------|
| Log directory | `/var/log` |
| Cron logs | `more cron` |
| Boot logs | `more boot` |
| Mail logs | `more maillog` |
| System logs | `more messages` |
| Security logs | `more secure` |

---

# Key Learning

- Logs help in troubleshooting issues  
- Important for monitoring system activity  
- Used for debugging and security analysis  

---

# RHCSA Note

Log monitoring is important for:

- System troubleshooting  
- Security auditing  
- Performance monitoring  

It is a **core skill for Linux administrators and RHCSA exams**. 