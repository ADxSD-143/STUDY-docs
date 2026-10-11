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

## Create and inspect a container

```bash
docker run -d --name demo-nginx nginx
docker ps
docker ps -a
docker logs demo-nginx
docker inspect demo-nginx
```

`-d` runs it in the background. `--name` assigns a stable name.

## Lifecycle

```bash
docker stop demo-nginx
docker start demo-nginx
docker restart demo-nginx
docker rm -f demo-nginx
```

`docker rm -f` stops and removes the named container. Use it only when deletion is intended.

## Cleanup

```bash
docker image ls
docker rmi nginx
```

An image may not be removable while a container references it. Inspect your containers before cleanup.

## Checkpoint

Explain, without looking:
1. Image vs container.
2. `docker ps` vs `docker ps -a`.
3. Why `docker logs` is useful.
4. The difference between stopping and removing a container.
