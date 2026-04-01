# Job Control & Process Management in Linux

Linux provides powerful commands to control running processes and jobs.

This includes:

- Stopping processes
- Running in background
- Bringing to foreground
- Running processes after logout
- Controlling process priority

---

# 1. Stop Process (Ctrl + Z)

```
Ctrl + Z
```

- Suspends (pauses) the running process
- Moves process to background (stopped state)

Example:

```
sleep 10
Ctrl + Z
```

Output:

```
[1]+ Stopped sleep 10
```

---

# 2. jobs Command

```
jobs
```

- Displays all background/stopped jobs

Example:

```
[1]+ Stopped sleep 10
```

---

# 3. bg Command (Background)

```
bg %job_number
```

- Resumes stopped job in background

Example:

```
bg %1
```

Output:

```
[1]+ sleep 100 &
```

---

# 4. fg Command (Foreground)

```
fg %job_number
```

- Brings background job to foreground

Example:

```
fg %1
```

---

# 5. nohup Command

```
nohup command
```

- Runs process even after logout
- Output saved in `nohup.out`

Example:

```
nohup sleep 100
```

---

## Run in Background with nohup

```
nohup sleep 100 > /dev/null 2>&1 &
```

Explanation:

- `/dev/null` → discard output  
- `2>&1` → redirect errors  
- `&` → run in background  

---

# 6. pkill Command

```
pkill process_name
```

- Kills process using name

Example:

```
pkill sleep
```

---

# 7. nice Command (Set Priority)

```
nice -n value command
```

Example:

```
nice -n 5 sleep 100
```

---

# Priority Range

- `-20` → Highest priority  
- `0` → Default  
- `19` → Lowest priority  

---

# Summary

| Command | Purpose |
|--------|--------|
| `Ctrl + Z` | Stop process |
| `jobs` | List jobs |
| `bg` | Run in background |
| `fg` | Bring to foreground |
| `nohup` | Run after logout |
| `pkill` | Kill by name |
| `nice` | Set priority |

---

# RHCSA Note

These commands are important for:

- Process control
- Background job management
- System performance tuning

They are commonly used in **Linux system administration and RHCSA exams**. :contentReference[oaicite:0]{index=0}