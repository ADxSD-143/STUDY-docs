# Docker Course — Ports, Networks, Volumes and Compose

## 1. Port mapping
A container can listen on a port internally without automatically making it reachable from your host. Publish a port:

    docker run -d --name web-demo -p 8080:80 nginx

Open http://localhost:8080. The syntax is HOST_PORT:CONTAINER_PORT. If port 8080 is already occupied, map 8081:80 instead.

A web server inside a container generally needs to bind to 0.0.0.0, not only 127.0.0.1, to accept traffic through the published port.

## 2. Networking
Containers on a user-defined Docker network can discover each other by name. Avoid hardcoding container IP addresses because they can change.

    docker network create demo-net
    docker network ls
    docker network inspect demo-net

Compose normally creates a project network for its services.

## 3. Storage: writable layer, volume and bind mount
- Container writable layer: changes attached to that container; do not rely on it for durable business data.
- Named volume: Docker-managed storage, commonly used for databases and persistent state.
- Bind mount: maps a chosen host path into the container, useful for development code and explicit host files.

Create and inspect a volume:

    docker volume create demo-data
    docker volume ls
    docker volume inspect demo-data

Removing a container does not necessarily remove volumes. A volume is also not a backup; production data needs a backup and restore plan.

## 4. Your Windows setup
Your Docker Desktop screenshot showed the disk image location D:\DockerData\DockerDesktopWSL. Docker's Linux-container data is managed in that configured disk image. Project files remain in their own folders unless mounted. Do not manually move the WSL disk or run volume-pruning commands casually.

## 5. Environment variables and secrets
Use environment variables for non-secret configuration such as log level or a service URL. Do not put API keys or passwords in a Dockerfile, source control, image layers or logs. A local .env file is configuration convenience, not a secure vault. Use appropriate secret management for sensitive values.

## 6. Compose
Compose describes a set of services in a YAML file so a local stack can be started consistently. Create compose.yaml:

    services:
      web:
        image: nginx:alpine
        ports:
          - "8080:80"
      cache:
        image: redis:alpine

Run:

    docker compose up -d
    docker compose ps
    docker compose logs
    docker compose down

Visit http://localhost:8080 while the stack is running. This example starts two services; Nginx does not automatically use Redis just because both exist.

For a real web app and database, the app should connect to the database by service name, for example db:5432, not by a hardcoded container IP. Process startup does not always mean a dependency is ready; use health checks and retry logic where appropriate.

Compose down removes project containers and networks. Named volumes are normally retained unless explicitly requested for removal. Read commands carefully before adding destructive volume flags.

## Industry example
A developer's app works locally but cannot connect to the database in a teammate's environment. Compose can define the database service, network, environment configuration and volume so the setup is reproducible. It does not eliminate the need to manage secrets, backups and migrations.

## Checkpoint
1. Explain 8080:80.
2. How is a volume different from a bind mount?
3. Why should services use a Compose service name instead of a container IP?
4. Why is a volume alone not a backup strategy?
