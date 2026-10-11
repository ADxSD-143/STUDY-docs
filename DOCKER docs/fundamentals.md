# Docker — Learning Notes

A concise, practical reference for learning Docker step by step.

## 1. What is Docker?

Docker packages an application and its dependencies into a **container**, helping it run consistently across development and deployment environments.

- **Image:** A template used to create containers.
- **Container:** A running (or stopped) instance of an image.
- **Dockerfile:** Instructions used to build an image.
- **Registry:** A place to store and download images, such as Docker Hub.
- **Volume:** Persistent storage managed by Docker.
- **Port mapping:** Makes a container service reachable through a host port.

## 2. Basic commands

```bash
docker --version
docker pull hello-world
docker run hello-world
docker images
docker ps
docker ps -a
docker stop <container_id>
docker rm <container_id>
docker rmi <image_name>
```

## 3. Build and run an image

Create a file named `Dockerfile` in your project directory:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

Build and run it:

```bash
docker build -t my-python-app .
docker run --rm my-python-app
```

This example assumes the project contains `requirements.txt` and `app.py`. Adjust the base image and command to match your application.

## 4. Port mapping

For a web app that listens on port 8000 inside the container:

```bash
docker run --rm -p 8000:8000 my-python-app
```

The application must listen on `0.0.0.0` inside the container; listening only on `127.0.0.1` can prevent access through the mapped port.

## 5. Docker Compose

Docker Compose defines and runs multi-container applications from a YAML configuration, commonly named `compose.yaml`.

```bash
docker compose up --build
docker compose down
```

## 6. Useful workflow

1. Write or update the `Dockerfile`.
2. Build the image.
3. Run the container and test the application.
4. Inspect logs with `docker logs <container_id>`.
5. Check running containers with `docker ps`.
6. Use volumes when data must persist beyond a container's lifecycle.

## 7. Key distinction

Containers are isolated processes that share the host operating system's kernel; they are not the same as full virtual machines.

## Learning progress

- [ ] Install Docker and verify `docker --version`
- [ ] Run `hello-world`
- [ ] Build a simple Python image
- [ ] Run a web app with port mapping
- [ ] Practise volumes and Docker Compose

*Add commands, errors, fixes, and small experiments here as you practise.*
