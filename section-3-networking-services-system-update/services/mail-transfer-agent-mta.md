# Mail Transfer Agent (MTA)

## Overview

A Mail Transfer Agent (MTA) is software responsible for sending, receiving, and routing email messages between mail servers.

The MTA transfers emails from the sender to the recipient using the SMTP (Simple Mail Transfer Protocol).

Common Linux MTAs include:

- Postfix
- Sendmail
- Exim
- Qmail

In modern Linux systems, **Postfix** is the most commonly used MTA.

---

# What is an MTA?

MTA stands for:

```text
Mail Transfer Agent
```

Its primary functions are:

- Send emails
- Receive emails
- Route emails
- Queue emails
- Deliver emails to mailboxes

---

# Mail Flow

```text
User
  |
  v
Mail User Agent (MUA)
  |
  v
Mail Transfer Agent (MTA)
  |
  v
SMTP
  |
  v
Remote Mail Server
  |
  v
Recipient Mailbox
```

---

# Common Mail Components

| Component | Purpose |
|------------|----------|
| MUA | Mail User Agent |
| MTA | Mail Transfer Agent |
| MDA | Mail Delivery Agent |
| SMTP | Mail Transfer Protocol |
| POP3 | Retrieve Email |
| IMAP | Access Email |

---

# Mail Protocols

| Protocol | Port |
|-----------|------|
| SMTP | 25 |
| SMTP Secure | 465 |
| SMTP Submission | 587 |
| POP3 | 110 |
| IMAP | 143 |
| IMAPS | 993 |

---

# Postfix MTA

Postfix is the default MTA in many Linux distributions.

Package:

```text
postfix
```

Service:

```text
postfix
```

---

# Install Postfix

Install package:

```bash
dnf install postfix -y
```

Verify installation:

```bash
rpm -qa | grep postfix
```

---

# Start Postfix Service

Start service:

```bash
systemctl start postfix
```

Enable service:

```bash
systemctl enable postfix
```

Verify:

```bash
systemctl status postfix
```

---

# Main Configuration File

Location:

```text
/etc/postfix/main.cf
```

View:

```bash
cat /etc/postfix/main.cf
```

Edit:

```bash
vi /etc/postfix/main.cf
```

---

# Important Parameters

## Hostname

```conf
myhostname = mail.lab.local
```

---

## Domain Name

```conf
mydomain = lab.local
```

---

## Origin Domain

```conf
myorigin = $mydomain
```

---

## Network Interfaces

```conf
inet_interfaces = all
```

---

## Trusted Networks

```conf
mynetworks = 127.0.0.0/8, 192.168.1.0/24
```

---

# Restart Postfix

After configuration changes:

```bash
systemctl restart postfix
```

---

# Verify SMTP Port

Postfix listens on:

```text
TCP Port 25
```

Check:

```bash
ss -tulnp | grep 25
```

Expected Output:

```text
LISTEN 0 100 *:25
```

---

# Configure Firewall

Allow SMTP:

```bash
firewall-cmd --permanent --add-service=smtp
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

# Send Test Mail

Install mail utility:

```bash
dnf install mailx -y
```

Send email:

```bash
echo "Test Mail" | mail -s "Test Subject" root
```

---

# View Mail Queue

```bash
mailq
```

Example:

```text
Mail queue is empty
```

---

# Flush Mail Queue

```bash
postqueue -f
```

---

# Display Queue

```bash
postqueue -p
```

---

# Check Mail Logs

RHEL 8/9:

```bash
journalctl -u postfix
```

Traditional log file:

```bash
tail -f /var/log/maillog
```

---

# Mail Aliases

Edit aliases:

```bash
vi /etc/aliases
```

Example:

```text
admin: root
support: root
```

Apply changes:

```bash
newaliases
```

---

# Verify DNS MX Record

Check mail exchange record:

```bash
dig domain.com MX
```

Example:

```bash
dig gmail.com MX
```

---

# Troubleshooting

## Verify Service

```bash
systemctl status postfix
```

---

## Verify Port

```bash
ss -tulnp | grep 25
```

---

## Check Queue

```bash
mailq
```

---

## Check Logs

```bash
journalctl -u postfix
```

---

## Verify Hostname

```bash
hostnamectl
```

---

# Useful Commands

## Service Status

```bash
systemctl status postfix
```

---

## Restart Service

```bash
systemctl restart postfix
```

---

## View Queue

```bash
mailq
```

---

## Flush Queue

```bash
postqueue -f
```

---

## Check SMTP Port

```bash
ss -tulnp | grep 25
```

---

## Send Test Mail

```bash
mail -s "Subject" user
```

---

# Postfix Directory Structure

```text
/etc/postfix/
│
├── main.cf
├── master.cf
└── aliases
```

---

# RHCSA Notes

Important commands:

```bash
dnf install postfix
```

```bash
systemctl start postfix
```

```bash
systemctl enable postfix
```

```bash
mailq
```

```bash
postqueue -f
```

```bash
ss -tulnp | grep 25
```

```bash
journalctl -u postfix
```

These commands are commonly used in Linux administration and mail server management.

---

# Summary

| Command | Purpose |
|----------|----------|
| dnf install postfix | Install Postfix |
| systemctl start postfix | Start MTA |
| systemctl status postfix | Check status |
| mailq | View mail queue |
| postqueue -f | Flush queue |
| mail -s | Send test mail |
| ss -tulnp | Verify SMTP port |

---

# Conclusion

A Mail Transfer Agent (MTA) is responsible for sending, receiving, and routing email messages. Postfix is the most commonly used MTA in modern Linux environments. Understanding MTA concepts, SMTP, Postfix configuration, mail queues, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.