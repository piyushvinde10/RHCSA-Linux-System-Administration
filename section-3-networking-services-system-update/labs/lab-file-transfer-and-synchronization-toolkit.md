# Lab: Create a File Transfer and Synchronization Toolkit

## Objective

Build a simple toolkit for file transfer and synchronization using Linux commands such as:

- mkdir
- echo
- wget
- scp
- rsync
- ls

This lab demonstrates downloading files, copying files securely, and synchronizing directories.

---

# Scenario

You need a lightweight toolkit that can:

- Download files from the internet
- Transfer files securely
- Synchronize folders
- Create reusable file-transfer workflows

All work will be performed inside your home directory.

---

# Task 1: Set Up Workspace and Sample Data

## Create Working Directory

```bash
mkdir -p ~/transfer_lab
cd ~/transfer_lab
```

---

## Create Subdirectories

```bash
mkdir incoming outgoing mirror
```

Verify:

```bash
ls -l
```

Expected Output:

```text
incoming
outgoing
mirror
```

---

## Create Sample File

```bash
echo "This is a sample file for transfer testing." > sample.txt
```

Verify:

```bash
cat sample.txt
```

---

## Copy Sample File to Outgoing Folder

```bash
cp sample.txt outgoing/
```

Verify:

```bash
ls outgoing
```

---

# Task 2: Download a File into Incoming Folder

## Move to Incoming Directory

```bash
cd ~/transfer_lab/incoming
```

---

## Download Test Web Page

```bash
wget -O web.html https://example.com
```

Verify:

```bash
ls -lh
```

Expected Output:

```text
web.html
```

---

## View Downloaded File

```bash
head web.html
```

---

# Task 3: Copy Files Securely

## Copy Downloaded File

```bash
cp ~/transfer_lab/incoming/web.html \
~/transfer_lab/outgoing/web_copy.html
```

---

## Copy Sample File

```bash
cp ~/transfer_lab/sample.txt \
~/transfer_lab/outgoing/sample_copy.txt
```

---

## Verify Files

```bash
ls -lh ~/transfer_lab/outgoing
```

Expected Output:

```text
sample.txt
sample_copy.txt
web_copy.html
```

---

## SCP Example (Remote Copy)

```bash
scp sample.txt user@192.168.1.100:/tmp
```

Example:

```bash
scp web.html user@server:/home/user
```

> Requires SSH access to the remote server.

---

# Task 4: Synchronize Folders

## Create Mirror Copy

Synchronize outgoing folder to mirror folder:

```bash
rsync -av outgoing/ mirror/
```

---

## Verify Synchronization

```bash
ls -R mirror
```

Expected Output:

```text
mirror/
├── sample.txt
├── sample_copy.txt
└── web_copy.html
```

---

## Update Source File

```bash
echo "Updated content" >> outgoing/sample.txt
```

---

## Synchronize Again

```bash
rsync -av outgoing/ mirror/
```

Only changed files will be copied.

---

## Verify Updated File

```bash
cat mirror/sample.txt
```

---

# Verify Directory Structure

```bash
tree ~/transfer_lab
```

Expected Structure:

```text
transfer_lab/
├── incoming
│   └── web.html
├── outgoing
│   ├── sample.txt
│   ├── sample_copy.txt
│   └── web_copy.html
├── mirror
│   ├── sample.txt
│   ├── sample_copy.txt
│   └── web_copy.html
└── sample.txt
```

---

# Commands Used

| Command | Purpose |
|----------|----------|
| mkdir | Create directories |
| echo | Create sample data |
| wget | Download files |
| cp | Copy files |
| scp | Secure file transfer |
| rsync | Synchronize directories |
| ls | Verify files |

---

# Skills Practiced

- Directory creation
- File downloading
- Secure file transfer
- Directory synchronization
- Data verification
- Linux file management

---

# Summary

This lab demonstrates:

- Creating a file transfer workspace
- Downloading files using wget
- Copying files locally and remotely
- Synchronizing folders using rsync
- Verifying transferred files

These are common Linux administration tasks used for backups, migrations, file sharing, and automation.