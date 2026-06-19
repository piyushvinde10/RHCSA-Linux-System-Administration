# Installing, Configuring and Managing Docker

## Overview

Docker is an open-source containerization platform used to build, ship, and run applications inside containers.

Containers package:

- Application Code
- Libraries
- Dependencies
- Runtime Environment

Docker allows applications to run consistently across different environments.

---

# What is Docker?

Docker is a container engine that enables lightweight virtualization.

Architecture:

```text
Application
      |
Docker Container
      |
Docker Engine
      |
Linux Kernel
```

---

# Benefits of Docker

- Lightweight
- Fast Deployment
- Portable
- Scalable
- Resource Efficient
- Easy Application Management

---

# Docker Components

| Component | Description |
|------------|------------|
| Docker Engine | Container Runtime |
| Docker Image | Template for Container |
| Docker Container | Running Instance of Image |
| Docker Hub | Public Image Repository |
| Dockerfile | Instructions to Build Image |

---

# Install Docker

Update packages:

```bash
dnf update -y
```

Install Docker:

```bash
dnf install docker -y
```

Verify installation:

```bash
docker --version
```

Example Output:

```text
Docker version 27.x.x
```

---

# Start Docker Service

Start service:

```bash
systemctl start docker
```

Enable at boot:

```bash
systemctl enable docker
```

Check status:

```bash
systemctl status docker
```

---

# Verify Docker Information

```bash
docker info
```

---

# Verify Docker Version

```bash
docker version
```

---

# Search Docker Images

Search Nginx image:

```bash
docker search nginx
```

---

# Download Docker Image

Pull Nginx image:

```bash
docker pull nginx
```

Pull Ubuntu image:

```bash
docker pull ubuntu
```

---

# List Downloaded Images

```bash
docker images
```

Example:

```text
REPOSITORY   TAG      IMAGE ID
nginx        latest   xxxxxxxx
ubuntu       latest   xxxxxxxx
```

---

# Run a Container

Run Nginx:

```bash
docker run nginx
```

---

# Run Interactive Container

```bash
docker run -it ubuntu bash
```

---

# Run Container in Background

```bash
docker run -d nginx
```

---

# Assign Container Name

```bash
docker run -d --name webserver nginx
```

---

# Port Mapping

Expose Nginx service:

```bash
docker run -d \
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
docker ps
```

---

# List All Containers

```bash
docker ps -a
```

---

# Stop Container

```bash
docker stop nginx-web
```

---

# Start Container

```bash
docker start nginx-web
```

---

# Restart Container

```bash
docker restart nginx-web
```

---

# Remove Container

```bash
docker rm nginx-web
```

Force remove:

```bash
docker rm -f nginx-web
```

---

# Remove Image

```bash
docker rmi nginx
```

---

# Access Running Container

```bash
docker exec -it nginx-web bash
```

For Alpine containers:

```bash
docker exec -it container_name sh
```

---

# Display Container Logs

```bash
docker logs nginx-web
```

Follow logs:

```bash
docker logs -f nginx-web
```

---

# Inspect Container

```bash
docker inspect nginx-web
```

---

# Inspect Image

```bash
docker inspect nginx
```

---

# Copy Files to Container

```bash
docker cp index.html nginx-web:/usr/share/nginx/html/
```

---

# Copy Files from Container

```bash
docker cp nginx-web:/etc/nginx/nginx.conf .
```

---

# Create Docker Volume

```bash
docker volume create myvolume
```

List volumes:

```bash
docker volume ls
```

---

# Mount Volume

```bash
docker run -d \
-v myvolume:/data \
nginx
```

---

# Create Docker Network

```bash
docker network create mynetwork
```

List networks:

```bash
docker network ls
```

---

# Run Container on Custom Network

```bash
docker run -d \
--network mynetwork \
nginx
```

---

# Dockerfile Example

Create file:

```bash
vi Dockerfile
```

Example:

```dockerfile
FROM nginx

COPY index.html /usr/share/nginx/html/

EXPOSE 80
```

---

# Build Docker Image

```bash
docker build -t my-nginx .
```

Verify:

```bash
docker images
```

---

# Run Custom Image

```bash
docker run -d -p 8080:80 my-nginx
```

---

# Docker Service Management

Start:

```bash
systemctl start docker
```

Stop:

```bash
systemctl stop docker
```

Restart:

```bash
systemctl restart docker
```

Enable:

```bash
systemctl enable docker
```

Status:

```bash
systemctl status docker
```

---

# Useful Commands

## Version

```bash
docker --version
```

---

## Information

```bash
docker info
```

---

## Images

```bash
docker images
```

---

## Running Containers

```bash
docker ps
```

---

## All Containers

```bash
docker ps -a
```

---

## Pull Image

```bash
docker pull nginx
```

---

## Logs

```bash
docker logs container_name
```

---

# Troubleshooting

## Verify Service

```bash
systemctl status docker
```

---

## Verify Running Containers

```bash
docker ps
```

---

## Verify Images

```bash
docker images
```

---

## Check Logs

```bash
journalctl -u docker
```

---

## Verify Port Mapping

```bash
ss -tulnp
```

---

# Docker vs Podman

| Feature | Docker | Podman |
|----------|---------|---------|
| Daemon Required | Yes | No |
| Rootless Support | Limited | Yes |
| OCI Compatible | Yes | Yes |
| Container Management | Excellent | Excellent |
| Security | Good | Better |

---

# RHCSA Notes

Important commands:

```bash
docker --version
```

```bash
docker images
```

```bash
docker ps
```

```bash
docker pull nginx
```

```bash
docker run -d nginx
```

```bash
docker logs container_name
```

```bash
docker exec -it container_name bash
```

Docker is widely used for containerized application deployment and management.

---

# Summary

| Command | Purpose |
|----------|----------|
| docker pull nginx | Download image |
| docker images | List images |
| docker run -d nginx | Run container |
| docker ps | List running containers |
| docker logs | View logs |
| docker exec | Access container |
| docker rm | Remove container |

---

# Conclusion

Docker is a powerful containerization platform that enables applications to run consistently across different environments. Understanding Docker installation, image management, container operations, networking, storage, and troubleshooting is valuable for Linux administration, DevOps, and RHCSA-related container concepts.