# at Command (One-Time Job Scheduling in Linux)

The `at` command is used to **schedule a job to run once at a specific time**.

Unlike `cron`, which runs tasks repeatedly, `at` runs tasks **only once**.

---

# What is at?

- Used for one-time scheduling
- Executes commands at a specific future time
- Useful for temporary tasks

---

# 1. Schedule a Job

```
at HH:MM AM/PM
```

## Example

```
at 04:28 PM
```

Then enter command:

```
echo "Hello world" > /home/student/file.txt
```

Press:

```
Ctrl + D
```

The job will run at the specified time.

---

# 2. View Scheduled Jobs

```
atq
```

Displays:

- Job ID
- Scheduled time
- User

---

# 3. Remove Scheduled Job

```
atrm job_id
```

## Example

```
atrm 1
```

Removes job with ID 1.

---

# 4. Different Time Formats

## Specific Date & Time

```
at 12:00 AM 032726
```

---

## After Some Days

```
at 4PM + 4 days
```

---

## After Few Hours

```
at now + 5 hours
```

---

## Specific Day

```
at 8:00 AM Sun
```

---

## Next Month

```
at 10:00 AM next month
```

---

# Important Notes

- `atd` service must be running
- Commands are executed using `/bin/sh`
- Useful for temporary or delayed tasks

---

# Summary

| Command | Purpose |
|--------|--------|
| `at` | Schedule one-time job |
| `atq` | List scheduled jobs |
| `atrm` | Remove job |

---

# Difference Between at and cron

| Feature | at | cron |
|--------|----|------|
| Execution | One-time | Repeated |
| Use case | Temporary task | Regular scheduling |

---

# RHCSA Note

The `at` command is important for:

- One-time automation
- Task scheduling
- System maintenance

It is commonly used in **Linux administration and RHCSA preparation**. :contentReference[oaicite:0]{index=0}