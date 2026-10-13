# Docker Compose

## What is Compose?

Docker Compose describes a multi-container application in a YAML file, commonly `compose.yaml`, and lets you manage the services as a group.

## Minimal example

Create `compose.yaml`:

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
```

**Line-by-line meaning:**
- `services:` starts the list of application services.
- `web:` names a service.
- `image: nginx:alpine` selects the container image.
- `ports:` names a service.
- `- "8080:80"` is a list item, here a host-to-container port mapping.

**Expected result:** Saving the YAML file alone prints nothing and starts no containers. After `docker compose up -d`, check the service table with `docker compose ps`, view logs with `docker compose logs`, and open `http://localhost:8080`.


Run these commands from the directory containing the file:

```bash
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

**Command-by-command: purpose and expected output**

| Command | What it does | What you should see |
|---|---|---|
| `docker compose up -d` | Runs the Compose operation for the project in the current directory. | Compose creates/starts the service; first run may pull the image. Then verify the site in your browser. |
| `docker compose ps` | Runs the Compose operation for the project in the current directory. | A table showing service/container state and published ports. |
| `docker compose logs` | Runs the Compose operation for the project in the current directory. | Service logs, if the process has emitted any. |
| `docker compose down` | Runs the Compose operation for the project in the current directory. | Stops and removes project containers/network; named volumes are normally retained unless explicitly removed. |

Output wording varies. Ctrl+C during `logs -f` stops log-following, not necessarily the containers.


Visit `http://localhost:8080` while the service is running.

## Commands

- `docker compose up`: create/start services.
- `docker compose up --build`: build images before starting services when applicable.
- `docker compose ps`: show project containers.
- `docker compose logs`: show service logs.
- `docker compose down`: stop and remove project containers and networks.

Named volumes are normally retained by `down`; explicitly removing volumes is destructive, so inspect the command and data first.

## Checkpoint

- [ ] Explain why Compose is useful.
- [ ] Run the example and open the site.
- [ ] View logs and shut the stack down.
