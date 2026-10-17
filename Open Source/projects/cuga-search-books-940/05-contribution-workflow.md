# 05 — Contribution and PR Workflow

## Before coding

- [ ] Recheck the latest issue comments and linked PRs.
- [ ] Resolve the “I'd like to take this” coordination concern with the maintainer or choose another issue.
- [ ] Read the current repository's contribution instructions.
- [ ] Fork `cuga-project/cuga-apps` and clone your fork.
- [ ] Create a focused branch using the repository's naming conventions.
- [ ] Inspect current code and tests; confirm the tool is not already implemented.
- [ ] Run baseline checks and record results.

Do not comment that you are taking the issue or start a duplicate implementation until availability is clear.

## Implementation scope described by the issue

The issue requests changes to:
1. `cuga-apps/mcp_servers/knowledge/server.py`
2. `cuga-apps/tests/test_mcp_tools.py`

The issue says not to modify the Tools header list, README files, or the “36 MCP tools” count because maintainers coordinate those updates across concurrent PRs. Reconfirm this instruction before making any changes.

## Suggested sequence if maintainers confirm availability

1. Inspect the existing HTTP and response helpers.
2. Read neighboring knowledge tools and their tests.
3. Write or adapt focused tests for success and error cases.
4. Implement the smallest change that satisfies the agreed contract.
5. Run syntax check and relevant tests.
6. Review `git diff` and `git status`.
7. Confirm only intended files changed.
8. Follow the issue's requested commit sign-off convention.
9. Open a PR with the issue's suggested title and truthful validation output.
10. Respond to review feedback on the same PR branch and rerun checks.

## Issue-specific PR details

The issue suggests title:

```text
feat(mcp-knowledge): add search_books tool (Open Library)
```

It asks for a sign-off commit (`git commit -s`) and for the PR description to include `Closes #940` and the output of its smoke-test command. Confirm the correct issue-linking syntax across repositories because the issue is in `cuga-agent` while code is in `cuga-apps`; do not assume cross-repository closure behavior. Ask maintainers which issue reference they want if needed.

## PR description template

```markdown
## Summary
- Add the Open Library book-search MCP tool.
- Normalize book metadata and handle empty/no-result/upstream-error cases.

## Testing
- [ ] Syntax check:
- [ ] Unit tests:
- [ ] External smoke test (if available):

## Notes
- Mention any tests skipped because they require network or app setup.
```

Only include claims that match the actual diff and test results. Do not mark the issue complete until a maintainer merges the contribution.
