# Open-Source Journey

A practical, continuously maintained record of my open-source learning journey: understanding repositories, selecting issues, reading code, testing changes, communicating with maintainers, and contributing responsibly.

- **Contributor:** Aditya Narayan Laha
- **GitHub:** https://github.com/ADxSD-143
- **Learning style:** Learn one concept, apply it in a real repository, record what worked, and improve from review feedback.
- **Related track:** [GSoC preparation](../GSoC/README.md) is maintained separately.

## Start here

- [00 — Start Here: complete handbook index](00-START-HERE.md)
- [01 — Open-source fundamentals](01-fundamentals.md)
- [02 — Issue selection](02-issue-selection.md)
- [03 — Reading an unfamiliar codebase](03-reading-a-codebase.md)
- [04 — Git workflow reference](04-git-workflow.md)
- [05 — Testing, CI, and code review](05-testing-ci-review.md)
- [06 — Maintainer communication and responsible AI use](06-communication-and-ai.md)
- [07 — Glossary and quick revision](07-glossary-and-revision.md)

## Real repository case studies

Each project/issue gets its own subfolder with issue analysis, repository map, setup, concepts, tests, PR workflow, and progress log.

- [CUGA Agent #940 — Open Library `search_books` MCP tool](projects/cuga-search-books-940/README.md) — includes Python patterns, test/error model, libraries, MCP architecture, and PR-review notes.

**Important current note:** CUGA issue #940 was open and unassigned when checked on 2026-10-17, but another contributor had commented “I'd like to take this” on 2026-10-12. Treat it as a study case until availability is confirmed. Do not begin duplicate implementation.

## What this document is for

This is the main log for learning **open source itself**. It records reusable skills and real contribution experience—not just GSoC application preparation.

### Open source vs GSoC

| Open-source journey (this folder) | GSoC track (separate folder) |
|---|---|
| General contribution skills and habits | GSoC program, organizations, timelines, and eligibility |
| Repository exploration and issue selection | Organization and project research for GSoC |
| Git, code reading, tests, debugging, reviews | Proposal writing, project scope, mentor communication for the program |
| Contribution log across any repository | GSoC-specific milestones and application readiness |

## Current starting point

- [x] Completed the First Contributions workflow.
- [x] Created a fork, cloned the repository, created a branch, committed and pushed a change.
- [x] Opened a Pull Request that was merged: [PR #126562](https://github.com/firstcontributions/first-contributions/pull/126562).
- [x] Documented the first Git/GitHub workflow in [github.md](../github.md).
- [ ] Complete a meaningful code, test, bug-fix, or documentation contribution in an established project's actual codebase.
- [ ] Learn to independently trace a code path and explain why a change is correct.
- [ ] Build a repeatable contribution workflow: investigate → reproduce → implement → test → review → document.

**Important:** The First Contributions PR was useful Git/GitHub practice. A contributor-list edit does not by itself demonstrate the same skills as fixing a real bug or implementing a project feature.

## The contribution workflow

```text
Find a relevant project
       |
       v
Read README, CONTRIBUTING, AGENTS, and project docs
       |
       v
Check issue status, scope, discussion, and existing work
       |
       v
Trace relevant code and tests; reproduce the problem
       |
       v
Make a small, focused change on a separate branch
       |
       v
Add/update tests and run project checks
       |
       v
Review the diff and write a clear Pull Request
       |
       v
Respond to feedback, update the same branch, and retest
       |
       v
Record what was learned and what remains
```

## Learning log

### Entry 01 — First Contributions

- **Status:** Merged
- **Work:** Practiced fork → clone → branch → edit → stage → commit → push → PR.
- **Result:** [PR #126562](https://github.com/firstcontributions/first-contributions/pull/126562).
- **Lesson:** Verify `git remote -v`. My initial push failed because `origin` pointed to the upstream repository, where I did not have write permission. Updating `origin` to my fork fixed the target.
- **Next improvement:** Move from contribution-workflow practice to a meaningful change in a project's codebase.

### Entry 02 — Issue selection and contribution fundamentals

- **Status:** Concepts reviewed; practical issue availability must be checked before starting work.
- **Topics:** Issue scope, maintainer activity, repository instructions, code tracing, regression tests, CI failures, focused PRs, review feedback, asking for help, and responsible AI assistance.
- **Key lesson:** A label or PR count does not establish contribution quality. Choose a useful, understandable task and verify it with tests.
- **Next action:** Recheck the candidate issue's status and discussion before implementation.

## Contribution tracker

| Repository / issue | Goal | Status | PR link | Main lesson / next action |
|---|---|---|---|---|
| First Contributions | Practice Git/GitHub workflow | Merged | [#126562](https://github.com/firstcontributions/first-contributions/pull/126562) | Practice completed; next, work on a meaningful codebase issue |
| CUGA Agent #940 | Explore adding an Open Library `search_books` MCP tool | Study case; availability unconfirmed | — | Confirm current ownership/maintainer expectations before implementation |

## How we will maintain this handbook

After each learning session or real contribution:
1. Add a dated entry describing the concept/task, what was tried, and the actual outcome.
2. Update the relevant project/issue case-study documents.
3. Record useful commands with their purpose and expected output next to the command.
4. Keep blockers and unverified assumptions explicit.
5. Keep GSoC organization research, proposal drafts, and application milestones in the separate [GSoC preparation document](../GSoC/README.md).

Use [00 — Start Here](00-START-HERE.md) to navigate the complete handbook.