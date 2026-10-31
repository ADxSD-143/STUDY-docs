# 8-Week Beginner Machine Learning Roadmap
**Flow: Python → Maths alongside practice → Data → ML → Mini-capstone**  
**Duration:** 8 weeks × 10 hours/week = 80 focused hours. Free resources and tools only.

> **Honest scope:** This is an accelerated foundation, not complete ML mastery or job readiness. A true beginner may need to extend the schedule. The 8-week version prioritizes a first classical ML project. SVM, deep learning, transformers, RAG, advanced tuning and full production deployment are deferred.

## Two fixed primary videos
1. [Main Machine Learning course](https://youtu.be/trsyTEA22Gw) — primary ML course; follow assigned timestamps.
2. [Mathematics for ML](https://youtu.be/cO9xmfsJJu4) — maths companion; study relevant sections alongside each model, not all upfront.

Other resources are supplements, not competing main courses.

## Weekly rhythm
10 hours/week: 2–3 hours video/reading, 5–6 hours coding, 1–2 hours review/checkpoint. Extend a week if the checkpoint is not passed. Never skip coding to preserve the calendar.

## Phase map
| Phase | Weeks | Guide |
|---|---:|---|
| Python foundations | 1 | [Python](phases/02-python.md) |
| Maths for ML | 1–2 alongside practice | [Maths](phases/01-maths.md) |
| Data preparation | 2–3 | [Data](phases/03-data.md) |
| Core ML | 4–7 | [Machine Learning](phases/04-machine-learning.md) |
| Mini-capstone | 8 | [Projects and Engineering](phases/05-projects-engineering.md) |

## Weekly plan
| Week | Learn in this order | Deliverable |
|---|---|---|
| 1 | Python basics: variables, types, conditions, loops, functions, collections and files. [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X), sessions 1–12. Start maths companion with arithmetic, graphs, vectors and averages. | Python exercises and a script computing mean/min/max. |
| 2 | NumPy (CampusX sessions 13–15) → pandas (session 16 onward) → maths companion: vectors, matrices, probability and Bayes intuition. Supplements: [NumPy](https://youtu.be/VXU4LSAQDSc), [pandas](https://youtu.be/VXtjG_GzO7Q). | CSV notebook: filtering, missing values, groupby and one plot. |
| 3 | [CampusX data cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2) → [Krish Naik EDA](https://youtu.be/fHFOANOHwh8). Learn features/target, train/test split and leakage. | EDA notebook, 3 plots, documented cleaning and split. |
| 4 | Linear Regression: main course 27:13, R² 44:55, multiple regression 52:47. Logistic Regression: main course 2:15:32 and [StatQuest](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe). | Fit both with scikit-learn; inspect residuals and probabilities. |
| 5 | [Confusion matrix](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA). Then [Naive Bayes](https://youtu.be/O2L2Uv9pdDA) and [KNN](https://youtu.be/abnL_GUGub4). | Compare Logistic Regression, NB and scaled KNN; report metrics and threshold choice. |
| 6 | Decision Trees: main course 3:39:55 and 3:58:05. Then [Random Forest](https://youtu.be/J4Wdy0Wc_xQ), [AdaBoost](https://youtu.be/LsK-xG1cLYA) and [bias–variance](https://youtu.be/EuBBz3bI-aA). | Compare baseline, tree and forest; inspect depth vs validation performance. |
| 7 | [StatQuest cross-validation](https://youtu.be/fSytzGwwBVw) → [scikit-learn CV](https://scikit-learn.org/stable/modules/cross_validation.html) and [Pipeline](https://scikit-learn.org/stable/modules/compose.html). Optional: K-Means at main course 6:48:13 and PCA at 6:12:25 only after core work. | Leakage-safe pipeline and 3-model CV comparison. |
| 8 | CampusFix capstone: baseline-first text classification. Revisit only the videos/docs needed for the chosen model. | Reproducible model, evaluation report, error analysis and README. FastAPI is optional; Docker/production deployment deferred. |

## Checkpoints
- Week 1: write a function, use a loop and manipulate lists/dictionaries without copying.
- Week 2: load/filter/group a CSV and explain mean/variance.
- Week 3: explain features/target, missing values, train/test split and leakage.
- Week 4: explain regression vs classification and fit both model types.
- Week 5: interpret a confusion matrix and precision vs recall.
- Week 6: explain overfitting and compare a tree with a forest.
- Week 7: explain cross-validation and train-only preprocessing.
- Week 8: another person can rerun the project from the README and understand its limitations.

## Deferred to the next track
SVM, detailed boosting/XGBoost, advanced calibration/tuning, deeper clustering, neural-network derivations, PyTorch, transformers, LLMs, RAG, agents, Docker, CI/CD and monitoring. These are not removed from the full learning journey; they are intentionally excluded from this 80-hour beginner sprint.

## Data and evaluation rules
Fit preprocessing only on training data, preferably inside a Pipeline. Use validation/CV for model selection and keep the test set for final evaluation. Report appropriate metrics and failure cases, not accuracy alone. Record dataset source/licence and limitations.

## Capstone
Default: [CampusFix — campus infrastructure complaint triage](projects/campusfix/README.md). Obtain permission for campus complaint data and anonymize it. If unavailable, use a public service-request dataset and clearly label it as a proxy. Never present synthetic records as genuine complaints.
