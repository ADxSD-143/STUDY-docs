# 01 — Issue Analysis and Acceptance Criteria

## Source

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- Title: `feat(mcp-knowledge): add a search_books tool (Open Library, no key)`
- Last checked: 2026-10-17
- Issue metadata: open, unassigned, label `good first issue`
- Coordination warning: a contributor commented “I'd like to take this” on 2026-10-12. Availability needs confirmation.

## Problem in plain language

An AI model can invent book titles, authors, or publication details. The proposed tool should query the Open Library Search API so an agent can return real book records and links instead of relying on memory.

The requested change is a regular Python function exposed as an MCP tool, not a new model and not a paid API integration.

## Expected function

```python
search_books(query: str, max_results: int = 5) -> str
```

The issue's suggested behavior:
- Search by title, author, or subject.
- Default to five results.
- Clamp the requested limit to the 1–20 range.
- Return title, authors, first publication year, edition count, and Open Library URL.
- Reject blank queries with error code `bad_input`.
- Return `not_found` when there are no matching books.
- Convert upstream API failures into a structured `upstream` error.
- Return results through the existing `tool_result` helper.
- Expose the function with `@mcp.tool()`.

Treat this as the issue's proposed contract. Check the latest source and maintainer guidance before implementing.

## Requested files

1. `cuga-apps/mcp_servers/knowledge/server.py`: add a Books/Open Library section above the Semantic Scholar section as indicated by the issue.
2. `cuga-apps/tests/test_mcp_tools.py`: add success and empty-query tests near the existing knowledge-tool tests.

The issue explicitly says not to edit the Tools header list, README files, or the “36 MCP tools” count because maintainers coordinate those edits across concurrent PRs. Reconfirm this instruction against the latest issue before working.

## Acceptance checklist

- [ ] Function is registered with `@mcp.tool()`.
- [ ] Empty/whitespace-only query returns `bad_input`.
- [ ] Query is trimmed before use and in the returned metadata.
- [ ] Result limit follows the documented 1–20 bounds.
- [ ] API response fields are accessed safely.
- [ ] Output contains the requested normalized fields.
- [ ] Book URL is constructed only when a valid work key exists.
- [ ] Empty result list returns `not_found`.
- [ ] Network/API/JSON failures are handled with `upstream`.
- [ ] Tests cover important success and error cases.
- [ ] Existing tests and required checks are run.
- [ ] Final diff contains only intended files.

## Questions to answer while reading the code

1. What does `get_json` do and how does it signal HTTP/JSON errors?
2. What shape do `tool_result` and `tool_error` produce?
3. How do existing tools validate arguments and handle exceptions?
4. How are MCP tools discovered and tested in this repository?
5. Which tests run locally, and which require external services?
6. Does current implementation already contain this tool or a related change?

Do not assume answers based only on this issue description; inspect current source.
