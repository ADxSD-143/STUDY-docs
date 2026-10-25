# 24-Week Machine Learning Roadmap
**Flow:** Maths → Python → Data → ML → Real-world Project  
**Duration:** 24 weeks × 10 hours/week = 240 hours.  
**Weekly split:** 3 h focused learning, 5 h coding/experiments/project, 2 h revision and notes. One notebook/script each week (2–4 h, included in the weekly total). Diagnose existing Python/NumPy/pandas knowledge and skip material already mastered.

## 24-week schedule

| Week | Focus | Deliverable |
|---|---|---|
| 1 | Maths/Python diagnostic: vectors, matrices, probability/statistics, derivatives; Python, NumPy, pandas; Git/GitHub | Diagnostic notebook and gap list |
| 2 | Data cleaning, missing values, duplicates, outliers, categorical encoding, splitting and leakage basics | Clean real dataset notebook |
| 3 | EDA, visualization, feature engineering, preprocessing | EDA report; milestone review |
| 4 | Linear Regression, loss, gradient descent, assumptions, MAE/MSE/RMSE/R² | Linear Regression from scratch vs scikit-learn |
| 5 | Bias–variance, Ridge/Lasso, scaling, polynomial features | Regularization comparison |
| 6 | Logistic Regression, sigmoid, log loss, probabilities, threshold | Logistic Regression from scratch; CampusFix baseline starts |
| 7 | Confusion matrix, precision/recall/F1, specificity, FPR/FNR, ROC-AUC, PR-AUC, imbalance | Classifier evaluation and error review |
| 8 | Naive Bayes immediately after Logistic Regression; KNN, distances, scaling | Naive Bayes and KNN practice; milestone review |
| 9 | Decision Trees: splits, Gini/entropy, depth and overfitting | Small Decision Tree implementation |
| 10 | Random Forest, bagging/boosting/AdaBoost, GridSearchCV/RandomizedSearchCV | Tuned model comparison |
| 11 | SVM: margins, support vectors, polynomial/RBF kernels | Compare SVM against earlier models |
| 12 | Cross-validation, leakage review, model selection, calibration, cost-sensitive thresholds, error analysis | Reproducible comparison report; milestone review |
| 13 | K-Means from scratch, elbow method, DBSCAN | Clustering notebook; StuCore project starts |
| 14 | PCA, silhouette score, clustering interpretation | Finish clustering project; milestone review |
| 15 | Neural networks, perceptrons, layers, activations and loss | Small neural-network experiment |
| 16 | Forward/backpropagation, gradient descent and optimizers | Training experiment with learning curves |
| 17 | PyTorch tensors, Dataset/DataLoader, model and training loop | Small reproducible PyTorch model |
| 18 | Overfitting, regularization, early stopping, diagnostics | Training comparison; milestone review |
| 19 | Pipelines, reusable modules, reproducibility and pytest | Refactor earlier model into tested code |
| 20 | Model persistence, FastAPI, input validation, Docker | Local prediction API and run instructions |
| 21 | Capstone problem, data access/licensing, target, baseline and metrics | Problem brief and evaluation plan |
| 22 | Capstone implementation: data pipeline, baseline, feature work | Reproducible training pipeline |
| 23 | Model comparison, error analysis, API/UI integration and tests | Working MVP |
| 24 | Final held-out evaluation, docs, demo and portfolio polish | Final report/demo; milestone review |

**Milestone reviews:** Weeks 3, 8, 12, 14, 18, 24. Explain an algorithm without notes, rerun old work cleanly, verify baseline/metrics/leakage/errors, and update progress. Preprocessing must be fit only on training data; keep the final test set untouched until final evaluation. Compare from-scratch implementations with scikit-learn where applicable. If behind, use review/light weeks; do not silently exceed 10 hours/week. Deep learning is intentionally limited if capstone work needs the time.

## Real-world project: CampusFix — campus infrastructure complaint triage

**Problem:** Student reports about Wi-Fi outages, water supply, broken lifts, AC failures, and classroom/electrical faults can be difficult to sort, route and prioritize consistently.

