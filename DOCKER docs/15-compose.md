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

Run these commands from the directory containing the file:

```bash
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

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
