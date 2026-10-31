# Core Machine Learning — Weeks 4–7

Use the two fixed primary videos: [Main ML course](https://youtu.be/trsyTEA22Gw) and [Math for ML](https://youtu.be/cO9xmfsJJu4). Follow the timestamps below. Other videos are supplements. For each topic: understand intuition, watch the assigned section, write notes, code with scikit-learn, run one experiment and pass the checkpoint. From-scratch implementations are optional in this accelerated beginner track.

## Week 4 — Regression and Logistic Regression
- Main course: Linear Regression 27:13, R² 44:55, multiple regression 52:47; Logistic Regression 2:15:32.
- Learn features/target, coefficients, residuals, MAE/MSE/RMSE, R², classification vs regression, sigmoid and predicted probabilities.
- Code: fit Linear and Logistic Regression with scikit-learn; inspect residuals and probabilities.
- Checkpoint: explain regression vs classification and why logistic regression outputs probabilities.

## Week 5 — Metrics, Naive Bayes and KNN
- Watch [confusion matrix](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA) → [Naive Bayes](https://youtu.be/O2L2Uv9pdDA) → [KNN](https://youtu.be/abnL_GUGub4).
- Learn TP/FP/TN/FN, precision, recall, F1, threshold, Naive Bayes assumption, KNN distance and scaling.
- Code: compare Logistic Regression, Naive Bayes and scaled KNN on the same dataset.
- Checkpoint: explain precision vs recall and why KNN is sensitive to feature scale.

## Week 6 — Decision Trees and ensembles
- Main course decision-tree sections 3:39:55 and 3:58:05; then [Random Forest](https://youtu.be/J4Wdy0Wc_xQ) and [AdaBoost](https://youtu.be/LsK-xG1cLYA). Review [bias–variance](https://youtu.be/EuBBz3bI-aA) if needed.
- Learn tree splits, Gini/entropy intuition, depth, overfitting, bagging vs boosting and Random Forest.
- Code: compare baseline, tree and Random Forest; inspect training vs validation score across tree depths.
- Checkpoint: explain overfitting and bagging vs boosting.

## Week 7 — Validation, leakage and model selection
- Watch [StatQuest cross-validation](https://youtu.be/fSytzGwwBVw); read [CV guide](https://scikit-learn.org/stable/modules/cross_validation.html) and [Pipeline guide](https://scikit-learn.org/stable/modules/compose.html).
- Learn train/validation/test roles, k-fold CV, stratification, leakage and train-only preprocessing.
- Code: build a preprocessing/model Pipeline and compare at least three models with CV. Keep the test set for final evaluation.
- Checkpoint: explain why preprocessing before splitting can leak information and why repeated test-set tuning is unreliable.

## Optional after the core
K-Means (main course 6:48:13) and PCA (6:12:25). SVM, detailed boosting, neural networks and deep learning are deferred to the next track.