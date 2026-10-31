# Classical ML Practice Projects

Complete these projects after learning the corresponding algorithm. They are practice projects, separate from the Week 8 CampusFix capstone. Use the same [Stage 0–13 workflow](../06-reference/ml-project-workflow.md), scaled to each dataset.

## Project ladder

| Algorithm | Project | Dataset | Main learning outcome |
|---|---|---|---|
| Linear Regression | House Price Prediction | [Housing Prices — Kaggle](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset) | Predict a continuous house price; interpret coefficients and regression errors. |
| Logistic Regression | Breast Cancer Classification | scikit-learn built-in [Breast Cancer Wisconsin dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html) | Binary classification, probabilities, threshold, confusion matrix, precision/recall and ROC-AUC. |
| Decision Tree | Titanic Survival Prediction | [Titanic Dataset — Kaggle](https://www.kaggle.com/datasets/yasserh/titanic-dataset) | Predict survival; understand tree splits, depth, overfitting and feature importance. |
| Random Forest | Heart Disease Classification | [Heart Disease Data — Kaggle](https://www.kaggle.com/datasets/redwankarimsony/heart-disease-data) | Compare a forest with a single tree; evaluate classification and feature importance. |
| K-Means | Customer Segmentation | [Mall Customers — Kaggle](https://www.kaggle.com/datasets/shwetabh123/mall-customers) | Unsupervised learning, scaling, elbow method, silhouette score and cluster interpretation. |

### Why this Logistic Regression dataset?
I recommend the built-in Breast Cancer Wisconsin dataset from scikit-learn. It is a well-known binary classification teaching dataset, loads directly in Python without Kaggle download or account setup, and lets you focus on Logistic Regression rather than spending time finding/cleaning a dataset. The target represents two diagnosis classes; handle labels carefully and do not present this educational exercise as a clinical diagnostic tool.

## Project requirements

Every project should contain:
1. README.md — problem, dataset source, target, metric choice and limitations.
2. notebooks/01_eda.ipynb — data inspection and at least five written observations.
3. notebooks/02_model.ipynb — baseline, preprocessing, model and evaluation.
4. src/ — reusable preprocessing/training/prediction code once the notebook works.
5. models/ — saved complete pipeline, if persistence is part of the exercise.
6. requirements.txt — dependencies and versions.

## Minimum checklist by project

### 1. House Price Prediction — Linear Regression
- Identify target price and numeric/categorical features.
- Inspect missing values, distributions, outliers and correlations.
- Split data before fitting imputers/encoders/scalers.
- Compare a mean-prediction baseline with Linear Regression.
- Report MAE, RMSE and R²; inspect residuals.
- Explain coefficient interpretation and why correlation does not prove causation.

### 2. Breast Cancer Classification — Logistic Regression
- Load with sklearn.datasets.load_breast_cancer.
- Inspect class counts, feature scales and feature distributions.
- Use stratified train/test split and StandardScaler inside a Pipeline.
- Compare DummyClassifier with Logistic Regression.
- Report confusion matrix, precision, recall, F1 and ROC-AUC.
- Inspect predicted probabilities and how threshold changes false positives/false negatives.
- Treat this strictly as a learning exercise, not medical advice or a deployable diagnostic.

### 3. Titanic Survival — Decision Tree
- Define Survived as target; inspect missing values and categorical columns.
- Remove leakage/identifier-only columns where justified; document choices.
- Build preprocessing with imputation and one-hot encoding in a Pipeline.
- Compare a majority baseline with a Decision Tree.
- Vary max_depth and min_samples_leaf; compare train vs validation scores.
- Report confusion matrix, precision, recall and F1; inspect feature importance cautiously.

### 4. Heart Disease — Random Forest
- Verify the dataset's actual target column, class meanings, missing values and feature types before training; do not assume the target encoding.
- Use stratified splitting and preprocessing inside a Pipeline.
- Compare DummyClassifier, Decision Tree and Random Forest.
- Tune a small set of parameters with cross-validation, not the test set.
- Report per-class precision/recall/F1, confusion matrix and ROC-AUC where appropriate.
- Inspect feature importance and errors. This is an educational dataset, not a medical decision tool.

### 5. Mall Customers — K-Means
- Start with a clear segmentation question; there is no ground-truth target label for ordinary clustering.
- Inspect distributions and select meaningful numeric features; explain feature choices.
- Scale features before distance-based clustering.
- Fit K-Means for multiple values of k; plot inertia (elbow) and calculate silhouette score.
- Visualize clusters using selected features; describe cluster profiles without inventing business meaning.
- Explain sensitivity to scaling, initialization and outliers. Do not report classification accuracy.

## Important project rules
- Keep raw data unchanged; document dataset version and licence/usage conditions.
- Do not fit preprocessing on the full dataset before splitting.
- Use Pipelines to prevent leakage during cross-validation.
- Choose metrics based on the task; do not rely on accuracy alone for imbalanced classification.
- Never tune on the final test set.
- Document limitations and avoid claiming real-world/clinical/business impact from a classroom dataset.

## Suggested order
Linear Regression → Logistic Regression → Decision Tree → Random Forest → K-Means.

Finish the matching lesson and checkpoint in [Phase 4](../03-learning-path/phases/04-machine-learning.md) before starting each project.