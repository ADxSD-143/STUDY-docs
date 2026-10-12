# NLP Roadmap: Basics to Production

**Goal:** Build a clear foundation in NLP, then use it to build 2–3 portfolio projects. This is a practical course, not a list of libraries to memorize.

## Phase 1 — Text and language fundamentals
1. What NLP is; task types and end-to-end pipeline
2. Text normalization, Unicode, regular expressions, tokenization
3. Stop words, stemming, lemmatization; when *not* to clean text
4. N-grams, Bag of Words, TF-IDF, sparse vectors
5. Train/validation/test splits, leakage, class imbalance, evaluation metrics

**Outcome:** Understand and build a reliable classical text-classification baseline.

## Phase 2 — Classical NLP in practice
6. Naive Bayes and Logistic Regression for text
7. Precision, recall, F1, confusion matrix, threshold selection
8. Error analysis, cross-validation, pipelines, reproducibility
9. POS tagging, named entity recognition (NER), phrase extraction
10. Similarity, duplicate detection, keyword and information extraction

**Project 1:** NLP Classifier API — compare a simple baseline with a stronger model; report metrics and failure cases; serve predictions with FastAPI.

## Phase 3 — Neural NLP and embeddings
11. Neural-network essentials for language tasks
12. Word embeddings: Word2Vec, GloVe, FastText (concepts and practical relevance)
13. Sequence models: RNN, LSTM, GRU (why they mattered; limitations)
14. Attention and the Transformer architecture
15. Subword tokenization (BPE/WordPiece), contextual embeddings, encoder vs decoder models

**Outcome:** Explain how modern language models represent and process text.

## Phase 4 — Transformers and LLM application engineering
16. Use pretrained models with Hugging Face
17. Fine-tuning vs prompting vs retrieval: choosing the right approach
18. Text classification, NER, summarization, question answering
19. Embeddings, cosine similarity, semantic search
20. Efficient adaptation: transfer learning, PEFT/LoRA concepts, quantization basics

## Phase 5 — RAG systems
21. RAG architecture and when RAG is useful
22. Document ingestion, parsing, chunking, metadata
23. Embedding models and vector search
24. Retrieval quality: top-k, similarity, hybrid search, reranking
25. Context construction, grounded answers, citations, abstention
26. RAG evaluation: retrieval metrics, answer correctness, faithfulness, latency and cost
27. Advanced patterns: query rewriting, multi-step retrieval, corrective/adaptive RAG; agentic RAG where justified

**Project 2:** A document-grounded RAG assistant with citations and an evaluation set. Compare retrieval approaches rather than merely making a chatbot.

## Phase 6 — Agents and production
28. LLM tool/function calling and structured outputs
29. Workflows vs agents; state, planning, memory, retries and human approval
30. MCP: how models/clients connect to tools and data sources
31. Guardrails: prompt injection, untrusted documents, permissions and data privacy
32. Evaluation and observability: traces, regression tests, failure analysis
33. Deployment with FastAPI, Docker, logging, configuration and monitoring

**Project 3:** A bounded agentic knowledge assistant that retrieves evidence, calls approved tools, returns structured results, and records evaluation traces.

## Phase 7 — Advanced topics (select based on project needs)
- Multilingual NLP and code-mixed text
- Long-context processing and document intelligence
- Information extraction and knowledge graphs
- Rerankers and late-interaction retrieval
- Small language models, local inference and quantization
- Fine-tuning data quality, preference/alignment concepts
- Multimodal systems: text with images, audio or documents
- Agent reliability, benchmark design and cost/latency optimization

## Default tools
- Python, scikit-learn, pandas, spaCy or NLTK
- Hugging Face Transformers and Datasets
- PyTorch when neural-network internals become relevant
- Sentence Transformers for embeddings
- FAISS or a lightweight vector store for local retrieval
- FastAPI and Docker for serving/deployment

We will choose tools when needed, not install everything on day one. Prefer free/local models and datasets where feasible.

## Lesson format
Every lesson should contain: **intuition → key concepts/formulas → short runnable code → real-world use → common mistake → checkpoint**. Keep the pace small and focused. Update this roadmap if tools or industry practices materially change.

## Progress tracker
- [ ] Phase 1 — Foundations
- [ ] Phase 2 — Classical NLP
- [ ] Project 1 — Classifier API
- [ ] Phase 3 — Neural NLP and Transformers
- [ ] Phase 4 — Pretrained models and fine-tuning
- [ ] Phase 5 — RAG
- [ ] Project 2 — RAG assistant
- [ ] Phase 6 — Agents, MCP and production
- [ ] Project 3 — Agentic assistant
- [ ] Phase 7 — Advanced electives