**Prototype:** A small ML-assisted tool predicts complaint category and responsible department, suggests a review priority, and shows trends only when the data supports them. A human confirms routing and priority; the system never auto-closes or suppresses safety-critical reports.

**Data rules:** First seek permission to use anonymized campus complaints. Remove names, phone numbers, roll numbers, and identifying details. If campus data is unavailable, use a documented public complaint/service-request dataset as a proxy and clearly say it is not campus evidence. Do not fabricate synthetic data and present it as real. Document labels, label definitions, class counts, license, limitations, and consent/permissions.

**Schema (only permitted fields):** complaint text, category, department, priority, optional coarse location, and date if allowed. Avoid personal identifiers.

**ML plan:** Start with a keyword/rule baseline and majority-class baseline; then TF-IDF + Logistic Regression and/or Naive Bayes. Compare per-class precision/recall/F1 and confusion matrix. Inspect false negatives, especially for urgent categories. Route low-confidence predictions to manual review. Prevent duplicate/near-duplicate complaints from crossing train/test. Use chronological split only if suitable timestamps and enough data exist; otherwise use an appropriate stratified split. Do not claim faster campus response without a real pilot and measured evidence.

**Project schedule:** Data exploration Weeks 2–3; text classification baseline Weeks 6–8; evaluation/tuning Weeks 10–12; API/testing Weeks 19–20; capstone build/evaluation Weeks 21–24. This is a prototype unless a real campus stakeholder agrees to pilot it.

## Resources — use topic-wise, preserve all learner-provided links

