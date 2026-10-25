# Phase 4 — Machine Learning (Weeks 6–17)

**Designed for:** a learner who has completed Python and data preparation, but has never studied ML. If you do not understand features, targets, train/test split, or basic plots yet, revisit Phase 3 first.

**Fixed primary videos:** [Main ML course](https://youtu.be/trsyTEA22Gw) and [Math for ML](https://youtu.be/cO9xmfsJJu4). The main course is followed by timestamps listed below; the maths course is a companion, not something you must finish in full before starting ML. Other videos are supplements only.

**Weekly loop:** intuition → relevant video section → notes in your own words → code with scikit-learn → small experiment → checkpoint. Implementing every algorithm from scratch is not required; the roadmap marks it as optional when it would distract from understanding.

## Week 6 — Linear Regression
- Watch: main ML course at 27:13 (Linear Regression), 44:55 (R²), and 52:47 (multiple regression). Use [StatQuest Linear Models](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU) if the explanation is unclear.
- Learn: features/target, coefficients, predictions, residuals, MAE/MSE/RMSE and R².
- Code: plot feature vs target → fit scikit-learn Linear Regression → inspect residuals → implement simple linear regression with NumPy if ready.
- Deliverable: notebook with baseline, metrics, residual plot and plain-English interpretation.
- Checkpoint: explain slope, residual and why R² alone is not enough.

## Week 7 — Overfitting, Ridge and Lasso
- Watch: [bias–variance explanation](https://youtu.be/EuBBz3bI-aA), then [CampusX Regularization playlist](https://youtube.com/playlist?list=PLKnIA16_RmvZuSEZ24Wlm13QpsfLlJBM4). Main course sections: bias–variance 1:41:46 and regularization 1:56:52.
- Learn: overfitting vs underfitting, penalty intuition, L1 vs L2 and why feature scaling matters.
- Code: compare Linear Regression, Ridge and Lasso with a consistent validation setup.
- Deliverable: model comparison and training-vs-validation plot.
- Checkpoint: explain how a model can perform well on training data but poorly on unseen data.

## Week 8 — Logistic Regression
- Watch: [StatQuest Logistic Regression playlist](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe); main course section at 2:15:32.
- Learn in order: classification vs regression → sigmoid intuition → predicted probability → threshold → log-loss intuition.
- Code: train scikit-learn Logistic Regression, inspect probabilities, change threshold and plot a confusion matrix. Sigmoid/log-loss from scratch is an extension.
- Deliverable: binary classifier notebook and short error review.
- Checkpoint: explain why Logistic Regression is used for classification.

## Week 9 — Classification metrics
- Watch in order: [metrics overview](https://youtu.be/5vqk6HnITko) → [confusion matrix and type errors](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [StatQuest confusion matrix](https://youtu.be/Kdsp6soqA7o) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA).
- Learn: TP/FP/TN/FN, accuracy, precision, recall, specificity, F1, FPR/FNR and threshold trade-offs. Study ROC-AUC/PR-AUC after these basics.
- Code: calculate metrics, compare two thresholds and explain which error matters most for your problem.
- Deliverable: metric report and threshold justification.
- Checkpoint: explain why accuracy can mislead on imbalanced data.

## Week 10 — Naive Bayes and KNN
- Part A: watch [Naive Bayes](https://youtu.be/O2L2Uv9pdDA), then fit a scikit-learn model. Learn the conditional-independence assumption intuitively.
- Part B: watch [CampusX KNN](https://youtu.be/abnL_GUGub4). Learn distance, k, and why scaling affects KNN.
- Code: compare both models against a simple baseline on the same dataset; test scaled vs unscaled KNN. From-scratch versions are optional.
- Deliverable: comparison notebook, confusion matrices and model limitations.
- Checkpoint: explain Naive Bayes' assumption and why KNN usually needs scaling.

## Week 11 — Decision Trees
- Watch: main course sections 3:39:55 and 3:58:05; hyperparameters at 4:09:25.
- Learn: root/branch/leaf, decision rules, Gini and entropy intuition, depth and overfitting.
- Code: visualise a shallow scikit-learn tree and compare validation performance across depths. Hand-calculate Gini for one tiny example.
- Deliverable: tree visualisation and depth comparison.
- Checkpoint: explain why an unrestricted tree can overfit.

## Week 12 — Ensembles
- Watch: [StatQuest ensemble playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd), then [Random Forest Part 1](https://youtu.be/J4Wdy0Wc_xQ), [Part 2](https://youtu.be/mIlw5j3WyVk) and [AdaBoost](https://youtu.be/LsK-xG1cLYA). Main course sections: 4:18:01 and 4:34:20.
- Learn: why ensembles help, bagging vs boosting, Random Forest intuition and a high-level view of gradient boosting.
- Code: compare a baseline, tree, Random Forest and one boosting model using the same split and metrics.
- Deliverable: reproducible comparison and trade-off summary.
- Checkpoint: explain bagging vs boosting in plain language.

## Week 13 — Cross-validation and leakage
- Watch: [StatQuest cross-validation](https://youtu.be/fSytzGwwBVw) → [Krish Naik CV types](https://youtu.be/bq4LytNAjjM); read the [scikit-learn guide](https://scikit-learn.org/stable/modules/cross_validation.html).
- Learn: train/validation/test roles, k-fold CV, stratification, leakage, and why preprocessing must be fitted only on training folds.
- Code: build a preprocessing/model Pipeline and compare one split with cross-validation.
- Deliverable: leakage-safe notebook and explanation of one leakage trap.
- Checkpoint: explain why repeatedly selecting models on the test set makes its score unreliable.

## Week 14 — Tuning and model selection
- Read [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html), then [RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html); review [calibration](https://scikit-learn.org/stable/modules/calibration.html).
- Learn: learned parameters vs hyperparameters, baseline-first comparison, small search spaces, calibration intuition and threshold costs. Optuna is optional.
- Code: tune one or two models using CV and evaluate once on the held-out test set.
- Deliverable: model-selection report with baseline, chosen metric, CV results, final test result and errors.
- Checkpoint: explain how you selected a model without tuning against the test set.

## Week 15 — Support Vector Machines
- Watch in order: [SVM main ideas](https://youtu.be/efR1C6CvhmE) → [polynomial kernel](https://youtu.be/Toet3EiSFcM) → [RBF kernel](https://youtu.be/Qc5IyLW_hns). Use the [CampusX SVM playlist](https://youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL) only if needed.
- Learn: margin intuition, support vectors, linear vs non-linear boundaries, kernel intuition and scaling.
- Code: compare scaled Logistic Regression and SVM with linear/RBF kernels.
- Deliverable: comparison table and, if feasible, a decision-boundary plot.
- Checkpoint: explain how an RBF kernel can model non-linear boundaries.

## Week 16 — Unsupervised learning
- Watch [Unsupervised ML overview](https://youtu.be/Aa4MACKaDC0); main course sections: overview 6:35:30, K-Means 6:48:13, hierarchical 7:10:23 and DBSCAN 7:22:01.
- Learn: labelled vs unlabelled data, K-Means, choice of k, DBSCAN intuition and limitations of cluster evaluation.
- Code: use scikit-learn K-Means and DBSCAN on plottable data; implement K-Means core loop with NumPy only after the library version works.
- Deliverable: cluster plots, elbow plot where appropriate, silhouette score with caveats, and interpretation.
- Checkpoint: explain why cluster IDs are not automatically meaningful real-world categories.

## Week 17 — PCA and neural-network introduction
- Watch: main course PCA at 6:12:25 → neural-network intro 7:46:14 → perceptron 7:53:09 → softmax 8:04:02 → backpropagation 8:12:26.
- Learn: PCA and explained variance, neuron, weights, bias, activation, loss and the high-level purpose of backpropagation. This is an introduction, not full deep-learning mastery.
- Code: plot PCA explained variance on scaled data, then train a tiny neural network using a library. A single-neuron NumPy calculation is optional.
- Deliverable: PCA notebook, small neural-network demo and a list of remaining questions.
- Checkpoint: describe one training step in order and explain what PCA does.

## Phase 4 completion gate
- [ ] Establish a baseline before trying complex models.
- [ ] Explain regression vs classification and supervised vs unsupervised learning.
- [ ] Choose and interpret metrics appropriate to a stated problem.
- [ ] Use train/test splits and cross-validation without leakage.
- [ ] Compare at least three models fairly on the same task.
- [ ] Explain failure cases and limitations, not just the score.
- [ ] Re-run the notebooks and explain the main code without copying a tutorial.

If a checkpoint fails, review that topic and retry. Do not advance solely because the calendar week ended.