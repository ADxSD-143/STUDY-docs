# Data Preparation — Weeks 2–3

This phase covers project workflow Stages 1–5 at beginner depth. Use the full [Stage 0–13 project checklist](../ml-project-workflow.md) alongside the lessons.

## Week 2 — Data collection, NumPy and pandas (Stages 1–2)
Main resource: [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X), NumPy sessions 13–15 and pandas from session 16 onward. Supplements: [NumPy](https://youtu.be/VXU4LSAQDSc), [pandas](https://youtu.be/VXtjG_GzO7Q), [Matplotlib](https://youtu.be/c9vhHUGdav0).

Learn data sources, types, sampling/label quality, licence and privacy basics. SQL introduction: SELECT, WHERE, JOIN and GROUP BY; window functions and DVC are later topics.

Learn arrays/shape/indexing/vectorized operations; pandas Series/DataFrame, CSV loading, filtering, missing values, duplicates, dtypes, groupby, simple merge and plots.

**Deliverable:** a dataset source note (where it came from, licence/permission, target/labels and limitations) plus a notebook that loads a CSV, answers five questions, handles missing values and creates a useful plot.

## Week 3 — EDA, split, cleaning and feature preparation (Stages 2–5)
Watch [CampusX data assessing/cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2) → [Krish Naik EDA and feature engineering](https://youtu.be/fHFOANOHwh8). Read [scikit-learn preprocessing and composition](https://scikit-learn.org/stable/modules/compose.html).

Learn:
- Data audit: shape, dtypes, missingness, duplicates and summary statistics.
- Univariate and bivariate plots; target distribution and class imbalance.
- Outlier/skewness investigation and suspicious values.
- Features vs target; choose a suitable train/test split before fitting preprocessing.
- Missing-value imputation, one-hot encoding and scaling basics.
- Pipeline and ColumnTransformer; train-only fitting and leakage prevention.
- Simple, justified feature engineering.

**Deliverable:** EDA report with 5 findings, 3 plots, documented cleaning decisions, a valid split and a leakage-safe preprocessing pipeline.

## Readiness gate before core ML
- [ ] Explain where the dataset came from and any licence/privacy limits.
- [ ] Load, filter, group and merge data with pandas.
- [ ] Explain missing values, duplicates and class imbalance.
- [ ] Make plots and write evidence-based EDA findings.
- [ ] Identify features and target.
- [ ] Explain why splitting must happen before fitting transformations.
- [ ] Build a basic Pipeline that fits preprocessing on training data only.

Advanced encoders, SMOTE, KNN imputation, PCA, VIF and feature-selection algorithms are continuation topics; understand their purpose before attempting them.