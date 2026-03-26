# Linux Directory Service & Account Authentication

Account authentication in Linux is the process of verifying a user's identity before granting access to the system.

Linux supports different types of user accounts and authentication mechanisms.

---

# What is Account Authentication?

Authentication ensures that:

- The user is valid
- The password is correct
- Access is granted securely

---

# Types of Accounts

## 1. Local Account

A local account is created and stored **on the same Linux system**.

### Features

- Stored in local files:
  - `/etc/passwd`
  - `/etc/shadow`
  - `/etc/group`
- Used for standalone systems
- No network dependency

### Example

```
sudo useradd piyush
passwd piyush
```

### Use Case

- Personal systems
- Small environments
- Testing and development

---

## 2. Domain / Directory Accounts

Domain accounts are managed **centrally using a directory service**.

### Examples of Directory Services

- LDAP (Lightweight Directory Access Protocol)
- Active Directory (AD)

---

## Features

- Centralized authentication
- Single login across multiple systems
- User data stored on server
- Scalable for large organizations

---

## Example Scenario

- User logs into any system in network
- Credentials verified from central server
- Same username/password works everywhere

---

# Difference Between Local and Domain Accounts

| Feature | Local Account | Domain Account |
|--------|-------------|---------------|
| Storage | Local system | Central server |
| Management | Individual | Centralized |
| Scalability | Limited | High |
| Network Required | No | Yes |
| Example | useradd | LDAP / AD |

---

# Authentication Process

1. User enters username and password  
2. System verifies credentials  
3. If valid → access granted  
4. If invalid → access denied  

---

# Summary

- Authentication is required to access Linux systems  
- Local accounts are stored on the system  
- Domain accounts are centrally managed  
- Used based on system size and requirements  

---

# RHCSA Note

Understanding account types and authentication is important for:

- User management
- Security
- Enterprise system administration

This concept is useful for **RHCSA and real-world Linux environments**.