# Dockerfile: Build and Run an Application

## What is a Dockerfile?

A Dockerfile is a text file with instructions Docker uses to build an image.

## Minimal Python example

Create `app.py`:

```python
print("Hello from inside Docker!")
```

Create a file named exactly `Dockerfile` (no extension):

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

Build and run in that directory:

```bash
docker build -t hello-python .
docker run --rm hello-python
```

Expected output: `Hello from inside Docker!`

## Instruction meanings

- `FROM`: base image.
- `WORKDIR`: working directory inside the image.
- `COPY`: copy files from the build context into the image.
- `CMD`: default command when a container starts.
- `docker build -t hello-python .`: build an image tagged `hello-python`; the final dot sends the current directory as build context.

## Common mistakes

- File is accidentally named `Dockerfile.txt`.
- Terminal is in the wrong directory.
- The file name or path in `COPY` is incorrect.
- Build context is too broad and includes unnecessary files.
- Confusing build-time `RUN` instructions with the runtime command specified by `CMD`.

## Checkpoint

- [ ] Build succeeds.
- [ ] Container prints the expected message.
- [ ] Explain the roles of `FROM`, `WORKDIR`, `COPY` and `CMD`.
