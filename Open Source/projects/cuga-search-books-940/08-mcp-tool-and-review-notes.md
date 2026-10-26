# 08 — MCP Tool Structure and PR Review Notes

## 1. MCP is not an ML model

Model Context Protocol (MCP) is a protocol for an AI host/client to discover and call tools or access capabilities provided by a server. In this example, `search_books` is an ordinary Python function exposed as a tool. It is not itself a trained ML model.

Conceptual flow:

```text
AI application / MCP client
          |
          | tool call: search_books(query, max_results)
          v
MCP knowledge server
          |
          | calls Python function
          v
Existing helper: get_json(...)
          |
          | HTTP request
          v
Open Library Search API
          |
          | JSON payload
          v
Normalize fields + classify outcome
          |
          +--> tool_result(...)   success
          |
          +--> tool_error(...)    bad_input / upstream / not_found
          v
MCP client receives structured response
```

## 2. What the decorator does

```python
@mcp.tool()
def search_books(query: str, max_results: int = 5) -> str:
    """Search Open Library for books matching a query."""
    ...
```

The decorator registers the function with the MCP server according to the framework's rules. The function signature and docstring help describe the callable tool and its arguments. Check the framework/version in the repository before relying on framework-specific behavior.

## 3. Tool result vs tool error

- `tool_result(...)` is the existing project helper for successful output.
- `tool_error(..., code=...)` is the existing project helper for structured failure output.
- Use existing helpers instead of inventing a new response envelope.
- Their exact serialized schema must be confirmed from the real source implementation; these notes describe their intended role as documented by the issue.

## 4. No new ML model is needed

The task does not train, fine-tune, or load a model. It adds a deterministic retrieval tool that obtains book data from an external service. The AI agent may decide when to call the tool, but the tool's job is to retrieve and format information. This is an important architecture distinction:
- **Model:** produces predictions/generations based on learned parameters.
- **Tool:** executes a defined operation, such as an API request.
- **External API:** supplies data from another service.
- **MCP server:** exposes the tool through a standardized protocol.

## 5. PR availability and duplication decision

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- Existing PR observed during this learning session: https://github.com/cuga-project/cuga-apps/pull/36
- PR title: `feat(mcp-knowledge): add search_books tool (Open Library)`

The PR already contained an implementation and tests, so duplicating the work would be inappropriate. The issue also had a comment from another contributor expressing interest. We used the PR as a code-reading exercise, recorded reusable lessons, and decided to move to another candidate issue for actual contribution.

This is a key open-source habit: **before implementing, check the issue thread, branches, and existing pull requests in the code repository.** An issue tracker and implementation repository can differ, so check both.

## 6. What we learned from reading the diff

- `get_json(...)`: reuse existing shared HTTP/JSON behavior.
- `.strip()`: treat whitespace-only query as blank.
- `max(1, min(max_results, 20))`: clamp normal integer inputs to a safe range.
- `record.get("author_name") or []`: avoid a missing-author key error and provide an empty-list fallback.
- Conditional f-string URL: only create a URL when the work key exists.
- `try/except`: convert external request failures to the `upstream` error path.
- `_expect_ok` and `_expect_error`: test helpers for expected success/error envelopes.
- Success and empty-query tests cover distinct behaviors; a meaningful test checks output content, not just that a call returns.

## 7. What remains unverified

We read the proposed diff and discussed code patterns, but in this study session:
- We did not clone the CUGA source repository.
- We did not run unit tests, lint, or CI locally.
- We did not independently verify all helper implementations.
- We did not submit a review or contribute code to CUGA.
- We did not create a PR for this issue.

Never describe these actions as completed. A code-reading lesson is valuable but different from a tested implementation or merged contribution.

## 8. Review decision framework

Use these three choices deliberately:
- **Approve:** the change meets the contract and the reviewer has sufficient evidence; don't approve just because code looks plausible.
- **Request changes:** a concrete correctness, safety, compatibility, or test gap needs to be fixed.
- **Comment:** ask a useful question or share a non-blocking observation without asserting a blocking defect.

For this PR, our session was a beginner reading exercise, not a formal complete review. We have not submitted an approval or requested changes.

## Reusable review checklist

- [ ] Check issue status and existing PRs in both tracker and code repository.
- [ ] Confirm intended files and acceptance criteria.
- [ ] Trace inputs through validation, external call, output normalization, and errors.
- [ ] Check missing fields and boundaries.
- [ ] Read tests' assertions carefully.
- [ ] Identify external dependencies and non-deterministic tests.
- [ ] Verify test/CI status rather than inferring it from the diff.
- [ ] State only what you actually inspected or executed.
