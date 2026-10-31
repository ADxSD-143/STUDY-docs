# End-to-End Machine Learning Project Workflow

Use this reusable checklist for every ML project. The full lifecycle has 14 stages (Stage 0–13). The 8-week beginner roadmap teaches the workflow end to end, but advanced tools and algorithms are marked as continuation topics.

**Learning levels**
- **Core:** implement during the 8-week foundation.
- **Introduction:** understand the purpose and try a small example if time permits.
- **Continuation:** revisit after the foundation; do not force it into the beginner sprint.

## Stage 0 — Problem framing
- [ ] State the real problem in one sentence: what decision should a model improve?
- [ ] Identify the task: regression, binary/multiclass/multilabel classification, clustering, ranking or forecasting.
- [ ] Choose a success metric and explain why it fits the cost of errors.
- [ ] Define a simple baseline (rule-based, mean/majority predictor, or existing process).
- [ ] Record constraints: data availability/size, latency, interpretability, privacy, safety and compute.
**Common mistake:** choosing an algorithm before defining the problem and metric.

## Stage 1 — Data collection and understanding
- [ ] Identify the source: CSV, SQL database, API, permitted scraping, Kaggle, UCI or Hugging Face.
- [ ] Check data types, sampling bias, label quality, representativeness and missing context.
- [ ] Verify licence, consent, privacy and whether personal data must be removed.
- [ ] Preserve an immutable raw-data copy; write cleaned data separately.
- [ ] Learn SQL basics: SELECT, WHERE, JOIN and GROUP BY; window functions are a continuation skill.
- [ ] Record dataset source/version and collection date. DVC is optional later.

## Stage 2 — Exploratory Data Analysis
- [ ] Inspect shape, columns, dtypes, missing percentages, duplicates and summary statistics.
- [ ] Univariate analysis: histograms, boxplots and value counts.
- [ ] Bivariate analysis: scatterplots, correlation heatmaps and target-versus-feature plots where appropriate.
- [ ] Inspect target distribution and class imbalance.
- [ ] Investigate outliers, skewness and suspicious values.
- [ ] Write 5–10 evidence-based findings.
**Tools:** pandas, Matplotlib and Seaborn; ydata-profiling is optional.

## Stage 3 — Split before fitting preprocessing
- [ ] Choose the split based on how the model will be used.
- [ ] For IID data, use train/test (for example 80/20); optionally hold out validation data.
- [ ] For classification, consider stratification.
- [ ] For time series, split chronologically, not randomly.
- [ ] For repeated users/patients/devices, use group-aware splitting.
- [ ] Keep the test set untouched until final evaluation.
**Critical:** never fit imputers, scalers, encoders, feature selection or resampling on the full dataset before splitting. Fit learned transformations on training data only; use a Pipeline to keep cross-validation leakage-safe.

## Stage 4 — Cleaning and preprocessing
| Task | Techniques | Notes |
|---|---|---|
| Missing values | Drop only with justification; mean/median/mode; missing indicator; KNN imputation (advanced) | Fit on training data only |
| Outliers | Investigate with IQR/z-scores; clip only with justification | Do not remove valid unusual observations blindly |
| Encoding | One-hot; ordinal only when order is real; target/frequency encoding (advanced) | Target encoding needs leakage-safe cross-fitting |
| Scaling | StandardScaler, MinMaxScaler, RobustScaler | Important for distance/gradient models; usually unnecessary for tree splits |
| Skewness | Log/square-root; Box-Cox when appropriate | Apply consistently |
| Imbalance | Class weights, threshold tuning; SMOTE (advanced) | Resample only inside training folds |
| Text/date | TF-IDF basics; meaningful date parts | Prevent future information entering features |
- [ ] Separate numeric, categorical, text and date transformations.
- [ ] Use Pipeline and ColumnTransformer for consistent training/inference steps.
- [ ] Inspect transformed feature names and output shapes.
**Core:** imputation, one-hot encoding, scaling, TF-IDF basics, Pipeline and ColumnTransformer. **Continuation:** target/frequency encoding, KNN imputation, SMOTE and advanced transforms.

## Stage 5 — Feature engineering and selection
- [ ] Create justified ratios, interactions, group aggregates, date parts and domain features.
- [ ] Consider polynomial features only when appropriate.
- [ ] Explore correlation filters, mutual information, L1 regularization, tree importance and RFE.
- [ ] Check multicollinearity when it matters for coefficient interpretation; VIF is optional.
- [ ] Use PCA for dimensionality reduction when appropriate; it is not an automatic fix for multicollinearity.
- [ ] Fit data-dependent feature selection only on training folds.

## Stage 6 — Baseline model
- [ ] Regression: compare a mean/median predictor and a simple linear model where suitable.
- [ ] Classification: compare a majority-class or simple rule baseline; Logistic Regression is a useful first learned model.
- [ ] Record baseline metrics using the same split/validation strategy as later models.
**Rule:** compare every complex model with a meaningful baseline.

## Stage 7 — Modeling and algorithm selection
**Supervised core:** Linear Regression, Logistic Regression, KNN, Naive Bayes, Decision Tree and Random Forest.
**Introduction:** Ridge/Lasso/ElasticNet, SVM intuition, bagging vs boosting and AdaBoost.
**Continuation:** Gradient Boosting, XGBoost, LightGBM, CatBoost, stacking and advanced ensembles.
**Unsupervised introduction:** K-Means and PCA. **Continuation:** Hierarchical clustering, DBSCAN, t-SNE/UMAP for visualization and Isolation Forest.
**Shared theory:** loss functions (MSE/log-loss), gradient descent, learning rate, bias–variance, overfitting/underfitting, L1/L2 regularization, bagging, boosting and stacking.
**Implementation target:** understand NumPy implementations of Linear Regression and Logistic Regression; build a small Decision Tree exercise after learning tree splits. Do not sacrifice evaluation/project work to implement every algorithm from scratch.

