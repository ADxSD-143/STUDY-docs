# ML Projects — Learn, Then Build

The 8-week beginner roadmap applies the complete [Stage 0–13 ML project workflow](ml-project-workflow.md) to one small capstone in Week 8. Earlier weeks produce focused practice notebooks.

## Required mini-capstone
[CampusFix — Campus Infrastructure Complaint Triage](projects/campusfix/README.md): proposed ML-assisted classification/routing for campus Wi-Fi, water, lift, AC and classroom/electrical complaints.

| Week | Project work | Workflow stages |
|---|---|---|
| 1 | Problem brief and Python exercises | Stage 0 |
| 2 | Dataset source note, data audit and EDA notebook | Stages 1–2 |
| 3 | Split, cleaning, preprocessing and feature preparation | Stages 3–5 |
| 4 | Baseline, Linear Regression/Logistic Regression practice | Stages 6–7 |
| 5 | NB/KNN comparison and classification metrics | Stages 7–8 |
| 6 | Tree/forest comparison and error analysis | Stages 7–8, 10 |
| 7 | Cross-validation, tuning basics, final evaluation and saved pipeline | Stages 8–11 |
| 8 | CampusFix end-to-end mini-capstone and README | Stages 0–13 at beginner depth |

## CampusFix data rules
Ask permission for campus records and anonymize them. If unavailable, use a public service-request dataset and label it as a proxy. Never present synthetic records as genuine campus data. Do not auto-close or suppress safety-critical reports. Do not claim operational impact without a real pilot and measurements.

## Completion checklist
- [ ] Problem, intended user and success metric are stated before modeling.
- [ ] Data source, licence, privacy and labels are documented.
- [ ] EDA insights are recorded.
- [ ] Split and preprocessing avoid leakage.
- [ ] Baseline is included.
- [ ] Appropriate models and metrics are compared.
- [ ] Validation and test-set usage are correct.
- [ ] Error analysis and limitations are documented.
- [ ] Saved pipeline can be reloaded and predictions reproduced.
- [ ] README explains how to run the project and what it cannot prove.
- [ ] Deployment/monitoring claims match what is actually implemented.
