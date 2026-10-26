# 06 — Python Code Patterns from the CUGA search_books Case Study

> Learning notes from reading the proposed implementation in CUGA Agent issue #940 and its linked PR. This is a study record, not our own contribution. Check the live source before relying on line-level details.

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- PR studied: https://github.com/cuga-project/cuga-apps/pull/36
- Target module: `mcp_servers/knowledge/server.py`

## 1. Function signature and defaults

```python
def search_books(query: str, max_results: int = 5) -> str:
    ...
```

- `query: str` says the caller is expected to provide a string.
- `max_results: int = 5` sets a default limit of five if the caller omits it.
- `-> str` is a type annotation saying the function is expected to return a string. It does not, by itself, enforce the return type at runtime.
- The function is exposed to MCP clients through the server's tool registration mechanism.

## 2. Reject empty and whitespace-only input

```python
if not (query or "").strip():
    return tool_error("query must not be empty.", code="bad_input")
```

Read inside-out:
1. `query or ""` uses an empty string if query is falsy, such as `None`.
2. `.strip()` removes surrounding spaces, tabs, and newlines.
3. A string containing only whitespace becomes `""`.
4. `not ""` is `True`, so the invalid-input branch runs.
5. `tool_error(...)` creates the project's structured error response with code `bad_input`.

| Input | After strip() | Rejected? |
|---|---|---|
| `"the hobbit"` | `"the hobbit"` | No |
| `"   "` | `""` | Yes |
| `""` | `""` | Yes |

Input validation keeps obviously invalid input from reaching the external service.

## 3. Clamp a number to a safe range

```python
limit = max(1, min(max_results, 20))
```

- `min(max_results, 20)` prevents values above 20.
- `max(1, ...)` prevents the result from being below 1.
- For ordinary integer inputs: `0 → 1`, `7 → 7`, `99 → 20`.

This is called clamping. It is not full type validation: strings, floats, or `None` may need validation depending on how the MCP framework validates arguments. Inspect the actual contract before changing this logic.

## 4. Use an existing JSON helper

The proposed code calls the repository helper `get_json(...)` rather than creating another HTTP client call.

Why this matters:
- It can keep timeout, status-code handling, and JSON parsing consistent with the repository.
- Duplicating `requests.get` or `httpx.get` may bypass project conventions.
- The exact guarantees of `get_json` must be learned by opening its implementation. Do not assume it handles timeouts or HTTP status errors until verified.

The Open Library Search API is the free book-search data source for this task. JSON is the response format for structured data.

## 5. Catch an upstream failure

```python
try:
    payload = get_json(url)
except Exception as exc:
    return tool_error(str(exc), code="upstream")
```

The `try` block runs the external request. If an exception escapes from that call, the `except` block converts it into the project's structured error format.

- `upstream` identifies a problem with the external service/request path.
- This is more controlled than letting a raw exception crash the tool call.
- Exception text may help debugging; production code should avoid leaking secrets or excessive internal detail.
- Catching `Exception` broadly can hide programming errors if used carelessly. Follow neighboring project conventions.

## 6. Safe defaults for optional fields

```python
authors = record.get("author_name") or []
```

- `dict.get(key)` returns the value for a key, or `None` if the key is missing.
- `or []` supplies an empty list if the returned value is falsy.
- A record with no author field maps to an empty list instead of causing a missing-key exception.

This is defensive parsing, not fabricated data: `[]` means author data was not supplied in that field, not that the book has no authors in reality.

## 7. Conditional URL building and f-strings

```python
book_url = (
    f"https://openlibrary.org{record['key']}"
    if record.get("key")
    else None
)
```

This is a conditional expression: `value_if_true if condition else value_if_false`.

- If `record.get("key")` is a non-empty value such as `/works/OL...`, it builds a full URL.
- If the key is missing or falsy, the result is `None`.
- The f-string inserts the key into the URL string.

The condition prevents a malformed result such as `https://openlibrary.orgNone`.

## 8. Normalizing third-party data

A raw API can contain many fields. A tool should return the fields its caller needs in a stable shape, such as:
- `title`
- `authors`
- `first_publish_year`
- `edition_count`
- `url`

Use safe access for optional fields and preserve the API's meaning. Do not fabricate titles, authors, years, or URLs.

## Quick revision

- `.strip()` removes surrounding whitespace.
- `dict.get()` safely looks up potentially missing keys.
- `or []` supplies an empty-list fallback for falsy author data.
- `max(1, min(x, 20))` clamps ordinary numbers to 1–20.
- `try/except` turns expected external failures into controlled error responses.
- An f-string formats strings using values.
- `None` represents absence of a value; it is not the text "None".
- Type annotations describe expected types but do not guarantee runtime validity.
