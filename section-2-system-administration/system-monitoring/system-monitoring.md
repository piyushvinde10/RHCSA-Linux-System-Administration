# System Monitoring in Linux

System monitoring is used to check:

- CPU usage
- Memory usage
- Disk usage
- Network activity
- System performance

---

# 1. top Command

```
top
```

- Displays real-time system processes  
- Shows CPU, memory, and running processes  

Press:

```
q
```

to exit.

---

# 2. df Command

```
df
```

- Shows disk space usage  

## Human Readable Format

```
df -h
```

- Displays sizes in KB, MB, GB  

---

# 3. dmesg Command

```
dmesg
```

- Displays kernel messages  
- Useful for hardware and boot logs  

---

# 4. iostat Command

```
iostat -1
```

- Shows CPU and disk I/O statistics  
- Useful for performance monitoring  

---

# 5. netstat Command

```
netstat
```

- Displays network connections  
- Shows listening ports and active connections  

---

# 6. ip route Command

```
ip route
```

- Displays routing table  
- Shows network paths and gateways  

---

# 7. ss Command

```
ss | more
```

- Displays socket statistics  
- Faster alternative to `netstat`  

---

# 8. free Command

```
free
```

- Shows memory usage  

## In MB Format

```
free -m
```

---

# 9. CPU Information

```
cat /proc/cpuinfo
```

- Displays CPU details  
- Shows cores, model, speed  

---

# 10. Memory Information

```
cat /proc/meminfo
```

- Displays detailed memory usage  

---

# Summary

| Command | Purpose |
|--------|--------|
| `top` | Real-time monitoring |
| `df -h` | Disk usage |
| `dmesg` | Kernel logs |
| `iostat` | CPU & disk stats |
| `netstat` | Network info |
| `ip route` | Routing table |
| `ss` | Socket info |
| `free -m` | Memory usage |
| `/proc/cpuinfo` | CPU details |
| `/proc/meminfo` | Memory details |

---

# RHCSA Note

System monitoring is important for:

- Performance tuning  
- Troubleshooting issues  
- Resource management  

These commands are widely used in **Linux system administration and RHCSA exams**. :contentReference[oaicite:0]{index=0}