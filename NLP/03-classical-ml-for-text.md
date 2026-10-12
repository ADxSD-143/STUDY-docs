# Module 03 — Classical ML for Text

**Status:** Not started  
**Goal:** Train, compare and evaluate classical machine-learning models using text features from Module 02.

## Learning sequence

1. End-to-end text-classification pipeline and data splitting
2. Naive Bayes: intuition, assumptions, formula and code
3. Logistic Regression for sparse text features
4. Confusion matrix, precision, recall, F1 and class imbalance
5. Compare models and perform error analysis

## Core pipeline

```text
Labeled text
  → train/validation/test split
  → fit vectorizer on training text
  → transform text into features
  → train classifier
  → evaluate on unseen data
  → inspect mistakes
```

## Formula preview: precision and recall

\[
\text{Precision}=\frac{TP}{TP+FP}
\qquad
\text{Recall}=\frac{TP}{TP+FN}
\]

- **TP:** correctly predicted positive examples.
- **FP:** negative examples incorrectly predicted positive.
- **FN:** positive examples incorrectly predicted negative.

Precision answers “Of the items predicted positive, how many were correct?” Recall answers “Of all actual positive items, how many did we find?”

## Code preview

```python
from sklearn.pipeline import Pipeline
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression

texts = [
    "refund has not arrived",
    "excellent customer service",
    "my payment failed",
    "great product and fast delivery",
    "cancel my order and refund me",
    "very happy with this purchase",
]
labels = ["complaint", "positive", "complaint", "positive", "complaint", "positive"]

model = Pipeline([
    ("tfidf", TfidfVectorizer()),
    ("classifier", LogisticRegression(max_iter=1000)),
])
model.fit(texts, labels)
print(model.predict(["my refund is delayed"]))
```

**Important:** This tiny example is only for demonstrating the API, not for measuring performance. A real project needs a suitable labeled dataset, a held-out test set, and error analysis.

## Real-world connection

Support-ticket routing can direct a complaint to billing or delivery teams. Evaluation must consider the cost of each error: missing an urgent complaint may be more harmful than sending an ordinary ticket to a human for review.

## Interview questions

To be completed as we cover the module:
- Why is TF-IDF + Logistic Regression a useful baseline?
- How does Naive Bayes use conditional probabilities?
- When is recall more important than precision?
- Why must the test set remain untouched during model selection?

## Mini exercise

Given TP = 36, FP = 9 and FN = 4, calculate precision and recall. Explain which metric would be more relevant if missing a high-priority complaint were especially costly.

**Progress rule:** Do not mark this module complete until the concepts, code and checkpoint have been reviewed.
