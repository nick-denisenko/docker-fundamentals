# Docker Essential Commands

## 1. docker pull
Downloads images from Docker Hub or other registries.

```bash
# Pull latest version of an image
docker pull nginx
docker pull ubuntu
docker pull python

# Pull specific version/tag
docker pull nginx:1.29
docker pull python:3.13-alpine
docker pull postgres:17

# Pull from specific registry
docker pull gcr.io/google-containers/busybox
```

## 2. docker run
Creates and starts a new container from an image.

```bash
# Basic run command
docker run hello-world
docker run ubuntu echo "Hello Docker"

# Run with interactive terminal
docker run -it ubuntu bash

# Run with port mapping
docker run -p 8080:80 nginx

# Run with environment variables
docker run -e POSTGRES_PASSWORD=mypassword postgres

# Run with volume mounting
docker run -v /host/path:/container/path nginx
docker run -v $(pwd):/app python:3.13-alpine

# Run with name
docker run --name my-nginx nginx
docker run --name my-db postgres
```

## 3. docker run -d
Runs containers in detached mode (in the background).

```bash
# Run web server in background
docker run -d -p 8080:80 nginx
docker run -d -p 3000:3000 --name my-app python:3.13-alpine

# Run database in background
docker run -d --name my-postgres -e POSTGRES_PASSWORD=secret postgres
docker run -d --name my-redis redis

# Run with restart policy
docker run -d --restart=always nginx
docker run -d --restart=unless-stopped --name web-server nginx

# Run with resource limits
docker run -d --memory=512m --cpus=0.5 nginx
```

## 4. docker ps
Shows running containers.

```bash
# Show all running containers
docker ps

# Show with specific format
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"

# Show only container IDs
docker ps -q

# Show last created container
docker ps -l

# Show containers with specific filters
docker ps --filter "status=running"
docker ps --filter "name=nginx"
```

## 5. docker ps -a
Shows all containers (running and stopped).

```bash
# Show all containers
docker ps -a

# Show with size information
docker ps -a -s

# Show only stopped containers
docker ps -a --filter "status=exited"

# Show containers created in last hour
docker ps -a --filter "since=1h"

# Show with custom format
docker ps -a --format "table {{.Names}}\t{{.Image}}\t{{.Status}}\t{{.CreatedAt}}"
```

## 6. docker logs
Views logs from containers.

```bash
# Show logs from a container
docker logs my-container
docker logs nginx-server

# Follow logs in real-time
docker logs -f my-app
docker logs --follow web-server

# Show last N lines
docker logs --tail 50 my-container
docker logs -n 100 my-app

# Show logs with timestamps
docker logs -t my-container
docker logs --timestamps my-app

# Show logs since specific time
docker logs --since 2023-01-01 my-container
docker logs --since 1h my-app

# Combine options
docker logs -f --tail 20 --since 30m my-app
```