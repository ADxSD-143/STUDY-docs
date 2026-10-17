# Open-Source Journey — Start Here

Welcome to the practical open-source handbook in [STUDY-docs](https://github.com/ADxSD-143/STUDY-docs). This folder is meant to be useful months later for revision and useful to another beginner who wants a repeatable workflow—not merely a record of conversations.

## Learning path

```text
Start Here
   |
   v
01 Fundamentals and collaboration
   |
   v
02 Finding and evaluating issues
   |
   v
03 Understanding a repository
   |
   v
04 Git branch and contribution workflow
   |
   v
05 Tests, debugging, CI, and code review
   |
   v
Project case study: inspect one real issue
   |
   v
Record evidence, decisions, outcomes, and lessons
```

## Core handbook

1. [Open-source fundamentals](01-fundamentals.md) — terminology, contribution types, expectations, and the end-to-end workflow.
2. [Issue selection](02-issue-selection.md) — how to judge scope, fit, maintainer activity, duplicate work, and risk.
3. [Repository exploration](03-reading-a-codebase.md) — read project instructions, trace code, map tests, and establish a baseline.
4. [Git workflow](04-git-workflow.md) — fork, clone, branch, inspect, stage, commit, push, and open a PR.
5. [Testing, CI, and reviews](05-testing-ci-review.md) — regression tests, test failures, CI logs, PR descriptions, and review feedback.
6. [Communication and AI use](06-communication-and-ai.md) — asking maintainers good questions and using AI responsibly.
7. [Glossary and quick revision](07-glossary-and-revision.md) — short definitions, checklists, and self-check prompts.

## Real repository case studies

- [CUGA Agent issue #940 — Open Library `search_books` tool](projects/cuga-search-books-940/README.md). This is a case study in understanding an issue, MCP tools, Python API calls, tests, and contribution workflow. **Important:** the issue has a public “I'd like to take this” comment from another contributor. It is not assigned, but availability is not confirmed; do not start duplicate implementation or claim it without checking the latest issue discussion and maintainer expectations.

Every future repository or issue should get its own subfolder under `projects/`. Keep its actual code investigation, setup, commands, outputs, tests, decisions, PR, and retrospective there.

## Current progress

- [x] Practiced fork → clone → branch → commit → push → PR with First Contributions.
- [x] Merged practice PR: [#126562](https://github.com/firstcontributions/first-contributions/pull/126562).
- [ ] Make and complete a meaningful code/test/bug-fix/documentation contribution in an established codebase.
- [ ] Independently investigate a real issue and explain the implementation and tests.
- [ ] Record the complete lifecycle of a real contribution in its case-study folder.

See [the main Open-Source Journey log](README.md) for current progress and contribution tracking. GSoC-specific organization research and proposals are in the separate [GSoC track](../GSoC/README.md).

## Documentation standard for every case study

For each issue, document:
- source links, date checked, issue state, and whether someone has claimed it;
- the problem in plain language and acceptance criteria;
- repository structure and exact files to inspect;
- prerequisites, setup commands, why each command is used, and expected output;
- concepts explained from beginner level, with a flowchart where useful;
- implementation options and why one is selected;
- tests, expected behavior, real outputs, and failure troubleshooting;
- PR instructions, review feedback, and final outcome;
- what was learned, what remains uncertain, and what to do next.

Never invent test output, claim an issue is available without checking, or mark work as merged before it is merged.
