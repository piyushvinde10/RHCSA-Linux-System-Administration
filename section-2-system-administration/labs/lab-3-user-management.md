# Lab 3: Manage Team Accounts and Enforce Password Policies

This lab focuses on managing user accounts, reviewing system information, and monitoring user activity in Linux.

---

# Task 1: Examine Existing User and Group Information

Use the following commands to check user and group details.

## Check User ID

```
id labuser
```

## Check User Groups

```
groups labuser
```

## View User Information

```
cat /etc/passwd
```

## View Group Information

```
cat /etc/group
```

### Outcome

- Understand user account structure
- View group membership
- Analyze system user records

---

# Task 2: Review Password and Account Details

## Search for Specific User

```
cat /etc/passwd | grep labuser
```

## Check File Permissions in /etc

```
ls -l /etc
```

### Outcome

- Understand account entries
- Review authentication-related files
- Analyze system configuration files

---

# Task 3: Check Access Rights and Environment

## Check Current User

```
whoami
```

## Check Home Directory

```
echo $HOME
```

## Check Default Shell

```
echo $SHELL
```

## Check User Identity

```
id
```

### Outcome

- Identify current user
- Understand environment variables
- Verify user permissions

---

# Task 4: Monitor User Activity

## Check Logged-in Users

```
who
```

## Check Active Sessions

```
w
```

## Check Login History

```
last
```

### Outcome

- Monitor system users
- Track login sessions
- Analyze user activity history

---

# Summary

This lab covers:

- User and group management basics
- Password and account verification
- Environment and access checking
- Monitoring system users

---

# RHCSA Note

This lab is important for:

- Real-world Linux administration
- Security monitoring
- User account management

It is a core part of **RHCSA preparation and system administration practice**. :contentReference[oaicite:0]{index=0}