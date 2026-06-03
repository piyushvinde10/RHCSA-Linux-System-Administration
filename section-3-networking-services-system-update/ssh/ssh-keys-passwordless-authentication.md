# SSH Keys - Access Remote Server without Password

## Overview

SSH Key Authentication is a secure method that allows users to access remote Linux servers without entering a password every time.

Instead of passwords, SSH uses a pair of cryptographic keys:

- Public Key
- Private Key

SSH key authentication is more secure and convenient than password-based authentication.

---

# How SSH Key Authentication Works

```text
Client Machine
│
├── Private Key (Keep Secret)
└── Public Key (Share with Server)

            |
            | Authentication
            v

Remote Server
│
└── authorized_keys
```

The server verifies the user's public key and grants access if it matches the client's private key.

---

# Benefits of SSH Keys

- Stronger security
- No password required
- Faster login
- Supports automation and scripts
- Reduces brute-force attacks

---

# Step 1: Generate SSH Key Pair

On the client machine:

```bash
ssh-keygen
```

Example Output:

```text
Generating public/private rsa key pair.
Enter file in which to save the key:
```

Press Enter to accept the default location.

---

# Generated Files

```text
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

| File | Purpose |
|--------|----------|
| id_rsa | Private Key |
| id_rsa.pub | Public Key |

---

# Step 2: View Public Key

```bash
cat ~/.ssh/id_rsa.pub
```

Example:

```text
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQ...
```

---

# Step 3: Copy Public Key to Remote Server

## Recommended Method

```bash
ssh-copy-id user@192.168.1.100
```

Example:

```bash
ssh-copy-id root@192.168.1.100
```

This automatically copies the public key to:

```text
~/.ssh/authorized_keys
```

on the remote server.

---

# Manual Method

Copy the public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Login to remote server:

```bash
ssh user@192.168.1.100
```

Create SSH directory:

```bash
mkdir -p ~/.ssh
```

Set permissions:

```bash
chmod 700 ~/.ssh
```

Add public key:

```bash
vi ~/.ssh/authorized_keys
```

Paste the key and save.

Set permissions:

```bash
chmod 600 ~/.ssh/authorized_keys
```

---

# Step 4: Test Passwordless Login

From client:

```bash
ssh user@192.168.1.100
```

Expected Result:

```text
Login successful without password prompt.
```

---

# Verify SSH Key Authentication

Display authorized keys:

```bash
cat ~/.ssh/authorized_keys
```

Verify key files:

```bash
ls -l ~/.ssh
```

Example:

```text
id_rsa
id_rsa.pub
authorized_keys
```

---

# SSH Key File Permissions

## Client

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```

## Server

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

Incorrect permissions may prevent SSH key authentication from working.

---

# Disable Password Authentication

After confirming SSH key login works:

Edit SSH configuration:

```bash
sudo vi /etc/ssh/sshd_config
```

Change:

```text
PasswordAuthentication no
```

Save and restart SSH:

```bash
sudo systemctl restart sshd
```

---

# Verify SSH Configuration

Check syntax:

```bash
sudo sshd -t
```

No output indicates valid configuration.

---

# Generate Modern ED25519 Key

Recommended key type:

```bash
ssh-keygen -t ed25519
```

Generated Files:

```text
id_ed25519
id_ed25519.pub
```

Benefits:

- Strong security
- Faster authentication
- Smaller key size

---

# Useful SSH Commands

## Generate SSH Key

```bash
ssh-keygen
```

---

## Copy Key to Server

```bash
ssh-copy-id user@host
```

---

## Connect to Server

```bash
ssh user@host
```

---

## Secure File Transfer

```bash
scp file.txt user@host:/home/user
```

---

## Display Public Key

```bash
cat ~/.ssh/id_rsa.pub
```

---

# Common Troubleshooting

## Check SSH Service

```bash
systemctl status sshd
```

---

## Verify Authorized Keys

```bash
cat ~/.ssh/authorized_keys
```

---

## Verify Permissions

```bash
ls -ld ~/.ssh
ls -l ~/.ssh
```

---

## Debug SSH Connection

```bash
ssh -v user@192.168.1.100
```

---

# Security Best Practices

- Use SSH keys instead of passwords.
- Use ED25519 keys when possible.
- Protect private keys.
- Disable password authentication.
- Disable root login.
- Use strong passphrases.
- Rotate keys periodically.

---

# Summary

| Command | Purpose |
|----------|----------|
| ssh-keygen | Generate SSH keys |
| ssh-copy-id | Copy public key to server |
| ssh user@host | Connect to server |
| ssh -v user@host | Debug SSH connection |
| scp | Secure file transfer |
| chmod 600 authorized_keys | Secure key file |

---

# Conclusion

SSH Key Authentication is the preferred method for secure remote access. It eliminates the need for passwords, improves security, and is widely used in Linux administration, automation, DevOps, and RHCSA environments.