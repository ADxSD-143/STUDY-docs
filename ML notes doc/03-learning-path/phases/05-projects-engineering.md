# Week 8 — End-to-End Mini-Capstone

Default project: [CampusFix — Campus Infrastructure Complaint Triage](../../04-projects/campusfix/README.md).

Use the [Stage 0–13 ML project workflow](../../06-reference/ml-project-workflow.md) as the project checklist. The goal is to apply the full lifecycle at beginner depth, not to build a production platform in one week.

## CampusFix project sequence
1. **Problem framing:** define intended user, complaint category target, baseline and suitable evaluation metrics.
2. **Data collection:** ask permission for anonymized campus records. If unavailable, use a documented public service-request dataset and label it as a proxy. Record source/licence and limitations. Never present invented records as genuine complaints.
3. **EDA:** inspect missingness, duplicates, class distribution, text lengths and label quality; write findings.
4. **Split:** choose a valid split before fitting any learned preprocessing. Avoid duplicate/near-duplicate leakage.
5. **Preprocessing/features:** TF-IDF for text; use a scikit-learn Pipeline so vectorization is fit on training data only.
6. **Baseline:** majority-class and/or simple keyword/rule baseline.
7. **Modeling:** TF-IDF + Logistic Regression; optionally compare Multinomial Naive Bayes.
8. **Evaluation:** report per-class precision/recall/F1 and confusion matrix; do not rely on accuracy alone.
9. **Error analysis:** inspect false negatives, urgent categories, weak classes and low-confidence predictions.
10. **Packaging:** save the complete vectorizer + model pipeline, record requirements and make a reproducible prediction script.
11. **Documentation:** README with problem, data source/licence, baseline, results, errors, limitations, privacy and run instructions.

A human must confirm routing and priority. The system must never auto-close or suppress safety-critical reports.

## Deliverable
Problem brief, dataset source note, EDA notebook, leakage-safe training pipeline, baseline/model comparison, final evaluation, error analysis, saved pipeline and reproducible README.

## Optional engineering extension
A local FastAPI endpoint or Streamlit/Gradio UI may be attempted only after the model and evaluation are complete. Docker, cloud deployment, CI/CD, monitoring and drift detection are continuation work—not required to call this beginner capstone complete.

## Claims and safety
Do not claim faster campus response or operational impact without a real stakeholder pilot and measured evidence. Do not log sensitive complaint text unnecessarily. Document cases that require human review.