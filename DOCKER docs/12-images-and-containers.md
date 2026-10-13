# Docker Images and Containers

## Mental model

- An **image** is the template used to start containers.
- A **container** is an instance created from an image; it can be running or stopped.
- One image can create many containers.
- Image layers are reused where possible to reduce repeated downloads and builds.

## Inspect images

```bash
docker pull nginx
docker image ls
docker image inspect nginx
```

**Command-by-command: purpose and expected result**

| Command | What it does | What to expect |
|---|---|---|
| `docker pull nginx` | Downloads the image from its registry if it is not already local. | Layer download progress and a successful pull message. |
| `docker image ls` | Lists images stored locally. | Image table with repository, tag, ID and size. |
| `docker image inspect nginx` | Executes the Docker operation shown. | Expect a status line, table or resource name depending on the command. |

IDs, timestamps, image sizes and progress text vary by machine and Docker version.


## Create and inspect a container

```bash
docker run -d --name demo-nginx nginx
docker ps
docker ps -a
docker logs demo-nginx
docker inspect demo-nginx
```

**Command-by-command: purpose and expected result**

| Command | What it does | What to expect |
|---|---|---|
| `docker run -d --name demo-nginx nginx` | Creates and starts a container from the specified image. | Usually a container ID; a browser test may be needed for web services. |
| `docker ps` | Lists running containers only. | Container table; may be empty if nothing is running. |
| `docker ps -a` | Lists running and stopped containers. | Container table including exited containers. |
| `docker logs demo-nginx` | Prints captured container output. | Log lines, or no output if the process emitted none. |
| `docker inspect demo-nginx` | Shows detailed configuration/state metadata. | JSON-like output with state, mounts, networking or image details. |

IDs, timestamps, image sizes and progress text vary by machine and Docker version.


`-d` runs it in the background. `--name` assigns a stable name.

## Lifecycle

```bash
docker stop demo-nginx
docker start demo-nginx
docker restart demo-nginx
docker rm -f demo-nginx
```

**Command-by-command: purpose and expected result**

| Command | What it does | What to expect |
|---|---|---|
| `docker stop demo-nginx` | Stops the named container. | Usually the container name; status becomes exited. |
| `docker start demo-nginx` | Starts an existing stopped container. | Usually the container name; verify with docker ps. |
| `docker restart demo-nginx` | Restarts an existing container. | Usually the container name and a running state if startup succeeds. |
| `docker rm -f demo-nginx` | Removes a container; the -f variant also force-stops it. | Usually the name/ID; verify with docker ps -a. Use only when deletion is intended. |

IDs, timestamps, image sizes and progress text vary by machine and Docker version.


`docker rm -f` stops and removes the named container. Use it only when deletion is intended.

## Cleanup

```bash
docker image ls
docker rmi nginx
```

**Command-by-command: purpose and expected result**

| Command | What it does | What to expect |
|---|---|---|
| `docker image ls` | Lists images stored locally. | Image table with repository, tag, ID and size. |
| `docker rmi nginx` | Removes a container; the -f variant also force-stops it. | Usually the name/ID; verify with docker ps -a. Use only when deletion is intended. |

IDs, timestamps, image sizes and progress text vary by machine and Docker version.


An image may not be removable while a container references it. Inspect your containers before cleanup.

## Checkpoint

Explain, without looking:
1. Image vs container.
2. `docker ps` vs `docker ps -a`.
3. Why `docker logs` is useful.
4. The difference between stopping and removing a container.
