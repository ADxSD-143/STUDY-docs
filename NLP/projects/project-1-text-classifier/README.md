# Project 1 — Support-Ticket / Review Classifier

**Status:** Planned

## Objective
Classify short text into useful categories (for example, support-ticket type or review sentiment) and expose predictions through an API.

## Planned workflow
1. Select a real, appropriately licensed dataset and document its source.
2. Inspect label definitions, class balance, duplicates and missing values.
3. Establish a majority-class baseline.
4. Compare TF-IDF + Naive Bayes against TF-IDF + Logistic Regression.
5. Evaluate with a confusion matrix, precision, recall, F1 and class-wise metrics.
6. Inspect failure cases and document limitations.
7. Serve the chosen pipeline through FastAPI; add tests and run instructions.

## Results
| Model | Dataset/split | Accuracy | Precision/Recall/F1 | Notes |
|---|---|---:|---|---|
| Baseline | Pending | — | — | Not measured |
| Naive Bayes | Pending | — | — | Not measured |
| Logistic Regression | Pending | — | — | Not measured |

Do not enter guessed metrics. Populate this table after running experiments.

## Resume bullets
Draft only; finalize after implementation and measurement:
- Built a text-classification pipeline using TF-IDF and classical ML, comparing models with class-wise evaluation and error analysis.
- Exposed the trained pipeline through a tested FastAPI endpoint.

## Limitations
To be documented after experiments.
