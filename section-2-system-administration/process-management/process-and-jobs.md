# Process and Job Management in Linux

A **process** is a running instance of a program.  
Linux allows you to manage processes and control jobs efficiently.

---

# What is a Process?

- A program in execution
- Each process has a unique **PID (Process ID)**
- Can run in foreground or background

---

# 1. View Running Processes

## ps Command

```
ps
```

Shows processes of current terminal.

## Full Process List

```
ps -ef
```

Displays all running processes.

---

## top Command

```
top
```

- Shows real-time processes
- Displays CPU and memory usage
- Press `q` to exit

---

# 2. Background and Foreground Jobs

## Run Process in Background

```
command &
```

Example:

```
sleep 100 &
```

---

## View Jobs

```
jobs
```

Shows running background jobs.

---

## Bring Job to Foreground

```
fg %job_number
```

Example:

```
fg %1
```

---

## Send Job to Background

```
bg %job_number
```

---

# 3. Kill Process

## Kill using PID

```
kill PID
```

Example:

```
kill 1234
```

---

## Force Kill

```
kill -9 PID
```

- Terminates process immediately

---

## Kill by Name

```
pkill process_name
```

Example:

```
pkill sleep
```

---

# 4. Process Priority (nice & renice)

## Start Process with Priority

```
nice -n 10 command
```

## Change Priority

```
renice -n 5 -p PID
```

- Lower value → higher priority  
- Higher value → lower priority  

---

# 5. Process States

| State | Meaning |
|------|--------|
| R | Running |
| S | Sleeping |
| Z | Zombie |
| T | Stopped |

---

# Summary

- Process = running program  
- Use `ps`, `top` to monitor  
- Use `kill`, `pkill` to stop  
- Use `jobs`, `fg`, `bg` to manage jobs  
- Use `nice`, `renice` for priority  

---

# RHCSA Note

Process management is important for:

- System performance
- Troubleshooting
- Resource control

It is a **very important topic in RHCSA exams and real-world Linux administration**.