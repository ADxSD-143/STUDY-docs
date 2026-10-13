# Docker — Complete Learning Path (Beginner → Intermediate → Advanced)

This is a guided, practical Docker course for a beginner. Each lesson explains the idea in plain language, shows commands and realistic examples, includes common mistakes, and ends with a checkpoint. Follow the parts in order; do not skip checkpoints just to finish quickly.

## How to study

1. Read one part only.
2. Run commands in Docker Desktop Terminal or PowerShell when the part says to practise.
3. Read the expected output and understand what changed on disk or in Docker.
4. Answer the checkpoint in your own words.
5. Record errors and fixes in [Troubleshooting & Lab Log](troubleshooting.md).
6. Move forward after the checkpoint is understood.

**Environment:** Windows + Docker Desktop + WSL 2; your configured Docker disk image location is `D:\DockerData\DockerDesktopWSL`. Keep destructive cleanup commands out of beginner practice unless their effects are understood.

## Stage 0 — Beginner foundations

1. [Part 1 — What Is Docker and Why Do We Need It?](part-01-what-is-docker.md)
2. [Part 2 — Image, Container, Dockerfile and Registry](part-02-image-container-dockerfile-registry.md)
3. [Part 3 — Docker Engine, CLI and Daemon](part-03-engine-cli-daemon.md)
4. [Part 4 — First Commands and Container Lifecycle](part-04-first-commands.md)
5. [Part 5 — Write Your First Dockerfile](part-05-first-dockerfile.md)

## Stage 1 — Practical application basics

6. [Part 6 — Ports, Networking, Environment and Storage](part-06-ports-network-storage.md)
7. [Part 7 — Docker Compose and Multi-container Apps](part-07-compose.md)
8. [Part 8 — Debugging and Common Failures](part-08-debugging.md)

## Stage 2 — Intermediate / production habits

9. [Part 9 — Production-quality Images and Build Optimization](part-09-image-optimization.md)
10. [Part 10 — Security, Secrets and Supply-chain Basics](part-10-security.md)
11. [Part 11 — Health Checks, Reliability and Resource Limits](part-11-reliability.md)
12. [Part 12 — CI/CD and Image Registries](part-12-cicd.md)

## Stage 3 — Advanced concepts and real-world use

13. [Part 13 — Advanced Docker Internals and Operations](part-13-advanced.md)
14. [Part 14 — Containerizing an ML App: CampusX Laptop Price Predictor](part-14-ml-capstone.md)
15. [Part 15 — Industry Scenarios, Future Skills and Final Project](part-15-industry-capstone.md)

## Reference pages

- [Fundamentals cheat sheet](fundamentals.md)
- [Installation and Setup](installation.md)
- [Images and Containers reference](images-and-containers.md)
- [Dockerfile reference lab](dockerfile.md)
- [Ports, Networks and Volumes reference](ports-networks-volumes.md)
- [Docker Compose reference](compose.md)
- [Learning roadmap and resources](learning-roadmap.md)
- [Troubleshooting and learning log](troubleshooting.md)

## Industry learning outcomes

By completing and practising the path, you should be able to:

- Explain images, containers, registries, the Docker Engine and the container lifecycle.
- Build, tag, run, inspect, log, stop and remove containers deliberately.
- Write a Dockerfile with dependency-aware caching and a `.dockerignore`.
- Publish application ports and persist data using volumes or bind mounts.
- Define multi-service development environments with Compose.
- Diagnose startup, networking, dependency and storage problems.
- Apply non-root execution, secret hygiene, image scanning and pinned versions appropriately.
- Understand CI builds, registry publishing, health checks and deployment trade-offs.
- Package and test a small ML application without confusing packaging with model evaluation.

## Safety rules for practice

- Never put passwords, API keys, tokens or private certificates in a Dockerfile, image, Git commit or public log.
- Treat downloaded images and serialized model files as software from an external source; verify trust and provenance.
- Avoid `docker system prune --all --volumes`, volume deletion, or WSL disk manipulation until you know exactly what data they can remove.
- Containers are not a complete security boundary by themselves. Production environments need least privilege, patching, monitoring, network controls and platform-specific hardening.
- Examples are educational; production requirements vary by application and organization.

## Official references

- [Docker Get Started](https://docs.docker.com/get-started/)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Docker security](https://docs.docker.com/engine/security/)
- [Docker Desktop WSL 2 backend](https://docs.docker.com/desktop/features/wsl/)
