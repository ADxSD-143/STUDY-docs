# Lesson 1 — What Is NLP?

**Status:** In progress  
**Goal:** Understand what NLP does and how a real NLP system turns raw text into a useful output.

## 1. Definition

**Natural Language Processing (NLP)** is the area of AI that helps computers process, analyze, and generate human language.

Examples:
- Email spam detection
- Sentiment analysis of reviews
- Extracting names, dates and locations from documents
- Search that understands meaning
- Translation and summarization
- RAG systems that answer from your documents

## 2. The basic pipeline

```text
Raw text
   ↓
Inspect and prepare the text
   ↓
Represent text numerically
   ↓
Model learns patterns / retrieves relevant information
   ↓
Prediction or generated answer
   ↓
Evaluate errors and improve
```

Example input: `"The delivery was late, and support never replied."`

Possible tasks:
- **Sentiment analysis:** negative
- **Classification:** delivery/support complaint
- **Information extraction:** delivery issue, support issue
- **Summarization:** "The customer reports a late delivery and no support response."
- **Semantic search:** find similar complaints

One sentence can support different tasks. The task definition and expected output determine the system.

## 3. Why text must be represented

Most traditional ML algorithms operate on numbers, not raw sentences. We therefore convert text into numeric features.

A tiny example:

```python
from sklearn.feature_extraction.text import CountVectorizer

texts = [
    "I like NLP",
    "I like machine learning",
    "NLP is useful",
]

vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)

print(vectorizer.get_feature_names_out())
print(X.toarray())
```

**What happens?**
- The vectorizer builds a vocabulary from the training texts.
- Each row represents one document.
- Each column represents a vocabulary word.
- Each cell counts how often that word appears in that document.

This is called a **Bag of Words** representation. It is simple and useful as a baseline, but it largely ignores word order and deeper meaning. We will study it properly later.

**Important:** In a real ML pipeline, fit the vectorizer on training data only, then use the fitted vectorizer to transform validation/test data. Fitting it on all data can leak information.

## 4. Traditional NLP vs modern LLM applications

| Approach | Core idea | Typical use |
|---|---|---|
| Rules / regex | Explicit patterns | IDs, dates, predictable formats |
| TF-IDF + ML | Word statistics + classifier | Spam, ticket routing, sentiment baselines |
| Neural models / Transformers | Learned contextual representations | NER, classification, summarization |
| Embeddings + retrieval | Search by semantic similarity | Semantic search, document retrieval |
| LLM + RAG | Generate using retrieved evidence | Document Q&A with citations |
| Agentic workflow | Model selects from approved tools/steps | Multi-step tasks with controls and evaluation |

These approaches are not interchangeable. A small classifier or deterministic rule may be cheaper and more reliable than an LLM for a narrow task. RAG helps when answers need external or changing knowledge; agents are useful only when a task genuinely requires multiple actions or tool use.

## 5. How we judge an NLP system

Do not judge a model only by whether a few examples look correct. Choose metrics based on the task:
- Classification: precision, recall, F1 and confusion matrix
- Search/retrieval: Recall@k, MRR or nDCG
- Generated answers: correctness, evidence faithfulness, citation quality, plus latency and cost

We will learn each metric before relying on it in projects.

## 6. Industry connection

A support-ticket system might classify the ticket first, extract order details second, and retrieve the relevant policy before drafting a response. This is a pipeline of smaller components—not necessarily one giant model.

For a resume-ready project, show the **problem, dataset, baseline, evaluation, error analysis, API/demo, and limitations**. A project is stronger when you can explain why you chose each component and demonstrate measured performance.

## 7. Checkpoint

Answer in your own words; short answers are fine.

1. Why do many traditional ML algorithms need text to be converted into numbers?
2. In the example above, what does one row and one column of the Bag of Words matrix represent?
3. You need to answer questions using a company's latest internal policy documents. Which broad approach is more suitable: a fixed text classifier or RAG? Why?
4. Why should a vectorizer be fitted on training data only?

**Next lesson:** Text data, normalization, Unicode, and regular expressions.
