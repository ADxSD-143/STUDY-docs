# 02 — Selecting an Issue Worth Working On

## Step 1: Verify the current state

Before investing time, inspect:
- Is the issue open?
- Is it assigned?
- Has anyone commented that they are taking it?
- Are there linked PRs, branches, or duplicate issues?
- Has a maintainer clarified the scope or asked contributors to coordinate first?
- Is the problem still relevant in the current codebase?

An unassigned issue can still be actively claimed by a contributor. Read the discussion, not only the issue header.

## Step 2: Judge the task

| Dimension | Good sign | Warning sign |
|---|---|---|
| Scope | One understandable outcome | Multiple unrelated changes |
| Code fit | Relevant file and nearby tests are findable | No clear starting point |
| Testability | Expected behavior can be verified | Success criteria are vague |
| Setup | Supported runtime and setup docs exist | Setup is broken or unexplained |
| Maintainers | Recent reviews and useful responses | Long unexplained inactivity |
| Fit | You can learn the required concepts | Core concepts are far beyond current ability |
| Coordination | No duplicate work; maintainer expectations are clear | Another contributor appears to be working on it |

## Step 3: Ask a specific question when needed

Example template (adapt it; do not send blindly):

> Hi! I’m exploring this issue and have read the description and existing discussion. I plan to investigate [specific area]. I noticed [specific uncertainty]. Is this still available to work on, and is there any implementation direction I should follow before I start?

If a contributor already says they want to take the issue, do not compete by starting duplicate code. Ask the maintainer whether help is needed, or choose another issue.

## Step 4: Make a decision

- **Proceed:** issue is available, scoped, understood, and fits your current time/skills.
- **Clarify:** there is one important ambiguity about expected behavior or coordination.
- **Defer:** setup or scope is currently too large; learn the missing prerequisite first.
- **Choose another issue:** someone else is already handling it or maintainers indicate it is unavailable.

## Example: CUGA issue #940

The issue page currently shows state **open** and no assignee. However, its comments include a contributor's “I'd like to take this” message dated 2026-10-12. Therefore, open + unassigned does **not** prove that it is available.

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- Candidate code repository: https://github.com/cuga-project/cuga-apps
- Current decision: **do not begin a duplicate implementation until the latest discussion and maintainer expectations are checked.**
- Learning value remains high even if we do not implement it: the issue can be used as a reading exercise for MCP tools, API integration, input validation, and tests.

## Quick decision checklist

- [ ] Read all issue comments and linked PRs.
- [ ] Check the code repository's current implementation.
- [ ] Confirm no duplicate work is underway.
- [ ] Understand expected inputs, outputs, and errors.
- [ ] Identify tests and local validation commands.
- [ ] Confirm the task fits the time available.
- [ ] Ask a focused question or select a different issue if availability is uncertain.
