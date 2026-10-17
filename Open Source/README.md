# Open-Source Journey

A practical, continuously maintained record of my open-source learning journey: understanding repositories, selecting issues, reading code, testing changes, communicating with maintainers, and contributing responsibly.

- **Contributor:** Aditya Narayan Laha
- **GitHub:** https://github.com/ADxSD-143
- **Learning style:** Learn one concept, apply it in a real repository, record what worked, and improve from review feedback.
- **Related track:** [GSoC preparation](../GSoC/README.md) is maintained separately.

## 1. What this document is for

This is the main log for learning **open source itself**. It records reusable skills and real contribution experience—not just GSoC application preparation.

Use this document to answer:
- How do I understand an unfamiliar repository?
- How do I choose a useful issue?
- How do I set up a project and reproduce a bug?
- How do I make a small, testable change?
- How do I work with tests, linting, CI, and review feedback?
- How do I communicate clearly with maintainers?
- What did I contribute, what did I learn, and what should I improve next?

### Open source vs GSoC

| Open-source journey (this document) | GSoC track (separate document) |
|---|---|
| General contribution skills and habits | GSoC program, organizations, timelines, and eligibility |
| Repository exploration and issue selection | Organization and project research for GSoC |
| Git, code reading, tests, debugging, reviews | Proposal writing, project scope, mentor communication for the program |
| Contribution log across any repository | GSoC-specific milestones and application readiness |

The skills overlap, but the notes and progress logs stay separate.

## 2. My current starting point

