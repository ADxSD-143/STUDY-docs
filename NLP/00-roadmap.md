# NLP: Basics to Advanced — Roadmap + Progress

**Goal:** AI/ML Engineer-level NLP skills + 3 resume-ready projects.  
**Style:** theory → formula → code → real-world example → interview questions → mini exercise.  
**Pacing:** One module targets 60–90 minutes. Split it into smaller lessons if needed; understanding matters more than speed.

## Roadmap

| # | Module | Core ideas | Industry use |
|---|---|---|---|
| 01 | Text preprocessing | Tokenization, normalization, stemming, lemmatization, stopwords, regex | Search, chatbots, text analytics |
| 02 | Text representation | Bag of Words, TF-IDF, n-grams, sparse vectors | Search relevance, keyword extraction, baseline ML |
| 03 | Classical ML for text | Naive Bayes, Logistic Regression, precision, recall, F1, confusion matrix | Spam filtering, ticket routing, sentiment analysis |
| P1 | **Project 1: Text classifier** | Support-ticket/review classifier, baseline comparison, error analysis, API | Customer-support automation |
| 04 | Word embeddings | Word2Vec, GloVe, vector similarity, cosine similarity | Semantic search, recommendations |
| 05 | Sequence models | RNN, LSTM, seq2seq, attention | Understand the evolution toward Transformers |
| 06 | Transformers | Tokenization, self-attention, positional information, BERT vs GPT | Foundation of modern NLP and LLMs |
| 07 | Hugging Face + fine-tuning | Pretrained models, NER, QA, summarization, fine-tuning, LoRA/PEFT concepts | Document intelligence and information extraction |
| P2 | **Project 2: Transformer** | Fine-tuned transformer for NER or classification, metrics and error analysis | Resume/document intelligence |
| 08 | LLMs, RAG + agentic integration | Prompting, embeddings, chunking, vector search, hybrid retrieval, reranking, RAG evaluation, tool calling, MCP | Grounded enterprise assistants and controlled workflows |
| P3 | **Project 3: RAG assistant** | Document Q&A, citations, retrieval/generation evaluation, optional bounded tool use | Chat with documents |
| 09 | Deployment + evaluation | FastAPI, Docker, tests, monitoring, cost/latency, reproducibility | Production-ready ML/AI services |

## Progress tracker

- [x] 01 Text preprocessing
- [x] 02 Text representation
- [ ] 03 Classical ML for text
- [ ] P1 — Text classifier
- [ ] 04 Word embeddings
- [ ] 05 Sequence models
- [ ] 06 Transformers
- [ ] 07 Hugging Face + fine-tuning
- [ ] P2 — Fine-tuned transformer
- [ ] 08 LLMs, RAG, vector DBs + agentic integration
- [ ] P3 — RAG document Q&A app
- [ ] 09 Deployment + evaluation

## Module note checklist

Each completed module note should contain:
1. **Theory** — intuition and key concepts.
2. **Formulas** — notation explained, with a worked example when useful.
3. **Code** — short, runnable Python examples.
4. **Real-world example** — where and why the technique is used.
5. **Interview questions** — focused questions with clear answers.
6. **Mini exercise** — a checkpoint to verify understanding.

Notes are committed as we finish modules. The progress tracker must reflect actual learning progress; do not mark a module complete merely because its file exists.

## Project standards

Each project gets a separate folder containing a README, reproducible setup/run instructions, dataset/source notes, a results table, known limitations, and resume bullet points. Results must come from actual experiments, not invented metrics.

- **Project 1:** Compare a simple baseline with a stronger classical text classifier. Include class-wise metrics and error analysis.
- **Project 2:** Fine-tune or adapt a pretrained Transformer for a defined NER/classification task. Record the data split, baseline, metrics and failure cases.
- **Project 3:** Build a document Q&A RAG system with citations. Evaluate retrieval separately from answer quality; include hallucination/abstention cases.

## Modern topics included without bloating the course

- RAG: chunking, embedding models, vector search, hybrid retrieval, reranking and evaluation.
- Agentic integration: structured outputs, approved tool calling, workflows and MCP basics.
- Production concerns: prompt injection and untrusted retrieved content, testing, observability, latency and cost.
- Advanced electives only when useful: multilingual/code-mixed NLP, quantization, multimodal document processing and advanced retrieval.

We will learn older methods such as RNNs and LSTMs to understand the progression of NLP, but spend more implementation time on Transformers, retrieval systems and reliable LLM applications.

## Next lesson

**Module 03 — Classical ML for text:** begin with the end-to-end text-classification pipeline, then learn Naive Bayes and Logistic Regression for text, followed by evaluation metrics.