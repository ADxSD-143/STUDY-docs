# Docker — Learning Roadmap and Resource Notes

This page connects the resources you are following to the complete guided Docker course. Study one lesson at a time and complete its checkpoint before moving forward.

## Main course

**[Open Docker — Complete Learning Path (Beginner → Intermediate → Advanced)](README.md)**

The course covers core concepts, first commands, Dockerfiles, networking, volumes, Compose, debugging, image optimization, security, reliability, CI/CD, advanced internals, industry scenarios, and a CampusX ML capstone.

## Resources you are following

- **Video lesson:** [YouTube — Docker tutorial](https://youtu.be/GToyQTGDOS4)
- **Uploaded PDF:** *Introduction to Docker* (6 pages; dated 7 August 2024).
- **Practice application:** [CampusX Laptop Price Predictor](https://github.com/campusx-official/laptop-price-predictor-regression-project)

The PDF introduces Docker's purpose and consistency/isolation/scalability, Engine components, images and Dockerfile instructions, containers, registries and application use cases. The course expands these fundamentals into hands-on practice and industry scenarios.

## Suggested learning sequence

1. Understand what Docker solves and learn image/container/Dockerfile/registry.
2. Learn Docker Engine, CLI and daemon.
3. Run hello-world and inspect image/container state.
4. Build a tiny Python image.
5. Practise port mapping, networking, environment variables and storage.
6. Run a multi-service Compose example.
7. Learn logs, inspect, common errors and safe cleanup.
8. Improve image size and cache behaviour; use .dockerignore and multi-stage builds.
9. Learn security basics, secrets, health checks, resource visibility and CI/CD.
10. Containerize the CampusX Streamlit app only after verifying it runs locally and its dependencies/model artifacts are compatible.

## Industry and future-relevant topics

The course includes reproducible builds, supply-chain provenance, dependency/image scanning, least privilege, secrets hygiene, multi-platform builds, observability and rollback. These are durable engineering concerns; exact tools and platform capabilities should be checked against current official documentation.

## Official documentation

- [Docker Get Started](https://docs.docker.com/get-started/)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Compose Quickstart](https://docs.docker.com/compose/gettingstarted/)
- [Multi-stage builds](https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/)
- [Build secrets](https://docs.docker.com/build/building/secrets/)
- [Docker Desktop WSL 2 backend](https://docs.docker.com/desktop/features/wsl/)

## Important safety notes

- Never store secrets in Dockerfiles, image layers, Git commits or logs.
- Treat downloaded images and pickle model files as untrusted until their source is verified.
- Avoid destructive cleanup commands and manual WSL disk moves unless you understand the impact.
- A container build proves packaging, not model quality or production readiness.