- [x] Completed the First Contributions workflow.
- [x] Created a fork, cloned the repository, created a branch, committed and pushed a change.
- [x] Opened a Pull Request that was merged: [PR #126562](https://github.com/firstcontributions/first-contributions/pull/126562).
- [x] Documented the first Git/GitHub workflow in [github.md](../github.md).
- [ ] Complete a meaningful code, test, bug-fix, or documentation contribution in an established project's actual codebase.
- [ ] Learn to independently trace a code path and explain why a change is correct.
- [ ] Build a repeatable contribution workflow: investigate → reproduce → implement → test → review → document.

**Important:** The First Contributions PR was useful Git/GitHub practice. A contributor-list edit does not by itself demonstrate the same skills as fixing a real bug or implementing a project feature.

## 3. The contribution workflow

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

This is a guide, not a rigid rule. Follow each repository's own contribution instructions and workflow.

## 4. Issue-selection checklist

Before choosing an issue, check:

- [ ] The issue is still open and not already being actively handled by someone else.
- [ ] The expected outcome is clear enough to investigate.
- [ ] The task is small enough for my current skills and available time.
- [ ] I can locate the relevant code, tests, or documentation.
- [ ] The repository has understandable setup instructions.
- [ ] The issue fits the project's purpose and existing design.
- [ ] Recent maintainer activity and review behavior look healthy.
- [ ] I have read the discussion and checked for duplicate issues or PRs.

A `good first issue` label is a useful signal, not a guarantee. Prefer clear scope, codebase fit, testability, and responsive maintainers over labels alone. Do not select issues only to increase PR count.

## 5. Understanding an unfamiliar codebase

1. Read `README.md`, `CONTRIBUTING.md`, `AGENTS.md` (if present), and relevant project docs.
2. Identify the language, package manager, supported runtime version, and test/lint commands.
3. Find the function, module, or route mentioned by the issue.
4. Trace its callers, dependencies, inputs, outputs, and error paths.
5. Read nearby tests to learn the project's conventions.
6. Run the existing tests before changing anything, if setup permits.
7. Write down what you understand and what remains unclear.

Use AI to explain specific confusing code or suggest investigation steps. Verify the explanation against the repository. Do not blindly rewrite an unfamiliar file or accept generated code you cannot explain.

## 6. Reproducing a bug and testing a fix

A reliable bug-fix loop:

1. Reproduce the reported behavior.
2. Write a focused regression test that fails for the expected reason.
3. Make the smallest change that fixes the cause.
4. Confirm the new test passes.
5. Run relevant existing tests and project checks.
6. Review edge cases and the final diff.

A passing test is evidence, not proof that every behavior is correct. Tests should assert meaningful outcomes and cover important edge cases. Never fabricate expected data or remove a valid test simply to get a green result.

### Test commands

There is no universal test command. Follow the repository's instructions. For example, in a Python project using pytest:

```powershell
python -m pytest
```

**What it does:** Runs tests discovered by pytest using the active Python environment.

**Expected result:** A summary showing passed, failed, skipped, or errored tests. Exact counts depend on the repository. If the command is not found, check the environment and project setup instructions rather than assuming the code is broken.

## 7. Git workflow and safe habits

The detailed first-contribution commands and the actual remote-permission issue are recorded in [GitHub & Git: First Open-Source Contribution](../github.md).

Before every commit:

```powershell
git status
git diff
```

- `git status` shows the current branch and staged/unstaged/untracked changes.
- `git diff` shows unstaged changes. Use `git diff --staged` to inspect staged changes.
- **Expected result:** The changes shown should be exactly the changes you intend to commit. Review filenames and remove accidental edits or secrets.

Use a separate branch, make focused commits, and push to your fork unless the project gives you another workflow. Never commit passwords, access tokens, private keys, or other secrets.

## 8. Pull Requests, CI, and maintainer feedback

A useful PR description explains:
- **Problem:** What issue or behavior is being addressed?
- **Solution:** What changed and why is this approach appropriate?
- **Testing:** Which commands/checks ran and what were the results?
- **Limitations:** What remains uncertain or incomplete?

When CI fails, read the logs, identify the failing check, reproduce locally if possible, fix the underlying cause, and push again. “Works on my machine” is not a reason to ignore a failing check.

When a maintainer requests changes, understand the feedback, update the same branch, add or adjust tests, rerun checks, and push. The existing PR updates automatically. If feedback is unclear or you disagree technically, explain your reasoning respectfully and ask a focused question.

## 9. Asking for help effectively

Before asking:
- Inspect the relevant implementation and tests.
- Search the project documentation and issue discussion.
- Try a reasonable approach and capture the result.
- Ask about the specific blocker, not for someone else to solve the whole issue.

A good question states the goal, files/behavior investigated, attempts and outcomes, and the exact point needing clarification. Avoid sharing secrets or private logs.

## 10. Using AI responsibly

AI can help explain code, find likely files, suggest test cases, or review a proposed diff. The contributor remains responsible for correctness.

Before submitting AI-assisted changes:
- Understand the important lines and be able to explain the design.
- Verify claims against actual source code and repository conventions.
- Inspect error handling, edge cases, security implications, and dependencies.
- Run tests, linting, and other required checks yourself.
- Follow the project's AI-use and disclosure policies.

## 11. Learning log

Update this section after meaningful work. Keep entries factual and concise; do not claim a contribution is merged unless it is.

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
- **Next action:** Recheck the current status and discussion of any candidate issue before investing in implementation.

## 12. Contribution tracker

Add a row whenever a real contribution is started. Keep “status” accurate.

| Repository / issue | Goal | Status | PR link | Main lesson / next action |
|---|---|---|---|---|
| First Contributions | Practice Git/GitHub workflow | Merged | [#126562](https://github.com/firstcontributions/first-contributions/pull/126562) | Practice completed; next, work on a meaningful codebase issue |
| CUGA Agent #940 | Explore adding an Open Library `search_books` MCP tool | Availability not verified; do not start until checked | — | Check issue discussion, existing claims, repository instructions, and current implementation first |

## 13. Definition of progress

Progress is not just the number of PRs. Track whether I can increasingly:

- [ ] Explain the issue in my own words before coding.
- [ ] Find the relevant implementation and tests without step-by-step instructions.
- [ ] Reproduce a bug and write a meaningful regression test.
- [ ] Make a focused change consistent with project conventions.
- [ ] Diagnose test, lint, or CI failures from logs.
- [ ] Explain my diff and trade-offs in a PR.
- [ ] Respond constructively to review feedback.
- [ ] Record lessons and apply them to the next repository.

## 14. How we will maintain this document

After each learning session or real contribution, update only the relevant sections:
1. Add a short learning-log entry with the concept or task, what was tried, and the outcome.
2. Update the contribution tracker and checklist.
3. Record useful commands with their purpose and expected behavior next to the command.
4. Keep unresolved blockers explicit; do not present assumptions as verified facts.
5. Keep GSoC program research, proposal drafts, organization comparisons, and application milestones in the separate [GSoC preparation document](../GSoC/README.md).

**Next session:** Verify the candidate issue's current status, then inspect the repository's instructions and relevant code before deciding whether to contribute.
