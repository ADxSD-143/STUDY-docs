# Week 8 — Mini-Capstone and Reproducible Delivery

Default project: [CampusFix — Campus Infrastructure Complaint Triage](../projects/campusfix/README.md).

**Scope:** build a small, honest, reproducible ML prototype. Full production deployment, Docker, monitoring and a large application are not expected in this beginner sprint.

## Work sequence
1. Define intended user, problem and target label. Ask permission before using campus complaints; anonymize records. If access is unavailable, use a public service-request dataset and label it as a proxy. Never present invented records as real complaints.
2. Build a majority-class baseline and a simple keyword/rule baseline.
3. For text, try TF-IDF + Logistic Regression; optionally compare Multinomial Naive Bayes.
4. Use a leakage-safe split; report class-level precision/recall/F1, confusion matrix and common errors. Do not rely on accuracy alone.
5. Document limitations, privacy considerations and cases requiring human review.
6. Organize notebook/code, requirements file and README so another person can rerun the experiment.

## Deliverable
Problem statement, dataset source/licence/data card, label definitions, baseline, trained model, evaluation/error analysis, limitations/privacy notes and run instructions.

## After the 8-week core
Continue with FastAPI, tests, Docker, CI, monitoring and drift. These are valuable engineering skills but should not replace model understanding and evaluation.