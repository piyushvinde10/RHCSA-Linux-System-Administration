# Monitor Users in Linux

Monitoring users in Linux helps administrators track:

- Who is currently logged in
- User activity
- Login history
- System usage

---

# 1. who Command

The `who` command shows **currently logged-in users**.

## Syntax

```
who
```

## Example Output

```
student  tty2   2026-03-24 14:24
devops   pts/1  2026-03-24 14:53
```

---

# 2. last Command

The `last` command shows **login history of users**.

## Syntax

```
last
```

## Example

- Displays login and logout times
- Shows system reboots
- Helps track past user activity

---

# 3. w Command

The `w` command shows:

- Logged-in users
- What they are doing
- System load

## Syntax

```
w
```

## Output Includes:

- Username
- Login time
- Idle time
- Running processes

---

# 4. finger Command

The `finger` command provides **detailed user information**.

## Syntax

```
finger username
```

Example:

```
finger piyush
```

---

# 5. id Command

The `id` command shows:

- User ID (UID)
- Group ID (GID)
- Groups the user belongs to

## Syntax

```
id
```

## Example

```
id devops
```

Output:

```
uid=1001(devops) gid=1001(devops) groups=1001(devops)
```

---

# Summary

| Command | Purpose |
|--------|--------|
| `who` | Show current users |
| `last` | Show login history |
| `w` | Show active users + activity |
| `finger` | Detailed user info |
| `id` | User and group identity |

---

# RHCSA Note

Monitoring users is important for:

- Security auditing
- Tracking system usage
- Detecting unauthorized access

These commands are commonly used in **Linux system administration and RHCSA exams**. :contentReference[oaicite:0]{index=0}