# 07 — Glossary and Quick Revision

## Glossary

- **Upstream:** original project repository.
- **Fork:** your hosted copy of another repository.
- **Clone:** local copy of a repository.
- **Branch:** separate line of work.
- **Working tree:** files as they currently exist in your local checkout.
- **Stage:** select changes for the next commit.
- **Commit:** recorded snapshot of staged changes.
- **PR:** proposal to merge a branch into a target branch.
- **Maintainer:** project contributor responsible for review and project direction.
- **Regression:** previously fixed behavior breaking again.
- **Regression test:** test designed to catch that regression.
- **Mock:** controlled substitute for a dependency, often used in tests.
- **CI:** automated checks executed by the project.
- **Lint:** automated checks for code-quality/style problems.
- **Scope:** the boundaries of the change being proposed.
- **Acceptance criteria:** observable conditions that define whether the task is done.

## Before starting an issue

- [ ] Read issue description, comments, and linked PRs.
- [ ] Confirm status and check whether someone is already working on it.
- [ ] Read project contribution instructions.
- [ ] Locate relevant code and tests.
- [ ] Define expected success and failure behavior.
- [ ] Decide whether to proceed, ask a question, or choose another issue.

## Before committing

- [ ] Correct branch.
- [ ] `git status` checked.
- [ ] `git diff` and staged diff reviewed.
- [ ] Only intended files included.
- [ ] No secrets or unrelated changes.
- [ ] Tests/checks run and results recorded accurately.

## Before opening a PR

- [ ] Focused change matches issue scope.
- [ ] Tests cover relevant behavior.
- [ ] Lint/type/format checks run if required.
- [ ] CI-specific or external tests are clearly identified.
- [ ] PR explains problem, solution, tests, and limitations.
- [ ] Base and head repositories/branches are correct.
- [ ] Project sign-off and contribution rules followed.

## Self-check prompts

Try to answer in your own words:
1. Why can an open, unassigned issue still be unavailable?
2. Why should a regression test fail before the fix?
3. What is the difference between syntax checking and behavioral testing?
4. Why should a test for an external API often use a mock?
5. What information makes a maintainer question actionable?
6. Why does a PR being open not mean the contribution is accepted?
7. What should you verify before submitting AI-generated code?

Add answers to your personal notes after attempting them. Use the project case studies for concrete examples.
