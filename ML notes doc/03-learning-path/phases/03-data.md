# Data Preparation — Weeks 2–3

This phase covers workflow Stages 1–5 at beginner depth. Use the full [Stage 0–13 project checklist](../../06-reference/ml-project-workflow.md) alongside these lessons.

## Week 2 — Data collection, NumPy and pandas (Stages 1–2)

**Video resources**
- [CampusX Python playlist](https://youtube.com/playlist?list=PLxvLUL96MOO4saKDW4nHTCe1cDbDMTR5X): NumPy sessions 13–15; pandas from session 16 onward.
- [Bro Code NumPy](https://youtu.be/VXU4LSAQDSc) — supplementary.
- [Bro Code pandas](https://youtu.be/VXtjG_GzO7Q) — supplementary.
- [Bro Code Matplotlib](https://youtu.be/c9vhHUGdav0) — supplementary.
- [CampusX data assessing/cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2) — begin after core pandas.
- [Krish Naik EDA and Feature Engineering](https://youtu.be/fHFOANOHwh8) — supplementary EDA walkthrough.

**Concepts to cover**
- Data source, data types, sampling bias, label quality, licensing and privacy.
- NumPy arrays, shape, indexing, slicing, vectorized operations and basic aggregation.
- pandas Series/DataFrame, reading CSV, selecting/filtering, sorting, missing values, duplicates, dtypes, groupby, merge/join and exporting.
- Basic SQL awareness: database/table/row/column, SELECT, WHERE, ORDER BY, GROUP BY, aggregates, INNER/LEFT JOIN and NULL. The full SQL playlist is optional—see [SQL resources](../../05-resources/README.md#sql--optional-awareness-resource).

**Deliverable:** a dataset source note (source, licence/permission, target/labels and limitations) plus a notebook that loads a CSV, answers five questions, handles missing values and creates a useful plot.

## Week 3 — EDA, split, cleaning and feature preparation (Stages 2–5)

**Video and documentation resources**
- [CampusX data assessing/cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2)
- [Krish Naik EDA and Feature Engineering](https://youtu.be/fHFOANOHwh8)
- [Pandas user guide](https://pandas.pydata.org/docs/user_guide/index.html)
- [Seaborn tutorial](https://seaborn.pydata.org/tutorial.html)
- [scikit-learn preprocessing and composition](https://scikit-learn.org/stable/modules/compose.html)
- [scikit-learn data leakage pitfalls](https://scikit-learn.org/stable/common_pitfalls.html#data-leakage)

**Concepts to cover**
1. **Data audit:** shape, dtypes, missing-value count/percentage, duplicates and summary statistics.
2. **Univariate EDA:** histograms, boxplots, count/value plots and distributions.
3. **Bivariate EDA:** scatterplots, correlation heatmaps and target-vs-feature analysis where appropriate.
4. **Target inspection:** target distribution and class imbalance.
5. **Data quality:** outliers, skewness, suspicious/impossible values and inconsistent categories.
6. **Train/validation/test split:** random/stratified split for suitable IID data; time-based split for time series; group-aware split when repeated entities could leak across sets.
7. **Missing values:** row/column removal only when justified; mean/median/mode imputation and missing indicators.
8. **Encoding:** one-hot encoding for nominal categories; ordinal encoding only when a genuine order exists. Target/frequency encoding is advanced.
9. **Scaling:** StandardScaler, MinMaxScaler and RobustScaler; learn why scaling matters for KNN/distance/gradient-based models but is usually unnecessary for tree splits.
10. **Feature engineering:** create simple, justified features; avoid using future or target-derived information.
11. **Pipeline:** use Pipeline and ColumnTransformer so learned preprocessing is fitted on training folds only and reused consistently at prediction time.

**Important:** split before fitting imputers, scalers, encoders, feature selectors or resampling. Never fit transformations on the full dataset before splitting. Use a Pipeline during cross-validation to prevent leakage.

**Deliverable:** EDA report with at least five written findings and three plots, documented cleaning decisions, a suitable split and a leakage-safe preprocessing pipeline.

## Data topic coverage audit

| Topic | Coverage in this beginner path |
|---|---|
| Data sourcing, types, sampling/label quality, privacy/licensing | Core awareness |
| NumPy arrays and vectorized operations | Core |
| pandas loading, selection, filtering, sorting, missing values, duplicates, groupby and merge | Core |
| SQL basics | Awareness only; full playlist optional |
| Missing-value imputation | Core basics |
| Outlier and skewness analysis | Core awareness; advanced treatment later |
| Univariate/bivariate EDA and visualization | Core |
| Class imbalance inspection | Core awareness; handling strategies later |
| Train/test split, stratification, time/group-aware split | Core concepts |
| One-hot encoding and scaling | Core |
| Ordinal, target and frequency encoding | Introduction/continuation |
| Pipeline and ColumnTransformer | Core |
| Text preprocessing and TF-IDF | Covered in ML phase and CampusFix |
| Date features, advanced outlier handling, SMOTE, KNN imputation | Continuation |
| Feature selection, mutual information, RFE, VIF and PCA | Continuation |
| Data versioning with DVC | Continuation |

## Readiness gate before core ML
- [ ] Explain where the dataset came from and its licence/privacy limits.
- [ ] Load, filter, group and merge data with pandas.
- [ ] Explain missing values, duplicates and class imbalance.
- [ ] Make plots and write evidence-based EDA findings.
- [ ] Identify features and target.
- [ ] Explain and choose a suitable split strategy.
- [ ] Explain why splitting must happen before fitting transformations.
- [ ] Build a basic Pipeline that fits preprocessing on training data only.

Advanced encoders, SMOTE, KNN imputation, PCA, VIF, feature-selection algorithms and DVC are not required before moving to beginner ML.