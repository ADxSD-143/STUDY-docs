# Capstone — Containerize the CampusX Laptop Price Predictor

## Goal
Package an existing Streamlit regression app with Docker and test it locally. This is a deployment exercise, not proof that the model is accurate or reflects current laptop prices.

## Source project
https://github.com/campusx-official/laptop-price-predictor-regression-project

The repository contains app.py, a Jupyter notebook, laptop_data.csv, df.pkl, pipe.pkl, requirements.txt and deployment-related files. The Streamlit app loads a saved pipeline and dataframe, collects laptop configuration values, calculates PPI from resolution and screen size, and displays a predicted price.

## Step 1 — Run locally first
Clone the repository into your own project folder. Read app.py and run the application in a virtual environment before adding Docker. This establishes a baseline to compare against.

Never load pickle files from an untrusted source; Python pickle deserialization can execute code.

## Step 2 — Audit dependencies and model compatibility
The repository's current requirements.txt lists streamlit and sklearn, while app.py imports NumPy too. Verify a clean environment and declare every direct dependency. The usual package name for scikit-learn in requirements is scikit-learn; verify the installed version is compatible with the saved pipeline before changing versions. Serialized sklearn models can be version-sensitive.

Do not invent dependencies or retrain the model just to complete the Docker lesson. Test what the project actually needs.

## Step 3 — Starting Dockerfile
After confirming the correct Python and package versions, a starting template is:

    FROM python:3.11-slim
    WORKDIR /app
    ENV PYTHONDONTWRITEBYTECODE=1
    ENV PYTHONUNBUFFERED=1
    COPY requirements.txt .
    RUN pip install --no-cache-dir -r requirements.txt
    COPY app.py df.pkl pipe.pkl ./
    EXPOSE 8501
    CMD ["streamlit", "run", "app.py", "--server.address=0.0.0.0", "--server.port=8501"]

This is not guaranteed to build until the environment is verified. Choose a Python version compatible with the saved artifacts and include any other files the app truly requires.

Add .dockerignore:

    .git
    .venv
    __pycache__
    *.pyc
    .env

Do not exclude model files required at runtime, and do not include unrelated datasets or secrets.

## Step 4 — Build and run
From the project root:

    docker build -t laptop-price-predictor:dev .
    docker run --rm -p 8501:8501 laptop-price-predictor:dev

Open http://localhost:8501 and submit a test configuration. If the host port is busy, use -p 8502:8501 and open http://localhost:8502.

## Step 5 — Troubleshoot
- Build error: inspect the first meaningful error in the build output.
- Missing module: verify dependency declarations.
- Pickle/model error: check source trust and Python/scikit-learn compatibility.
- Browser cannot connect: check container status, logs, published port and Streamlit binding.
- Prediction differs: compare with the local baseline; Docker packaging does not improve model quality.

## Step 6 — Production improvements
After local success, consider non-root execution, tested/pinned dependencies, health checks, image scanning, model artifact provenance and repeatable CI builds. Check data/model license and sensitivity before publishing.

## Acceptance checklist
- [ ] App works locally before containerization.
- [ ] Dependencies and serialized-model compatibility are documented.
- [ ] Image builds from a clean context.
- [ ] App opens at localhost:8501.
- [ ] One prediction completes.
- [ ] Logs and failure behavior are understood.
- [ ] No secrets or untrusted serialized files are introduced.
