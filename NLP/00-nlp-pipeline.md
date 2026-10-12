# NLP Pipeline — Traditional Foundations to Modern AI Systems

**Purpose:** Understand the end-to-end lifecycle before studying individual NLP techniques. This extends the classic NLP pipeline with current Transformer, RAG, evaluation, security and deployment practices.

## 1. What is an NLP pipeline?

An NLP pipeline is a sequence of connected steps that turns raw language data into a useful output. It includes more than model training: defining the problem, preparing data, representing text, selecting a model, evaluating results, deploying the system and improving it over time.

There is no single pipeline for every task. A spam classifier, named-entity recognizer, semantic search engine and RAG assistant share some foundations but have different processing paths.

## 2. High-level pipeline

```text
Problem definition and success metrics
                  ↓
Data acquisition and permissions
                  ↓
Data inspection, validation and labeling
                  ↓
Data splitting and leakage prevention
                  ↓
Text processing and representation
                  ↓
       ┌──────────┴───────────┐
       ↓                      ↓
Traditional NLP/ML       Modern NLP/LLM
TF-IDF, classifier       Transformer, embeddings,
or task pipeline         retrieval, RAG, optional tools
       └──────────┬───────────┘
                  ↓
Task-specific evaluation and error analysis
                  ↓
Application/API, testing, security and deployment
                  ↓
Monitoring, feedback, versioning and re-evaluation
                  ↺
```

The order is conceptual. Real systems may repeat stages or use different paths.

## 3. Stages and why they matter

### Stage 1 — Problem definition
Define the user, input, expected output, constraints and success criteria. Decide whether the task needs classification, extraction, search, summarization, generation or a multi-step workflow. Choose metrics before tuning the model.

### Stage 2 — Data acquisition
Obtain data from permitted datasets, APIs, documents or approved internal sources. Track provenance, licensing, privacy, label definitions and freshness. Supervised learning needs trustworthy labels; do not invent ground truth.

### Stage 3 — Data inspection and preparation
Check missing values, duplicates, label imbalance, encoding issues, noisy records and data quality. Split data into train/validation/test sets appropriately. Prevent duplicates or related examples from leaking across splits. Fit data-dependent transforms only on training data.

### Stage 4 — Text processing and representation
Apply task-appropriate normalization and tokenization. Classical models may use Bag of Words or TF-IDF; embedding-based systems use dense vectors; Transformers use model-specific tokenizers and token IDs. Do not blindly remove punctuation, stopwords or negation: preprocessing choices depend on the task and model.

### Stage 5A — Traditional NLP/ML path
Build a baseline, such as TF-IDF + Naive Bayes or Logistic Regression. For extraction tasks, use an appropriate sequence-labeling or library pipeline. Keep the preprocessing and model together so training and inference behave consistently.

### Stage 5B — Modern NLP/LLM path
Choose the simplest approach that meets requirements:
- **Pretrained Transformer:** classification, NER, summarization or question answering.
- **Embeddings + retrieval:** semantic search and matching.
- **RAG:** retrieve external evidence and provide it to a language model for grounded answering.
- **Fine-tuning/PEFT:** adapt a model when examples, task requirements and evaluation justify it.
- **Agentic workflow:** use approved tools and multi-step control only when the task requires actions or iterative decisions. Not every LLM app needs an agent.

### Stage 6 — Evaluation and error analysis
Evaluate on held-out data and inspect representative mistakes. Classification commonly uses precision, recall, F1 and a confusion matrix; ranking uses metrics such as Recall@k, MRR or nDCG; generation needs answer correctness, evidence faithfulness and citation checks. Use latency, reliability and resource use where relevant. For RAG, evaluate retrieval and generation separately.

### Stage 7 — Application and deployment
Package the full pipeline behind an API or UI. Add tests, reproducible configuration, logging, error handling, access control and safe handling of untrusted input. Use FastAPI and Docker when they fit the project; tools are means, not goals.

### Stage 8 — Monitoring and iteration
Track failures, latency, model/data versions and meaningful quality signals. Watch for changing data distributions, stale documents and regressions after updates. Re-evaluate before shipping changes. Collect user feedback responsibly and do not treat unreviewed feedback as automatically correct labels.

## 4. Modern RAG has two connected pipelines

### Offline indexing pipeline
```text
Approved documents
 → parse/extract text, tables and metadata
 → clean/validate and preserve source locations
 → structure-aware chunking
 → embedding + lexical indexing
 → store searchable chunks and metadata
 → evaluate index/retrieval quality
```

### Online question-answering pipeline
```text
User question
 → validate input and permissions
 → optional query rewrite/decomposition
 → lexical + dense retrieval when useful
 → fuse candidates and optionally rerank
 → build bounded context with source metadata
 → generate answer grounded in retrieved evidence
 → validate citations / abstain if evidence is insufficient
 → return answer and record safe evaluation traces
```

Hybrid retrieval is a useful option because lexical search can catch exact identifiers and rare terms while dense retrieval can find paraphrases. Reranking can improve candidate ordering, but adds latency and should be justified by evaluation. There is no universal chunk size, top-k or model choice: tune against a representative evaluation set and resource budget.

Security is part of the pipeline: apply authorization filters before content reaches the model, treat retrieved documents as untrusted data, and test prompt-injection and citation failures.

## 5. How the pipeline changes by task

| Task | Main path | Typical evaluation |
|---|---|---|
| Spam / ticket classification | Clean/inspect → TF-IDF → classifier | Precision, recall, F1 |
| NER / document extraction | Tokenizer → pretrained/fine-tuned model → structured entities | Entity-level precision, recall, F1 |
| Semantic search | Query/document embeddings → nearest-neighbor retrieval | Recall@k, MRR, nDCG |
| RAG document Q&A | Ingestion/indexing + retrieval + grounded generation | Retrieval quality, correctness, faithfulness, citation quality |
| Agentic assistant | Bounded workflow + approved tools + validation | Task success, tool correctness, safety, latency and cost |

## 6. Core principles to remember

1. Start with the problem and evaluation criteria, not the fanciest model.
2. A model cannot recover information that was lost or never retrieved.
3. Keep train/test boundaries clean to avoid misleading metrics.
4. Choose preprocessing for the task; more cleaning is not always better.
5. Use a baseline and change one component at a time where possible.
6. Evaluate each component and the end-to-end system.
7. Add RAG or agents only when they solve a real requirement.
8. Treat privacy, access control, untrusted text and monitoring as engineering concerns, not afterthoughts.

## 7. Learning sequence for this course

- First, discuss this pipeline and clarify its terminology.
- Then study the terms in manageable steps: data acquisition, cleaning, tokenization, representation, model, evaluation and deployment.
- Continue with Module 03 — Classical ML for Text.
- Study Transformers and embeddings before implementing RAG.
- Add agentic workflows after retrieval and tool-calling fundamentals.
- Build and measure three projects; update this document when practical decisions or architecture change.

## Sources for further reading

- CampusX, *End to End NLP Pipeline*: https://youtu.be/29qyNyNkLHs
- Hugging Face, *RAG Evaluation Cookbook*: https://huggingface.co/learn/cookbook/rag_evaluation
- Hugging Face Transformers documentation: https://huggingface.co/docs/transformers
