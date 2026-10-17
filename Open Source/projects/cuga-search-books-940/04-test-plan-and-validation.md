# 04 — Test Plan and Validation

## Test strategy

Separate deterministic behavior from live-service behavior. The issue suggests an external test for a real Open Library search and a local empty-query test. Inspect current test markers and helper functions before running anything.

## Suggested test matrix

| Case | Input/setup | Expected behavior |
|---|---|---|
| Successful search | Query `the hobbit`, limit 2; API responds with valid records | Success wrapper with query, total count, and normalized book fields |
| Empty query | `query=""` | `bad_input` error |
| Whitespace query | `query="   "` | `bad_input` error |
| No results | API returns `{"docs": []}` | `not_found` error |
| Missing optional fields | Record lacks author/year/key | Safe output; no invented values or malformed URL |
| API request failure | HTTP helper raises | `upstream` error |
| Malformed response | Unexpected/missing `docs` shape | Handled according to project conventions; no unhandled crash |
| Result limit | Small, default, and out-of-range limits | Output respects the issue's stated 1–20 bounds |

These are recommended cases for analysis. They are not claims that tests have already been written or run.

## Why mock an external API?

A test that requires a live API can fail because of a network outage, rate limit, or upstream change rather than a code regression. A mock supplies a controlled response or exception, making the test repeatable. Keep live external tests only where the repository intentionally uses them and marks them appropriately.

## Commands from the issue

The issue provides this manual smoke test from the nested `cuga-apps` source directory:

```bash
python -c "
import json
from mcp_servers.knowledge.server import search_books as s
r = json.loads(s('the hobbit', 2)); print(r['ok'], r['data']['books'][0])
print(s('qqzzxxyyvvnotabook')); print(s(''))
" 2>/dev/null
```

Purpose: import the function, perform a live search, print one returned book, and check no-result and empty-query error paths.

The issue's example output includes a successful `The Hobbit` record, a `not_found` response, and a `bad_input` response. **Live API results such as edition counts can change**, and this command has not been executed by this documentation task. Do not paste expected example output as if it were your own actual result.

Syntax check:

```bash
python -m py_compile mcp_servers/knowledge/server.py tests/test_mcp_tools.py && echo compiled
```

Purpose: compile the named Python files to catch syntax errors, then print `compiled` if compilation succeeds. This is not a substitute for unit tests.

Run the repository's current documented test and lint commands after inspecting its configuration. The issue says some full-app tests may skip locally; record skipped tests explicitly and do not report them as passed.

## Record actual results

| Date | Command | Result | Notes |
|---|---|---|---|
| Not run | Not run | Not run | This case study was documented before local setup or code execution. |

Update this table only with commands actually executed and the exact outcome.
