# Docker — Learning Roadmap and Resource Notes

This documentation accompanies the video lesson and the uploaded **Introduction to Docker** PDF. It records source topics, practical steps, and how Docker will be applied to an ML project.

## Resources

- **Video lesson:** [YouTube — Docker tutorial](https://youtu.be/GToyQTGDOS4)
- **Uploaded PDF:** *Introduction to Docker* (6 pages; dated 7 August 2024).
- **Practice application:** [CampusX Laptop Price Predictor](https://github.com/campusx-official/laptop-price-predictor-regression-project)

## Two-hour focused study

1. **0–20 min:** Docker purpose, consistency, isolation, scalability, Engine.
2. **20–40 min:** Images, containers, registries and core commands.
3. **40–75 min:** Dockerfile instructions; build and run a simple Python app.
4. **75–100 min:** Ports, volumes and basic networking.
5. **100–115 min:** Containerize or at least understand the existing Streamlit ML app.
6. **115–120 min:** Recap and note errors.

This is a beginner sprint, not mastery of every Docker topic.

## What the PDF covers

| PDF pages | Topics |
|---|---|
| Page 1 | What Docker is; consistency across environments, isolation and scalability |
| Page 2 | Docker Engine; daemon (`dockerd`), CLI (`docker`) and REST API |
| Page 3 | Docker images, image lifecycle and Dockerfile instructions: `FROM`, `LABEL`, `RUN`, `COPY`, `ENV`, `WORKDIR`, `EXPOSE`, `CMD`, `VOLUME`, `ARG` |
| Page 4 | Containers, registries, repositories, image tags, Docker Hub and private/third-party registries |
| Page 5 | Registry benefits and Docker use cases: microservices, CI/CD, cloud migration, scalable web apps, QA, ML/AI, APIs |
| Page 6 | A continuation of the API development/deployment use case |

The PDF uses a registry → image → container diagram on page 2. Page 3 discusses image layers and Dockerfile instructions. Use these diagrams as the mental model while studying.

## Core mental model

- **Dockerfile:** build instructions.
- **Image:** packaged template built from those instructions.
- **Container:** a running or stopped instance created from an image.
- **Registry:** place where images are stored and distributed.
- **Docker Engine:** runs and manages containers. The CLI sends requests to the daemon through Docker's API.

Typical flow:

```text
Dockerfile -> docker build -> Image -> docker run -> Container
                               ↕
                         Docker Registry
```

## Commands to practise

Run one at a time in PowerShell:

```powershell
docker --version
docker compose version
docker info
docker run hello-world
docker image ls
docker ps
docker ps -a
docker pull nginx
docker run -d --name docker-demo -p 8080:80 nginx
docker logs docker-demo
docker stop docker-demo
docker rm docker-demo
```

While the Nginx container is running, open `http://localhost:8080`. If port 8080 is already occupied, choose another host port, for example `8081:80`.

## Dockerfile mini-practice

Create a folder and save these files inside it.

`app.py`:

```python
print("Hello from inside Docker!")
```

`Dockerfile`:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

Build and run:

```powershell
docker build -t hello-python .
docker run --rm hello-python
```

Expected output: `Hello from inside Docker!`

## Applying Docker to the CampusX ML project

The project repository contains `laptop_data.csv`, `laptop-price-predictor.ipynb`, `app.py`, `requirements.txt`, `df.pkl`, `pipe.pkl`, `Procfile`, and `setup.sh`. Its Streamlit app loads the serialized pipeline and dataframe, collects laptop configuration fields, transforms inputs such as touchscreen/IPS and screen resolution, and predicts a price.

Suggested learning sequence:

1. First run the project locally using its README/instructions and verify the current app works.
2. Understand `app.py`, `requirements.txt`, `df.pkl`, and `pipe.pkl`; do not retrain or alter the model just to learn Docker.
3. Add a Dockerfile in your own local clone, preserving the existing app structure.
4. Build an image and run Streamlit in a container.
5. Publish the Streamlit port to localhost and test a prediction.
6. Record build/run errors and how you resolved them.

**Important:** the repository's `requirements.txt` currently lists `streamlit` and `sklearn` only. The app imports `numpy`, so verify that the full environment is declared and working before building the image. The committed pickle artifacts must be loaded only from a trusted source; pickle files can execute code when deserialized.

## Checkpoint checklist

- [ ] Can explain consistency, isolation, and scalability.
- [ ] Can describe CLI → REST API → Docker daemon.
- [ ] Can distinguish image, container, Dockerfile, and registry.
- [ ] Have successfully run `hello-world`.
- [ ] Have inspected images and containers.
- [ ] Have started an Nginx container and reached localhost through port mapping.
- [ ] Have built and run `hello-python`.
- [ ] Can name the most common Dockerfile instructions.
- [ ] Understand how Docker could package the CampusX Streamlit application.

## Session log

After practising, add:

- **Date and elapsed time:**
- **Topic/video timestamp:**
- **Command executed:**
- **Expected output vs actual output:**
- **Error and fix:**
- **Question to revisit:**
- **Next topic:**

## Further reference

- [Docker Get Started](https://docs.docker.com/get-started/)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/)
