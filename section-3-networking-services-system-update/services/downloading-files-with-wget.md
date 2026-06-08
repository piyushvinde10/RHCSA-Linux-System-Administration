# Downloading Files or Apps using wget

## Overview

`wget` (Web Get) is a command-line utility used to download files from the internet.

It supports:

- HTTP
- HTTPS
- FTP

Linux administrators commonly use wget to download:

- Software packages
- ISO images
- Configuration files
- Scripts
- Updates

---

# Features of wget

- Download files from URLs
- Resume interrupted downloads
- Download in background
- Recursive website downloads
- Supports HTTP, HTTPS, and FTP
- Non-interactive operation

---

# Install wget

## RHEL / CentOS / Rocky Linux

```bash
sudo yum install wget -y
```

## Verify Installation

```bash
wget --version
```

---

# Basic Syntax

```bash
wget <URL>
```

---

# Download a File

```bash
wget https://example.com/file.txt
```

Example:

```bash
wget https://speed.hetzner.de/100MB.bin
```

---

# Save File with Different Name

```bash
wget -O myfile.txt https://example.com/file.txt
```

Example:

```bash
wget -O backup.txt https://example.com/data.txt
```

---

# Download in Background

```bash
wget -b https://example.com/file.iso
```

Check download log:

```bash
tail -f wget-log
```

---

# Resume Interrupted Download

```bash
wget -c https://example.com/file.iso
```

Useful for large downloads.

---

# Download Multiple Files

Create a file:

```bash
vi urls.txt
```

Example:

```text
https://example.com/file1.txt
https://example.com/file2.txt
https://example.com/file3.txt
```

Download all:

```bash
wget -i urls.txt
```

---

# Download Entire Website

```bash
wget --mirror https://example.com
```

---

# Limit Download Speed

```bash
wget --limit-rate=500k https://example.com/file.iso
```

---

# Download Using FTP

```bash
wget ftp://ftp.example.com/file.txt
```

---

# Download with Username and Password

```bash
wget --user=username --password=password URL
```

Example:

```bash
wget --user=admin --password=admin123 https://example.com/file.zip
```

---

# Ignore SSL Certificate Check

```bash
wget --no-check-certificate https://example.com/file.iso
```

> Use only for testing purposes.

---

# Download and Save Log

```bash
wget URL -o download.log
```

Example:

```bash
wget https://example.com/file.iso -o download.log
```

---

# Display Download Progress

```bash
wget https://example.com/file.iso
```

Example Output:

```text
100%[====================>] 100M
```

---

# Verify Downloaded File

List downloaded files:

```bash
ls -lh
```

Check file size:

```bash
du -sh filename
```

---

# Common Examples

## Download Linux ISO

```bash
wget https://download.rockylinux.org/pub/rocky.iso
```

---

## Download Script

```bash
wget https://example.com/install.sh
```

---

## Download Configuration File

```bash
wget https://example.com/config.conf
```

---

## Resume ISO Download

```bash
wget -c rocky-linux.iso
```

---

# Common Troubleshooting

## Verify Internet Connectivity

```bash
ping google.com
```

---

## Verify DNS Resolution

```bash
host google.com
```

---

## Test URL

```bash
curl -I https://example.com
```

---

## Check Download Log

```bash
cat wget-log
```

---

# wget vs curl

| Feature | wget | curl |
|----------|----------|----------|
| Download Files | Yes | Yes |
| Resume Downloads | Yes | Limited |
| Recursive Download | Yes | No |
| API Requests | Limited | Excellent |
| Website Mirroring | Yes | No |
| Script Friendly | Yes | Yes |

---

# Useful wget Options

| Option | Description |
|----------|-------------|
| -O | Save file with different name |
| -c | Resume download |
| -b | Download in background |
| -i | Read URLs from file |
| --mirror | Download website |
| --limit-rate | Limit speed |
| --user | Username |
| --password | Password |

---

# RHCSA Notes

wget is commonly used to:

- Download RPM packages
- Download ISO images
- Download scripts
- Download configuration files
- Retrieve updates from repositories

Example:

```bash
wget https://example.com/package.rpm
```

---

# Summary

| Command | Purpose |
|----------|----------|
| wget URL | Download file |
| wget -O file URL | Save with custom name |
| wget -c URL | Resume download |
| wget -b URL | Download in background |
| wget -i file | Download multiple files |
| wget --mirror URL | Mirror website |

---

# Conclusion

`wget` is one of the most useful Linux utilities for downloading files and applications from the internet. It supports HTTP, HTTPS, and FTP protocols, allows resuming interrupted downloads, and is widely used by Linux administrators for software installation, updates, and automation tasks.
