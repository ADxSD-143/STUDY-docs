# Phase 5 — Projects and Engineering (Weeks 18–24)
Capstone brief: [CampusFix](../projects/campusfix/README.md).

## Week 18 — Define the problem before coding
Identify the workflow: student reports about Wi-Fi, water supply, lifts, AC and classroom/electrical faults need categorizing/routing. Ask permission to use anonymized campus complaints. If unavailable, use a public service-request dataset as a clearly labelled proxy. Never present invented records as real.
Deliverable: problem statement, intended user, data card, label guide, baseline, metrics and privacy/risk notes.

## Week 19 — Data and baseline
Audit missingness, duplicates/near duplicates and class counts. Build majority-class and simple keyword/rule baselines. Prevent duplicate reports crossing train/test; fit preprocessing on training folds only.
Deliverable: repeatable data pipeline and baseline report.

## Week 20 — Text classification
Train TF-IDF + Logistic Regression and compare Naive Bayes. Report per-class precision/recall/F1 and confusion matrix; inspect false negatives and uncertainty. Low-confidence predictions go to human review.
Deliverable: reproducible model notebook/script and error examples.

## Week 21 — Improve responsibly
Compare models with validation/CV; tune a small justified parameter set. Only model priority if reliable labelled data and a clear definition exist; otherwise priority remains human-assigned.
Deliverable: model selection report, limitations and manual-review policy.

## Week 22 — Tests and reproducibility
Separate data loading, preprocessing, training, evaluation and inference. Add tests for blank input, missing fields, unknown categories and output shape. Use a pipeline so vectorization is fit on training data. Save environment and dataset provenance.
Resources: [pytest](https://docs.pytest.org/), [scikit-learn pipelines](https://scikit-learn.org/stable/modules/compose.html), [model persistence](https://scikit-learn.org/stable/model_persistence.html).
Deliverable: tested package and setup instructions.

## Week 23 — API and demo
Build a minimal [FastAPI endpoint](https://fastapi.tiangolo.com/tutorial/) with input validation and manual-review flag. Add [Docker](https://docs.docker.com/get-started/) only if time/hardware permits.
Deliverable: local API/demo and exact run instructions.

## Week 24 — Final evaluation and release
Evaluate on the held-out test set once, after model choices are locked. Document source/licence, split, baselines, metrics, errors, privacy and limitations. Include stakeholder feedback only if a real stakeholder reviewed it.
Deliverable: release-ready repo, demo and reflection.

Safety: CampusFix is decision support, not autonomous complaint handling. Never suppress/close safety-critical reports or claim faster response times without a real pilot and measurements.
