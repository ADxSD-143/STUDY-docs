# Module 02 — Text Representation

**Status:** Completed  
**Purpose:** Convert text into numeric features that models can process.

## Theory

### Bag of Words (BoW)

Build a vocabulary and count each vocabulary term in each document. It is simple and interpretable, but ignores most word order and semantic similarity.

### N-grams

An n-gram is a contiguous sequence of n tokens. Unigrams are single tokens; bigrams capture pairs such as “not good.” N-grams can preserve some local context but increase feature dimensionality.

### TF-IDF

TF-IDF gives more weight to terms that are frequent in a document but less common across the full collection.

One common definition is:

\[
\operatorname{tfidf}(t,d)=\operatorname{tf}(t,d)\times\log\left(\frac{N}{\operatorname{df}(t)}\right)
\]

Where:
- \(\operatorname{tf}(t,d)\): frequency of term \(t\) in document \(d\) (implementation may normalize it).
- \(N\): number of documents.
- \(\operatorname{df}(t)\): number of documents containing term \(t\).

Libraries may use smoothing and normalization, so exact numeric values can differ.

## Code

```python
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer

texts = [
    "delivery was late",
    "late delivery and poor support",
    "support solved the issue",
]

bow = CountVectorizer(ngram_range=(1, 2))
X_bow = bow.fit_transform(texts)
print("BoW shape:", X_bow.shape)
print("Some features:", bow.get_feature_names_out()[:10])

tfidf = TfidfVectorizer(ngram_range=(1, 2))
X_tfidf = tfidf.fit_transform(texts)
print("TF-IDF shape:", X_tfidf.shape)
```

## Real-world use

TF-IDF is a strong, fast baseline for ticket classification, keyword-based retrieval and duplicate-text detection. Dense embeddings are often more suitable when semantic similarity matters beyond shared words.

## Critical data-leakage rule

Split data first. Fit the vectorizer only on training text, then call `transform` on validation/test text. In production, save and reuse the fitted vectorizer with the model.

## Interview checks

1. BoW vs TF-IDF? BoW counts terms; TF-IDF downweights terms common across documents.
2. Why use bigrams? They can capture short phrases and local word order.
3. Main limitation of TF-IDF? Sparse lexical features do not inherently understand synonyms or deeper meaning.

## Mini exercise

Compare “the service is good” and “the service is not good.” Explain how unigrams and bigrams may represent them differently, and what information could still be lost.

## Completion note

Module marked complete according to the course progress tracker. Module 03 builds on these representations to train and evaluate classifiers.
