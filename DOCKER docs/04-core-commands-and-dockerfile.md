# Docker Course — Core Commands and Your First Image

## Learning goals
By the end of this lesson, you should be able to inspect Docker, run a container, build a simple image, and explain the command you used.

## 1. Check Docker is running
Open Docker Desktop and wait for Engine running. In its Terminal or PowerShell, run:

    docker version
    docker info
    docker run hello-world

The first two commands show client/server and engine information. The hello-world test downloads its image if necessary, creates a container, prints a message, and exits.

## 2. Images and containers
Run:

    docker image ls
    docker ps
    docker ps -a

Images are templates. Containers are instances created from images. The ps command shows running containers; ps -a includes stopped containers.

Try a web server:

    docker run -d --name demo-nginx -p 8080:80 nginx

Open http://localhost:8080. The -d flag runs in the background, --name gives the container a readable name, and -p maps host port 8080 to container port 80.

Inspect and stop it:

    docker logs demo-nginx
    docker stop demo-nginx
    docker ps -a
    docker start demo-nginx
    docker stop demo-nginx
    docker rm demo-nginx

Removing a container does not automatically remove the image. Read commands before running cleanup operations.

## 3. First Dockerfile
Create a folder such as D:\DockerLabs\hello-python. Save app.py:

    print("Hello from inside Docker!")

Create a file named Dockerfile with no extension:

    FROM python:3.12-slim
    WORKDIR /app
    COPY app.py .
    CMD ["python", "app.py"]

Meaning:
- FROM chooses the base image and runtime.
- WORKDIR sets the working directory inside the image.
- COPY adds app.py from the build context.
- CMD sets the default command when the container starts.

From that folder run:

    docker build -t hello-python .
    docker run --rm hello-python

Expected output: Hello from inside Docker!

The dot means the current directory is the build context. Do not use your entire drive as the build context. A .dockerignore file can exclude .git, .venv, caches and local secrets from the context.

## 4. Build-time versus run-time
RUN executes during image building and contributes to image layers. CMD specifies the default command when a container starts. ENTRYPOINT is often used to define the main executable; CMD can supply default arguments. The exact choice depends on the app.

## Troubleshooting
- Docker daemon unavailable: start Docker Desktop and wait for Engine running.
- File not found: confirm terminal folder and exact file name.
- Dockerfile.txt: enable file extensions in Explorer and rename to Dockerfile.
- Port conflict: use a different host port, such as 8081:80.
- Container exits: inspect docker ps -a and docker logs <name>.
- Missing Python module: declare dependencies and install them during the build.

## Checkpoint
1. What is the difference between an image and a container?
2. What does the dot in docker build -t hello-python . mean?
3. What is the difference between RUN and CMD?
4. Why can docker ps show nothing even though hello-world succeeded?
