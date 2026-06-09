# New System Utility Command (timedatectl)

## Overview

`timedatectl` is a Linux system utility used to manage:

- System date
- System time
- Time zone
- Hardware clock (RTC)
- NTP synchronization

It is part of the **systemd** suite and is the recommended tool for time management in modern Linux distributions.

---

# What is timedatectl?

`timedatectl` provides a simple interface to:

- View current date and time
- Change system time
- Configure time zones
- Enable or disable NTP synchronization
- View RTC (Real-Time Clock) information

---

# Basic Syntax

```bash
timedatectl [OPTION]
```

---

# Display Current Date and Time

```bash
timedatectl
```

Example Output:

```text
Local time: Tue 2026-01-20 10:30:15 IST
Universal time: Tue 2026-01-20 05:00:15 UTC
RTC time: Tue 2026-01-20 05:00:15
Time zone: Asia/Kolkata (IST, +0530)
System clock synchronized: yes
NTP service: active
RTC in local TZ: no
```

---

# Display System Time

```bash
date
```

Example:

```text
Tue Jan 20 10:30:15 IST 2026
```

---

# List Available Time Zones

```bash
timedatectl list-timezones
```

Example:

```text
Asia/Kolkata
America/New_York
Europe/London
```

---

# Search Time Zone

```bash
timedatectl list-timezones | grep Asia
```

Example:

```text
Asia/Kolkata
Asia/Dubai
Asia/Tokyo
```

---

# Set Time Zone

Example:

```bash
timedatectl set-timezone Asia/Kolkata
```

Verify:

```bash
timedatectl
```

---

# Display Current Time Zone

```bash
timedatectl show --property=Timezone
```

Example Output:

```text
Timezone=Asia/Kolkata
```

---

# Enable NTP Synchronization

```bash
timedatectl set-ntp true
```

Verify:

```bash
timedatectl
```

Expected Output:

```text
NTP service: active
System clock synchronized: yes
```

---

# Disable NTP Synchronization

```bash
timedatectl set-ntp false
```

---

# Check NTP Status

```bash
timedatectl status
```

or

```bash
timedatectl
```

---

# Set System Date

Example:

```bash
timedatectl set-time "2026-01-20"
```

---

# Set System Time

Example:

```bash
timedatectl set-time "10:45:00"
```

---

# Set Date and Time Together

```bash
timedatectl set-time "2026-01-20 10:45:00"
```

Verify:

```bash
date
```

---

# Display Detailed Properties

```bash
timedatectl show
```

Example Output:

```text
Timezone=Asia/Kolkata
NTP=yes
CanNTP=yes
```

---

# Display Hardware Clock

```bash
hwclock
```

Example:

```text
2026-01-20 10:45:00
```

---

# Synchronize Hardware Clock with System Clock

```bash
hwclock --systohc
```

---

# Synchronize System Clock with Hardware Clock

```bash
hwclock --hctosys
```

---

# Display RTC Information

```bash
timedatectl
```

Example:

```text
RTC time: Tue 2026-01-20 05:15:00
```

---

# Common Administration Tasks

## Verify Time Synchronization

```bash
timedatectl
```

---

## Set Correct Time Zone

```bash
timedatectl set-timezone Asia/Kolkata
```

---

## Enable NTP

```bash
timedatectl set-ntp true
```

---

## Verify Time

```bash
date
```

---

# Troubleshooting

## Verify Chrony Service

```bash
systemctl status chronyd
```

---

## Verify NTP Synchronization

```bash
timedatectl
```

---

## Check Current Time Zone

```bash
timedatectl show --property=Timezone
```

---

## Check Hardware Clock

```bash
hwclock
```

---

## Verify Synchronization Source

```bash
chronyc tracking
```

---

# Useful Commands

## Show Current Settings

```bash
timedatectl
```

---

## List Time Zones

```bash
timedatectl list-timezones
```

---

## Set Time Zone

```bash
timedatectl set-timezone Asia/Kolkata
```

---

## Enable NTP

```bash
timedatectl set-ntp true
```

---

## Disable NTP

```bash
timedatectl set-ntp false
```

---

## Set Date and Time

```bash
timedatectl set-time "YYYY-MM-DD HH:MM:SS"
```

---

# RHCSA Notes

Important commands:

```bash
timedatectl
```

```bash
timedatectl list-timezones
```

```bash
timedatectl set-timezone Asia/Kolkata
```

```bash
timedatectl set-ntp true
```

```bash
date
```

```bash
hwclock
```

These commands are commonly used in RHCSA exams and enterprise Linux environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| timedatectl | Display time settings |
| timedatectl list-timezones | List time zones |
| timedatectl set-timezone | Set timezone |
| timedatectl set-ntp true | Enable NTP |
| timedatectl set-ntp false | Disable NTP |
| timedatectl set-time | Set date and time |
| hwclock | Display hardware clock |

---

# Conclusion

`timedatectl` is the modern Linux utility for managing system date, time, timezone, RTC, and NTP synchronization. It simplifies time administration and works seamlessly with Chrony and systemd-based systems. Understanding timedatectl is an important RHCSA skill for managing Linux servers accurately and efficiently.