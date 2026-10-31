# Core Machine Learning — Weeks 4–7

This phase covers workflow Stages 6–11: baseline, modeling, evaluation, tuning, error analysis and packaging. The complete checklist is [End-to-End ML Project Workflow](../../06-reference/ml-project-workflow.md).

Use the two fixed primary videos: [Main ML course](https://youtu.be/trsyTEA22Gw) and [Math for ML](https://youtu.be/cO9xmfsJJu4). Follow assigned timestamps. Complete reference playlists are supplementary, not mandatory to finish end-to-end:
- [CampusX — Complete Machine Learning playlist](https://youtube.com/playlist?list=PLKnIA16_Rmvbr7zKYQuBfsVkjoLcJgxHH&si=vLWpBfFztXIrFY5A)
- [StatQuest — Complete Machine Learning playlist](https://youtube.com/playlist?list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&si=Uck5deAI2vq0Jhjg)

For each topic: understand intuition, watch the assigned section, write notes, code, run an experiment, evaluate and pass the checkpoint.

## Week 4 — Baseline, Linear Regression and Logistic Regression (Stages 6–7)
- Main course: Linear Regression 27:13, R² 44:55, multiple regression 52:47; Logistic Regression 2:15:32.
- Learn baseline predictors, features/target, coefficients, residuals, MAE/MSE/RMSE, R², classification vs regression, sigmoid and predicted probabilities.
- Code: compare a simple baseline with Linear Regression and Logistic Regression on suitable small datasets.
- Checkpoint: explain why the baseline matters, regression vs classification, and why logistic regression outputs probabilities.

## Week 5 — Classification metrics, Naive Bayes and KNN (Stages 7–8)
- Watch [confusion matrix](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA) → [Naive Bayes](https://youtu.be/O2L2Uv9pdDA) → [KNN](https://youtu.be/abnL_GUGub4).
- Learn TP/FP/TN/FN, precision, recall, F1, threshold, Naive Bayes assumption, KNN distance and scaling. Understand why accuracy alone can mislead on imbalanced data.
- Code: compare Logistic Regression, Naive Bayes and scaled KNN on the same dataset. Explain why the selected metric fits the task.
- Checkpoint: interpret a confusion matrix, explain precision vs recall and why KNN is sensitive to feature scale.

## Week 6 — Decision Trees, ensembles and error analysis (Stages 7–8, 10)
- Main course Decision Tree sections 3:39:55 and 3:58:05; then [Random Forest](https://youtu.be/J4Wdy0Wc_xQ), [AdaBoost](https://youtu.be/LsK-xG1cLYA) and [bias–variance](https://youtu.be/EuBBz3bI-aA).
- Learn tree splits, Gini/entropy intuition, depth, overfitting, bagging vs boosting and Random Forest.
- Code: compare baseline, tree and Random Forest; inspect training vs validation scores across tree depths.
- Inspect false positives/false negatives and examples where the model performs poorly.
- Checkpoint: explain overfitting, bagging vs boosting and one concrete model failure.

## Week 7 — Validation, tuning basics and packaging (Stages 8–11)
- Watch [StatQuest cross-validation](https://youtu.be/fSytzGwwBVw); read [CV guide](https://scikit-learn.org/stable/modules/cross_validation.html), [Pipeline guide](https://scikit-learn.org/stable/modules/compose.html) and [model persistence](https://scikit-learn.org/stable/model_persistence.html).
- Learn train/validation/test roles, k-fold CV, stratification, leakage, train-only preprocessing and why test data must not be used for tuning.
- Code: build a preprocessing/model Pipeline, compare at least three models with CV, perform a small GridSearchCV or RandomizedSearchCV experiment, and save/reload the best pipeline.
- Keep the test set for final evaluation; report its score once after model selection.
- Checkpoint: explain leakage, cross-validation and why repeated test-set tuning is unreliable.

## Optional introduction and continuation
- Intro only if core work is complete: K-Means (main course 6:48:13), PCA (6:12:25), Ridge/Lasso, SVM intuition and boosting.
- Continuation: XGBoost/LightGBM/CatBoost, DBSCAN, Optuna, SHAP, calibration in depth, MLflow and advanced feature selection.
- Neural networks, PyTorch and deep learning are separate follow-on topics.

From-scratch implementations are useful learning exercises, but in this accelerated path prioritize correct baselines, leakage-safe experiments, evaluation and error analysis over implementing every algorithm from scratch.