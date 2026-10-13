# Docker Installation and Setup

## Goal

Confirm that Docker is installed and that the Docker engine is reachable before learning other commands.

## Verify

Run these in PowerShell or your terminal:

```bash
docker --version
docker compose version
docker info
```

**Command-by-command: what happens and what you should see**

| Command | What it does | Expected output / verification |
|---|---|---|
| `docker --version` | Prints the installed CLI/plugin version; it does not start the Engine. | A version line, e.g. Docker version ... or Docker Compose version v2.... |
| `docker compose version` | Prints the installed CLI/plugin version; it does not start the Engine. | A version line, e.g. Docker version ... or Docker Compose version v2.... |
| `docker info` | Queries the Engine for configuration and resource information. | A long report with server, storage, container and image details; exact fields vary. |

Output note: these are expected behaviours, not fixed transcripts. IDs, image sizes, versions, download progress and timestamps vary by machine and cache state.


Version commands verify that the CLI exists. `docker info` also tries to contact the engine/daemon.

## Windows with Docker Desktop

1. Install Docker Desktop using the official instructions.
2. Complete any WSL 2 prerequisite shown by the installer.
3. Start Docker Desktop and wait until its engine is running.
4. Open a fresh PowerShell window and run the verification commands above.
5. Run a first test:

```bash
docker run hello-world
```

**Command-by-command: what happens and what you should see**

| Command | What it does | Expected output / verification |
|---|---|---|
| `docker run hello-world` | Pulls the image if needed, runs a short test container and exits. | A message beginning Hello from Docker!; pull progress may appear on first run. |

Output note: these are expected behaviours, not fixed transcripts. IDs, image sizes, versions, download progress and timestamps vary by machine and cache state.


Official guide: https://docs.docker.com/desktop/setup/install/windows-install/

## Troubleshooting

- **`docker` is not recognized:** Check installation and PATH; reopen the terminal after installation.
- **Cannot connect to the daemon:** Start Docker Desktop/Engine and wait for it to become ready.
- **WSL-related error:** Follow Docker's current WSL 2 setup guidance; do not randomly change system settings.
- **Permission error:** Follow the platform-specific Docker guidance rather than running every command with elevated privileges.

## Checkpoint

- [ ] `docker --version` works.
- [ ] `docker info` reaches the engine.
- [ ] `docker run hello-world` completes successfully.

Record the exact error and full command if something fails.
