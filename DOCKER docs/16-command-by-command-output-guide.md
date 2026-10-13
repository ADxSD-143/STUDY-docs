# Docker Command-by-Command Guide: Purpose, Expected Output, and Debugging

This companion explains the commands and code examples used in the Docker course. Run commands from the folder specified in the lesson. Exact IDs, timestamps, image sizes, download progress and versions vary; the expected behaviour is what matters.

## How to use this guide

For every lab, understand: **what the command does**, **what its flags mean**, **what successful output looks like**, and **what to inspect if it differs**. Replace placeholders such as CONTAINER_NAME with your actual container name; do not type placeholder brackets literally.

## 1. Verify Docker installation

### docker --version
**Purpose:** Prints the installed Docker CLI version. It does not prove the Engine is running.

**Expected output (example):**
~~~text
Docker version 2x.x.x, build ...
~~~
Your version and build hash will differ. If PowerShell says docker is not recognized, check installation/PATH and open a new terminal.

### docker compose version
**Purpose:** Prints the installed Docker Compose plugin version.

**Expected output (example):**
~~~text
Docker Compose version v2.x.x
~~~
If the command is unavailable, verify Docker Desktop installation and open a fresh terminal.

### docker version
**Purpose:** Shows both Docker client and server/Engine versions. It tries to contact the Engine.

**Expected result:** A Client section and a Server section. If the server section is missing or a connection error appears, Docker Desktop/Engine may not be running.

### docker info
**Purpose:** Shows Engine configuration, storage driver, image/container counts, runtime and resource information.

**Expected result:** A long report with fields such as Server Version, Storage Driver, Containers and Images. Fields differ by version/platform. If it cannot connect, start Docker Desktop, wait for Engine running, and retry.

## 2. First container and basic listings

### docker run hello-world
**Purpose:** Looks for the hello-world image locally; pulls it if missing; creates and runs a short-lived container; prints a test message; then exits.

**Expected output:** Possibly a message that the image is not found locally and download progress, followed by a message beginning “Hello from Docker!” and an explanation that Docker is working. If the image is cached, the pull step may be skipped. The container normally exits after printing.

### docker image ls (or docker images)
**Purpose:** Lists images stored locally.

**Expected result:** A table with repository, tag, image ID, creation time and size. hello-world should normally appear after the first test.

### docker ps
**Purpose:** Lists only running containers.

**Expected result:** A container table. It can have no rows if nothing is currently running; that is not necessarily an error.

### docker ps -a
**Purpose:** Lists all containers, including stopped ones. The -a flag means all.

**Expected result:** The hello-world container may appear with a status such as Exited (0), usually meaning its short task completed successfully. IDs and generated names vary.

## 3. Nginx container lifecycle

### docker run -d --name demo-nginx -p 8080:80 nginx
**Purpose:** Pulls the nginx image if needed and creates/starts an Nginx web server.

- -d runs it in the background.
- --name demo-nginx assigns a predictable name.
- -p 8080:80 publishes host port 8080 to container port 80. Format is HOST_PORT:CONTAINER_PORT.
- nginx is the image to run.

**Expected output:** Usually a long container ID. The prompt returns because the process is detached. Open http://localhost:8080 and expect the default Nginx welcome page. docker ps should show demo-nginx as running and a port mapping.

**Common problems:** If port 8080 is busy, use -p 8081:80 and open http://localhost:8081. If the name is already in use, inspect docker ps -a and either use a new name or intentionally remove the old container. If the browser cannot connect, check docker ps, logs, port mapping and Engine status.

### docker logs demo-nginx
**Purpose:** Prints captured standard output/error logs for the container.

**Expected result:** Nginx startup/access/error lines may appear. There may be few or no lines if no requests were made; empty logs do not automatically mean failure.

### docker stop demo-nginx
**Purpose:** Gracefully stops the container.

**Expected result:** Usually prints demo-nginx. docker ps no longer lists it; docker ps -a should show it as exited.

### docker start demo-nginx
**Purpose:** Starts an existing stopped container; it does not create a new one.

**Expected result:** Usually prints demo-nginx. Verify with docker ps and reopen the browser URL.

### docker restart demo-nginx
**Purpose:** Stops and starts the existing container.

**Expected result:** Usually prints the container name and the container returns to running if its process starts successfully.

### docker rm demo-nginx
**Purpose:** Removes a stopped container, not the image.

**Expected result:** Usually prints the container name. If it is running, Docker normally refuses until you stop it.

### docker rm -f demo-nginx
**Purpose:** Force-stops and removes the container. Use only when deletion is intended.

**Expected result:** Usually prints the name; docker ps -a no longer lists it. This does not automatically remove the image or separately managed named volumes.

### docker rmi nginx
**Purpose:** Removes the local nginx image.

**Expected result:** Usually prints the image name/ID. Docker may refuse if a container still references the image. It does not delete a registry copy; Docker can pull the image again later.

## 4. Python app and first Dockerfile

Create a folder such as D:\DockerLabs\hello-python. Put app.py and Dockerfile inside it.

