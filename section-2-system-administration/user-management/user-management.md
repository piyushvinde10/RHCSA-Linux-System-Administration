# User Account Management (Linux)

User account management is an essential task in Linux system administration.  
It involves creating, modifying, and deleting users and groups.

---

# 1. useradd Command

The `useradd` command is used to create a new user.

## Syntax

```
sudo useradd username
```

## Example

```
sudo useradd piyush
```

Check user entry:

```
cat /etc/passwd | grep piyush
```

This file stores user account information. :contentReference[oaicite:0]{index=0}

---

# 2. userdel Command

The `userdel` command is used to delete a user.

## Syntax

```
sudo userdel username
```

## Example

```
sudo userdel piyush
```

---

# 3. groupadd Command

The `groupadd` command is used to create a new group.

## Syntax

```
sudo groupadd groupname
```

## Example

```
sudo groupadd tester
```

Check group:

```
cat /etc/group | grep tester
```

---

# 4. groupdel Command

The `groupdel` command is used to delete a group.

## Syntax

```
sudo groupdel groupname
```

## Example

```
sudo groupdel tester
```

---

# 5. /etc/shadow File

The `/etc/shadow` file stores encrypted user passwords.

Check user password details:

```
sudo cat /etc/shadow | grep username
```

This file is accessible only by root user. :contentReference[oaicite:1]{index=1}

---

# 6. usermod Command

The `usermod` command is used to modify user accounts.

---

## Change Username

```
sudo usermod -l newname oldname
```

Example:

```
sudo usermod -l demo1 demo
```

---

## Change Primary Group

```
sudo usermod -g groupname username
```

Example:

```
sudo usermod -g tester demo1
```

---

## Add User to Multiple Groups

```
sudo usermod -aG groupname username
```

Example:

```
sudo usermod -aG dev demo1
```

Check groups:

```
groups demo1
```

---

# 7. Example Workflow

Create group:

```
sudo groupadd superheroes
```

Create user with group:

```
sudo useradd -g superheroes -m spiderman
```

Check:

```
groups spiderman
```

Output:

```
spiderman : superheroes
```

---

# Important Files

| File | Description |
|------|------------|
| `/etc/passwd` | Stores user details |
| `/etc/shadow` | Stores encrypted passwords |
| `/etc/group` | Stores group information |

---

# Summary

User management includes:

- Creating users → `useradd`
- Deleting users → `userdel`
- Creating groups → `groupadd`
- Deleting groups → `groupdel`
- Modifying users → `usermod`

---

# RHCSA Note

User account management is one of the **most important topics in RHCSA**.

It is used for:

- Managing system users
- Assigning permissions
- Controlling access to resources