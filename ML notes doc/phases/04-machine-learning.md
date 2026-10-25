# Phase 4 — Machine Learning (Weeks 6–17)

## Week 6 — Linear Regression
1. Master ML course: 27:13 Linear Regression, 44:55 R², 52:47 multiple regression; assumptions 1:13:19 if time.
2. [StatQuest Linear Regression/Linear Models playlist](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU).
3. [Regression metrics](https://youtu.be/Ti7c-Hz7GSM).
Code: implement simple linear regression and loss with NumPy, then compare to scikit-learn. Deliverable: from-scratch model and metric comparison.

## Week 7 — Regularization
1. [CampusX Regularization playlist](https://youtube.com/playlist?list=PLKnIA16_RmvZuSEZ24Wlm13QpsfLlJBM4).
2. Master course bias-variance 1:41:46 and regularization/hyperparameter discussion 1:56:52.
Code: compare Linear/Ridge/Lasso with scaled features and validation. Deliverable: metrics and overfitting explanation.

## Week 8 — Logistic Regression
1. [StatQuest Logistic Regression playlist](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe).
2. Master course at 2:15:32.
Code sigmoid, log loss and gradient descent; compare with sklearn. Deliverable: Logistic Regression from scratch.

## Week 9 — Classification evaluation
Watch: [performance metrics](https://youtu.be/5vqk6HnITko) → [confusion matrix/Type I-II errors](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [StatQuest confusion matrix](https://youtu.be/Kdsp6soqA7o) → [CampusX ROC-AUC](https://youtu.be/gdW6hj9IXaA). Master chapters: 2:54:17 and 5:07:18.
Deliverable: confusion matrix, precision, recall, F1, specificity, FPR/FNR, ROC-AUC/PR-AUC and threshold interpretation.

## Week 10 — Naive Bayes, then KNN
1. [Naive Bayes](https://youtu.be/O2L2Uv9pdDA), master 5:52:16 and tuning 6:02:45.
2. Immediately after NB: [CampusX KNN](https://youtu.be/abnL_GUGub4), master 3:06:38 and distances 3:25:06.
3. [Encoding video](https://youtu.be/589nCGeWG1w); target encoding must be leakage-safe inside folds.
Deliverable: KNN and a simple NB implementation from scratch, then compare with sklearn.

## Week 11 — Decision Trees
Master chapters 3:39:55 and 3:58:05; hyperparameters 4:09:25. Code entropy/Gini examples, train a sklearn tree and compare depth vs validation performance.

## Week 12 — Ensembles
Watch [StatQuest ensemble playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd), [CampusX ensemble playlist](https://youtube.com/playlist?list=PLnD9uS5lPM6l3oB5aPLTA8uUTayvLDF5T), [Random Forest Part 1](https://youtu.be/J4Wdy0Wc_xQ), [Part 2](https://youtu.be/mIlw5j3WyVk), [AdaBoost](https://youtu.be/LsK-xG1cLYA). Master chapters 4:18:01 and 4:34:20.
Deliverable: compare tree, Random Forest and boosting with baseline.

## Week 13 — Cross-validation and leakage
Watch [StatQuest CV](https://youtu.be/fSytzGwwBVw) → [Krish Naik CV types](https://youtu.be/bq4LytNAjjM); read [scikit-learn CV docs](https://scikit-learn.org/stable/modules/cross_validation.html). Revisit encoding video if needed.
Deliverable: pipeline and experiment demonstrating validation variability and train-only preprocessing.

## Week 14 — Tuning and decision quality
Read [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) and [RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html). Review [bias-variance](https://youtu.be/EuBBz3bI-aA), [calibration](https://scikit-learn.org/stable/modules/calibration.html), threshold and cost trade-offs. [Optuna](https://youtu.be/E2b3SKMw934) is optional after basic tuning.
Deliverable: model-selection report and error analysis.

## Week 15 — SVM
Watch [Part 1: main ideas](https://youtu.be/efR1C6CvhmE) → [Part 2: polynomial kernel](https://youtu.be/Toet3EiSFcM) → [Part 3: RBF kernel](https://youtu.be/Qc5IyLW_hns); supplement with [CampusX SVM playlist](https://youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL). Master SVM 5:20:59, primal/dual 5:34:49, RBF 5:46:25.
Deliverable: scaled SVM comparison and conceptual explanation.

## Week 16 — Unsupervised learning
Watch [Complete Unsupervised ML in Hindi](https://youtu.be/Aa4MACKaDC0). Master chapters: overview 6:35:30; K-Means 6:48:13; hierarchical 7:10:23; DBSCAN 7:22:01.
Deliverable: K-Means from scratch, elbow and silhouette discussion, clustering report.

## Week 17 — PCA and neural-network intro
Master chapters: PCA 6:12:25; neural-network intro 7:46:14; perceptron 7:53:09; softmax 8:04:02; backprop 8:12:26; from-scratch sections 8:30:19 onward. Supplement with [supplied neural network playlist](https://youtube.com/playlist?list=PLlpUUtQ9RrF47CpLH6PSFL2oeP3izPMhE).
Deliverable: PCA explained variance and a small neural-network notebook. Keep this block bounded so capstone time remains protected.