### Maths
- [Data Dissection — Complete Math for ML and AI (~8h20)](https://youtu.be/cO9xmfsJJu4) — probability/statistics, Bayes, distributions, linear algebra, derivatives. Watch only gaps.
- [Data Dissection — Complete ML course in Hindi (~10h48)](https://youtu.be/trsyTEA22Gw) — master course used across topics.

### Python, data and visualization
- [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X)
- [Bro Code NumPy](https://youtu.be/VXU4LSAQDSc)
- [Bro Code pandas](https://youtu.be/VXtjG_GzO7Q)
- [Bro Code Matplotlib](https://youtu.be/c9vhHUGdav0)
- [Sheryians AI School visualization](https://youtu.be/-jTD74eEy2I) — Matplotlib, Seaborn, Plotly, IPL project
- [CampusX data assessing/cleaning, Session 28](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2)
- [Krish Naik EDA and Feature Engineering](https://youtu.be/fHFOANOHwh8)

### Regression and regularization
- [StatQuest Linear Regression and Linear Models playlist](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU)
- [Regression metrics: MSE, MAE, RMSE, R², adjusted R²](https://youtu.be/Ti7c-Hz7GSM)
- [CampusX Regularization playlist](https://youtube.com/playlist?list=PLKnIA16_RmvZuSEZ24Wlm13QpsfLlJBM4)
- Master course chapters: Linear Regression 27:13; R² 44:55; multiple regression 52:47; assumptions 1:13:19; polynomial regression 1:26:15; bias–variance 1:41:46; regularization/hyperparameter discussion 1:56:52.

### Logistic Regression, metrics and Naive Bayes
- [StatQuest Logistic Regression playlist](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe)
- [Performance metrics: accuracy, precision, recall, F-beta](https://youtu.be/5vqk6HnITko)
- [Accuracy, confusion matrix, Type I/II errors — Part 1](https://youtu.be/c09drtuCS3c)
- [Precision, recall and F1 — Part 2](https://youtu.be/iK-kdhJ-7yI)
- [CampusX ROC curve and ROC-AUC](https://youtu.be/gdW6hj9IXaA)
- [StatQuest Confusion Matrix](https://youtu.be/Kdsp6soqA7o)
- [StatQuest Naive Bayes](https://youtu.be/O2L2Uv9pdDA)
- [StatQuest encoding: One-Hot, Label, Target and K-Fold Target Encoding](https://youtu.be/589nCGeWG1w)
- Master course: Logistic Regression 2:15:32; precision/recall 2:54:17; ROC-AUC 5:07:18; Naive Bayes 5:52:16 and tuning 6:02:45. Teach Naive Bayes directly after Logistic Regression even though it appears later in the video.

### KNN, Decision Trees and Ensembles
- [CampusX KNN overview](https://youtu.be/abnL_GUGub4)
- Master course KNN 3:06:38; distance/cosine similarity 3:25:06; decision trees 3:39:55 and 3:58:05; tree hyperparameters 4:09:25; Random Forest 4:18:01; boosting 4:34:20.
- [StatQuest Ensemble Learning playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd)
- [CampusX Ensemble Learning playlist](https://youtube.com/playlist?list=PLnD9uS5lPM6l3oB5aPLTA8uUTayvLDF5T)
- [StatQuest Random Forests Part 1](https://youtu.be/J4Wdy0Wc_xQ)
- [StatQuest Random Forests Part 2: missing data and clustering](https://youtu.be/mIlw5j3WyVk)
- [StatQuest AdaBoost](https://youtu.be/LsK-xG1cLYA)

### Validation, evaluation and tuning
- [StatQuest Bias and Variance](https://youtu.be/EuBBz3bI-aA)
- [StatQuest Cross Validation](https://youtu.be/fSytzGwwBVw) — this URL was supplied twice; listed once.
- [Krish Naik types of cross-validation](https://youtu.be/bq4LytNAjjM)
- [Optuna: hyperparameter tuning and Bayesian optimization](https://youtu.be/E2b3SKMw934)
- [scikit-learn cross-validation docs](https://scikit-learn.org/stable/modules/cross_validation.html)
- [GridSearchCV docs](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)
- [RandomizedSearchCV docs](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html)
- [Calibration docs](https://scikit-learn.org/stable/modules/calibration.html)

### SVM
- [StatQuest SVM Part 1: Main Ideas](https://youtu.be/efR1C6CvhmE)
- [StatQuest SVM Part 2: Polynomial Kernel](https://youtu.be/Toet3EiSFcM)
- [StatQuest SVM Part 3: RBF Kernel](https://youtu.be/Qc5IyLW_hns)
- [CampusX SVM playlist](https://youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL)
- Master course: SVM 5:20:59; primal/dual 5:34:49; RBF kernel 5:46:25.

### Unsupervised learning
- [Complete Unsupervised ML tutorial in Hindi: K-Means, DBSCAN, Hierarchical Clustering](https://youtu.be/Aa4MACKaDC0)
- Master course: PCA 6:12:25; unsupervised overview 6:35:30; K-Means 6:48:13; hierarchical clustering 7:10:23; DBSCAN 7:22:01.

### Deep learning
- Master course: neural-network intro 7:46:14; perceptron 7:53:09; backpropagation 8:12:26; neural networks from scratch 8:30:19 onward; TensorFlow/Keras 9:25:45 onward.
- Prefer a small reproducible PyTorch exercise; deep learning must not consume the capstone block.

### Engineering
- [scikit-learn Pipelines and composite estimators](https://scikit-learn.org/stable/modules/compose.html)
- [pytest documentation](https://docs.pytest.org/)
- [FastAPI tutorial](https://fastapi.tiangolo.com/tutorial/)
- [Docker getting started](https://docs.docker.com/get-started/)
- [scikit-learn model persistence](https://scikit-learn.org/stable/model_persistence.html)

### Supplied links awaiting title verification
Keep these in the resource inventory and verify their content before assigning them; they are not discarded:
- https://youtu.be/_L39rN6gz7Y
- https://youtu.be/wpNl-JwwplA
- https://youtu.be/g9c66TUylZ4
- https://youtu.be/D0efHEJsfHo

## Final completion criteria
- Implement from scratch: Linear Regression, Logistic Regression, KNN, Naive Bayes, Decision Tree and K-Means.
- Complete EDA, regression/classification evaluation, tuning and clustering notebooks.
- Deliver CampusFix or a comparable stakeholder-backed real-world capstone with a baseline, held-out evaluation, error analysis and clear limitations.
- Use reproducible project structure, tests and (if feasible) a containerized API.
- Document sources, licensing, assumptions, class imbalance, privacy safeguards and what the evaluation does not prove.
