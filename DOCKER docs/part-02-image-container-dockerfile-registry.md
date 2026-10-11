# Part 2 — Image, Container, Dockerfile, and Registry

## Goal

Understand four core Docker terms and how they connect. Do not memorize them as isolated definitions; follow the example flow.

## 1. Docker image

An **image** is a packaged, read-only template used to create containers. It can include application code, a language runtime, required libraries, and configuration defaults.

Example: the `nginx` image contains what is needed to start an Nginx web server. The image itself is not the running server; it is the template.

## 2. Docker container

A **container** is an instance created from an image. When you run an image, Docker creates and starts a container. A container can be running or stopped.

Analogy: an image is like a recipe/template, while a container is one prepared instance made from it. One image can create multiple containers.

## 3. Dockerfile

A **Dockerfile** is a text file containing instructions Docker uses to build an image. For example, it can specify a base Python image, choose a working directory, copy your application code, and set the command that runs when a container starts.

Tiny example — do not run this yet; we will build it in a later part:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

This file describes how to build an image for a small Python app, assuming `app.py` exists in the build context.

## 4. Registry

A **container registry** stores and distributes images. Docker Hub is one common registry. You can download an image from a registry or upload an image to one if you have the right access.

A registry stores images; it is not the same thing as a running container.

## 5. How the pieces fit together

```text
Dockerfile --build--> Image --run--> Container
                         ^
                         |
                 Registry stores/shares images
```

- Write a Dockerfile to describe how to package the application.
- Build an image from the Dockerfile.
- Run the image to create a container.
- Use a registry to share or download images when needed.

## Checkpoint

1. Which one is the template: image or container?
2. Which one contains instructions for building an image?
3. Where are images stored/shared so other people can download them?
4. In your own words, explain this flow: Dockerfile → Image → Container.

## Progress

- [ ] I can explain image vs container.
- [ ] I can explain what a Dockerfile is.
- [ ] I can explain what a registry does.
- [ ] I can explain how the four concepts connect.

**Next part:** how Docker Engine, Docker CLI, and the daemon work together.

## Source basis

The user's uploaded *Introduction to Docker* PDF discusses Docker Engine components on page 2, image lifecycle and Dockerfile instructions on page 3, and containers and registries on page 4. The definitions here are simplified for a beginner while preserving those core distinctions.
