# Docker Course — Ports, Networks, Volumes and Compose

## 1. Port mapping
A container can listen on a port internally without automatically making it reachable from your host. Publish a port:

```text
docker run -d --name web-demo -p 8080:80 nginx
```

**Command-by-command: what it does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker run -d --name web-demo -p 8080:80 nginx` | Creates and starts a container; -d detaches, --name sets its name, -p publishes ports. | Usually a container ID; open the mapped localhost URL for web apps. |

Output details such as IDs, sizes, versions and progress vary by machine and cache state.


**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Open http://localhost:8080. The syntax is HOST_PORT:CONTAINER_PORT. If port 8080 is already occupied, map 8081:80 instead.

A web server inside a container generally needs to bind to 0.0.0.0, not only 127.0.0.1, to accept traffic through the published port.

## 2. Networking
Containers on a user-defined Docker network can discover each other by name. Avoid hardcoding container IP addresses because they can change.

```text
docker network create demo-net
docker network ls
docker network inspect demo-net
```

**Command-by-command: what it does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker network create demo-net` | Creates/lists/inspects a Docker network. | Network ID, table or JSON-like details. |
| `docker network ls` | Creates/lists/inspects a Docker network. | Network ID, table or JSON-like details. |
| `docker network inspect demo-net` | Creates/lists/inspects a Docker network. | Network ID, table or JSON-like details. |

Output details such as IDs, sizes, versions and progress vary by machine and cache state.


**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Compose normally creates a project network for its services.

## 3. Storage: writable layer, volume and bind mount
- Container writable layer: changes attached to that container; do not rely on it for durable business data.
- Named volume: Docker-managed storage, commonly used for databases and persistent state.
- Bind mount: maps a chosen host path into the container, useful for development code and explicit host files.

Create and inspect a volume:

```text
docker volume create demo-data
docker volume ls
docker volume inspect demo-data
```

**Command-by-command: what it does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker volume create demo-data` | Creates/lists/inspects Docker-managed storage. | Volume name, table or metadata details. |
| `docker volume ls` | Creates/lists/inspects Docker-managed storage. | Volume name, table or metadata details. |
| `docker volume inspect demo-data` | Creates/lists/inspects Docker-managed storage. | Volume name, table or metadata details. |

Output details such as IDs, sizes, versions and progress vary by machine and cache state.


**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Removing a container does not necessarily remove volumes. A volume is also not a backup; production data needs a backup and restore plan.

## 4. Your Windows setup
Your Docker Desktop screenshot showed the disk image location D:\DockerData\DockerDesktopWSL. Docker's Linux-container data is managed in that configured disk image. Project files remain in their own folders unless mounted. Do not manually move the WSL disk or run volume-pruning commands casually.

## 5. Environment variables and secrets
Use environment variables for non-secret configuration such as log level or a service URL. Do not put API keys or passwords in a Dockerfile, source control, image layers or logs. A local .env file is configuration convenience, not a secure vault. Use appropriate secret management for sensitive values.

## 6. Compose
Compose describes a set of services in a YAML file so a local stack can be started consistently. Create compose.yaml:

```text
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
  cache:
    image: redis:alpine
```

**Line-by-line meaning:**
- `services:` begins the list of services.
- `web:` names a service.
- `image: nginx:alpine` chooses the image for that service.
- `ports:` names a service.
- `- "8080:80"` is a port mapping list entry.
- `cache:` names a service.
- `image: redis:alpine` chooses the image for that service.

**Expected result:** Saving this file alone prints nothing and starts no containers. After `docker compose up -d`, check `docker compose ps`, `docker compose logs`, and open the mapped localhost URL.


**What this configuration does:** Defines services and their settings; saving YAML alone does not start containers. **Expected result:** no terminal output until you run the matching Compose command. Verify service state with `docker compose ps`, read logs with `docker compose logs`, and test the configured browser URL.


Run:

```text
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

**Command-by-command: what it does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker compose up -d` | Operates on the Compose project in the current folder. | Service progress/status, logs or removal messages. |
| `docker compose ps` | Operates on the Compose project in the current folder. | Service progress/status, logs or removal messages. |
| `docker compose logs` | Operates on the Compose project in the current folder. | Service progress/status, logs or removal messages. |
| `docker compose down` | Operates on the Compose project in the current folder. | Service progress/status, logs or removal messages. |

Output details such as IDs, sizes, versions and progress vary by machine and cache state.


**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


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
