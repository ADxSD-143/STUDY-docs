# Docker Course — Core Commands and Your First Image

## Learning goals
By the end of this lesson, you should be able to inspect Docker, run a container, build a simple image, and explain the command you used.

## 1. Check Docker is running
Open Docker Desktop and wait for Engine running. In its Terminal or PowerShell, run:

```text
docker version
docker info
docker run hello-world
```

**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


The first two commands show client/server and engine information. The hello-world test downloads its image if necessary, creates a container, prints a message, and exits.

## 2. Images and containers
Run:

```text
docker image ls
docker ps
docker ps -a
```

**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Images are templates. Containers are instances created from images. The ps command shows running containers; ps -a includes stopped containers.

Try a web server:

```text
docker run -d --name demo-nginx -p 8080:80 nginx
```

**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Open http://localhost:8080. The -d flag runs in the background, --name gives the container a readable name, and -p maps host port 8080 to container port 80.

Inspect and stop it:

```text
docker logs demo-nginx
docker stop demo-nginx
docker ps -a
docker start demo-nginx
docker stop demo-nginx
docker rm demo-nginx
```

**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Removing a container does not automatically remove the image. Read commands before running cleanup operations.

## 3. First Dockerfile
Create a folder such as D:\DockerLabs\hello-python. Save app.py:

```text
print("Hello from inside Docker!")
```

**What it does:** Python executes these statements in order. `print()` writes the following text to standard output.

**Expected output:**
~~~text
Hello from inside Docker!
~~~


Create a file named Dockerfile with no extension:

```text
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

**Line-by-line meaning:**
- `FROM python:3.12-slim`: chooses the base image/runtime; it may be downloaded during build.
- `WORKDIR /app`: sets the working directory inside the image.
- `COPY app.py .`: copies matching files from the build context into the image.
- `CMD ["python", "app.py"]`: default command when a container starts.

**Expected result:** Build progress rather than application output. App output appears when a container starts. If the build fails, inspect the first meaningful error.


Meaning:
- FROM chooses the base image and runtime.
- WORKDIR sets the working directory inside the image.
- COPY adds app.py from the build context.
- CMD sets the default command when the container starts.

From that folder run:

```text
docker build -t hello-python .
docker run --rm hello-python
```

**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


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
