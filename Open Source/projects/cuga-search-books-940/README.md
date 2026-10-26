# Case Study — CUGA Agent #940: Open Library `search_books` Tool

**Status: investigation/case-study only; implementation not started.** The issue is open and unassigned in the latest inspected snapshot, but another contributor commented “I'd like to take this” on 2026-10-12. Do not start a duplicate implementation unless the latest discussion or maintainer explicitly confirms it is available.

- **Issue:** https://github.com/cuga-project/cuga-agent/issues/940
- **Code repository named by the issue:** https://github.com/cuga-project/cuga-apps
- **Target server file:** [`cuga-apps/mcp_servers/knowledge/server.py`](https://github.com/cuga-project/cuga-apps/blob/main/cuga-apps/mcp_servers/knowledge/server.py)
- **Target test file:** [`cuga-apps/tests/test_mcp_tools.py`](https://github.com/cuga-project/cuga-apps/blob/main/cuga-apps/tests/test_mcp_tools.py)
- **Issue label:** `good first issue`
- **Last checked:** 2026-10-17 (verify again before acting; issue state can change).

## Why this case study exists

This issue is a useful learning example because it combines ordinary Python, an external JSON API, an MCP tool decorator, input validation, error handling, and tests. The notes are intended to let a beginner understand the task from first principles and later reuse the process for another repository.

This is a case study and plan, not evidence that a PR has been submitted or merged.

## Subdocuments

1. [01 — Issue analysis and acceptance criteria](01-issue-analysis.md)
2. [02 — Repository map and setup](02-repository-map-and-setup.md)
3. [03 — Python, HTTP JSON, and MCP tool concepts](03-python-api-and-mcp-concepts.md)
4. [04 — Test plan and validation](04-test-plan-and-validation.md)
5. [05 — Contribution and PR workflow](05-contribution-workflow.md)
6. [06 — Python code patterns](06-python-code-patterns.md)
7. [07 — Tests, libraries, and error model](07-tests-libraries-and-error-model.md)
8. [08 — MCP tool structure and PR review notes](08-mcp-tool-and-review-notes.md)
9. [Progress log and decision record](progress-log.md)

## System flow

```text
Agent / MCP client
      |
      v
search_books(query, max_results)
      |
      v
Validate query
  | invalid
  +-------> tool_error(bad_input)
      |
      v
get_json(Open Library Search API)
  | exception
  +-------> tool_error(upstream)
      |
      v
Read docs from JSON safely
      |
      v
Normalize book fields and build URL
  | no results
  +-------> tool_error(not_found)
      |
      v
tool_result({query, total_found, books})
```

## Current verified facts vs unverified assumptions

**Verified from the issue page on 2026-10-17:**
- The issue is open and has no assignee in the returned issue metadata.
- One comment from another GitHub user says “I'd like to take this.”
- The issue asks for an Open Library search tool and tests in the linked test file.
- The issue includes a suggested implementation and example validation commands.

**Not yet verified by local execution:**
- Current source code may have changed since the issue's linked commit.
- Local environment setup and commands have not been run as part of this case study.
- No tests have been run by this study log.
- No PR exists from this learning session.

## Next action

Recheck the issue's latest comments and linked PRs, then ask the maintainer whether the task is available if necessary. If it is already being handled, keep this case study as a reading exercise and select a different available issue for actual implementation.
