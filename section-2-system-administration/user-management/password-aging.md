# Password Aging in Linux (chage Command)

Password aging is used to **control how long a user password remains valid**.  
It helps improve system security by enforcing password expiration policies.

---

# 1. Check Current Password Aging

Use the following command:

```
chage -l username
```

Example:

```
chage -l piyush
```

Output shows:

- Last password change
- Password expiry
- Password inactive time
- Account expiry
- Minimum/maximum days between password changes
- Warning period before password expires

---

# 2. chage Command

The `chage` command is used to **set password aging policies**.

## Syntax

```
chage [options] username
```

---

## Important Options

| Option | Description |
|--------|------------|
| `-d` | Last password change (days) |
| `-m` | Minimum days between password change |
| `-M` | Maximum days before password expires |
| `-W` | Warning days before expiry |
| `-I` | Inactive days after expiry |
| `-E` | Account expiration date |

---

## Example

```
chage -d 5 -m 15 -M 15 -W 10 -I 18 -E 22 piyush
```

This sets:

- Last password change → 5 days ago  
- Minimum days → 15  
- Maximum days → 15  
- Warning period → 10 days  
- Inactive period → 18 days  
- Account expiry → day 22  

---

# 3. /etc/login.defs File

This file defines **default password aging policies**.

View file:

```
cat /etc/login.defs
```

Important parameters:

| Parameter | Description |
|----------|------------|
| `PASS_MAX_DAYS` | Maximum days password is valid |
| `PASS_MIN_DAYS` | Minimum days between changes |
| `PASS_MIN_LEN` | Minimum password length |
| `PASS_WARN_AGE` | Days before expiry to warn user |

---

# Summary

Password aging helps:

- Enforce password security
- Force regular password changes
- Prevent unauthorized long-term access

---

# RHCSA Note

Password aging is important for:

- Security policies
- User account management
- Enterprise Linux administration

It is commonly used in **real-world Linux systems and RHCSA exams**. :contentReference[oaicite:0]{index=0}