## Stage 8 — Evaluation
| Task | Useful metrics |
|---|---|
| Regression | MAE, MSE/RMSE, R²; MAPE only when meaningful for target values |
| Classification | Confusion matrix, precision, recall, F1, ROC-AUC, PR-AUC, log-loss; accuracy alone is insufficient for imbalanced data |
| Clustering | Silhouette and Davies–Bouldin, plus domain interpretation |
- [ ] Use suitable cross-validation: k-fold, stratified, time-series or group-aware.
- [ ] Inspect learning curves to diagnose over/underfitting.
- [ ] Select metrics based on the use case and error costs.
- [ ] Inspect probability calibration and thresholds when decisions use probabilities.
- [ ] Report class/segment performance, not only one aggregate score.

## Stage 9 — Hyperparameter tuning
- [ ] Tune with cross-validation on training data, never against the final test set.
- [ ] Start with a small manual search, then GridSearchCV or RandomizedSearchCV.
- [ ] Learn Optuna/Bayesian optimization in the continuation track.
- [ ] Understand tree depth, n_estimators, learning rate, regularization and min_samples_leaf.

## Stage 10 — Interpretation and error analysis
- [ ] Inspect false positives/false negatives and large regression errors.
- [ ] Identify weak classes, user groups, time periods or data segments.
- [ ] Use coefficients/tree importance carefully; consider permutation importance.
- [ ] SHAP and partial dependence are continuation tools, not mandatory for the beginner project.
- [ ] Perform a basic fairness/bias check where people or groups are affected.
- [ ] Record what to improve next and what the model must not decide autonomously.

## Stage 11 — Final evaluation and packaging
- [ ] Select the model using validation/CV, then evaluate on the untouched test set once.
- [ ] Save the complete preprocessing + model Pipeline (for example, with joblib).
- [ ] Record random seeds, data version, package versions and requirements.
- [ ] Track experiments in a simple results table; MLflow is optional later.
- [ ] Verify a fresh process can load the saved pipeline and reproduce predictions.

## Stage 12 — Deployment
- [ ] Expose predictions through a FastAPI /predict endpoint when an API is useful.
- [ ] Validate inputs with Pydantic and handle invalid/missing fields.
- [ ] Test input schema, preprocessing and prediction output.
- [ ] A Streamlit/Gradio UI is optional.
- [ ] Docker, cloud deployment and GitHub Actions/CI are continuation skills; check current free-tier limits.
**Beginner scope:** a local reproducible prediction script is acceptable. Deployment does not replace correct evaluation.

## Stage 13 — Monitoring and documentation
- [ ] Understand data drift vs concept drift and signals for investigation/retraining.
- [ ] Define safe prediction logging; avoid storing sensitive raw inputs unnecessarily.
- [ ] README: problem, data/source/licence, approach, baseline, results, architecture, run instructions, limitations and future work.
- [ ] Keep notebooks focused on exploration; move reusable code into src/ modules.
- [ ] Include screenshots/live link only if a working interface exists.
Do not claim active drift monitoring if the project is only a local prototype.

## Suggested project structure
- project/data/raw/ — immutable source data
- project/data/processed/ — derived data
- project/notebooks/ — EDA and experiments
- project/src/ — preprocessing.py, train.py, predict.py
- project/models/ — saved model/pipeline
- project/app/ — optional FastAPI app
- project/tests/ — tests
- project/requirements.txt and project/README.md

## Maths used across the pipeline
- **Linear algebra:** vectors, matrices, dot product; eigenvalues/eigenvectors for PCA.
- **Statistics/probability:** mean, variance, distributions, Bayes, sampling, correlation vs causation; hypothesis tests and confidence intervals later.
- **Calculus:** derivatives, chain rule and gradient descent.
- **Optimization:** loss surfaces, learning rate and convergence.
Learn each concept when it becomes relevant rather than studying all maths in isolation first.

## Free-first tools
Python, NumPy, pandas, Matplotlib, Seaborn, scikit-learn, Git/GitHub, SQL and Jupyter/Colab/Kaggle. Later: XGBoost/LightGBM, Optuna, SHAP, MLflow, FastAPI, Docker, Streamlit/Gradio. Check free-tier limits before relying on hosted deployment.

## Project completion checklist
- [ ] Problem, intended user and success metric defined before modeling.
- [ ] Data source, licence, privacy and label quality documented.
- [ ] EDA insights recorded.
- [ ] Correct split used before fitting preprocessing; no leakage.
- [ ] Baseline recorded and compared.
- [ ] Multiple appropriate models compared when data size permits.
- [ ] Metrics and validation strategy fit the problem.
- [ ] Error analysis and limitations documented.
- [ ] Final test set used only for final evaluation.
- [ ] Saved pipeline can be loaded and predictions reproduced.
- [ ] README explains how to run and what the model cannot prove.
- [ ] Deployment/monitoring claims match what is actually implemented.
- [ ] You can explain the project and its decisions without copied code.

## Common mistakes
1. Data leakage from preprocessing or feature selection before splitting.
2. Using accuracy alone on imbalanced classification.
3. Repeatedly tuning against the test set.
4. Skipping a baseline.
5. Choosing metrics without considering error costs.
6. Skipping error analysis.
7. Treating a notebook score as proof of production readiness.
8. Claiming deployment, monitoring or real-world impact that has not been tested.