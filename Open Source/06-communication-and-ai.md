# 06 — Maintainer Communication and Responsible AI Use

## Before asking a question

1. Read the issue and existing comments.
2. Read the project instructions and relevant code/tests.
3. Try to reproduce the problem or make a small investigation.
4. Record exact commands/errors and what they tell you.
5. Ask one precise question about the unresolved point.

## Maintainer question template

> Hi! I’m investigating [issue/behavior]. I checked [files/docs/tests] and tried [approach]. The observed result is [result], while I expected [expected behavior]. I’m unsure about [specific question]. Is this consistent with the project’s intended behavior, or is there a preferred direction?

Adapt this to the situation. Do not ask a maintainer to repeat information already present in the issue or ask them to solve the whole task.

## Review feedback

Treat review as collaboration. For each comment:
- identify the concern (correctness, scope, test coverage, style, compatibility, or design);
- make the requested change if appropriate;
- ask for clarification when ambiguous;
- explain evidence respectfully if you believe another approach is better;
- update the same PR branch and rerun checks.

Do not treat requested changes as personal criticism. Do not mark a discussion resolved until the concern is addressed, unless the project uses another convention.

## Responsible AI use

AI can help explain unfamiliar code, suggest investigation commands, draft tests, or review a diff. It can also hallucinate APIs, miss project-specific rules, or produce plausible but incorrect code.

Before using generated code:
- verify every important claim against repository source and official docs;
- understand the behavior well enough to explain it;
- check invalid inputs, error paths, security, dependencies, and compatibility;
- run tests and relevant checks;
- follow repository rules about AI-assisted contributions and disclosure;
- never paste secrets, private data, or credentials into a prompt.

## Better AI prompts

Instead of “fix this issue,” try:
- “Read this function and its tests. Explain the current behavior and list the smallest files likely involved; do not change code yet.”
- “Given these expected behaviors, propose test cases for success, empty input, missing fields, and upstream failure.”
- “Review this diff for scope, edge cases, error handling, and compatibility. Separate evidence from assumptions.”
- “Explain this traceback, identify the first relevant project frame, and give me one diagnostic step.”

## Progress rule

Use AI to accelerate understanding, not replace it. The contributor is accountable for the final code, tests, and claims in the PR.
