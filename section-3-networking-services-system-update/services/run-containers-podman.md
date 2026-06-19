# Run Containers - Podman

## Overview

Podman is a container management tool used to develop, manage, and run OCI containers on Linux systems.

Podman is a daemonless container engine and is considered a secure alternative to Docker.

Features:

- Daemonless Architecture
- Rootless Containers
- OCI Compatible
- Docker Command Compatibility
- Secure Container Management
- Pod Support

---

# What is Podman?

Podman stands for:

```text
Pod Manager
```

Podman allows users to:

- Pull container images
- Run containers
- Stop containers
- Remove containers
- Manage container images
- Create pods

---

# Podman Architecture

```text
User
  |
  |
Podman
  |
  |
Container Runtime
  |
  |
Linux Kernel
```

Unlike Docker:

```text
No Background Daemon Required
```

---

# Install Podman

Install package:

```bash
dnf install podman -y
```

Verify installation:

```bash
podman --version
```

Example:

```text
podman version 5.x.x
```

---

# Podman Information

Display system information:

```bash
podman info
```

---

# Search Container Images

Search image:

```bash
podman search nginx
```

Example Output:

```text
docker.io/library/nginx
```

---

# Pull Container Image

Download image:

```bash
podman pull nginx
```

Pull Ubuntu image:

```bash
podman pull ubuntu
```

---

# List Downloaded Images

```bash
podman images
```

Example Output:

```text
REPOSITORY          TAG
docker.io/nginx     latest
docker.io/ubuntu    latest
```

---

# Run a Container

Start Nginx container:

```bash
podman run nginx
```

Run in interactive mode:

```bash
podman run -it ubuntu bash
```

---

# Run Container in Background

```bash
podman run -d nginx
```

Example Output:

```text
Container ID
```

---

# Name a Container

```bash
podman run -d --name webserver nginx
```

---

# Map Ports

Expose Nginx web server:

```bash
podman run -d \
--name nginx-web \
-p 8080:80 nginx
```

Verify:

```bash
curl http://localhost:8080
```

---

# List Running Containers

```bash
podman ps
```

Example:

```text
CONTAINER ID
IMAGE
STATUS
PORTS
```

---

# List All Containers

```bash
podman ps -a
```

---

# Stop Container

Using Container ID:

```bash
podman stop CONTAINER_ID
```

Using Name:

```bash
podman stop nginx-web
```

---

# Start Container

```bash
podman start nginx-web
```

---

# Restart Container

```bash
podman restart nginx-web
```

---

# Remove Container

```bash
podman rm nginx-web
```

Remove forcefully:

```bash
podman rm -f nginx-web
```

---

# Remove Image

```bash
podman rmi nginx
```

---

# Execute Command Inside Container

```bash
podman exec -it nginx-web bash
```

Example:

```bash
podman exec -it nginx-web sh
```

---

# Display Container Logs

```bash
podman logs nginx-web
```

Follow logs:

```bash
podman logs -f nginx-web
```

---

# Inspect Container

```bash
podman inspect nginx-web
```

---

# Inspect Image

```bash
podman inspect nginx
```

---

# Copy Files to Container

```bash
podman cp index.html nginx-web:/usr/share/nginx/html/
```

---

# Copy Files from Container

```bash
podman cp nginx-web:/etc/nginx/nginx.conf .
```

---

# Create Pod

```bash
podman pod create --name webpod
```

List pods:

```bash
podman pod ps
```

---

# Run Container in Pod

```bash
podman run -dt \
--pod webpod nginx
```

---

# Generate Systemd Service

```bash
podman generate systemd nginx-web
```

---

# Save Image

```bash
podman save nginx -o nginx.tar
```

---

# Load Image

```bash
podman load -i nginx.tar
```

---

# Verify Open Ports

```bash
ss -tulnp
```

Example:

```bash
ss -tulnp | grep 8080
```

---

# Useful Commands

## Version

```bash
podman --version
```

---

## System Information

```bash
podman info
```

---

## Pull Image

```bash
podman pull nginx
```

---

## List Images

```bash
podman images
```

---

## Run Container

```bash
podman run -d nginx
```

---

## Running Containers

```bash
podman ps
```

---

## All Containers

```bash
podman ps -a
```

---

## Logs

```bash
podman logs container_name
```

---

## Remove Container

```bash
podman rm container_name
```

---

# Troubleshooting

## Verify Installation

```bash
podman --version
```

---

## Verify Container Status

```bash
podman ps -a
```

---

## Check Logs

```bash
podman logs container_name
```

---

## Check Port Mapping

```bash
ss -tulnp
```

---

## Verify Images

```bash
podman images
```

---

# Podman vs Docker

| Feature | Podman | Docker |
|----------|----------|----------|
| Daemon Required | No | Yes |
| Rootless Containers | Yes | Limited |
| OCI Compatible | Yes | Yes |
| Pods Support | Yes | No |
| Security | Higher | Standard |

---

# RHCSA Notes

Important commands:

```bash
dnf install podman
```

```bash
podman pull nginx
```

```bash
podman images
```

```bash
podman run -d nginx
```

```bash
podman ps
```

```bash
podman logs container_name
```

```bash
podman exec -it container_name bash
```

Container management with Podman is an important skill for modern Linux administration and Red Hat environments.

---

# Summary

| Command | Purpose |
|----------|----------|
| podman pull nginx | Download image |
| podman images | List images |
| podman run -d nginx | Run container |
| podman ps | List running containers |
| podman logs | View logs |
| podman exec | Access container |
| podman rm | Remove container |

---

# Conclusion

Podman is a powerful and secure container engine used to run and manage containers on Linux systems. It provides rootless operation, daemonless architecture, and full OCI compatibility. Understanding Podman installation, image management, container operations, and troubleshooting is valuable for RHCSA preparation and enterprise Linux administration.