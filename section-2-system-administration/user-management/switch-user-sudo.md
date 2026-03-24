# Switch User and Sudo Access in Linux

In Linux, users can switch between accounts and execute commands with elevated privileges using `su` and `sudo`.

---

# 1. Switch User (su Command)

The `su` command is used to switch from one user to another.

## Syntax

```
su - username
```

## Example

```
su - demo
```

- Switches to user `demo`
- Loads user environment (home directory, variables)

---

# 2. sudo Command

The `sudo` command allows a user to execute commands with **root (admin) privileges**.

## Syntax

```
sudo command
```

## Example

```
sudo useradd -m piyush1
```

This creates a new user with administrative privileges.

---

## Why use sudo?

- Provides secure access to admin commands
- Avoids logging in directly as root
- Tracks command usage

---

# 3. visudo Command

The `visudo` command is used to safely edit the sudo configuration file.

## Syntax

```
sudo visudo
```

- Opens `/etc/sudoers` file
- Prevents syntax errors
- Ensures system safety

---

# 4. /etc/sudoers File

This file defines **which users can run what commands with sudo**.

## Example Entry

```
root    ALL=(ALL)    ALL
```

This means:

- User `root` can run all commands on all systems

---

## Grant Sudo Access to User

Add entry:

```
username ALL=(ALL) ALL
```

Example:

```
piyush ALL=(ALL) ALL
```

---

## Allow Sudo Without Password

```
username ALL=(ALL) NOPASSWD: ALL
```

⚠️ Use carefully (security risk)

---

# Example Workflow

Switch user:

```
su - devops
```

Try creating file:

```
touch /etc/myfile.txt
```

Permission denied.

Now use sudo:

```
sudo touch /etc/myfile.txt
```

Now file is created successfully.

---

# Summary

- `su` → Switch user
- `sudo` → Execute commands as root
- `visudo` → Edit sudo permissions safely
- `/etc/sudoers` → Controls admin access

---

# RHCSA Note

Understanding `su`, `sudo`, and `/etc/sudoers` is essential for:

- System administration
- User privilege management
- Security control in Linux systems

These concepts are **very important for RHCSA exams and real-world environments**. :contentReference[oaicite:0]{index=0}