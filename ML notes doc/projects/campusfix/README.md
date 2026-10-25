# CampusFix — Campus Infrastructure Complaint Triage

A proposed real-world ML capstone for learning data cleaning, text classification, model evaluation and ML engineering through a concrete operations problem.

## Problem
Student reports about Wi-Fi outages, water supply, broken lifts, AC failures and classroom/electrical faults need categorizing and routing. CampusFix tests whether an ML-assisted tool can suggest a complaint category and responsible department.

This is a proposed project, not a claim that campus administration has agreed to use it.

## Intended output
Input: one complaint description. Output: suggested category/department, model score if useful, and a manual-review flag for uncertain predictions. Predict priority only if trustworthy labels and a clear operational definition exist; otherwise a human assigns priority. Never auto-close or suppress safety-critical complaints.

## Data plan
1. Ask permission to use anonymized campus complaint records.
2. Remove names, phone numbers, roll numbers, emails and identifying room-level details.
3. Record source, licence, collection window, label definitions, class counts and preprocessing.
4. If campus data is unavailable, use a public complaint/service-request dataset as a proxy and explicitly state it is not campus evidence.
5. Do not fabricate records and present them as genuine complaints. Disclose labelling rules and limitations for any manually labelled sample.

Possible permitted fields: complaint text, category, department, priority, coarse location and date. Exclude personal identifiers.

## Baselines and models
- Baseline 1: majority-class prediction.
- Baseline 2: transparent keyword/rule mapping.
- Model 1: TF-IDF + Logistic Regression.
- Model 2: Multinomial Naive Bayes.
- Optional: linear SVM if time allows.

## Evaluation
- Prevent identical or near-duplicate complaints crossing train/test.
- Use a chronological split only when timestamps/data volume justify future prediction; otherwise use a suitable stratified split.
- Fit vectorization only on training folds through a pipeline.
- Report per-class precision, recall, F1, confusion matrix and macro-F1; compare against both baselines.
- Inspect false negatives for potentially urgent categories; do not rely on accuracy alone.
- Use validation/CV for selection and touch the final test set once after decisions are locked.
- Low-confidence predictions go to manual review.

## Schedule
| Week | Work |
|---|---|
| 4–5 | Cleaning, EDA and feature preparation |
| 8–10 | Logistic Regression, metrics, Naive Bayes and KNN learning |
| 18 | Problem framing, data permission and labels |
| 19 | Data audit and baselines |
| 20 | TF-IDF + Logistic Regression and Naive Bayes |
| 21 | Validation and error analysis |
| 22 | Tests, pipeline and reproducibility |
| 23 | FastAPI demo; Docker if feasible |
| 24 | Final evaluation, documentation and demo |

## Completion criteria
The project runs from documented instructions, compares models to baselines, reports held-out performance honestly, shows failure cases and documents data/privacy limits. Real impact claims require a stakeholder pilot and measured outcomes.
