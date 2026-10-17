# 01 — Open-Source Fundamentals

## What is open source?

Open-source software makes its source code available under a license that grants people defined rights to inspect, use, modify, and redistribute it. Each project has its own license and contribution rules, so “public on GitHub” does not mean “ignore the license.”

A contribution is a proposed improvement to a shared project. It can be code, a bug report, tests, documentation, examples, accessibility work, or a reproducible diagnosis.

## Common terms

| Term | Meaning |
|---|---|
| Repository (repo) | Project files plus their version history |
| Upstream | The original project repository you want to contribute to |
| Fork | Your GitHub copy of another repository |
| Clone | A local copy of a repository |
| Branch | A separate line of work |
| Commit | A named snapshot of staged changes |
| Pull Request (PR) | A proposal to integrate changes into a target branch |
| Issue | A discussion/task/bug report used to coordinate work |
| Maintainer | A person responsible for project direction, review, and releases |
| CI | Automated checks run on code changes |
| Regression test | A test that protects against a previously observed bug returning |
| Review | Feedback on correctness, design, maintainability, tests, and scope |

## Typical contribution lifecycle

```text
Understand project
   -> Find problem
   -> Check issue/discussion
   -> Read instructions and code
   -> Reproduce / define expected behavior
   -> Implement focused change
   -> Add or update tests
   -> Run checks and inspect diff
   -> Open PR
   -> Respond to review
   -> Merge or learn from outcome
```

## What makes a good first contribution?

A useful first issue has a clear outcome, manageable scope, discoverable code/tests, and a project workflow you can follow. A `good first issue` label helps but is not a guarantee. A task without that label may still be appropriate if the scope and context are clear.

Do not choose based on PR count or perceived prestige alone. Prefer work that solves a real project problem and that you can understand and verify.

## Contribution quality

A strong contribution generally:
- solves the stated problem rather than an adjacent problem;
- follows existing conventions and keeps the diff focused;
- includes tests or evidence appropriate to the change;
- handles relevant invalid inputs and failure modes;
- explains its purpose and validation in the PR;
- responds constructively to maintainer feedback.

## Beginner traps

- Coding before checking whether someone else is already working on the issue.
- Rewriting a file without tracing its callers or tests.
- Assuming a green test suite proves every edge case is correct.
- Ignoring project-specific setup, formatting, license, or sign-off rules.
- Making a PR much larger than the issue requires.
- Treating AI output as verified fact.
- Claiming a contribution is accepted because a PR was opened rather than merged.

## Revision checklist

Can you explain the difference between a fork and a clone? Why should you inspect an issue's comments before coding? Why is a focused PR easier to review? What evidence should a PR provide that the change works?

**Practical exercise:** Open a public repository you use. Find its README, contribution guide, issue tracker, tests, and latest merged PR. Write down what each tells you about the project.
