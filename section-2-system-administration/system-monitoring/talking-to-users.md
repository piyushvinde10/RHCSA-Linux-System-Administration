# Talking to Users in Linux (users, wall, write)

Linux provides commands to communicate with other logged-in users on the system.

These commands are useful for:

- Sending system-wide messages
- Communicating with specific users
- Monitoring logged-in users

---

# 1. users Command

The `users` command displays **currently logged-in users**.

## Syntax

```
users
```

## Example

```
users
```

Output:

```
student devops piyush
```

---

# 2. wall Command (Write All)

The `wall` command sends a message to **all logged-in users**.

## Syntax

```
wall
```

Then type your message and press:

```
Ctrl + D
```

## Example

```
wall
System will be restarted in 5 minutes
```

All users will receive this message.

---

# 3. write Command

The `write` command sends a message to a **specific user**.

## Syntax

```
write username terminal
```

## Example

```
write devops pts/1
```

Then type your message:

```
Hello, please check the server logs
```

Press:

```
Ctrl + D
```

to send the message.

---

# Find User Terminal

Before using `write`, check user terminal using:

```
who
```

Example output:

```
devops pts/1 2026-03-24 14:53
```

Use `pts/1` in the write command.

---

# Summary

| Command | Purpose |
|--------|--------|
| `users` | Show logged-in users |
| `wall` | Send message to all users |
| `write` | Send message to a specific user |

---

# RHCSA Note

These commands are useful for:

- System announcements
- Admin-to-user communication
- Multi-user environment management

They are commonly used in **Linux system administration and RHCSA preparation**.