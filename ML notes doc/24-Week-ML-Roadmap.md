# 8-Week Beginner Machine Learning Roadmap

**Flow:** Python → Maths alongside practice → Data → Machine Learning → Mini-capstone  
**Duration:** 8 weeks × 10 hours/week = 80 hours (accelerated foundation, not mastery).  
**Weekly split:** Aim for 3 hours of focused learning, 5 hours of coding/experiments, and 2 hours of revision and notes. Adjust the pace when a topic needs more time; do not rush past the readiness checks.

This roadmap is designed to be approachable for a beginner. If you already know a topic, use the checkpoint to verify your understanding and move ahead rather than repeating it.

## Primary learning resources

Use these two videos as the fixed primary resources throughout the roadmap:

- [Data Dissection — Complete ML course in Hindi](https://youtu.be/trsyTEA22Gw) — main ML course. Follow only the topics assigned each week.
- [Data Dissection — Complete Math for ML and AI](https://youtu.be/cO9xmfsJJu4) — maths companion. Study the relevant sections alongside coding; do not try to finish all maths before starting ML.

Other resources listed below are supplementary. Use them when a topic in the main videos is unclear; they are not additional mandatory courses.

## 8-week schedule

| Week | Focus | Deliverable |
|---|---|---|
| 1 | Python fundamentals: variables, data types, conditions, loops, functions, strings, collections, files, exceptions and basic debugging | Python practice notebook/scripts; pass the Python checkpoint |
| 2 | NumPy, pandas and essential maths: arrays, indexing, vector operations, DataFrames, descriptive statistics, probability and basic derivatives | NumPy/pandas practice notebook and maths summary |
| 3 | Data cleaning, missing values, duplicates, outliers, basic encoding, EDA, visualization, feature basics and train/test split | Clean dataset notebook and short EDA report |
| 4 | Linear Regression and Logistic Regression: prediction vs classification, loss, gradient descent intuition, sigmoid and decision threshold | Regression and classification notebooks using scikit-learn |
| 5 | Evaluation: confusion matrix, accuracy, precision, recall, F1, specificity, FPR/FNR and ROC-AUC; Naive Bayes and KNN | Model evaluation notebook and Naive Bayes/KNN practice |
| 6 | Decision Trees, tree splitting, overfitting, Random Forest and an introduction to boosting/AdaBoost | Tree and ensemble comparison notebook |
| 7 | Train/validation/test workflow, cross-validation, data leakage, preprocessing pipelines and basic model selection; optional introduction to K-Means/PCA only after core checkpoints | Reproducible model comparison report |
| 8 | CampusFix mini-capstone: define the problem, prepare permitted data, build a baseline, train/evaluate a text classifier and document limitations | Working, documented mini-project with evaluation report |

## How to study each topic

Use the same learning loop for every major concept:

1. Understand the problem the algorithm solves.
2. Build an intuition using a small example or visual.
3. Learn only the maths needed to understand that idea.
4. Follow the relevant section of the primary ML video.
5. Implement and experiment in Python using scikit-learn.
6. Evaluate the result and inspect mistakes.
7. Write a short explanation in your own words and complete the checkpoint.

Do not copy code without understanding what the inputs, outputs and important steps mean. From-scratch implementations are optional in this accelerated beginner track; prioritize understanding, correct experiments and evaluation.

## Maths — learn alongside ML

Use the maths video as a companion, not as a gate that delays practical ML.

- **Week 1:** Basic arithmetic, reading graphs, mean/median, variance and standard deviation; understand what vectors and matrices represent.
- **Week 2:** Vectors, matrices, dot product, basic probability, conditional probability, Bayes' theorem, derivatives and the intuition behind gradient descent.
- **Weeks 3–8:** Revisit maths only when it is needed for the current ML topic—for example, error/loss for regression, probability for classification, and distance for KNN.

Advanced calculus, matrix calculus and detailed eigenvalue derivations are outside this 8-week foundation.

## Project: CampusFix — campus infrastructure complaint triage

**Problem:** Student reports about Wi-Fi outages, water supply, broken lifts, AC failures and classroom/electrical faults can be difficult to sort consistently.

**Week 8 prototype:** Build a small ML-assisted tool that predicts a complaint category from text and can suggest a department for human review. A human must confirm routing and priority. The system must never auto-close or suppress safety-critical reports.

**Data rules:** First seek permission to use anonymized campus complaints. Remove names, phone numbers, roll numbers and identifying details. If campus data is unavailable, use a documented public complaint/service-request dataset as a proxy and clearly state that it is not campus evidence. Do not fabricate data and present it as real. Document labels, label definitions, class counts, license, limitations and permissions.

**Baseline and model:** Start with a simple keyword/rule or majority-class baseline. Then try TF-IDF + Logistic Regression; Multinomial Naive Bayes is an optional comparison if time permits. Report per-class precision, recall and F1, along with a confusion matrix. Inspect false negatives, especially for urgent categories. Send low-confidence predictions to manual review. Do not claim faster campus response or operational impact without a real pilot and measured evidence.

## Supplementary resources

Use these only when extra explanation or practice is needed.

### Python, data and visualization
- [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X) — sessions 1–12: Python; 13–15: NumPy; 16 onward: pandas.
- [Bro Code NumPy](https://youtu.be/VXU4LSAQDSc)
- [Bro Code pandas](https://youtu.be/VXtjG_GzO7Q)
- [Bro Code Matplotlib](https://youtu.be/c9vhHUGdav0)
- [CampusX data cleaning, Session 28](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2)
- [Krish Naik EDA and Feature Engineering](https://youtu.be/fHFOANOHwh8)

### Complete supplementary ML playlists
- [CampusX — Machine Learning complete playlist](https://youtube.com/playlist?list=PLKnIA16_Rmvbr7zKYQuBfsVkjoLcJgxHH&si=vLWpBfFztXIrFY5A)
- [StatQuest — Machine Learning complete playlist](https://youtube.com/playlist?list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&si=Uck5deAI2vq0Jhjg)

These are complete reference playlists. They are supplementary—not mandatory to finish within the 8-week schedule. Use topic-wise when you need another explanation or deeper practice.

### Regression and regularization
- [StatQuest Linear Regression and Linear Models playlist](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU)
- [Regression metrics: MSE, MAE, RMSE, R², adjusted R²](https://youtu.be/Ti7c-Hz7GSM)
- Main ML course sections: Gradient Descent 09:50; Linear Regression 27:13; R² 44:55; Multiple Regression 52:47.

Ridge and Lasso are useful follow-up topics after the 8-week foundation; they are not required for the Week 4 checkpoint.

### Logistic Regression, metrics and Naive Bayes
- [StatQuest Logistic Regression playlist](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe)
- [Performance metrics: accuracy, precision, recall, F-beta](https://youtu.be/5vqk6HnITko)
- [Confusion matrix and Type I/II errors](https://youtu.be/c09drtuCS3c)
- [Precision, recall and F1](https://youtu.be/iK-kdhJ-7yI)
- [CampusX ROC curve and ROC-AUC](https://youtu.be/gdW6hj9IXaA)
- [StatQuest Confusion Matrix](https://youtu.be/Kdsp6soqA7o)
- [StatQuest Naive Bayes](https://youtu.be/O2L2Uv9pdDA)

Main ML course sections: Logistic Regression 2:15:32; precision/recall 2:54:17; ROC-AUC 5:07:18; Naive Bayes 5:52:16. Learn the core Naive Bayes intuition from the supplementary explanation if the course's later placement interrupts the weekly sequence.

### KNN, Decision Trees and Ensembles
- [CampusX KNN overview](https://youtu.be/abnL_GUGub4)
- Main ML course: KNN 3:06:38; Decision Trees 3:39:55 and 3:58:05; Random Forest 4:18:01; boosting 4:34:20.
- [StatQuest Ensemble Learning playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd)
- [StatQuest Random Forests Part 1](https://youtu.be/J4Wdy0Wc_xQ)
- [StatQuest AdaBoost](https://youtu.be/LsK-xG1cLYA)

### Validation and model selection
- [StatQuest Bias and Variance](https://youtu.be/EuBBz3bI-aA)
- [StatQuest Cross Validation](https://youtu.be/fSytzGwwBVw)
- [scikit-learn cross-validation documentation](https://scikit-learn.org/stable/modules/cross_validation.html)
- [scikit-learn Pipeline documentation](https://scikit-learn.org/stable/modules/compose.html)

### Optional preview: unsupervised learning
Only explore these after completing the required Week 1–8 checkpoints.
- [Unsupervised ML tutorial: K-Means, DBSCAN and Hierarchical Clustering](https://youtu.be/Aa4MACKaDC0)
- Main ML course: PCA 6:12:25; K-Means 6:48:13.

## Topics deliberately deferred to the continuation track

These are valuable, but they should not be squeezed into the beginner 8-week foundation:

- Ridge/Lasso in depth, polynomial regression and advanced feature selection.
- SVM, detailed boosting/XGBoost and advanced hyperparameter optimization.
- K-Means, DBSCAN and PCA in depth.
- Neural networks, backpropagation derivations and PyTorch.
- Transformers, NLP in depth, LLMs, RAG and agents.
- Production engineering: advanced testing, FastAPI deployment, Docker, CI/CD, monitoring and model lifecycle management.

Complete the foundation first, then choose a continuation track based on the projects or internship role you are targeting.

## Completion criteria

By the end of Week 8, you should be able to:

- Explain the basic ML workflow: problem definition, data preparation, train/test split, model training, evaluation and iteration.
- Work with Python, NumPy and pandas for a small dataset.
- Perform basic data cleaning and EDA.
- Explain the purpose of Linear Regression, Logistic Regression, Naive Bayes, KNN, Decision Trees and Random Forest.
- Choose and interpret basic regression and classification metrics.
- Recognize data leakage and use a basic validation workflow correctly.
- Complete and document a small baseline-first ML project with a clear evaluation and limitations.

**Important:** 80 hours is an accelerated foundation, not a promise of ML mastery or job readiness. Beginners may need more than 8 calendar weeks. Understanding and being able to reproduce the work matters more than finishing on schedule.
