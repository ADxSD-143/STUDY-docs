# Practical ML Projects — Apply Each Algorithm

This phase contains the hands-on projects for the classical ML algorithms in Phase 4. Complete the matching lesson first, then build the project using the full [Stage 0–13 ML project workflow](../../06-reference/ml-project-workflow.md).

These are **five separate practice projects**. They are not one combined capstone, and CampusFix is not part of this project list.

## Project roadmap

| Order | Algorithm | Project | Dataset |
|---|---|---|---|
| 1 | Linear Regression | House Price Prediction | [Housing Prices — Kaggle](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset) |
| 2 | Logistic Regression | Breast Cancer Classification | [Breast Cancer Wisconsin — scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html) |
| 3 | Decision Tree | Titanic Survival Prediction | [Titanic Dataset — Kaggle](https://www.kaggle.com/datasets/yasserh/titanic-dataset) |
| 4 | Random Forest | Heart Disease Classification | [Heart Disease Data — Kaggle](https://www.kaggle.com/datasets/redwankarimsony/heart-disease-data) |
| 5 | K-Means Clustering | Mall Customer Segmentation | [Mall Customers — Kaggle](https://www.kaggle.com/datasets/shwetabh123/mall-customers) |

## 1. Linear Regression — House Price Prediction

**Dataset:** [Housing Prices](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset)

- Define the target house price and identify numerical/categorical features.
- Inspect data types, missing values, distributions, outliers and feature relationships.
- Split data before fitting imputers, encoders or scalers.
- Build a mean-prediction baseline and compare it with Linear Regression.
- Evaluate using MAE, RMSE and R²; inspect residuals.
- Explain coefficient interpretation and why correlation does not prove causation.

**Deliverable:** EDA notebook, baseline/model comparison, residual analysis and a short README.

## 2. Logistic Regression — Breast Cancer Classification

**Dataset:** [Breast Cancer Wisconsin — scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html)

This built-in dataset avoids a separate download and provides a binary classification task suitable for learning Logistic Regression.

- Inspect class distribution, feature scales and feature distributions.
- Use a stratified train/test split.
- Put StandardScaler and Logistic Regression in a Pipeline.
- Compare DummyClassifier with Logistic Regression.
- Report confusion matrix, precision, recall, F1 and ROC-AUC.
- Inspect predicted probabilities and how changing the threshold affects false positives and false negatives.

**Deliverable:** classification notebook, metric comparison, threshold experiment and README.

**Scope note:** this is an educational dataset, not medical advice or a deployable diagnostic system.

## 3. Decision Tree — Titanic Survival Prediction

**Dataset:** [Titanic Dataset](https://www.kaggle.com/datasets/yasserh/titanic-dataset)

- Define `Survived` as the target; inspect missing values and categorical features.
- Identify and document any identifier or leakage-prone columns.
- Build preprocessing with imputation and one-hot encoding in a Pipeline.
- Compare a majority-class baseline with a Decision Tree.
- Experiment with `max_depth` and `min_samples_leaf`; compare training and validation scores.
- Report confusion matrix, precision, recall and F1.
- Inspect feature importance cautiously; importance is not causation.

**Deliverable:** decision-tree comparison, depth experiment, feature-importance notes and README.

## 4. Random Forest — Heart Disease Classification

**Dataset:** [Heart Disease Data](https://www.kaggle.com/datasets/redwankarimsony/heart-disease-data)

- Inspect the dataset schema and verify the actual target column and class meanings before modeling.
- Check missing values, feature types and class distribution.
- Use stratified splitting and preprocessing inside a Pipeline.
- Compare DummyClassifier, Decision Tree and Random Forest.
- Tune a small set of hyperparameters with cross-validation, not the test set.
- Report per-class precision/recall/F1, confusion matrix and ROC-AUC where appropriate.
- Inspect feature importance and error cases.

**Deliverable:** three-model comparison, cross-validation results, error analysis and README.

**Scope note:** this is an educational dataset, not a medical decision tool.

## 5. K-Means — Mall Customer Segmentation

**Dataset:** [Mall Customers](https://www.kaggle.com/datasets/shwetabh123/mall-customers)

- Define a segmentation question before clustering; this dataset has no ordinary ground-truth class label.
- Inspect distributions and select meaningful numerical features; explain the selection.
- Scale features before applying a distance-based algorithm.
- Fit K-Means for several values of `k`.
- Plot inertia and use the elbow method as one diagnostic.
- Calculate silhouette score and compare candidate cluster counts.
- Visualize and describe cluster profiles without inventing business meaning.
- Discuss sensitivity to scaling, initialization and outliers.

**Deliverable:** clustering notebook with elbow plot, silhouette comparison, cluster visualization and interpretation.

**Important:** do not report classification accuracy for an unlabeled clustering task.

## Common requirements for all projects

Follow these steps in every project:

1. **Problem framing:** state the task, target (if supervised), intended use and success metric.
2. **Data understanding:** document source, licence, schema, labels and limitations.
3. **EDA:** inspect quality and distributions; write at least five findings.
4. **Split:** choose an appropriate split before fitting learned preprocessing. For clustering, explain why a supervised train/test setup may not apply in the same way.
5. **Preprocessing:** use a scikit-learn Pipeline/ColumnTransformer where appropriate; prevent leakage.
6. **Baseline:** use a simple baseline for supervised tasks.
7. **Modeling:** train the algorithm and run at least one meaningful experiment.
8. **Evaluation:** select metrics that suit the task; inspect failure cases.
9. **Interpretation:** explain important features, model behavior and limitations.
10. **Packaging:** keep reusable code separate from exploratory notebooks; save the full pipeline where appropriate.
11. **Documentation:** write a README with problem, data source, approach, results, run instructions and limitations.

## Suggested folder structure

```text
project-name/
├── data/
│   ├── raw/              # keep source data unchanged
│   └── processed/
├── notebooks/
│   ├── 01_eda.ipynb
│   └── 02_modeling.ipynb
├── src/
│   ├── preprocessing.py
│   ├── train.py
│   └── predict.py
├── models/               # saved pipeline, when applicable
├── requirements.txt
└── README.md
```

## Completion checklist

- [ ] I can explain the problem and why this algorithm is suitable.
- [ ] I documented the dataset source, licence and limitations.
- [ ] I performed EDA and recorded findings.
- [ ] I avoided preprocessing/data leakage errors.
- [ ] I compared with a baseline where appropriate.
- [ ] I selected appropriate evaluation metrics.
- [ ] I inspected model errors or cluster profiles.
- [ ] I can reproduce the work from the README.
- [ ] I can explain the project without simply reading copied code.

## After these projects

Once these five projects are complete, continue with SVM, Hierarchical Clustering, DBSCAN, PCA, boosting (XGBoost/LightGBM/CatBoost), advanced tuning, SHAP, MLflow and deployment engineering as separate follow-on exercises.