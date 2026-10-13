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