### app.py
~~~python
print("Hello from inside Docker!")
~~~
**Purpose:** Python prints one line to standard output and exits. Running it directly with Python should print: Hello from inside Docker!

### Dockerfile
~~~dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
~~~
**Line-by-line:**
- FROM selects the Python 3.12 slim base image. It may be downloaded during the first build.
- WORKDIR sets /app as the working directory inside the image and creates it if needed.
- COPY app.py . copies app.py from the build context into /app.
- CMD sets the default command to run when a container starts.

These instructions should not print the Python greeting during build; it prints when the container runs.

### docker build -t hello-python .
**Purpose:** Builds an image from the Dockerfile in the current directory.
- build builds the image.
- -t hello-python assigns the image name/tag.
- The final dot means the current directory is the build context; Docker can copy files from this context unless excluded by .dockerignore.

**Expected result:** Build-step output for loading the Dockerfile/context, resolving the base image, executing instructions and exporting the image. The final success output normally indicates hello-python:latest was tagged. Progress wording varies by Docker version.

**If it fails:** Confirm the terminal is in the project folder, the filename is exactly Dockerfile (not Dockerfile.txt), and app.py exists. Read the first meaningful error above the final failure summary.

### docker run --rm hello-python
**Purpose:** Creates and runs a container from the image. --rm automatically removes the stopped container afterward.

**Expected output:**
~~~text
Hello from inside Docker!
~~~
Then the prompt returns. docker ps will not show it because it has exited; docker ps -a may not show it because --rm removed it.

### RUN versus CMD versus ENTRYPOINT
- Dockerfile RUN executes during image build and its result can be part of an image layer, e.g. installing requirements.
- CMD defines the default command when a container starts.
- ENTRYPOINT is commonly used for the main executable; CMD can supply default arguments. Choose based on the app's runtime needs.

## 5. Networks

### docker network ls
**Purpose:** Lists Docker networks. Expected: a table with IDs, names and drivers. Built-in networks commonly include bridge, host and none, depending on platform.

### docker network create demo-net
**Purpose:** Creates a user-defined network named demo-net.
**Expected output:** A network ID. If the name already exists, Docker reports a conflict.

### docker network inspect demo-net
**Purpose:** Shows network configuration and connected containers.
**Expected output:** JSON-like details such as name, driver, subnet/IPAM and a Containers section. The container list can be empty.

### docker network rm demo-net
**Purpose:** Removes the network.
**Expected output:** Usually the network name. Docker can refuse while containers remain connected; do not remove a network used by an active app.

## 6. Volumes and persistence

### docker volume ls
**Purpose:** Lists Docker-managed volumes. Expected: a table of names/drivers; it may be empty.

### docker volume create demo-data
**Purpose:** Creates a named volume for data that should outlive a container's writable layer.
**Expected output:** Usually demo-data.

### docker volume inspect demo-data
**Purpose:** Shows volume metadata and its Docker-managed mountpoint.
**Expected output:** JSON-like fields such as Name, Driver, Mountpoint and CreatedAt. On Docker Desktop, the Linux mountpoint may be inside its Linux backend, not a normal Windows path.

A volume is persistent storage, not a backup. Valuable data still needs a backup and restore plan.

**Bind mount versus named volume:** A bind mount connects a chosen host path to a container path, for example a project folder mapped to /app. A named volume is managed by Docker, for example demo-data mapped to /var/lib/app-data. Destination paths depend on the app. Mounting over an existing directory can hide the image's files at that path.

## 7. Compose

Create compose.yaml:

~~~yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
  cache:
    image: redis:alpine
~~~

**Code meaning:** services defines the app components; web and cache are service names; image selects each image; ports publishes host 8080 to container 80 for web. The port is quoted to keep the YAML value as a string. This example starts two independent services; Nginx is not automatically configured to use Redis.

### docker compose up -d
**Purpose:** Reads the Compose file, creates/reuses the project network and containers, and starts services in the background.
**Expected result:** Pull/create/start progress; first run may take longer while images download. docker compose ps should show the services running. Open http://localhost:8080 for the Nginx welcome page.

### docker compose up --build
**Purpose:** Builds images for services that have a build configuration, then starts the stack. Services configured only with image do not have a local Dockerfile to build.
**Expected result:** Build output, followed by service creation/start output.

### docker compose ps
**Purpose:** Lists containers in the current Compose project.
**Expected result:** A table showing services/containers, state and ports. A different directory/project context may show no matching containers.

### docker compose logs
**Purpose:** Prints logs from Compose services.
**Expected result:** Service-labelled output where processes emit logs. docker compose logs -f follows new lines live; Ctrl+C stops following logs, not necessarily the containers.

### docker compose down
**Purpose:** Stops and removes project containers and the project network.
**Expected result:** Messages about stopping/removing services and network. Named volumes are normally retained unless explicitly requested for removal. Do not add volume-removal flags casually.

## 8. .dockerignore, dependencies and non-root user

Example .dockerignore:
~~~text
.git
.venv
__pycache__
*.pyc
.env
.env.*
~~~
**Purpose:** Excludes matching files from the build context, reducing unnecessary files and helping prevent local secrets from being sent to the builder. It usually prints no message by itself. During build, excluded files should not be available to COPY. Do not exclude files the app needs; this is not a substitute for safe secret handling.

