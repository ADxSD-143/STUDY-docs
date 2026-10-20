# 01 — Set Up a Reproducible ML Project

**Estimated time:** 20–30 minutes  
**Goal:** create a small Python project that another person can run too.

## Why does this matter?

Code that works only on your computer is hard to debug, share, or use in a team. A reproducible project records its files and dependencies so someone can set up the same basic environment.

## A simple project structure

```text
student-marks-ml/
├── data/
│   └── README.md
├── notebooks/
├── src/
│   └── train.py
├── requirements.txt
└── README.md
```

- `data/`: dataset files or instructions for obtaining them. Do not commit private data or huge files.
- `notebooks/`: exploration and experiments.
- `src/`: reusable Python code.
- `requirements.txt`: Python packages needed by the project.
- `README.md`: what the project does and how to run it.

For a tiny first experiment, you do not need every folder immediately. The structure becomes useful as the project grows.

## Step 1 — Create a project and virtual environment

Open a terminal in the folder where you keep projects:

```powershell
mkdir student-marks-ml
cd student-marks-ml
py -m venv .venv
`.venv\Scripts\Activate.ps1
python --version
```

If PowerShell blocks activation, you can still use the environment's Python directly:

```powershell
.\.venv\Scripts\python.exe --version
```

A **virtual environment** keeps this project's installed packages separate from other Python projects.

## Step 2 — Install only the packages you need

For this course, a basic tabular-ML environment commonly uses:

```powershell
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib scikit-learn jupyter
python -m pip freeze > requirements.txt
```

Use `python -m pip` so pip is associated with the Python interpreter you are using. If you already have a working environment, do not reinstall everything just for this lesson.

## Step 3 — Check which Python is running

Run:

```powershell
python -c "import sys; print(sys.executable)"
python -c "import numpy, pandas, sklearn; print('Imports OK')"
```

The first command prints the Python interpreter path. Ideally, it points inside this project's `.venv` folder. The second checks that the main packages can be imported.

## Step 4 — Record how to run the project

A useful README should explain:

1. What the project predicts or investigates.
2. Where the data comes from and its licence or usage conditions.
3. How to create and activate the environment.
4. How to install dependencies.
5. How to run the code.
6. What results to expect and what the limitations are.

## Common problems

- **`ModuleNotFoundError`:** the package may be missing from the active environment, or your editor may be using a different interpreter.
- **Wrong Python version/path:** check `python --version` and `python -c "import sys; print(sys.executable)"`.
- **Notebook uses another environment:** select the project's interpreter/kernel in your notebook or editor.
- **It works on my machine:** record dependencies and setup steps; avoid relying on packages installed globally.

## Checkpoint

1. Why use a virtual environment?
2. What does `requirements.txt` record?
3. Which command shows the Python interpreter currently running?
4. If an import fails in an editor but works in a terminal, what should you check first?

<details>
<summary>Answers</summary>

1. To keep project dependencies separate from other projects.
2. The installed Python packages and their versions.
3. `python -c "import sys; print(sys.executable)"`
4. Check whether the editor and terminal use the same Python interpreter/environment.
</details>

## Next lesson

After this setup, we will use it to run and organise a small ML experiment. We will not repeat Python, NumPy, or pandas fundamentals you already know.
