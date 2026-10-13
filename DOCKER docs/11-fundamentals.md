# Docker — Learning Notes

A practical, step-by-step Docker learning guide. Use this file as a quick reference while studying; topic-specific notes will live in separate files linked from [README.md](README.md).

## 1. What is Docker?

Docker packages an application and its required dependencies into a container so it can run consistently across environments.

- **Image:** A read-only template used to create containers.
- **Container:** An isolated process created from an image.
- **Dockerfile:** Instructions used to build an image.
- **Registry:** A service for storing and downloading images (for example, Docker Hub).
- **Volume:** Persistent storage managed by Docker.
- **Port mapping:** Forwards a host port to a port inside a container.
- **Docker Compose:** A tool for defining and running multi-container applications.

## 2. Check installation

Run in PowerShell or a terminal:

```bash
docker --version
docker compose version
docker info
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker --version` | Prints the installed Docker CLI version. | A version line; it does not confirm that Engine is running. |
| `docker compose version` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |
| `docker info` | Queries Engine configuration and resource information. | A long report with server, storage, container and image details. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


If `docker info` fails, make sure Docker Desktop is installed and running. On Windows, Docker Desktop may require WSL 2 setup. Resolve setup problems before moving on.

## 3. Run your first container

```bash
docker run hello-world
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker run hello-world` | Pulls the image if needed, runs a short test container, then exits. | A success message beginning Hello from Docker!; pull progress may appear. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Docker downloads the image if necessary, creates a container, runs it, and prints a success message.

Useful inspection commands:

```bash
docker images
docker ps
docker ps -a
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker images` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker ps` | Lists only running containers. | A table; no rows is normal if nothing is running. |
| `docker ps -a` | Lists running and stopped containers. | A container table with status values. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


- `docker images`: locally stored images.
- `docker ps`: currently running containers.
- `docker ps -a`: running and stopped containers.

## 4. Container lifecycle

```bash
docker run -d --name web nginx
docker ps
docker logs web
docker stop web
docker start web
docker rm -f web
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker run -d --name web nginx` | Creates and starts a container. | Usually a container ID or application output. |
| `docker ps` | Lists only running containers. | A table; no rows is normal if nothing is running. |
| `docker logs web` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker stop web` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker start web` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker rm -f web` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Here `-d` runs in the background and `--name` gives the container a readable name. `docker rm -f` forcibly removes the container; use it only when you intend to stop and delete it.

Remove an image only when it is no longer needed:

```bash
docker rmi nginx
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker rmi nginx` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Docker may refuse to remove an image that is still referenced by a container.

## 5. Images versus containers

Think of an image as a class/template and a container as an instance created from it. One image can be used to create multiple containers. A container's writable layer is not a substitute for persistent storage.

## 6. Build a simple Python image

Create a folder containing these two files.

**app.py**

```python
print("Hello from inside Docker!")
```

**Dockerfile** (no extension)

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

Build and run:

```bash
docker build -t hello-python .
docker run --rm hello-python
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker build -t hello-python .` | Builds an image from Dockerfile and current context. | Build progress and a tagged image if successful. |
| `docker run --rm hello-python` | Creates and starts a container. | Usually a container ID or application output. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


- `FROM` chooses a base image.
- `WORKDIR` sets the working directory inside the image.
- `COPY` copies a file into the image.
- `CMD` specifies the default command.
- `-t` assigns an image name/tag; the final `.` is the build context.
- `--rm` automatically removes the stopped container.

## 7. Port mapping

For a web application listening on port 8000 inside the container:

```bash
docker run --rm -p 8000:8000 my-web-app
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker run --rm -p 8000:8000 my-web-app` | Creates and starts a container. | Usually a container ID or application output. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


The syntax is `HOST_PORT:CONTAINER_PORT`. The application must listen on `0.0.0.0` inside the container; binding only to `127.0.0.1` can prevent access through the mapped port.

## 8. Volumes and persistence

A container's writable layer can disappear when the container is removed. A volume stores data outside that layer.

```bash
docker volume create app-data
docker volume ls
docker volume inspect app-data
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker volume create app-data` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker volume ls` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker volume inspect app-data` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Volumes are useful for state that must survive container replacement, such as database files. Learn the exact mount syntax and permissions when practising a real service.

## 9. Docker Compose

Compose defines services in a YAML file, commonly named `compose.yaml`, and manages them together.

Common commands:

```bash
docker compose up --build
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker compose up --build` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |
| `docker compose up -d` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |
| `docker compose ps` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |
| `docker compose logs` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |
| `docker compose down` | Operates on the Compose project in this folder. | Service status/progress, logs or removal messages. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Use `docker compose down` to stop and remove the resources created for the Compose project. Named volumes are normally retained unless you explicitly request volume removal.

## 10. Debugging checklist

```bash
docker ps -a
docker logs <container_name>
docker inspect <container_name>
docker image ls
docker volume ls
```

**What each command does and expected output**

| Command | What it does | Expected result |
|---|---|---|
| `docker ps -a` | Lists running and stopped containers. | A container table with status values. |
| `docker logs <container_name>` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker inspect <container_name>` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker image ls` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |
| `docker volume ls` | Runs the named command; exact details depend on Docker state. | Expect a status message, table, logs or prompt return, depending on the command. |

Output details vary by version and machine. If it fails, copy the exact error and inspect Docker Desktop/Engine status.


Common causes:
- Docker daemon/Desktop is not running.
- The image build failed.
- The container exited because its main command finished or crashed.
- The host port is already in use.
- The application is listening on the wrong interface or port.
- Required files are missing from the build context.

## 11. Two-hour sprint checklist

- [ ] Verify Docker installation.
- [ ] Run `hello-world`.
- [ ] Explain image vs container.
- [ ] Inspect images and containers.
- [ ] Start, stop, view logs and remove a container.
- [ ] Build and run `hello-python`.
- [ ] Explain host-to-container port mapping.
- [ ] Understand when to use volumes.
- [ ] Run the basic Compose commands.
- [ ] Record any errors and fixes in [troubleshooting.md](troubleshooting.md).

## Key distinction

Containers isolate processes while sharing the host operating system's kernel. A virtual machine normally runs its own guest operating system.

## Learning log

After each study session, add the date, commands actually tested, outcomes, errors, fixes, and topics to revisit. Do not mark a task complete until you have tried it yourself.

## Reference

- [Docker Get Started](https://docs.docker.com/get-started/)
- [Docker CLI reference](https://docs.docker.com/reference/cli/docker/)