Dependency-first Dockerfile:
~~~dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
~~~
- COPY requirements.txt . copies the dependency manifest first.
- RUN pip install --no-cache-dir -r requirements.txt installs packages during image build. --no-cache-dir avoids keeping pip's download cache; it does not disable Docker's build cache.
- COPY . . copies the remaining build context into /app.
- CMD runs the app when a container starts.

**Expected result:** pip lists packages being installed and completes successfully. Exact output depends on dependencies. Keeping requirements separate can let Docker reuse the dependency layer when only app source changes.

Non-root pattern:
~~~dockerfile
FROM python:3.12-slim
WORKDIR /app
RUN useradd --create-home appuser
COPY --chown=appuser:appuser app.py .
USER appuser
CMD ["python", "app.py"]
~~~
- RUN useradd creates an unprivileged user.
- COPY --chown assigns file ownership.
- USER appuser makes subsequent instructions/runtime use that user by default.
**Expected result:** Build succeeds if the base image has useradd and permissions are correct. Test writes/permissions; this is a teaching pattern, not a universal production Dockerfile.

## 9. Buildx

### docker buildx version
**Purpose:** Prints Buildx plugin version. Expected: a version line.

### docker buildx ls
**Purpose:** Lists available builders, drivers, status and supported platforms. Expected: a table; names/platforms vary.

### docker buildx inspect
**Purpose:** Shows details for the selected builder. Expected: builder name, driver, status and platform details. A build alone does not prove the app runs correctly on every target architecture.

## 10. CampusX Streamlit capstone

Example Dockerfile:
~~~dockerfile
FROM python:3.11-slim
WORKDIR /app
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py df.pkl pipe.pkl ./
EXPOSE 8501
CMD ["streamlit", "run", "app.py", "--server.address=0.0.0.0", "--server.port=8501"]
~~~
- ENV PYTHONDONTWRITEBYTECODE=1 prevents Python writing .pyc bytecode files.
- ENV PYTHONUNBUFFERED=1 helps Python logs appear promptly.
- EXPOSE 8501 documents the app's container port; it does not publish it on the host.
- --server.address=0.0.0.0 allows Streamlit to accept traffic through the container network.
- --server.port=8501 selects the internal Streamlit port.

**Before building:** Verify the source of pickle files; untrusted pickle deserialization can execute code. Check Python, Streamlit, NumPy, scikit-learn and saved-model compatibility. This template is not guaranteed to build until those dependencies are checked.

### docker build -t laptop-price-predictor:dev .
**Purpose:** Builds the image and tags it laptop-price-predictor:dev.
**Expected result:** Successful build output and an image with repository laptop-price-predictor and tag dev in docker image ls.

### docker run --rm -p 8501:8501 laptop-price-predictor:dev
**Purpose:** Starts the app, publishes host port 8501 to container port 8501, and removes the container after exit.
**Expected result:** Streamlit startup output with a local URL, commonly http://localhost:8501. Open it and submit a test configuration. Keep the terminal open while the foreground app runs; Ctrl+C stops it. If port 8501 is busy, use -p 8502:8501 and open http://localhost:8502.

**Troubleshooting:** Missing module means check requirements and rebuild. Pickle/model errors require checking trust and library compatibility. Browser failure requires checking logs, port mapping and app binding. Compare prediction outputs to a local baseline; Docker packaging does not improve model quality.

## 11. Diagnostic commands

| Command | Purpose | Expected result |
|---|---|---|
| docker ps -a | Check running and exited containers | Container table with STATUS |
| docker logs CONTAINER_NAME | Read app output/errors | Logs, or possibly no output |
| docker inspect CONTAINER_NAME | Inspect state/config/mounts/network | JSON-like metadata |
| docker image ls | List local images | Image/tag table |
| docker volume ls | List named volumes | Volume table |
| docker network ls | List networks | Network table |
| docker compose ps | Check Compose service state | Service/container table |
| docker compose logs | Read Compose logs | Service-labelled output when available |

Recommended order: check Engine status → inspect docker ps -a → read logs → inspect ports/mounts/configuration → change one thing → rerun and verify. Save the first meaningful error when asking for help.

## 12. Destructive commands: pause before using

- docker rm CONTAINER_NAME removes a container.
- docker rm -f CONTAINER_NAME force-stops and removes it.
- docker rmi IMAGE removes a local image if allowed.
- docker network rm NETWORK removes a network if no dependency blocks it.
- docker volume rm VOLUME deletes the named volume and its stored data.
- docker compose down -v removes Compose project volumes as well as containers/networks in the applicable project.

Identify the exact resource and confirm the data is disposable before deletion. Avoid broad prune commands, especially those that include volumes, until you understand their scope.

## Learning log requirement

For every lab, record the command, what you expected, what actually happened, and how you fixed any error in [09 — Troubleshooting and Lab Log](09-troubleshooting.md). Do not mark a command as tested just because you read it.
