# ML Resource Library
Resources are grouped by topic and assigned in the [8-week roadmap](roadmap.md). The two fixed primary videos are the [main ML course](https://youtu.be/trsyTEA22Gw) and [Math for ML](https://youtu.be/cO9xmfsJJu4). All other videos are supplementary; follow only the sections assigned in the roadmap rather than watching every playlist end-to-end.

## Resources mapped to the Stage 0–13 project workflow

The complete [ML project workflow checklist](ml-project-workflow.md) defines what to do at each stage. Use these official/free references as needed; they are a library, not a requirement to study every tool in the 8-week sprint.

| Workflow stage | Resource |
|---|---|
| Stage 0 — Problem framing and metrics | [scikit-learn model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html) |
| Stage 1 — Data collection and SQL | [Kaggle Learn: Intro to SQL](https://www.kaggle.com/learn/intro-to-sql), [Hugging Face Datasets](https://huggingface.co/docs/datasets/index) |
| Stage 2 — EDA | [Pandas user guide](https://pandas.pydata.org/docs/user_guide/index.html), [Seaborn tutorial](https://seaborn.pydata.org/tutorial.html) |
| Stage 3–4 — Split, preprocessing and leakage-safe pipelines | [scikit-learn preprocessing](https://scikit-learn.org/stable/modules/preprocessing.html), [Pipeline and ColumnTransformer](https://scikit-learn.org/stable/modules/compose.html), [data leakage pitfalls](https://scikit-learn.org/stable/common_pitfalls.html#data-leakage) |
| Stage 5 — Feature engineering | [scikit-learn feature selection](https://scikit-learn.org/stable/modules/feature_selection.html), [mutual information](https://scikit-learn.org/stable/modules/feature_selection.html#univariate-feature-selection) |
| Stage 6–7 — Baselines and models | [Dummy estimators](https://scikit-learn.org/stable/api/sklearn.dummy.html), [scikit-learn supervised learning](https://scikit-learn.org/stable/supervised_learning.html) |
| Stage 8 — Evaluation and validation | [Model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html), [cross-validation](https://scikit-learn.org/stable/modules/cross_validation.html), [calibration](https://scikit-learn.org/stable/modules/calibration.html) |
| Stage 9 — Hyperparameter tuning | [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html), [RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html), [Optuna](https://optuna.org/) |
| Stage 10 — Interpretation and error analysis | [Permutation importance](https://scikit-learn.org/stable/modules/permutation_importance.html), [SHAP documentation](https://shap.readthedocs.io/en/latest/) |
| Stage 11 — Packaging and reproducibility | [Model persistence](https://scikit-learn.org/stable/model_persistence.html), [joblib](https://joblib.readthedocs.io/en/latest/) |
| Stage 12 — Deployment | [FastAPI tutorial](https://fastapi.tiangolo.com/tutorial/), [Docker getting started](https://docs.docker.com/get-started/), [Streamlit](https://docs.streamlit.io/) |
| Stage 13 — Monitoring and experiment tracking | [Evidently documentation](https://docs.evidentlyai.com/), [MLflow tracking](https://mlflow.org/docs/latest/ml/tracking/) |

**Learning order:** first understand the stage and complete the core scikit-learn implementation. Add advanced tools such as DVC, Optuna, SHAP, MLflow, Docker and monitoring only when a project genuinely needs them. Check current hosting free-tier limits before planning a deployment.

## Complete ML playlists (supplementary)
- [CampusX — Machine Learning complete playlist](https://youtube.com/playlist?list=PLKnIA16_Rmvbr7zKYQuBfsVkjoLcJgxHH&si=vLWpBfFztXIrFY5A)
- [StatQuest — Machine Learning complete playlist](https://youtube.com/playlist?list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&si=Uck5deAI2vq0Jhjg)

Use these as full topic-wise reference libraries when you need another explanation or deeper practice. They are not extra mandatory playlists for the 8-week schedule.

## Maths
- [Data Dissection — Complete Math for ML and AI (~8h20)](https://youtu.be/cO9xmfsJJu4): probability/statistics, Bayes, distributions, linear algebra and calculus. Use targeted sections after diagnostic.
- [Data Dissection — Complete ML Course in Hindi (~10h48)](https://youtu.be/trsyTEA22Gw): master course; use chapter timestamps in roadmap.

## Python, data, visualization
- [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X): Python sessions 1–12, NumPy 13–15, pandas from 16 onward.
- [Bro Code NumPy](https://youtu.be/VXU4LSAQDSc)
- [Bro Code pandas](https://youtu.be/VXtjG_GzO7Q)
- [Bro Code Matplotlib](https://youtu.be/c9vhHUGdav0)
- [Sheryians AI School visualization](https://youtu.be/-jTD74eEy2I): Matplotlib, Seaborn, Plotly and IPL mini-project.
- [CampusX Data Assessing/Cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2)
- [Krish Naik EDA and Feature Engineering](https://youtu.be/fHFOANOHwh8)

## Regression and regularization
- [StatQuest Linear Regression and Linear Models playlist](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU)
- [Regression metrics: MSE, MAE, RMSE, R², adjusted R²](https://youtu.be/Ti7c-Hz7GSM)
- [CampusX Regularization playlist](https://youtube.com/playlist?list=PLKnIA16_RmvZuSEZ24Wlm13QpsfLlJBM4)
- Master chapters: gradient descent 09:50; regression 27:13; R² 44:55; multiple regression 52:47; assumptions 1:13:19; polynomial regression 1:26:15; bias-variance 1:41:46; regularization/hyperparameter discussion 1:56:52.

## Logistic Regression, classification metrics, Naive Bayes
- [StatQuest Logistic Regression playlist](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe)
- [Accuracy, precision, recall, F-beta](https://youtu.be/5vqk6HnITko)
- [Confusion matrix and Type I/II errors](https://youtu.be/c09drtuCS3c)
- [Precision, recall and F1](https://youtu.be/iK-kdhJ-7yI)
- [CampusX ROC curve and ROC-AUC](https://youtu.be/gdW6hj9IXaA)
- [StatQuest Confusion Matrix](https://youtu.be/Kdsp6soqA7o)
- [StatQuest Naive Bayes](https://youtu.be/O2L2Uv9pdDA)
- [One-Hot, Label, Target and K-Fold Target Encoding](https://youtu.be/589nCGeWG1w)
- Master chapters: Logistic Regression 2:15:32; mini project 2:29:57; precision/recall 2:54:17; ROC-AUC 5:07:18; Naive Bayes 5:52:16; tuning Naive Bayes 6:02:45.
- Course sequencing rule: teach Naive Bayes immediately after Logistic Regression even though it appears later in the master video.

## KNN, trees and ensembles
- [CampusX KNN](https://youtu.be/abnL_GUGub4)
- Master chapters: KNN 3:06:38; KNN bias-variance 3:17:32; cosine similarity/distances 3:25:06; SMOTE 3:32:54 (only use correctly inside training folds); Decision Tree parts 3:39:55 and 3:58:05; tree hyperparameters 4:09:25; Random Forest 4:18:01; boosting 4:34:20.
- [StatQuest Ensemble Learning playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd)
- [CampusX Ensemble Learning playlist](https://youtube.com/playlist?list=PLnD9uS5lPM6l3oB5aPLTA8uUTayvLDF5T)
- [Random Forest Part 1](https://youtu.be/J4Wdy0Wc_xQ)
- [Random Forest Part 2: missing data and clustering](https://youtu.be/mIlw5j3WyVk)
- [AdaBoost](https://youtu.be/LsK-xG1cLYA)

## Validation and tuning
- [StatQuest Bias and Variance](https://youtu.be/EuBBz3bI-aA)
- [StatQuest Cross Validation](https://youtu.be/fSytzGwwBVw) (duplicate supplied link included once)
- [Krish Naik types of cross-validation](https://youtu.be/bq4LytNAjjM)
- [Optuna Bayesian tuning](https://youtu.be/E2b3SKMw934), optional after grid/random search.
- [Cross-validation docs](https://scikit-learn.org/stable/modules/cross_validation.html)
- [GridSearchCV docs](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)
- [RandomizedSearchCV docs](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html)
- [Calibration docs](https://scikit-learn.org/stable/modules/calibration.html)

## SVM
- [SVM Part 1 — main ideas](https://youtu.be/efR1C6CvhmE)
- [SVM Part 2 — polynomial kernel](https://youtu.be/Toet3EiSFcM)
- [SVM Part 3 — RBF kernel](https://youtu.be/Qc5IyLW_hns)
- [CampusX SVM playlist](https://youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL)
- Master chapters: SVM 5:20:59; primal/dual 5:34:49; RBF 5:46:25.

## Unsupervised learning and PCA
- [Complete Unsupervised ML in Hindi: K-Means, DBSCAN, Hierarchical Clustering](https://youtu.be/Aa4MACKaDC0)
- Master chapters: PCA 6:12:25; unsupervised overview 6:35:30; K-Means 6:48:13; hierarchical 7:10:23; DBSCAN 7:22:01.

## Deep learning
- [Learner-supplied neural network playlist](https://youtube.com/playlist?list=PLlpUUtQ9RrF47CpLH6PSFL2oeP3izPMhE)
- Master chapters: neural network intro 7:46:14; perceptron 7:53:09; softmax 8:04:02; backpropagation 8:12:26; from-scratch parts 8:30:19, 8:46:35, 9:02:48; TensorFlow/Keras 9:25:45.

## Engineering
- [scikit-learn Pipelines](https://scikit-learn.org/stable/modules/compose.html)
- [pytest](https://docs.pytest.org/)
- [FastAPI](https://fastapi.tiangolo.com/tutorial/)
- [Docker getting started](https://docs.docker.com/get-started/)
- [scikit-learn model persistence](https://scikit-learn.org/stable/model_persistence.html)

## Supplied links awaiting title verification
Preserved for follow-up; verify titles/content before assigning them to a topic:
- https://youtu.be/_L39rN6gz7Y
- https://youtu.be/wpNl-JwwplA
- https://youtu.be/g9c66TUylZ4
- https://youtu.be/D0efHEJsfHo
