# Core Machine Learning — Weeks 4–7

This phase covers workflow Stages 6–11: baseline, modeling, evaluation, tuning, error analysis and packaging. Use the complete [End-to-End ML Project Workflow](../../06-reference/ml-project-workflow.md) as the master checklist.

## Primary video resources

These are the two fixed primary resources. Follow the assigned sections rather than watching every minute in sequence.

- [Main Machine Learning course — Data Dissection](https://youtu.be/trsyTEA22Gw)
- [Mathematics for ML — Data Dissection](https://youtu.be/cO9xmfsJJu4)

## Complete supplementary video playlists

Use these as complete topic-wise reference libraries when you need another explanation or want deeper practice. **They are not mandatory to finish during the 8-week roadmap.**

- [CampusX — Complete Machine Learning playlist](https://youtube.com/playlist?list=PLKnIA16_Rmvbr7zKYQuBfsVkjoLcJgxHH&si=vLWpBfFztXIrFY5A)
- [StatQuest — Complete Machine Learning playlist](https://youtube.com/playlist?list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&si=Uck5deAI2vq0Jhjg)

## Week 4 — Baselines, Linear Regression and Logistic Regression

**Main course sections**
- Gradient Descent intuition: 09:50
- Linear Regression: 27:13
- R²: 44:55
- Multiple Regression: 52:47
- Logistic Regression: 2:15:32

**Concepts**
- Baseline predictors and why every model needs a baseline comparison.
- Features, target, coefficients, predictions and residuals.
- MAE, MSE, RMSE and R².
- Regression vs classification.
- Sigmoid, predicted probability, decision threshold and log-loss intuition.

**Code**
- Build a simple regression baseline and compare it with Linear Regression.
- Train Logistic Regression for a suitable binary classification problem.
- Inspect residuals and predicted probabilities.

**Checkpoint:** explain why a baseline matters, distinguish regression from classification, and explain why Logistic Regression produces probabilities.

## Week 5 — Classification metrics, Naive Bayes and KNN

**Video order**
1. [Confusion matrix and Type I/II errors](https://youtu.be/c09drtuCS3c)
2. [Precision, recall and F1](https://youtu.be/iK-kdhJ-7yI)
3. [ROC curve and ROC-AUC — CampusX](https://youtu.be/gdW6hj9IXaA)
4. [Naive Bayes — StatQuest](https://youtu.be/O2L2Uv9pdDA)
5. [KNN — CampusX](https://youtu.be/abnL_GUGub4)

**Concepts**
- TP, FP, TN, FN; accuracy, precision, recall, F1 and specificity.
- False-positive rate and false-negative rate.
- ROC-AUC and when PR-AUC is more informative for imbalanced data.
- Decision threshold and error-cost trade-offs.
- Naive Bayes conditional independence assumption and probability intuition.
- KNN distance, k value and why scaling matters.

**Code**
- Compare Logistic Regression, Naive Bayes and scaled KNN on the same classification dataset.
- Report confusion matrix, precision, recall and F1; explain which metric matters most for this problem.

**Checkpoint:** interpret a confusion matrix, explain precision vs recall, and explain why KNN is sensitive to feature scale.

## Week 6 — Decision Trees, ensembles, feature importance and error analysis

**Main course sections**
- Decision Trees: 3:39:55 and 3:58:05

**Supplementary videos**
- CampusX playlist study sequence: Day 16–17 — Classification Metrics and Feature Importance (playlist video numbers 75, 76, 134 and 97, as supplied in the study plan).
- [Random Forest — StatQuest](https://youtu.be/J4Wdy0Wc_xQ)
- [AdaBoost — StatQuest](https://youtu.be/LsK-xG1cLYA)
- [Bias–variance — StatQuest](https://youtu.be/EuBBz3bI-aA)

**Concepts**
- Tree splits, Gini impurity and entropy intuition.
- Maximum depth, leaf size and overfitting.
- Bagging vs boosting; Random Forest and AdaBoost at an introductory level.
- Feature importance: impurity-based importance, permutation importance intuition and why importance is not causation.
- Error analysis: false positives/negatives, weak classes and examples the model gets wrong.

**Code**
- Compare a baseline, Decision Tree and Random Forest.
- Inspect training and validation scores across tree depths.
- Inspect a few model errors and describe a possible cause.
- Extract and compare feature-importance rankings; check whether they make domain sense.

**Checkpoint:** explain overfitting, bagging vs boosting, and identify one concrete model failure.

## Week 7 — Validation, tuning, interpretation and unsupervised learning

**Videos and documentation**
- [StatQuest — Cross-validation](https://youtu.be/fSytzGwwBVw)
- [scikit-learn cross-validation guide](https://scikit-learn.org/stable/modules/cross_validation.html)
- [scikit-learn Pipeline guide](https://scikit-learn.org/stable/modules/compose.html)
- [scikit-learn model persistence](https://scikit-learn.org/stable/model_persistence.html)

**Concepts**
- Train, validation and test roles.
- K-fold and stratified cross-validation; time/group-aware validation awareness.
- Data leakage and fitting preprocessing inside each training fold.
- GridSearchCV and RandomizedSearchCV basics; tune only within training/CV.
- Final held-out test evaluation once after decisions are fixed.
- Basic coefficient/feature-importance inspection and error review.
- Save/reload a complete preprocessing + model pipeline; random seeds and requirements.

**Code**
- Build a preprocessing/model Pipeline.
- Compare at least three suitable models using cross-validation.
- Perform a small GridSearchCV or RandomizedSearchCV experiment.
- Save and reload the selected pipeline; test one prediction in a fresh process.
- Keep the final test set untouched until final evaluation.

**Checkpoint:** explain leakage, cross-validation, why test-set tuning is unreliable, and demonstrate a saved model pipeline that reloads successfully.


### Unsupervised learning — clustering module (required introduction)

This is part of the ML foundation, not a topic to silently skip. Learn the purpose and basic implementation of clustering after supervised learning.

**Video sequence**
- CampusX playlist study sequence: Day 18 — Basics of Unsupervised Learning; Day 18–19 — K-Means (playlist video numbers 103, 104 and 105); Day 20 — Hierarchical Clustering. The supplied Day 18 basics link was not included in the message, so use the main-course overview below until that link is added.
- Main course unsupervised learning overview: 6:35:30
- K-Means: 6:48:13
- Hierarchical clustering: 7:10:23
- DBSCAN overview: 7:22:01 (intro/continuation; detailed tuning is not required in this sprint)
- [CampusX — Complete ML playlist](https://youtube.com/playlist?list=PLKnIA16_Rmvbr7zKYQuBfsVkjoLcJgxHH&si=vLWpBfFztXIrFY5A): use the clustering lessons corresponding to playlist videos 103, 104 and 105 for K-Means, and the Hierarchical Clustering lesson around Day 20 in your supplied sequence.

**Concepts**
- Supervised vs unsupervised learning; features without target labels.
- Clustering use cases and why clusters are not automatically meaningful categories.
- K-Means: centroids, assignment/update loop, inertia, choosing k with elbow method and silhouette score; sensitivity to scaling, initialization and outliers.
- Hierarchical clustering: agglomerative approach, dendrogram, linkage choices and selecting a cut level.
- Compare cluster assignments and describe limitations; do not evaluate clustering with classification accuracy when no ground-truth labels exist.

**Code**
- Scale suitable numeric features, fit KMeans for several k values and plot inertia.
- Use silhouette score as one diagnostic, not as proof that clusters are useful.
- Fit AgglomerativeClustering and visualize a dendrogram on a small sample.
- Write a short comparison: when K-Means is suitable vs when hierarchical clustering may be useful.

**Checkpoint:** explain supervised vs unsupervised learning, the K-Means loop, elbow/silhouette, and how a dendrogram represents hierarchical merges.

## Topic coverage audit

| Topic | Coverage |
|---|---|
| Baseline and model selection | Core |
| Linear Regression and Logistic Regression | Core |
| Naive Bayes and KNN | Core |
| Decision Trees and Random Forest | Core |
| AdaBoost and bagging/boosting intuition | Introduction |
| Regression and classification metrics | Core |
| Specificity, FPR/FNR and threshold choice | Core concepts |
| ROC-AUC and PR-AUC | Core concepts; PR-AUC may be a code exercise |
| Cross-validation and leakage prevention | Core |
| GridSearchCV/RandomizedSearchCV | Basic introduction |
| Error analysis | Core |
| Feature importance and permutation importance intuition | Core introduction |
| Ridge/Lasso/ElasticNet | Continuation |
| SVM and kernel methods | Continuation |
| XGBoost, LightGBM, CatBoost, stacking | Continuation |
| K-Means and Hierarchical clustering | Core introduction and small implementation |\n| PCA | Optional introduction after core |
| DBSCAN | Intro only; deeper use is continuation |\n| t-SNE/UMAP, anomaly detection | Continuation |
| Probability calibration, SHAP, Optuna, MLflow | Continuation |
| Neural networks, PyTorch and deep learning | Separate follow-on track |

**Important scope note:** this is a beginner classical-ML core, not every ML algorithm in existence. The full continuation list is in the [project workflow guide](../../06-reference/ml-project-workflow.md) and [resource library](../../05-resources/README.md).

## Optional after the core

- Main course PCA: 6:12:25. K-Means and Hierarchical clustering are now part of the required beginner introduction.
- SVM intuition and deeper ensemble methods are continuation topics.
- Do not start neural networks or deep learning until the core modeling, validation and error-analysis checkpoints are comfortable.

From-scratch implementations are useful exercises, but in this accelerated roadmap prioritize correct baselines, leakage-safe experiments, evaluation and error analysis over implementing every algorithm from scratch.