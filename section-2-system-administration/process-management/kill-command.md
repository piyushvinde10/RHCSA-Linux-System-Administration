# kill Command (Linux Process Control)

The `kill` command is used to **terminate or send signals to processes** in Linux.

Each process is identified by a **PID (Process ID)**.

---

# 1. List All Signals

```
kill -l
```

Displays all available signals.

Examples:

- `SIGKILL` (9)
- `SIGTERM` (15)
- `SIGINT` (2)

---

# 2. Kill Process by PID

```
kill PID
```

Example:

```
kill 1020
```

Sends default signal (`SIGTERM`) to terminate process.

---

# 3. Common Signals

## 3.1 kill -1 (SIGHUP)

```
kill -1 PID
```

- Reloads process
- Often used for configuration reload

---

## 3.2 kill -2 (SIGINT)

```
kill -2 PID
```

- Interrupt signal (same as Ctrl + C)

---

## 3.3 kill -9 (SIGKILL)

```
kill -9 PID
```

- Forcefully terminates process
- Cannot be ignored

---

## 3.4 kill -15 (SIGTERM)

```
kill -15 PID
```

- Gracefully stops process
- Default signal

---

# Difference Between Signals

| Signal | Number | Purpose |
|-------|--------|--------|
| SIGHUP | 1 | Reload process |
| SIGINT | 2 | Interrupt |
| SIGKILL | 9 | Force kill |
| SIGTERM | 15 | Graceful stop |

---

# Example Workflow

Check process:

```
ps -ef | grep nginx
```

Kill process:

```
kill -15 9391
```

Force kill:

```
kill -9 9391
```

---

# Important Notes

- Always try `kill -15` first  
- Use `kill -9` only if process does not stop  
- Requires permission (root for some processes)

---

# Summary

- `kill` is used to manage processes  
- Signals control how process behaves  
- Helps in troubleshooting and system management  

---

# RHCSA Note

The `kill` command is important for:

- Process management
- Troubleshooting stuck processes
- System performance tuning

It is a **core concept in RHCSA and real-world Linux administration**. :contentReference[oaicite:0]{index=0}