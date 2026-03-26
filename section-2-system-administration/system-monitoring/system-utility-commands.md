# System Utility Commands in Linux

System utility commands are used to check system information, time, and perform basic operations.

---

# 1. date Command

Displays the current system date and time.

## Syntax

```
date
```

## Example

```
date
```

Output:

```
Thu Mar 26 13:31:31 UTC 2026
```

---

# 2. uptime Command

Shows how long the system has been running.

## Syntax

```
uptime
```

## Example

```
uptime
```

Output includes:

- System running time
- Number of users
- Load average

---

# 3. hostname Command

Displays the system name.

## Syntax

```
hostname
```

## Example

```
hostname
```

Output:

```
workstation
```

---

# 4. uname Command

Displays system and kernel information.

## Syntax

```
uname
```

## Example

```
uname
```

Output:

```
Linux
```

## Useful Option

```
uname -a
```

Displays all system details.

---

# 5. which Command

Shows the location of a command.

## Syntax

```
which command_name
```

## Example

```
which ls
```

Output:

```
/usr/bin/ls
```

---

# 6. cal Command

Displays calendar.

## Syntax

```
cal
```

## Example

```
cal
```

Displays current month calendar.

---

# 7. bc Command

`bc` is a calculator used for arithmetic operations.

## Syntax

```
bc
```

## Example

```
bc
5+2
7
```

Exit:

```
Ctrl + C
```

---

# Summary

| Command | Purpose |
|--------|--------|
| `date` | Show current date and time |
| `uptime` | Show system running time |
| `hostname` | Show system name |
| `uname` | Show system info |
| `which` | Locate command path |
| `cal` | Show calendar |
| `bc` | Calculator |

---

# RHCSA Note

These commands are useful for:

- System monitoring
- Troubleshooting
- Checking system information

They are commonly used in **Linux system administration and RHCSA preparation**. :contentReference[oaicite:0]{index=0}