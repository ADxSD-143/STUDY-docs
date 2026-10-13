# Docker — Complete Learning Path (Beginner → Intermediate → Advanced)

This is a guided, practical Docker course for a beginner. Each lesson uses plain-language explanations, commands, real-world examples, common mistakes, checkpoints and hands-on tasks. Follow the learning order and move forward only after you understand each checkpoint.

## How we will study

1. Learn one concept at a time.
2. Run commands in Docker Desktop Terminal or PowerShell when asked.
3. Understand what each command changes and where data is stored.
4. Answer the checkpoint in your own words.
5. Record actual outcomes and errors in [Troubleshooting & Lab Log](09-troubleshooting.md).
6. Do not mark a topic complete just because you read it.

**Your environment:** Windows + Docker Desktop + WSL 2. Your configured Docker disk image location is on the D: drive. Avoid destructive cleanup and manual WSL disk moves.

## Course sequence

| Order | Topic | What you will learn |
|---|---|---|
| 00 | [Start here](00-START-HERE.md) | How to use this folder and follow the sequence |
| 01 | [Installation and setup](01-installation.md) | Docker Desktop, WSL 2, verification |
| 02 | [Part 1 — What is Docker?](02-part-01-what-is-docker.md) | The problem Docker solves; portability and isolation |
| 03 | [Part 2 — Image, container, Dockerfile and registry](03-part-02-image-container-dockerfile-registry.md) | The core mental model |
| 04 | [Core commands and first Dockerfile](04-core-commands-and-dockerfile.md) | Run, inspect, build and troubleshoot basic containers |
| 05 | [Networking, storage and Compose](05-network-storage-compose.md) | Ports, networks, environment, volumes and multi-service apps |
| 06 | [Production images and security](06-production-images-security.md) | Image optimization, non-root users, secrets and reliability |
| 07 | [CI/CD and advanced concepts](07-cicd-advanced.md) | Registries, image promotion, build systems and operations |
| 08 | [CampusX ML capstone](08-ml-capstone-campusx.md) | Containerize a Streamlit ML app |
| 09 | [Troubleshooting and lab log](09-troubleshooting.md) | Diagnose failures and record real results |
| 10 | [Learning roadmap and resources](10-learning-roadmap.md) | Course map and maintained references |

## Command explanations and expected output

- [Command-by-command guide: what commands/code do, expected output, and troubleshooting](16-command-by-command-output-guide.md)

## Reference sheets

- [Fundamentals cheat sheet](11-fundamentals.md)
- [Images and containers reference](12-images-and-containers.md)
- [Dockerfile reference lab](13-dockerfile.md)
- [Ports, networks and volumes reference](14-ports-networks-volumes.md)
- [Docker Compose reference](15-compose.md)

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
