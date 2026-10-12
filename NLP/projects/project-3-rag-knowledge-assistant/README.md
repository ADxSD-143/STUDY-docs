# Project 3 — RAG Knowledge Assistant

**Status:** Planned

## Objective
Build a document question-answering application that retrieves relevant evidence and produces answers with source citations. Add bounded tool use only when it improves a defined workflow.

## Planned workflow
1. Collect a small, permitted document corpus and define representative questions.
2. Parse documents, preserve metadata and experiment with chunking.
3. Build a local embedding + vector-search baseline.
4. Compare retrieval options, including lexical/hybrid search and reranking where useful.
5. Generate grounded answers with citations and an explicit “insufficient evidence” path.
6. Evaluate retrieval separately from generation.
7. Add tests for irrelevant queries, conflicting evidence and prompt injection in retrieved documents.
8. Expose the app through a simple interface/API and document latency and compute requirements.

## Evaluation plan
| Component | Candidate measures | Status |
|---|---|---|
| Retrieval | Recall@k, MRR or nDCG on a labeled question set | Pending |
| Answers | Correctness, faithfulness to evidence, citation quality | Pending |
| Operations | Latency, failure rate, resource use | Pending |

Metrics and thresholds will be chosen based on the task. No performance claims until evaluated.

## Resume bullets
Draft only; finalize after implementation and measurement:
- Built a document-grounded RAG assistant with source citations and a retrieval evaluation set.
- Compared retrieval configurations and documented answer failures, latency and system limitations.

## Advanced extension
If justified, add a controlled agentic workflow with structured outputs and approved tools. Study MCP as an integration standard; do not add an agent merely for branding.

## Limitations
To be documented after experiments.
