# OpenLDAP Installation and Configuration

## Overview

OpenLDAP is an open-source implementation of the Lightweight Directory Access Protocol (LDAP).

LDAP is used to centrally manage:

- User Accounts
- Groups
- Authentication
- Directory Information
- Access Control

OpenLDAP enables centralized authentication across multiple Linux systems.

---

# What is LDAP?

LDAP stands for:

```text
Lightweight Directory Access Protocol
```

LDAP stores information in a hierarchical directory structure.

Example:

```text
dc=example,dc=com
│
├── ou=People
│   ├── user1
│   └── user2
│
└── ou=Groups
    ├── admins
    └── developers
```

---

# Benefits of OpenLDAP

- Centralized user management
- Centralized authentication
- Single sign-on support
- Easy user administration
- Scalability
- Cross-platform support

---

# LDAP Ports

| Protocol | Port |
|-----------|------|
| LDAP | 389 |
| LDAPS | 636 |

---

# Install OpenLDAP Packages

Install server and client packages:

```bash
dnf install openldap openldap-servers openldap-clients -y
```

Verify installation:

```bash
rpm -qa | grep openldap
```

---

# Start OpenLDAP Service

Start service:

```bash
systemctl start slapd
```

Enable service:

```bash
systemctl enable slapd
```

Verify status:

```bash
systemctl status slapd
```

---

# Verify LDAP Port

Check listening ports:

```bash
ss -tulnp | grep slapd
```

Expected:

```text
389/tcp
```

---

# Configure Firewall

Allow LDAP service:

```bash
firewall-cmd --permanent --add-service=ldap
```

Reload firewall:

```bash
firewall-cmd --reload
```

Verify:

```bash
firewall-cmd --list-services
```

---

# Create LDAP Administrator Password

Generate password hash:

```bash
slappasswd
```

Example Output:

```text
{SSHA}abc123xyz456
```

Copy the generated hash.

---

# Configure LDAP Database

Create file:

```bash
vi rootpw.ldif
```

Add:

```ldif
dn: olcDatabase={2}mdb,cn=config
changetype: modify
replace: olcRootPW
olcRootPW: {SSHA}abc123xyz456
```

Apply configuration:

```bash
ldapmodify -Y EXTERNAL -H ldapi:/// -f rootpw.ldif
```

---

# Create Base Domain

Example Domain:

```text
example.com
```

Create file:

```bash
vi basedomain.ldif
```

Add:

```ldif
dn: dc=example,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
o: Example Company
dc: example

dn: ou=People,dc=example,dc=com
objectClass: organizationalUnit
ou: People

dn: ou=Groups,dc=example,dc=com
objectClass: organizationalUnit
ou: Groups
```

Import data:

```bash
ldapadd -x -D "cn=Manager,dc=example,dc=com" -W -f basedomain.ldif
```

---

# Verify LDAP Entries

Display entries:

```bash
ldapsearch -x -b "dc=example,dc=com"
```

Expected Output:

```text
dc=example,dc=com
ou=People
ou=Groups
```

---

# Create LDAP User

Create file:

```bash
vi user1.ldif
```

Add:

```ldif
dn: uid=user1,ou=People,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount

cn: User One
sn: One
uid: user1
uidNumber: 10001
gidNumber: 10001
homeDirectory: /home/user1
loginShell: /bin/bash
userPassword: password123
```

Add user:

```bash
ldapadd -x -D "cn=Manager,dc=example,dc=com" -W -f user1.ldif
```

---

# Search LDAP User

```bash
ldapsearch -x uid=user1
```

---

# Modify LDAP User

Create file:

```bash
vi modifyuser.ldif
```

Example:

```ldif
dn: uid=user1,ou=People,dc=example,dc=com
changetype: modify
replace: loginShell
loginShell: /bin/sh
```

Apply:

```bash
ldapmodify -x -D "cn=Manager,dc=example,dc=com" -W -f modifyuser.ldif
```

---

# Delete LDAP User

```bash
ldapdelete -x -D "cn=Manager,dc=example,dc=com" -W \
"uid=user1,ou=People,dc=example,dc=com"
```

---

# Useful LDAP Commands

## Search Directory

```bash
ldapsearch -x
```

---

## Add Entry

```bash
ldapadd -x -D "cn=Manager,dc=example,dc=com" -W
```

---

## Modify Entry

```bash
ldapmodify -x -D "cn=Manager,dc=example,dc=com" -W
```

---

## Delete Entry

```bash
ldapdelete -x -D "cn=Manager,dc=example,dc=com" -W
```

---

# OpenLDAP Directory Structure

```text
dc=example,dc=com
│
├── ou=People
│   ├── user1
│   ├── user2
│   └── user3
│
└── ou=Groups
    ├── admins
    ├── developers
    └── support
```

---

# Troubleshooting

## Verify Service

```bash
systemctl status slapd
```

---

## Verify Port

```bash
ss -tulnp | grep 389
```

---

## Check Logs

```bash
journalctl -u slapd
```

---

## Verify LDAP Search

```bash
ldapsearch -x
```

---

# RHCSA Notes

Important commands:

```bash
dnf install openldap openldap-servers openldap-clients
```

```bash
systemctl start slapd
```

```bash
systemctl enable slapd
```

```bash
ldapsearch -x
```

```bash
ldapadd
```

```bash
ldapmodify
```

```bash
ldapdelete
```

LDAP is commonly used in enterprise Linux environments for centralized authentication and user management.

---

# Summary

| Command | Purpose |
|----------|----------|
| systemctl start slapd | Start LDAP service |
| systemctl enable slapd | Enable at boot |
| ldapsearch | Search LDAP entries |
| ldapadd | Add entries |
| ldapmodify | Modify entries |
| ldapdelete | Delete entries |
| slappasswd | Generate password hash |

---

# Conclusion

OpenLDAP provides centralized authentication and directory services for Linux environments. It simplifies user and group management across multiple systems. Understanding OpenLDAP installation, configuration, user management, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.