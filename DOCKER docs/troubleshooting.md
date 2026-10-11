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
