# Standard Signals vs Real-Time Signals in Linux

Linux signals are divided into two main categories:

1. Standard Signals
2. Real-Time Signals

These signals are used to control and communicate with processes.

---

# 1. Standard Signals

Standard signals are the **traditional UNIX signals**.

## Features

- Fixed set of signals
- Do NOT queue (only one instance is delivered)
- If multiple signals are sent → only one is handled
- Lower priority than real-time signals

---

## Common Standard Signals

| Signal | Number | Description |
|-------|--------|-------------|
| SIGHUP | 1 | Reload configuration |
| SIGINT | 2 | Interrupt (Ctrl + C) |
| SIGQUIT | 3 | Quit process |
| SIGKILL | 9 | Force kill (cannot be ignored) |
| SIGTERM | 15 | Graceful termination |
| SIGSTOP | 19 | Stop process |
| SIGCONT | 18 | Continue process |

---

## Example

```
kill -15 1234
```

Gracefully terminates process.

---

# 2. Real-Time Signals

Real-time signals are **advanced signals introduced in POSIX**.

## Features

- Signals are **queued**
- Multiple signals are NOT lost
- Delivered in order
- Higher priority than standard signals
- Used for real-time applications

---

## Range of Real-Time Signals

```
SIGRTMIN to SIGRTMAX
```

Check range:

```
kill -l
```

Example output:

```
SIGRTMIN+1, SIGRTMIN+2 ... SIGRTMAX
```

---

## Example

```
kill -34 1234
```

(Signal 34 is usually first real-time signal)

---

# Key Differences

| Feature | Standard Signals | Real-Time Signals |
|--------|----------------|------------------|
| Queue | ❌ No | ✅ Yes |
| Delivery | May lose signals | Guaranteed |
| Order | Not guaranteed | Ordered |
| Priority | Lower | Higher |
| Range | Fixed | Dynamic (SIGRTMIN–SIGRTMAX) |

---

# Important Points

- Standard signals are used for **basic process control**
- Real-time signals are used for **advanced communication**
- Real-time signals ensure **no signal loss**

---

# Summary

- Standard signals → simple, widely used  
- Real-time signals → reliable, queued, advanced  
- Both are important for process management  

---

# RHCSA Note

Understanding signal types helps in:

- Process control
- Debugging applications
- Advanced Linux administration

This is an **advanced concept useful for RHCSA and system-level understanding**.