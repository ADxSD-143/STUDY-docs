# Module 01 — Text Preprocessing

**Status:** Completed  
**Purpose:** Convert raw text into a consistent form without deleting information the task needs.

## Theory

Text preprocessing may include Unicode normalization, whitespace cleanup, lowercasing, tokenization, regular expressions, stopword filtering, stemming and lemmatization. The correct steps depend on the task; aggressive cleaning can remove meaning.

- **Tokenization:** split text into tokens (words, subwords or punctuation).
- **Normalization:** standardize text, such as whitespace or Unicode forms.
- **Regex:** match predictable patterns such as IDs, dates or email-like strings.
- **Stopwords:** frequent words sometimes removed for particular tasks; do not remove them blindly.
- **Stemming:** heuristic reduction, e.g. “playing” → “play” or sometimes a non-word stem.
- **Lemmatization:** map a word to a dictionary form using linguistic information.

## Example

```python
import re
import unicodedata

text = "  The delivery was LATE!!!  Order #A-123  "
text = unicodedata.normalize("NFKC", text)
text = re.sub(r"\s+", " ", text).strip()
tokens = re.findall(r"\b\w+\b|[^\w\s]", text.lower())

print(text)
print(tokens)
```

Output tokens include `late`, `order`, `a`, `123` and punctuation tokens. Regex patterns should be adjusted if order IDs need to remain intact.

## Real-world use

Support-ticket routing may normalize whitespace and extract order IDs, while sentiment analysis should preserve negation such as “not good.” Search pipelines may use different preprocessing from a classifier.

## Common mistakes

- Removing “not”, “never” or punctuation when they carry meaning.
- Applying English stopword lists to multilingual/code-mixed text.
- Using the same preprocessing rules for every task.
- Fitting data-dependent transformations before splitting the dataset.

## Interview checks

1. Stemming vs lemmatization? Stemming uses heuristics; lemmatization uses linguistic analysis to find a lemma.
2. Should every NLP task remove stopwords? No; the decision depends on the task and model.
3. Why normalize Unicode? Visually similar text can have different underlying code-point sequences.

## Mini exercise

For “I do NOT recommend this product!!!”, identify which preprocessing steps are safe and explain why removing “NOT” could harm sentiment classification.

## Completion note

Module marked complete according to the course progress tracker. Revise with the mini exercise if any concept feels unclear.
