# Docker Course — Production Images, Security and Reliability

## 1. Image quality
A useful production image should be reproducible, focused, reasonably small, maintainable and safe to run. The smallest image is not automatically the best if it makes debugging or compatibility worse.

Create a .dockerignore file suited to your project. Typical exclusions include:

```text
.git
.venv
__pycache__
*.pyc
.env
.env.*
```

**What this file does:** These patterns exclude matching files from the Docker build context. **Expected result:** saving the file prints nothing; the next build omits matching files from the context. Do not exclude files the application needs, and do not rely on this alone to protect secrets.


**What this file does:** Each line is a pattern excluded from the Docker build context. **Expected result:** no terminal output from saving the file; later builds send fewer unnecessary files to the builder. Files excluded here cannot be copied into the image, so do not exclude runtime requirements.


**What this example does:** Shows the configuration/data structure discussed above. Saving it alone does not execute it. **Expected result:** run the related command described nearby; success is shown by its status/output or the service behaving as configured.


Never exclude files the app needs, and never include credentials or unnecessary datasets.

## 2. Build cache
For Python applications, copy dependency manifests before frequently changing source files:

```text
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

**Line-by-line meaning:**
- `FROM python:3.12-slim`: selects the base image.
- `WORKDIR /app`: sets the working directory inside the image.
- `COPY requirements.txt .`: copies files from the build context; --chown sets ownership when specified.
- `RUN pip install --no-cache-dir -r requirements.txt`: executes during image build; a failure stops the build.
- `COPY . .`: copies files from the build context; --chown sets ownership when specified.
- `CMD ["python", "app.py"]`: default command at container startup.

**Expected result:** The image build should complete and tag the image if the base image, file paths and permissions are valid. The app's output appears when a container starts. Test permissions rather than assuming the example is production-ready.


**Line-by-line meaning:**
- `FROM python:3.12-slim`: chooses the base image/runtime; it may be downloaded during build.
- `WORKDIR /app`: sets the working directory inside the image.
- `COPY requirements.txt .`: copies matching files from the build context into the image.
- `RUN pip install --no-cache-dir -r requirements.txt`: executes during image build; failure stops the build.
- `COPY . .`: copies matching files from the build context into the image.
- `CMD ["python", "app.py"]`: default command when a container starts.

**Expected result:** Build progress rather than application output. App output appears when a container starts. If the build fails, inspect the first meaningful error.


This is a teaching template, not a universal production Dockerfile. Verify the app's real dependencies, runtime command and OS requirements. Copying the requirements file first can allow the dependency layer to be reused when only source code changes.

## 3. Multi-stage builds
A multi-stage build uses separate stages for building/testing and the final runtime. Copy only required artifacts into the final stage. This can reduce image size and attack surface when compilers or development tools are not needed at runtime.

## 4. Versioning and updates
Pin tested dependencies and choose a deliberate base-image version policy. Pinning improves repeatability but can leave old vulnerable versions in place if no one updates them. Combine reproducible builds with regular patching and vulnerability scanning. Tags can move; a digest identifies specific image content.

## 5. Security baseline
- Use trusted, maintained base images.
- Scan images and dependency manifests.
- Run as a non-root user when feasible.
- Avoid privileged containers unless a documented need exists.
- Limit capabilities, mounts, network exposure and writable paths.
- Do not bake secrets into ARG or ENV values, source control, image layers or logs.
- Use BuildKit secret mounts for build-time credentials and platform-appropriate secrets at runtime.
- Treat downloaded model files and serialized pickle artifacts as untrusted until provenance is established. Python pickle deserialization can execute code.
- Keep Docker Engine, Docker Desktop, base images and dependencies updated.

Example non-root pattern (test the base image and file permissions first):

```text
FROM python:3.12-slim
WORKDIR /app
RUN useradd --create-home appuser
COPY --chown=appuser:appuser app.py .
USER appuser
CMD ["python", "app.py"]
```

**Line-by-line meaning:**
- `FROM python:3.12-slim`: selects the base image.
- `WORKDIR /app`: sets the working directory inside the image.
- `RUN useradd --create-home appuser`: executes during image build; a failure stops the build.
- `COPY --chown=appuser:appuser app.py .`: copies files from the build context; --chown sets ownership when specified.
- `USER appuser`: selects the user for subsequent runtime operations.
- `CMD ["python", "app.py"]`: default command at container startup.

**Expected result:** The image build should complete and tag the image if the base image, file paths and permissions are valid. The app's output appears when a container starts. Test permissions rather than assuming the example is production-ready.


**Line-by-line meaning:**
- `FROM python:3.12-slim`: chooses the base image/runtime; it may be downloaded during build.
- `WORKDIR /app`: sets the working directory inside the image.
- `RUN useradd --create-home appuser`: executes during image build; failure stops the build.
- `COPY --chown=appuser:appuser app.py .`: copies matching files from the build context into the image.
- `USER appuser`: selects the user for following instructions/runtime.
- `CMD ["python", "app.py"]`: default command when a container starts.

**Expected result:** Build progress rather than application output. App output appears when a container starts. If the build fails, inspect the first meaningful error.


## 6. Reliability
A running process is not necessarily ready to serve traffic. Health checks should test a real, cheap health endpoint or command. Do not copy a health check that assumes a port or tool your image does not have.

Production patterns include:
- Logs to stdout/stderr.
- Graceful handling of termination signals.
- Bounded retries with backoff for transient dependencies.
- Persistent state outside replaceable containers.
- Measured CPU/memory needs and appropriate limits.
- Monitoring for latency, errors, restarts and resource pressure.
- Rollback to a known, tested image.

## Industry incidents
**Huge image:** inspect build context and layers, add .dockerignore, use cache effectively and consider multi-stage builds.

**Token leaked:** revoke/rotate it, audit exposure, remove it from future builds, clean repository history as appropriate and rebuild a safe artifact. Deleting a line from the current Dockerfile does not remove a secret from old layers or Git history.

**Container restarts:** inspect logs and exit status, dependency readiness, health checks, configuration and resource pressure before changing restart policies.

## Checkpoint
1. Why is .dockerignore important?
2. Why is pinning alone not a complete dependency strategy?
3. Name three ways to reduce container risk.
4. What should you investigate before fixing a restarting container?
