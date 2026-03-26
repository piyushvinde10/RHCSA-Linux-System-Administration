# top Command (Linux Process Monitoring)

The `top` command is used to **monitor system processes in real-time**.

It shows:

- CPU usage
- Memory usage
- Running processes
- System load

---

# 1. Basic top Command

```
top
```

Displays:

- Running processes
- CPU usage
- Memory usage
- Load average

Press:

```
q
```

to exit.

---

# 2. top for Specific User

```
top -u username
```

Example:

```
top -u student
```

Shows only processes of a specific user.

---

# 3. Kill Process from top

Run:

```
top
```

Then press:

```
k
```

- Enter PID (Process ID)
- Press Enter
- Process will be terminated

---

# 4. Sort Processes

Inside `top`, use:

## Sort by Memory

```
M
```

## Sort by CPU

```
P
```

---

# What You See in top

- PID → Process ID  
- USER → Owner of process  
- %CPU → CPU usage  
- %MEM → Memory usage  
- COMMAND → Process name  

---

# Summary

| Command | Purpose |
|--------|--------|
| `top` | Real-time process monitoring |
| `top -u user` | User-specific processes |
| `k` (inside top) | Kill process |
| `M` | Sort by memory |
| `P` | Sort by CPU |

---

# RHCSA Note

The `top` command is important for:

- Monitoring system performance
- Troubleshooting high CPU usage
- Managing processes

It is widely used in **Linux system administration and RHCSA exams**. :contentReference[oaicite:0]{index=0}