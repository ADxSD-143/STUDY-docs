# ML Projects — Learn, Then Build

The 8-week beginner roadmap includes one small capstone in Week 8. Earlier weeks produce focused practice notebooks.

## Required mini-capstone
[CampusFix — Campus Infrastructure Complaint Triage](projects/campusfix/README.md): proposed ML-assisted classification/routing for campus Wi-Fi, water, lift, AC and classroom/electrical complaints.

| Week | Project work | Purpose |
|---|---|---|
| 2 | CSV exploration notebook | NumPy/pandas practice |
| 3 | Data audit and EDA report | Cleaning, feature/target understanding and safe split |
| 4–7 | Regression/classification/model comparison notebooks | Learn models and evaluation |
| 8 | CampusFix mini-capstone | End-to-end baseline, text model, evaluation and reproducible README |

## CampusFix data rules
Ask permission for campus records and anonymize them. If unavailable, use a public service-request dataset and label it as a proxy. Never present synthetic records as genuine campus data. Do not auto-close or suppress safety-critical reports. Do not claim operational impact without a real pilot and measurements.

## Completion checklist
- [ ] Problem and intended user are stated.
- [ ] Data source, licence, privacy and labels are documented.
- [ ] Simple baseline is included.
- [ ] Split and preprocessing avoid leakage.
- [ ] Metrics match the problem and class-level errors are inspected.
- [ ] Limitations and human-review cases are documented.
- [ ] Another person can reproduce the result from the README.
