# Complete 24-Week ML Roadmap
**Flow: Maths → Python → Data → ML → Projects**  
**Budget:** 24 weeks × 10 hours = 240 hours. Free resources/tools only.

## Weekly rhythm
3 h focused videos/reading, 5 h coding/experiments, 2 h review/notes. Each week has a deliverable included in those 10 hours. Diagnose existing Python, NumPy, pandas and regression knowledge; revise weak areas rather than restarting everything. Video watching alone does not count as completion.

## Phase map
| Phase | Weeks | Detailed guide |
|---|---:|---|
| Maths | 1–2 | [Maths](phases/01-maths.md) |
| Python | 3 | [Python](phases/02-python.md) |
| Data | 4–5 | [Data](phases/03-data.md) |
| ML | 6–17 | [Machine Learning](phases/04-machine-learning.md) |
| Projects and engineering | 18–24 | [Projects and Engineering](phases/05-projects-engineering.md) |

## Weekly calendar: what to watch, then what to build
| Week | Study and video order | Coding deliverable |
|---|---|---|
| 1 | Maths diagnostic; watch only weak sections of [Math for ML](https://youtu.be/cO9xmfsJJu4); master ML gradient descent at 09:50 if needed | NumPy examples: statistics, dot product, matrices, derivative |
| 2 | Targeted linear algebra, probability/Bayes and derivatives from Math for ML; connect to master ML regression chapter at 27:13 | Gradient descent experiment and loss plot |
| 3 | Python diagnostic; CampusX Python playlist only for weak topics; Bro Code NumPy/pandas/Matplotlib as supplements | CSV-to-cleaned-data notebook, clean environment and Git commit |
| 4 | [CampusX data cleaning](https://www.youtube.com/live/-HnN8GBINnc?si=OvOHi67BLx1uJWe2), then [Krish Naik EDA/feature engineering](https://youtu.be/fHFOANOHwh8) | Data audit, missing values, duplicates and safe split |
| 5 | [Sheryians visualization](https://youtu.be/-jTD74eEy2I), then continue Krish Naik EDA/feature engineering; Matplotlib supplement if needed | EDA report, justified features and leakage checklist |
| 6 | Master ML: Linear Regression 27:13, R² 44:55, Multiple Regression 52:47; [StatQuest Linear Models](https://youtube.com/playlist?list=PLblh5JKOoLUIzaEkCLIUxQFjPIlapw8nU); [regression metrics](https://youtu.be/Ti7c-Hz7GSM) | Linear Regression from scratch vs scikit-learn |
| 7 | [CampusX regularization](https://youtube.com/playlist?list=PLKnIA16_RmvZuSEZ24Wlm13QpsfLlJBM4); master ML bias-variance 1:41:46 and regularization/hyperparameter 1:56:52 | Compare Linear, Ridge and Lasso |
| 8 | [StatQuest Logistic Regression](https://youtube.com/playlist?list=PLblh5JKOoLUKxzEP5HA2d-Li7IJkHfXSe); master ML 2:15:32 | Logistic Regression from scratch |
| 9 | Watch [classification metrics](https://youtu.be/5vqk6HnITko) → [confusion matrix/type errors](https://youtu.be/c09drtuCS3c) → [precision/recall/F1](https://youtu.be/iK-kdhJ-7yI) → [StatQuest confusion matrix](https://youtu.be/Kdsp6soqA7o) → [ROC-AUC](https://youtu.be/gdW6hj9IXaA); master 2:54:17 and 5:07:18 | Confusion matrix, precision, recall, F1, specificity, FPR/FNR, ROC-AUC/PR-AUC |
| 10 | [Naive Bayes](https://youtu.be/O2L2Uv9pdDA), master 5:52:16; then [CampusX KNN](https://youtu.be/abnL_GUGub4), master KNN 3:06:38 and distances 3:25:06 | KNN and simple Naive Bayes from scratch |
| 11 | Master decision trees 3:39:55, 3:58:05, hyperparameters 4:09:25 | Gini/entropy exercise, sklearn tree comparison |
| 12 | [StatQuest ensemble playlist](https://youtube.com/playlist?list=PLBUVsOl8j6mIHPlbWm_o2Sx_NQLdkC8xd), [CampusX ensemble playlist](https://youtube.com/playlist?list=PLnD9uS5lPM6l3oB5aPLTA8uUTayvLDF5T), [Random Forest 1](https://youtu.be/J4Wdy0Wc_xQ), [Random Forest 2](https://youtu.be/mIlw5j3WyVk), [AdaBoost](https://youtu.be/LsK-xG1cLYA); master 4:18:01 and 4:34:20 | Compare tree, Random Forest and boosting |
| 13 | [StatQuest cross-validation](https://youtu.be/fSytzGwwBVw) → [Krish Naik CV types](https://youtu.be/bq4LytNAjjM); [encoding](https://youtu.be/589nCGeWG1w) | Leakage-safe pipeline and CV comparison |
| 14 | Learn [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) and [RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html); [bias-variance](https://youtu.be/EuBBz3bI-aA), [calibration docs](https://scikit-learn.org/stable/modules/calibration.html); optional [Optuna](https://youtu.be/E2b3SKMw934) | Model selection report with error analysis |
| 15 | SVM in order: [Part 1](https://youtu.be/efR1C6CvhmE) → [polynomial kernel](https://youtu.be/Toet3EiSFcM) → [RBF kernel](https://youtu.be/Qc5IyLW_hns); [CampusX SVM playlist](https://youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL) | Compare scaled SVM with prior models |
| 16 | [Unsupervised ML Hindi](https://youtu.be/Aa4MACKaDC0); master PCA 6:12:25, K-Means 6:48:13, hierarchical 7:10:23, DBSCAN 7:22:01 | K-Means from scratch and clustering evaluation |
| 17 | Master neural network intro 7:46:14, perceptron 7:53:09, softmax 8:04:02, backprop 8:12:26, from scratch 8:30:19 onward; [supplied NN playlist](https://youtube.com/playlist?list=PLlpUUtQ9RrF47CpLH6PSFL2oeP3izPMhE) | PCA variance experiment and small neural network |
| 18 | No new long course; review data and classification material; define stakeholder, data permission, labels, baseline and metrics | CampusFix project brief and data card |
| 19 | Revisit cleaning/EDA resources only as needed | CampusFix data audit, rule baseline and majority baseline |
| 20 | Revisit Logistic Regression, Naive Bayes and classification metrics videos as needed | TF-IDF + Logistic Regression and Naive Bayes |
| 21 | Revisit cross-validation/tuning videos/docs as needed | Model comparison, error analysis and manual-review policy |
| 22 | [scikit-learn pipelines](https://scikit-learn.org/stable/modules/compose.html), [pytest](https://docs.pytest.org/), [model persistence](https://scikit-learn.org/stable/model_persistence.html) | Reusable modules and tests |
| 23 | [FastAPI](https://fastapi.tiangolo.com/tutorial/) then [Docker](https://docs.docker.com/get-started/) if feasible | Local inference API/demo |
| 24 | No new videos; rerun from a clean environment and review failures | Final test-set evaluation, README, demo and reflection |

## Gates
Review after Weeks 3, 7, 10, 14, 17 and 24. Explain a model without notes, rerun an earlier notebook, compare to a baseline, inspect errors, check leakage and update [progress tracker](progress.md).

## Evaluation rules
Fit preprocessing only on training data, preferably using a pipeline. Use validation/CV for choices and final test data only once. Report class-level metrics and failure cases, not accuracy alone. Record data source, licence, split, metrics, environment and limitations.

## Capstone
The default is [CampusFix](projects/campusfix/README.md), a proposed campus infrastructure complaint triage prototype. Only call it campus evidence if permissioned campus data is actually used. If unavailable, use a public service-request dataset and label it as a proxy. Never present synthetic records as genuine complaints.
