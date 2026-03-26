# systemctl Command (Service Management in Linux)

The `systemctl` command is used to manage system services in Linux systems that use **systemd**.

It is an important command for controlling services like:

- Web server
- Database server
- SSH service

---

# What is systemctl?

`systemctl` is used to:

- Start services
- Stop services
- Restart services
- Check service status
- Enable services at boot
- Control system power

---

# 1. Start a Service

```
systemctl start service_name
```

Example:

```
systemctl start httpd
```

---

# 2. Check Service Status

```
systemctl status service_name
```

Example:

```
systemctl status httpd
```

Shows:

- Running status
- Logs
- Process details

---

# 3. Stop a Service

```
systemctl stop service_name
```

Example:

```
systemctl stop httpd
```

---

# 4. Restart a Service

```
systemctl restart service_name
```

Example:

```
systemctl restart httpd
```

---

# 5. Enable Service at Boot

```
systemctl enable service_name
```

Example:

```
systemctl enable httpd
```

- Starts service automatically at system boot

---

# 6. Power Off System

```
systemctl poweroff
```

- Shuts down the system

---

# 7. Reboot System

```
systemctl reboot
```

- Restarts the system

---

# 8. Halt System

```
systemctl halt
```

- Stops all CPU functions

---

# Summary

| Command | Purpose |
|--------|--------|
| `systemctl start` | Start service |
| `systemctl status` | Check status |
| `systemctl stop` | Stop service |
| `systemctl restart` | Restart service |
| `systemctl enable` | Enable at boot |
| `systemctl poweroff` | Shutdown system |
| `systemctl reboot` | Restart system |
| `systemctl halt` | Halt system |

---

# RHCSA Note

The `systemctl` command is very important for:

- Managing system services
- Troubleshooting services
- Controlling system state

It is one of the **most important commands in RHCSA and real-world Linux administration**. :contentReference[oaicite:0]{index=0}