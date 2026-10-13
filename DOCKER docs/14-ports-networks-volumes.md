# Ports, Networks and Volumes

## Port mapping

Port publishing lets traffic entering a host port reach a port in a container.

Example:

```bash
docker run --rm -d --name web -p 8080:80 nginx
```

**Command-by-command: what it does and expected output**

| Command | What it does | What you should see |
|---|---|---|
| `docker run --rm -d --name web -p 8080:80 nginx` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |


Open `http://localhost:8080` in a browser. Here host port 8080 maps to container port 80. Stop it when finished:

```bash
docker stop web
```

**Command-by-command: what it does and expected output**

| Command | What it does | What you should see |
|---|---|---|
| `docker stop web` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |


Format: `-p HOST_PORT:CONTAINER_PORT`.

For custom web apps, the process must listen on the correct container port and generally bind to `0.0.0.0`, not only `127.0.0.1`.

## Networks

Containers can communicate over Docker networks. User-defined bridge networks are a common option for services on one host.

```bash
docker network ls
docker network create app-network
docker network inspect app-network
docker network rm app-network
```

**Command-by-command: what it does and expected output**

| Command | What it does | What you should see |
|---|---|---|
| `docker network ls` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |
| `docker network create app-network` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |
| `docker network inspect app-network` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |
| `docker network rm app-network` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |


Do not remove a network while containers still depend on it.

## Volumes

Containers are replaceable. Store data that must outlive a container in a volume.

```bash
docker volume create app-data
docker volume ls
docker volume inspect app-data
```

**Command-by-command: what it does and expected output**

| Command | What it does | What you should see |
|---|---|---|
| `docker volume create app-data` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |
| `docker volume ls` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |
| `docker volume inspect app-data` | Runs the Docker network/volume operation named by the command. | Expect a table, ID, resource name or JSON-like metadata; exact values vary. Verify using the corresponding list/inspect command. |


A volume is not the same as the container's writable layer. Avoid deleting volumes during practice if they might contain needed data.

## Checkpoint

- [ ] Explain `8080:80`.
- [ ] Explain why a service may be unreachable even when the container is running.
- [ ] Explain why a database should use persistent storage.
