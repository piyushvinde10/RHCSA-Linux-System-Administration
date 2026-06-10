# Central Logger (rsyslog)

## Overview

Rsyslog is a logging service used in Linux systems to collect, store, process, and forward log messages.

It is the default logging daemon in most Red Hat-based Linux distributions.

Rsyslog can:

- Collect system logs
- Store logs locally
- Forward logs to remote servers
- Centralize logs from multiple servers
- Filter and organize logs
- Improve troubleshooting and auditing

---

# What is Centralized Logging?

Centralized logging allows multiple servers to send their logs to a single log server.

Architecture:

```text
Server1
   |
Server2
   |
Server3
   |
   v
Central Log Server (rsyslog)
```

Benefits:

- Easier monitoring
- Centralized troubleshooting
- Security auditing
- Log retention
- Compliance requirements

---

# What is rsyslog?

Rsyslog stands for:

```text
Rocket-fast System for Log Processing
```

Service:

```text
rsyslog
```

Configuration File:

```text
/etc/rsyslog.conf
```

---

# Install rsyslog

Install package:

```bash
dnf install rsyslog -y
```

Verify installation:

```bash
rpm -qa | grep rsyslog
```

---

# Start rsyslog Service

Start service:

```bash
systemctl start rsyslog
```

Enable service:

```bash
systemctl enable rsyslog
```

Verify status:

```bash
systemctl status rsyslog
```

---

# Common Log Files

| Log File | Purpose |
|-----------|----------|
| /var/log/messages | General system logs |
| /var/log/secure | Authentication logs |
| /var/log/maillog | Mail logs |
| /var/log/cron | Cron job logs |
| /var/log/boot.log | Boot logs |
| /var/log/dmesg | Kernel messages |

---

# View Logs

View messages log:

```bash
tail -f /var/log/messages
```

---

View security log:

```bash
tail -f /var/log/secure
```

---

View mail log:

```bash
tail -f /var/log/maillog
```

---

# Rsyslog Configuration File

Main configuration:

```bash
vi /etc/rsyslog.conf
```

View configuration:

```bash
cat /etc/rsyslog.conf
```

---

# Configure Central Log Server

Edit:

```bash
vi /etc/rsyslog.conf
```

Enable UDP Reception:

```conf
module(load="imudp")
input(type="imudp" port="514")
```

---

Enable TCP Reception:

```conf
module(load="imtcp")
input(type="imtcp" port="514")
```

---

# Restart Service

```bash
systemctl restart rsyslog
```

---

# Verify Listening Ports

```bash
ss -tulnp | grep 514
```

Expected Output:

```text
udp LISTEN *:514
tcp LISTEN *:514
```

---

# Configure Firewall

Allow Syslog Port:

```bash
firewall-cmd --permanent --add-port=514/udp
```

```bash
firewall-cmd --permanent --add-port=514/tcp
```

Reload firewall:

```bash
firewall-cmd --reload
```

---

# Configure Log Client

Edit:

```bash
vi /etc/rsyslog.conf
```

Add:

```conf
*.* @192.168.1.100:514
```

For TCP:

```conf
*.* @@192.168.1.100:514
```

Where:

```text
@   = UDP
@@  = TCP
```

---

# Restart Client Service

```bash
systemctl restart rsyslog
```

---

# Verify Remote Logging

Generate test log:

```bash
logger "Test message from client"
```

Check server:

```bash
tail -f /var/log/messages
```

Expected:

```text
Test message from client
```

---

# Log Facilities

| Facility | Purpose |
|-----------|----------|
| auth | Authentication |
| authpriv | Secure authentication |
| cron | Cron jobs |
| daemon | System services |
| kern | Kernel logs |
| mail | Mail services |
| user | User processes |
| local0-local7 | Custom applications |

---

# Log Priorities

| Priority | Description |
|-----------|------------|
| emerg | Emergency |
| alert | Immediate action required |
| crit | Critical |
| err | Error |
| warning | Warning |
| notice | Normal but significant |
| info | Informational |
| debug | Debugging |

---

# Custom Log Rule

Example:

```conf
authpriv.*    /var/log/auth.log
```

---

Log cron messages:

```conf
cron.*        /var/log/cron.log
```

---

# Create Custom Log File

Example:

```conf
local7.*      /var/log/custom.log
```

Restart:

```bash
systemctl restart rsyslog
```

Generate test log:

```bash
logger -p local7.info "Custom log test"
```

Verify:

```bash
cat /var/log/custom.log
```

---

# Test Logging

Create message:

```bash
logger "This is a test log"
```

Verify:

```bash
tail /var/log/messages
```

---

# Rsyslog Service Management

Start:

```bash
systemctl start rsyslog
```

Stop:

```bash
systemctl stop rsyslog
```

Restart:

```bash
systemctl restart rsyslog
```

Enable:

```bash
systemctl enable rsyslog
```

Status:

```bash
systemctl status rsyslog
```

---

# Troubleshooting

## Verify Service

```bash
systemctl status rsyslog
```

---

## Verify Port

```bash
ss -tulnp | grep 514
```

---

## Verify Firewall

```bash
firewall-cmd --list-ports
```

---

## Verify Configuration

```bash
rsyslogd -N1
```

Expected:

```text
rsyslogd: End of config validation run.
```

---

## Check Logs

```bash
journalctl -u rsyslog
```

---

# Useful Commands

## View Messages

```bash
tail -f /var/log/messages
```

---

## Generate Test Log

```bash
logger "Test message"
```

---

## Validate Configuration

```bash
rsyslogd -N1
```

---

## Check Service

```bash
systemctl status rsyslog
```

---

## Verify Port

```bash
ss -tulnp | grep 514
```

---

# RHCSA Notes

Important commands:

```bash
systemctl status rsyslog
```

```bash
tail -f /var/log/messages
```

```bash
logger "Test Message"
```

```bash
rsyslogd -N1
```

```bash
journalctl -u rsyslog
```

```bash
ss -tulnp | grep 514
```

Centralized logging is commonly used in enterprise environments to collect logs from multiple Linux servers into a single location.

---

# Summary

| Command | Purpose |
|----------|----------|
| systemctl start rsyslog | Start service |
| systemctl enable rsyslog | Enable at boot |
| logger "message" | Generate log |
| tail -f /var/log/messages | View logs |
| rsyslogd -N1 | Validate config |
| ss -tulnp | Verify syslog port |

---

# Conclusion

Rsyslog is a powerful logging framework used to collect, store, and forward logs in Linux systems. Centralized logging improves monitoring, troubleshooting, security auditing, and operational visibility. Understanding rsyslog configuration, log forwarding, facilities, priorities, and troubleshooting is an important Linux administration skill and useful for RHCSA preparation.