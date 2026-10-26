# 07 — Tests, Libraries, and the Error Model

> These notes explain patterns reviewed in the CUGA #940 issue/PR. We did not clone the repository or run these tests during the learning session. Treat command results and live API behavior as unverified until actually executed.

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- Studied PR: https://github.com/cuga-project/cuga-apps/pull/36

## 1. What is a test?

A test is executable code that checks a behavior against an expectation. A passing test gives evidence that a specific condition worked; it does not prove the whole feature is bug-free.

### Happy path vs error path

- **Happy path:** valid input is supplied and the feature succeeds.
- **Error path:** invalid input or a dependency failure is handled as designed.
- **Edge case:** an unusual but plausible boundary or missing-data condition is checked.

For a book-search tool:
- Happy path: search `the hobbit` and check for successful structured data.
- Error path: send an empty query and expect `bad_input`.
- Other useful edge cases: whitespace-only query, no matching books, missing author/year/key, upstream request exception, and limit boundaries.

## 2. Read the two tests

The PR's success test uses this pattern:

```python
data = _expect_ok(
    call_mcp_tool(
        "knowledge",
        "search_books",
        {"query": "the hobbit", "max_results": 2},
    )
)
```

What each piece means:
- `call_mcp_tool(...)` invokes a tool through the repository's test helper.
- `"knowledge"` identifies the relevant MCP server/tool group in this test setup.
- `"search_books"` is the tool name.
- The dictionary supplies the tool arguments.
- `_expect_ok(...)` asserts the result is an expected success response and returns its data to the test.

The test then checks returned authors, using an assertion that at least one result includes `Tolkien` in its author names. If the API call errors, or the expected author is not present in the returned results, the test fails.

The invalid-input test follows this intent:

```python
_expect_error(
    call_mcp_tool("knowledge", "search_books", {"query": ""}),
    code="bad_input",
)
```

It checks that empty input produces the expected structured error. If the function silently performs a normal search or returns a success instead, the assertion should fail.

## 3. What is assert?

```python
assert "Tolkien" in author_text
```

- Condition true → test continues.
- Condition false → Python raises `AssertionError` and the test fails.
- Tests are about expectations, not just whether a function returned something.

Avoid assertions that are too dependent on a live external service unless that is intentional and appropriately marked.

## 4. Why tests can be flaky

A live API test depends on more than our own code:
- Internet connectivity
- Open Library availability and response behavior
- Rate limiting
- Changes in remote data

A test that fails due to a remote outage may not mean the implementation itself regressed. A mock can provide a fixed JSON response or simulated exception so unit tests remain deterministic. Keep a live test when the repository intentionally wants an end-to-end smoke check; don't remove an existing `external` marker without understanding the test configuration.

## 5. Recommended test matrix

| Scenario | Expected contract |
|---|---|
| Valid query with books | success wrapper and normalized results |
| Empty query | `bad_input` |
| Whitespace-only query | `bad_input` |
| No matches | `not_found` |
| API/network exception | `upstream` |
| Missing optional book fields | no crash; safe defaults or `None` where appropriate |
| Limit below range | clamp or reject as project contract specifies |
| Limit above range | clamp to 20 or reject as contract specifies |
| Malformed payload | predictable error, not accidental unhandled crash |

This is a study/review checklist, not a claim that the PR has tests for every row. The task request emphasized success and empty-query tests; verify the current PR and code before stating exact coverage.

## 6. Error model: invalid input vs upstream failure vs no results

| Error code | Meaning | Example |
|---|---|---|
| `bad_input` | Caller supplied invalid input | Empty/whitespace query |
| `upstream` | External dependency/request failed | Timeout, HTTP/JSON error |
| `not_found` | Request succeeded but no matching books were returned | Empty `docs` list |

These represent distinct causes and help the caller decide what happened. Do not report `not_found` just because the upstream request failed; no results and a failed search are different states.

## 7. Relevant libraries and why they appear

The issue lists these dependencies for the MCP server work:
- **`mcp` (`mcp>=1.0,<2` in the issue instructions):** protocol/server SDK used to expose a Python function as an MCP tool. The issue says to stay below version 2 for this codebase; recheck current repo guidance before setup.
- **`httpx`:** HTTP client library used by the project helper or dependencies. Prefer the existing `get_json` helper over adding a second request path.
- **`pydantic`:** data validation/modeling library used in many typed Python applications. The issue lists it as a dependency, but inspect actual use rather than assuming the new function directly invokes it.
- **`pytest`:** Python test runner used for tests.
- **Open Library Search API:** external book catalogue/search source; the issue says this task does not require a paid key.

Do not install these just because they appear in notes. Follow the current repo's lockfile, dependency manager, and contribution instructions first.

## 8. Commands and expected interpretation

From the nested source directory specified in the issue:

```bash
python -m py_compile mcp_servers/knowledge/server.py tests/test_mcp_tools.py
```

Purpose: syntax-compiles both files. On success it normally prints nothing and returns exit code 0; errors print a traceback and return non-zero. This does **not** run unit tests or call Open Library.

Run pytest using the repository's documented command and configuration after setup. A passing exit code indicates the selected tests passed, but note skipped tests and environment constraints. We did not run these commands in this session.

## 9. Review questions to ask before approving code

- Are empty and whitespace-only queries rejected?
- Is the limit constrained to the agreed range?
- Is the existing HTTP helper reused consistently?
- Are missing keys handled safely?
- Are error categories distinct and useful?
- Can tests pass deterministically without relying unnecessarily on the live API?
- Does the test validate meaningful behavior rather than merely asserting that the response exists?
- Are dependency versions compatible with the repository?
- Is the diff limited to the issue's agreed scope?

## Key lesson

**A green test means the checked expectation held under that test's conditions.** Always read what a test asserts, what it does not assert, and what outside services it depends on.
