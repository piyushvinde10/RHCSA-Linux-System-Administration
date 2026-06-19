# Installing, Configuring and Managing Ansible

## Overview

Ansible is an open-source automation tool used for:

- Configuration Management
- Application Deployment
- Server Provisioning
- Infrastructure Automation
- Orchestration

Ansible works without installing agents on managed nodes and uses SSH for communication.

---

# What is Ansible?

Ansible automates repetitive administration tasks across multiple Linux servers.

Features:

- Agentless Architecture
- SSH-Based Communication
- Simple YAML Playbooks
- Idempotent Operations
- Easy Configuration Management

---

# Ansible Architecture

```text
                 Control Node
                       |
          --------------------------
          |            |           |
      Managed      Managed     Managed
       Node          Node        Node
```

---

# Install Ansible on RHEL/CentOS

Install EPEL Repository:

```bash
dnf install epel-release -y
```

Install Ansible:

```bash
dnf install ansible -y
```

For older systems:

```bash
yum install epel-release -y
```

```bash
yum install ansible -y
```

---

# Verify Installation

Check version:

```bash
ansible --version
```

Example Output:

```text
ansible [core 2.x.x]
```

---

# Inventory File

Default inventory location:

```text
/etc/ansible/hosts
```

Edit inventory:

```bash
vi /etc/ansible/hosts
```

Example:

```ini
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
192.168.1.20
```

---

# Configure Passwordless SSH

Generate SSH Key:

```bash
ssh-keygen
```

Copy key to managed node:

```bash
ssh-copy-id user@192.168.1.10
```

Test login:

```bash
ssh user@192.168.1.10
```

---

# Test Ansible Connectivity

Ping all managed nodes:

```bash
ansible all -m ping
```

Expected Output:

```text
SUCCESS
```

---

# Ad-Hoc Commands

Check uptime:

```bash
ansible all -a "uptime"
```

Check disk usage:

```bash
ansible all -a "df -h"
```

Check memory:

```bash
ansible all -a "free -m"
```

---

# Create First Playbook

Create file:

```bash
vi install_apache.yml
```

Content:

```yaml
---
- name: Install Apache on webservers
  hosts: webservers
  become: yes

  tasks:

    - name: Install httpd
      yum:
        name: httpd
        state: present

    - name: Start and enable httpd
      service:
        name: httpd
        state: started
        enabled: true
```

---

# Run Playbook

Execute:

```bash
ansible-playbook install_apache.yml
```

---

# Verify Apache

Check service:

```bash
ansible webservers -a "systemctl status httpd"
```

---

# Inventory Commands

Display inventory:

```bash
ansible-inventory --list
```

---

# Syntax Check

Validate playbook:

```bash
ansible-playbook install_apache.yml --syntax-check
```

---

# Common Ansible Modules

| Module | Purpose |
|----------|----------|
| ping | Connectivity Test |
| yum | Package Management |
| dnf | Package Management |
| service | Service Control |
| copy | Copy Files |
| file | Manage Files |
| user | User Management |
| cron | Schedule Jobs |

---

# Service Management Example

```yaml
- name: Start Apache
  service:
    name: httpd
    state: started
```

---

# Package Installation Example

```yaml
- name: Install Git
  yum:
    name: git
    state: present
```

---

# Useful Commands

## Check Version

```bash
ansible --version
```

---

## Ping Nodes

```bash
ansible all -m ping
```

---

## Run Command

```bash
ansible all -a "hostname"
```

---

## Run Playbook

```bash
ansible-playbook playbook.yml
```

---

## Inventory List

```bash
ansible-inventory --list
```

---

## Syntax Check

```bash
ansible-playbook playbook.yml --syntax-check
```

---

# Troubleshooting

## Verify SSH Connectivity

```bash
ssh user@server-ip
```

---

## Verify Inventory

```bash
ansible-inventory --list
```

---

## Check Ping Module

```bash
ansible all -m ping
```

---

## Verify Ansible Installation

```bash
ansible --version
```

---

# Directory Structure

```text
/etc/ansible/
│
├── ansible.cfg
├── hosts
│
└── playbooks/
    ├── install_apache.yml
    └── install_nginx.yml
```

---

# RHCSA Notes

Important commands:

```bash
ansible --version
```

```bash
ansible all -m ping
```

```bash
ansible all -a "hostname"
```

```bash
ansible-playbook playbook.yml
```

```bash
ansible-inventory --list
```

```bash
ansible-playbook playbook.yml --syntax-check
```

---

# Summary

| Command | Purpose |
|----------|----------|
| ansible --version | Check Version |
| ansible all -m ping | Connectivity Test |
| ansible all -a "command" | Execute Command |
| ansible-playbook file.yml | Run Playbook |
| ansible-inventory --list | Display Inventory |
| --syntax-check | Validate Playbook |

---

# Conclusion

Ansible is a powerful automation tool used for configuration management, software deployment, and infrastructure automation. Understanding Ansible installation, inventory management, SSH configuration, ad-hoc commands, playbooks, and troubleshooting is valuable for RHCSA preparation and modern Linux administration.