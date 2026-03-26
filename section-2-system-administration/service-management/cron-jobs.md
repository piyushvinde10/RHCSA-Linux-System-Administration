# Cron Jobs (crontab) in Linux

Cron is used to **schedule tasks automatically** at specific times in Linux.

It is widely used for:

- Backups
- Automation scripts
- System maintenance

---

# What is crontab?

`crontab` is a command used to manage scheduled jobs (cron jobs).

Each user can have their own crontab file.

---

# 1. Edit Crontab

```
crontab -e
```

- Opens crontab file in editor
- Used to add new scheduled tasks

---

# 2. List Crontab

```
crontab -l
```

- Displays all scheduled jobs

---

# 3. Remove Crontab

```
crontab -r
```

- Deletes all cron jobs of current user

---

# Cron Job Format

```
* * * * * command
```

| Field | Meaning |
|------|--------|
| 1 | Minute (0–59) |
| 2 | Hour (0–23) |
| 3 | Day of month (1–31) |
| 4 | Month (1–12) |
| 5 | Day of week (0–7) |
| 6 | Command |

---

# Example

## Run every minute

```
* * * * * date
```

---

## Create Directory Every Minute

```
* * * * * mkdir /home/student/piyush-dir
```

---

# Check Cron Service

```
systemctl status crond
```

- Ensures cron service is running

---

# Important Points

- Cron service must be active
- Commands should have full path if needed
- Output can be redirected to files

---

# Example with Output

```
* * * * * date >> /home/student/output.txt
```

---

# Summary

| Command | Purpose |
|--------|--------|
| `crontab -e` | Edit cron jobs |
| `crontab -l` | List cron jobs |
| `crontab -r` | Remove cron jobs |
| `systemctl status crond` | Check cron service |

---

# RHCSA Note

Cron jobs are important for:

- Automation
- Scheduled tasks
- System maintenance

They are widely used in **Linux system administration and RHCSA exams**. :contentReference[oaicite:0]{index=0}