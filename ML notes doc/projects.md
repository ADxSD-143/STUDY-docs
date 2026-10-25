# ML Projects — Learn, Then Build
Projects follow the roadmap rather than starting before prerequisites.

## Required capstone
[CampusFix — Campus Infrastructure Complaint Triage](projects/campusfix/README.md): proposed ML-assisted classification/routing for campus Wi-Fi, water, lift, AC and classroom/electrical complaints. Weeks 18–24 are reserved for problem/data framing, baselines, text classification, error analysis, tests, API and final evaluation.

## Project ladder
| Stage | Weeks | Work | Purpose |
|---|---|---|---|
| Data drill | 4–5 | Data audit and EDA report | Cleaning and feature understanding |
| Model drills | 6–14 | Regression/classification comparison | Implement algorithms and evaluate baselines |
| Unsupervised drill | 16–17 | Clustering/PCA report | Learn unsupervised methods |
| Capstone | 18–24 | CampusFix | End-to-end ML and responsible demo |

## CampusFix rules
Ask permission for campus records and anonymize them. If unavailable, use a public service-request dataset and label it as a proxy. Never present synthetic records as genuine campus data. Do not auto-close or suppress safety-critical reports. Do not claim operational impact without a real pilot and measurements.

## Main-project completion checklist
- [ ] Problem and intended user are stated.
- [ ] Data source, licence, privacy and labels are documented.
- [ ] Simple baseline is included.
- [ ] Split/preprocessing avoid leakage.
- [ ] Metrics match the problem and class-level errors are inspected.
- [ ] Held-out evaluation is compared with baseline.
- [ ] Code reruns from documented instructions.
- [ ] Tests cover important preprocessing/inference behaviour.
- [ ] Failure cases and limitations are clear.
- [ ] Demo/API follows sound evaluation, not the other way around.
