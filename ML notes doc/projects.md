# Machine Learning Projects — Real Problems, Open-Source Practice

The goal is not to collect many copied projects. Build a small number of useful systems end-to-end, explain why each design choice was made, test failure cases, and make the work reproducible. The ideas below are starting points: validate the problem with potential users before claiming that a project solves it.

## Project ladder

### 1. Campus Issue Intelligence
**Problem:** Campus complaints about Wi-Fi, water, lifts, or classroom equipment get scattered across forms and messages, making recurring issues hard to prioritize.

**Build:** A complaint intake tool that classifies issue category, detects near-duplicate reports, groups reports by location, and shows a transparent priority queue. Keep human review in the loop; never let a model silently dismiss a safety-related complaint.

**Skills:** pandas, text preprocessing, TF-IDF, logistic regression, precision/recall, clustering, FastAPI, SQL, dashboarding.

**Open-source path:** Start with a small manually labelled and privacy-safe sample; publish schema, data card, annotation rules, baseline model, tests, and setup instructions. Do not upload private student messages or identifying information.

### 2. Public-Service Form and Notice Explainer
**Problem:** Long public notices and forms are difficult to navigate, especially for first-time applicants or readers more comfortable in Hindi/Hinglish.

**Build:** A tool that extracts text from public documents, identifies dates/deadlines/eligibility statements, and produces a plain-language summary with page/paragraph references. Show the source excerpt beside every extracted item; do not invent legal or eligibility advice.

**Skills:** preprocessing, information extraction, classification, OCR as an optional extension, evaluation, multilingual testing, API design.

**Open-source path:** Use openly licensed public documents, record the source and license, test extraction failures, and allow corrections through issues or pull requests.

### 3. Food-Waste Demand Forecaster
**Problem:** A canteen or small food provider needs to estimate demand to reduce leftovers without frequently running out.

**Build:** A forecasting baseline using historical sales, weekday, holidays, weather only if a legitimate data source is available, and special-event indicators. Compare against simple baselines and report uncertainty; recommendations should be advisory.

**Skills:** EDA, time-based split, regression, MAE/RMSE, feature engineering, leakage prevention, monitoring.

**Open-source path:** Use a public dataset or obtain explicit permission for anonymized data. Never pretend synthetic demo data proves real-world accuracy.

### 4. Accessibility-Friendly Learning Resource Finder
**Problem:** Students struggle to find an explanation at the right level, language, length, or format.

**Build:** Search and rank openly licensed learning resources using metadata such as topic, prerequisites, language, duration, captions, and resource type. Start with keyword search; add TF-IDF/embeddings only if evaluation shows a benefit.

**Skills:** text representation, ranking, evaluation, metadata quality, API and UI design.

**Open-source path:** Link to original resources rather than rehosting copyrighted videos or notes. Keep license and attribution metadata.

### 5. Local Air-Quality Pattern Explorer
**Problem:** Public air-quality measurements are hard to interpret over time and by location.

**Build:** An analysis dashboard that cleans public time-series measurements, flags missing/suspicious values, visualizes trends, and tests simple forecasting or anomaly-detection baselines. It must distinguish measured values from model estimates and avoid medical claims.

**Skills:** data quality, visualization, time-series validation, anomaly detection, uncertainty.

**Open-source path:** Use a documented public data source and publish data provenance, limitations, and reproducible analysis scripts.

### 6. Disaster-Report Triage Assistant
**Problem:** During a crisis, incoming public reports can be repetitive, incomplete, and difficult to sort quickly.

**Build:** A human-reviewed prototype that categorizes reports, detects duplicates, extracts reported location/time, and surfaces uncertainty. Do not invent labels, infer a precise location without evidence, or present model output as verified ground truth.

**Skills:** NLP, imbalanced classification, recall/precision trade-offs, geospatial data, evaluation, API engineering.

**Open-source path:** Use appropriately licensed crisis datasets, document label limitations, avoid publishing personal data, and make it clear that the prototype is not an emergency-response authority.

### 7. Claim Evidence Explorer
**Problem:** Readers need to inspect the evidence behind a claim rather than receive an unsupported “true/false” answer.

**Build:** A system that breaks a claim into checkable statements, retrieves sources, displays supporting/contradicting/unclear evidence, and links each conclusion to source passages. Begin with retrieval and evidence display; only add automated verdicts after evaluating them against human-reviewed examples.

**Skills:** text classification, retrieval, ranking, source provenance, evaluation, multilingual handling, backend engineering.

**Open-source path:** Keep source URLs, timestamps, snippets, and retrieval failures visible. Respect website terms, licenses, and rate limits; never fabricate citations.

### 8. Model Error Explorer
**Problem:** A model can look strong on one aggregate score while failing on particular classes or data slices.

**Build:** A reusable tool that takes predictions and labels, reports per-class metrics, shows false positives/negatives, compares thresholds, and flags likely data leakage or split mistakes for manual investigation.

**Skills:** metrics, calibration, subgroup evaluation, visualization, test design, data validation.

**Open-source path:** Start as a tested Python package with example datasets, then add a lightweight interface. This is a strong early contribution because it can be useful without training a large model.

## Required workflow for every project

1. **Problem validation:** Who experiences the problem? What decision will the tool improve? What is the baseline today?
2. **Data provenance:** Record source, license, collection date, schema, label process, privacy risks, and known gaps.
3. **Baseline first:** Use a simple rule or statistical baseline before complex ML.
4. **Leakage-resistant evaluation:** Choose train/validation/test strategy based on the data; for time-dependent problems, split by time.
5. **Error analysis:** Inspect representative failures and quantify the cost of false positives and false negatives.
6. **Useful interface:** Provide a CLI, API, or small UI only after the core method works.
7. **Engineering:** Add setup instructions, dependency file, configuration, tests, logging, reproducible seeds, and CI.
8. **Documentation:** Include problem statement, architecture, data card, model card, metrics, limitations, screenshots where useful, and a demo.
9. **Open-source contribution:** Use issues, small PRs, code review, tests, and changelog entries. Credit datasets and upstream projects.
10. **Honest release:** Separate measured results from goals; never claim real-world impact without a real evaluation.

## Definition of done

A project is ready to share when another person can reproduce the baseline, understand the data and license, run tests, see the evaluation protocol, inspect failures, and understand when not to trust the model. A polished README is not a substitute for evidence.

## Recommended first project

Start with **Model Error Explorer** or **Campus Issue Intelligence**. The first builds core evaluation and engineering skills with low data-collection risk. The second is more domain-specific, but should only use consented or public, privacy-safe data and should keep humans responsible for prioritization.
