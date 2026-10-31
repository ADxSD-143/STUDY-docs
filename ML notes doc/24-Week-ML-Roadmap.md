# 8-Week Beginner Machine Learning Roadmap

**Flow:** Python → Maths alongside practice → Data → End-to-end ML workflow → Mini-capstone  
**Duration:** 8 weeks × 10 hours/week = 80 focused hours. Free-first tools and resources.

> **Honest scope:** This is an accelerated foundation, not complete ML mastery or job readiness. The 8-week core teaches the complete project lifecycle at beginner depth. Advanced algorithms, tuning, deployment and monitoring are introduced selectively and continued later.

## Fixed primary videos
1. [Main Machine Learning course](https://youtu.be/trsyTEA22Gw) — primary ML course; follow assigned timestamps.
2. [Mathematics for ML](https://youtu.be/cO9xmfsJJu4) — maths companion; study relevant sections alongside each topic.

Complete reference playlists (CampusX and StatQuest) are in [resources](resources.md). They are supplementary; do not attempt to finish every playlist in 8 weeks.

## Weekly rhythm
Target 10 hours: 2–3 hours learning, 5–6 hours coding/experiments, 1–2 hours review. Extend a week if the checkpoint is not passed. Never skip coding to preserve the calendar.

## Phase map
| Phase | Weeks | Guide |
|---|---:|---|
| Python foundations | 1 | [Python](phases/02-python.md) |
| Maths for ML | 1–2 alongside practice | [Maths](phases/01-maths.md) |
| Data collection, EDA and preparation | 2–3 | [Data](phases/03-data.md) |
| Core modeling and evaluation | 4–7 | [Machine Learning](phases/04-machine-learning.md) |
| End-to-end project lifecycle | Throughout; applied in Week 8 | [Project workflow](ml-project-workflow.md) |
| Mini-capstone | 8 | [Projects](phases/05-projects-engineering.md) |

## Weekly plan
| Week | Pipeline stages | Learn and build | Deliverable |
|---|---|---|---|
| 1 | Stage 0 + Python foundation | Frame a simple ML problem; identify task, target, metric, baseline and constraints. Learn Python fundamentals. | Problem brief and Python practice scripts |
| 2 | Stage 1–2 | Collect/load a permitted dataset; learn basic SQL concepts; use NumPy/pandas; inspect data quality and perform EDA. | Dataset card/source notes and EDA notebook with written insights |
| 3 | Stage 3–5 | Choose a valid split; learn leakage; clean and preprocess; use basic encoders/scalers and Pipeline/ColumnTransformer; create justified features. | Leakage-safe preprocessing pipeline and feature notes |
| 4 | Stage 6–7 | Build a baseline; learn Linear Regression and Logistic Regression; compare baseline vs first learned model. | Baseline/model notebook and results table |
| 5 | Stage 7–8 | Learn Naive Bayes, KNN and classification metrics; choose metrics based on error costs; inspect threshold effects. | Model comparison and evaluation report |
| 6 | Stage 7–8 + 10 | Learn Decision Trees and Random Forest; understand bias/variance; perform basic error analysis and segment checks. | Tree/forest comparison and error analysis |
| 7 | Stage 8–11 | Learn cross-validation, model selection, leakage-safe tuning basics, final test evaluation, model persistence and reproducibility. | CV comparison, final evaluation and saved pipeline |
| 8 | Stage 0–13 applied | Complete CampusFix mini-capstone: problem brief, data audit, EDA, split, preprocessing, baseline, text model, evaluation, error analysis, packaging and README. Local API/UI is optional. | Reproducible project with report, saved pipeline and clear limitations |

## Weekly resources and sequence
- **Week 1:** [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X), sessions 1–12. Maths companion: arithmetic, graphs, vectors and averages.
- **Week 2:** CampusX Python playlist sessions 13–15 (NumPy), 16 onward (pandas). [NumPy supplement](https://youtu.be/VXU4LSAQDSc), [pandas supplement](https://youtu.be/VXtjG_GzO7Q). [CampusX data cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2), [Krish Naik EDA](https://youtu.be/fHFOANOHwh8).
- **Week 3:** Learn train/test split before fitting preprocessing. Read [scikit-learn preprocessing and composition](https://scikit-learn.org/stable/modules/compose.html).
- **Week 4:** Main course Linear Regression 27:13, R² 44:55, multiple regression 52:47; Logistic Regression 2:15:32.
- **Week 5:** [Confusion matrix](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA) → [Naive Bayes](https://youtu.be/O2L2Uv9pdDA) → [KNN](https://youtu.be/abnL_GUGub4).
- **Week 6:** Main course Decision Trees 3:39:55 and 3:58:05; [Random Forest](https://youtu.be/J4Wdy0Wc_xQ), [AdaBoost](https://youtu.be/LsK-xG1cLYA), [bias–variance](https://youtu.be/EuBBz3bI-aA).
- **Week 7:** [Cross-validation](https://youtu.be/fSytzGwwBVw), [scikit-learn CV](https://scikit-learn.org/stable/modules/cross_validation.html), [Pipeline](https://scikit-learn.org/stable/modules/compose.html), [model persistence](https://scikit-learn.org/stable/model_persistence.html).
- **Week 8:** Revisit only resources needed for the capstone. See [CampusFix project brief](projects/campusfix/README.md).

## Checkpoints
- Week 1: explain problem, target, task type and metric; write basic Python functions.
- Week 2: load a dataset, inspect quality and write at least five EDA findings.
- Week 3: explain split strategy and demonstrate that preprocessing is fit only on training data.
- Week 4: compare a baseline with Linear/Logistic Regression.
- Week 5: interpret confusion matrix and precision vs recall; compare NB and KNN.
- Week 6: explain overfitting and inspect model errors.
- Week 7: explain cross-validation, keep test data untouched and reload a saved pipeline.
- Week 8: another person can reproduce the project from the README and understand its limitations.

## Continuation track
After the foundation, deepen Ridge/Lasso/ElasticNet, SVM, XGBoost/LightGBM/CatBoost, DBSCAN, PCA, Optuna, SHAP, MLflow, FastAPI, Docker, CI/CD, deployment and monitoring. Neural networks, PyTorch, NLP, Transformers, LLMs, RAG and agents are separate follow-on tracks.

## Non-negotiable project rules
Split before fitting learned preprocessing. Use Pipeline/ColumnTransformer and cross-validation without leakage. Choose metrics based on error costs. Compare against a baseline. Inspect errors. Evaluate the final test set once. Record data source/licence/privacy and honest limitations.

**Full checklist:** [End-to-End ML Project Workflow — Stage 0 to Stage 13](ml-project-workflow.md).