# 03 — Python, HTTP JSON, and MCP Concepts

## 1. What is an API?

An API is a defined way for one program to request information or actions from another program. Open Library exposes a search endpoint that accepts a query and returns JSON.

Example endpoint from the issue:

```text
https://openlibrary.org/search.json?q=the+hobbit&limit=1&fields=title,author_name,first_publish_year
```

The query asks for books matching “the hobbit,” limits the response, and requests only selected fields. The issue's example response includes a `docs` list containing book records.

A live API can be unavailable, slow, rate-limited, or return unexpected data. Code should handle those conditions.

## 2. JSON and defensive parsing

JSON represents structured data using objects, arrays, strings, numbers, booleans, and null. In Python, JSON objects usually become dictionaries and arrays become lists.

A response may omit optional fields. Safe code should not assume every book has an author or publication year. The issue's suggested mapping uses patterns like:

```python
authors = record.get("author_name") or []
```

Meaning:
- `record.get("author_name")` returns the value if the key exists, otherwise `None`.
- `or []` supplies an empty list when the value is missing or falsy.

This is a defensive default; it should not fabricate an author.

## 3. What is an MCP tool?

Model Context Protocol (MCP) is a protocol through which an AI application can discover and call tools or access other capabilities provided by a server. In this issue, the tool is a Python function exposed to the MCP server.

```text
AI host/client
   -> MCP request to call tool
   -> knowledge server
   -> registered Python function
   -> Open Library API
   -> normalized result/error
   -> MCP client / agent
```

The `@mcp.tool()` decorator registers the function as a tool with the MCP server. A plain Python function without the decorator can still exist in the module, but it is not registered through that decorator.

The docstring matters because it describes the tool's purpose and arguments to the model/client. It should be accurate, concise, and explicit about the expected inputs and output.

## 4. Why reuse existing helpers?

The issue says `get_json`, `tool_result`, and `tool_error` already exist.

- `get_json`: performs the HTTP request and parses JSON according to the repository's existing conventions.
- `tool_result`: wraps a successful result in the standard tool response.
- `tool_error`: wraps a failure with an error message and code.

These are descriptions from the issue. Inspect their actual implementations before relying on exact behavior. Reusing project helpers keeps the new tool consistent with existing tools and avoids unnecessary duplicate logic.

## 5. Input validation and bounded limits

A blank query is not useful and should be rejected clearly. The suggested implementation checks `query.strip()` so whitespace-only input is treated as empty.

The issue describes `max_results` as 1–20 with default 5. The suggested implementation clamps it to that range using `max(1, min(max_results, 20))`. Verify the project's desired behavior for non-integer inputs or unusual values before changing the suggested approach.

## 6. Error categories

| Situation | Expected category in issue |
|---|---|
| Empty/whitespace query | `bad_input` |
| API/network/JSON request exception | `upstream` |
| Valid search but no books returned | `not_found` |
| Results returned | success via `tool_result` |

Avoid swallowing errors silently. Return useful, non-sensitive error information consistent with project conventions.

## 7. URL construction

The suggested mapping creates a work URL only when the response contains a `key`, e.g. `https://openlibrary.org/works/OL...`. If the key is missing, it returns `None` rather than fabricating a URL.

## 8. Alternatives and trade-offs

- **Use existing `get_json` helper:** preferred if it already handles timeout, status codes, and JSON parsing in the project-approved way.
- **Write a new HTTP client call:** avoid unless existing helpers cannot meet requirements; it can duplicate timeout/error behavior.
- **Call a paid book API:** unnecessary for this issue and conflicts with its free/no-key premise.
- **Return raw API JSON:** less useful to callers and exposes unnecessary fields; the issue asks for a normalized result.

## 9. Things to verify in source

Before coding, inspect the actual helper signatures, return types, exception behavior, MCP version, and nearby tests. This page explains the concepts but does not substitute for code inspection.
