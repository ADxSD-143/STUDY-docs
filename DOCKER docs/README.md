# Docker — Complete Learning Path (Beginner → Intermediate → Advanced)

This is a guided, practical Docker course for a beginner. Each lesson uses plain-language explanations, commands, real-world examples, common mistakes, checkpoints and hands-on tasks. Follow the learning order and move forward after you understand each checkpoint.

## How we will study

1. Learn one concept at a time.
2. Run commands in Docker Desktop Terminal or PowerShell when asked.
3. Understand what each command changes and where data is stored.
4. Answer the checkpoint in your own words.
5. Record actual outcomes and errors in [Troubleshooting & Lab Log](troubleshooting.md).
6. Do not mark a topic complete just because you read it.

**Your environment:** Windows + Docker Desktop + WSL 2. Your screenshot showed the Docker disk image location as `D:\DockerData\DockerDesktopWSL`. Avoid destructive cleanup and manual WSL disk moves.

## Stage 0 — Beginner foundations

1. [Part 1 — What Is Docker and Why Do We Need It?](part-01-what-is-docker.md)
2. [Part 2 — Image, Container, Dockerfile and Registry](part-02-image-container-dockerfile-registry.md)
3. [Part 3–5 — Docker Engine concepts, First Commands and Your First Dockerfile](03-core-commands-and-dockerfile.md)

## Stage 1 — Practical application basics

5. [Ports, Networking, Environment, Storage and Compose](04-network-storage-compose.md)
6. [Debugging and Common Failures](troubleshooting.md)

## Stage 2 — Intermediate / production habits

7. [Production Images, Build Optimization, Security and Reliability](05-production-images-security.md)
8. [CI/CD, Registries, Advanced Concepts and Operations](06-cicd-advanced.md)

## Stage 3 — Advanced concepts and real-world use

9. [Capstone — Containerize the CampusX Laptop Price Predictor](07-ml-capstone-campusx.md)
10. [Industry Scenarios and Future-relevant Skills](06-cicd-advanced.md#future-relevant-skills)

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

After completing and practising the course, you should be able to build and run images, diagnose containers, publish ports, manage persistent data, run a local multi-service stack, optimize builds, apply security basics, explain CI/CD and image promotion, and package an ML app without confusing deployment with model quality.

## Safety rules

- Never put API keys, passwords or certificates in Dockerfiles, image layers, Git commits or logs.
- Verify the source of downloaded images and serialized model files.
- Avoid `docker system prune --all --volumes` and volume deletion until you know what data will be removed.
- Containers are not a complete security boundary by themselves; production needs patching, least privilege, monitoring and platform-specific controls.
- Examples are educational. Test and adapt them before production use.

## Official, maintained references

- [Docker Get Started](https://docs.docker.com/get-started/)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Compose Quickstart](https://docs.docker.com/compose/gettingstarted/)
- [Multi-stage builds](https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/)
- [Build secrets](https://docs.docker.com/build/building/secrets/)
- [Docker Desktop WSL 2 backend](https://docs.docker.com/desktop/features/wsl/)
- [Docker Desktop WSL 2 best practices](https://docs.docker.com/desktop/features/wsl/best-practices/)

Tools and best practices evolve. Learn durable concepts and verify current platform-specific details in official documentation before applying them to production.
