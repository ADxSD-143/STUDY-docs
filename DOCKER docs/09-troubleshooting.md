# Docker Troubleshooting and Learning Log

## Useful diagnostic commands

```bash
docker ps -a
docker logs <container_name>
docker inspect <container_name>
docker image ls
docker volume ls
docker network ls
docker compose ps
docker compose logs
```

**Command-by-command: purpose and expected result**

| Command | What it does | What you should see |
|---|---|---|
| `docker ps -a` | Lists containers; -a includes stopped containers. | Container table with status, names and ports. |
| `docker logs <container_name>` | Prints captured stdout/stderr from the named container. | Application log lines, or empty output if none were emitted. |
| `docker inspect <container_name>` | Shows detailed configuration and state for a container. | JSON-like metadata including state, mounts and networking. |
| `docker image ls` | Lists local images. | Image table with repository, tag, ID and size. |
| `docker volume ls` | Lists named Docker volumes. | Volume table; may be empty if none exist. |
| `docker network ls` | Lists Docker networks. | Network table with names and drivers. |
| `docker compose ps` | Shows the current Compose project's container states. | Service/container table with status and published ports. |
| `docker compose logs` | Prints logs from Compose services. | Service-labelled log output where available. |

If output differs, save the exact command and error. Check Engine status first, then container status and logs before changing configuration.


## Common issues

| Symptom | What to check |
|---|---|
| Docker CLI not found | Installation and terminal PATH |
| Cannot connect to daemon | Docker Desktop/Engine is running |
| Container exits immediately | Main process, exit code and `docker logs` |
| Port cannot be bound | Whether another process already uses the host port |
| App is not reachable | Published port, app port, and binding to `0.0.0.0` |
| Dockerfile build fails | Current directory, file names, build context and exact error |
| Data disappears after removal | Whether persistent data should be stored in a volume |

## Session log template

Copy this section at the end of each study session:

### Session — YYYY-MM-DD

- **Topics studied:**
- **Commands actually run:**
- **Expected result:**
- **Actual result:**
- **Errors and fixes:**
- **What I understand now:**
- **What needs revision:**
- **Next step:**

Do not record a command as tested if you only read it.

## Two-hour checkpoint

- [ ] Installation verified
- [ ] `hello-world` completed
- [ ] Images and containers distinguished
- [ ] Basic lifecycle commands tried
- [ ] Python Docker image built and run
- [ ] Port mapping understood
- [ ] Volumes introduced
- [ ] Compose example tried
