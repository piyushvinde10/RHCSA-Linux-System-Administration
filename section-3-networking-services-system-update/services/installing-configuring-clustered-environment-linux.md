# Installing and Configuring a Clustered Environment on Linux

## Overview

A Cluster is a group of servers (nodes) that work together as a single system to provide:

- High Availability (HA)
- Load Balancing
- Fault Tolerance
- Scalability
- Service Continuity

Clustering is widely used in enterprise environments to minimize downtime and improve application availability.

---

# What is a Cluster?

A cluster consists of two or more servers connected together to provide a common service.

Architecture:

```text
             Client
                |
                |
        -----------------
        |               |
    Node-1         Node-2
   (Active)      (Passive)
        |               |
        -----------------
                |
          Shared Storage
```

---

# Benefits of Clustering

- High Availability
- Automatic Failover
- Load Distribution
- Improved Reliability
- Reduced Downtime
- Easy Scalability

---

# Cluster Components

| Component | Purpose |
|------------|----------|
| Node | Cluster Member |
| Corosync | Cluster Communication |
| Pacemaker | Resource Management |
| PCS | Cluster Administration Tool |
| Fencing | Prevent Split Brain |
| Shared Storage | Common Data Storage |

---

# Lab Environment

| Hostname | IP Address |
|-----------|------------|
| node1 | 192.168.100.161 |
| node2 | 192.168.100.162 |

---

# Step 1: Configure Hostname

Node1:

```bash
hostnamectl set-hostname node1
```

Node2:

```bash
hostnamectl set-hostname node2
```

Verify:

```bash
hostnamectl
```

---

# Step 2: Configure Hosts File

Edit:

```bash
vi /etc/hosts
```

Add:

```text
192.168.100.161 node1
192.168.100.162 node2
```

Verify:

```bash
ping node1
```

```bash
ping node2
```

---

# Step 3: Install Cluster Packages

Install packages on both nodes:

```bash
dnf install pcs pacemaker corosync fence-agents-all -y
```

Verify:

```bash
rpm -qa | grep pcs
```

```bash
rpm -qa | grep pacemaker
```

```bash
rpm -qa | grep corosync
```

---

# Step 4: Start PCS Service

Start:

```bash
systemctl start pcsd
```

Enable:

```bash
systemctl enable pcsd
```

Verify:

```bash
systemctl status pcsd
```

---

# Step 5: Set Password for hacluster User

```bash
passwd hacluster
```

Use the same password on both nodes.

---

# Step 6: Authenticate Cluster Nodes

Run from Node1:

```bash
pcs host auth node1 node2 \
-u hacluster \
-p redhat123
```

Expected Output:

```text
Authorized
```

---

# Step 7: Create Cluster

```bash
pcs cluster setup mycluster node1 node2
```

---

# Step 8: Start Cluster

```bash
pcs cluster start --all
```

Enable at boot:

```bash
pcs cluster enable --all
```

---

# Step 9: Verify Cluster Status

```bash
pcs status
```

Example Output:

```text
Cluster name: mycluster
2 nodes configured
```

---

# Step 10: Disable STONITH (Lab Environment)

For testing only:

```bash
pcs property set stonith-enabled=false
```

Verify:

```bash
pcs property list
```

---

# Step 11: Ignore Quorum (Two Node Lab)

```bash
pcs property set no-quorum-policy=ignore
```

---

# Step 12: Create Virtual IP Resource

```bash
pcs resource create VirtualIP \
ocf:heartbeat:IPaddr2 \
ip=192.168.100.200 \
cidr_netmask=24 \
op monitor interval=30s
```

Verify:

```bash
pcs resource show
```

---

# Step 13: Install Apache

Install on both nodes:

```bash
dnf install httpd -y
```

Start:

```bash
systemctl start httpd
```

Enable:

```bash
systemctl enable httpd
```

---

# Step 14: Create Apache Cluster Resource

```bash
pcs resource create WebServer \
systemd:httpd \
op monitor interval=30s
```

Verify:

```bash
pcs status
```

---

# Step 15: Test Failover

Stop node1:

```bash
pcs cluster stop node1
```

Verify resources move to node2:

```bash
pcs status
```

Expected:

```text
VirtualIP running on node2
WebServer running on node2
```

---

# Cluster Commands

## Cluster Status

```bash
pcs status
```

---

## Start Cluster

```bash
pcs cluster start --all
```

---

## Stop Cluster

```bash
pcs cluster stop --all
```

---

## Enable Cluster

```bash
pcs cluster enable --all
```

---

## Disable Cluster

```bash
pcs cluster disable --all
```

---

## Show Resources

```bash
pcs resource show
```

---

## Delete Resource

```bash
pcs resource delete WebServer
```

---

# Corosync Configuration

Configuration file:

```text
/etc/corosync/corosync.conf
```

View:

```bash
cat /etc/corosync/corosync.conf
```

---

# Pacemaker Service

Check:

```bash
systemctl status pacemaker
```

---

# Cluster Logs

View:

```bash
journalctl -u pacemaker
```

```bash
journalctl -u corosync
```

---

# Troubleshooting

## Verify Nodes

```bash
pcs status nodes
```

---

## Verify Resources

```bash
pcs resource show
```

---

## Verify Cluster

```bash
pcs cluster status
```

---

## Check Logs

```bash
journalctl -xe
```

---

# Useful Commands

## Cluster Status

```bash
pcs status
```

---

## Resource Status

```bash
pcs resource show
```

---

## Node Status

```bash
pcs status nodes
```

---

## Cluster Configuration

```bash
pcs config
```

---

# RHCSA Notes

Important commands:

```bash
dnf install pcs pacemaker corosync
```

```bash
systemctl start pcsd
```

```bash
pcs host auth
```

```bash
pcs cluster setup
```

```bash
pcs cluster start --all
```

```bash
pcs status
```

```bash
pcs resource create
```

Clustering is commonly used for high availability services in enterprise Linux environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| pcs status | View cluster status |
| pcs cluster start --all | Start cluster |
| pcs cluster stop --all | Stop cluster |
| pcs resource show | View resources |
| pcs resource create | Create resource |
| pcs config | View cluster configuration |

---

# Conclusion

Linux clustering provides high availability, fault tolerance, and service continuity. By using Pacemaker, Corosync, and PCS, administrators can build resilient environments capable of automatic failover and resource management. Understanding clustered environments is valuable for enterprise Linux administration and RHCSA/RHCE-level skills.