# 12 — Mini Capstone: ML Study Helper MCP Server

**Goal:** Build a tiny server with two safe tools and one piece of read-only context.  
**Prerequisite:** Lessons 01–10. Build only after the first server is working.

## Product brief

Create an MCP server to help with ML study and project work. It should:
1. Count words in a user-provided text.
2. Validate a set of metric values between 0 and 1 and return a summary.
3. Provide a short static resource explaining the metric conventions used by the project.

This is a learning helper, not an autonomous agent and not a production model service.

## Acceptance criteria

- [ ] The server starts locally with the pinned SDK version.
- [ ] Both tools are discoverable.
- [ ] Valid input produces predictable output.
- [ ] Invalid metric values are rejected.
- [ ] The resource provides readable context.
- [ ] Core Python logic can be unit-tested without MCP.
- [ ] README explains setup, expected output, and limitations.
- [ ] No paid LLM API, credentials, arbitrary shell execution, or unrestricted file access is required.

## Suggested file layout

```text
mcp-ml-study-helper/
├── server.py
├── logic.py
├── tests/
│   └── test_logic.py
├── requirements.txt
└── README.md
```

### Why separate `logic.py`?

It contains ordinary Python functions. `server.py` registers those functions with MCP. This separation makes functions easier to test and reuse from a normal application.

## Implementation steps

1. Implement and test `count_words(text)` in `logic.py`.
2. Implement `validate_metrics(precision, recall, f1)` and reject values outside `[0, 1]`.
3. Add unit tests for normal values, empty text, and invalid metrics.
4. Register the functions as tools from `server.py`.
5. Add a read-only resource describing precision, recall, and F1 in your own words.
6. Run the server with the Inspector and verify every capability.
7. Document exact setup commands and expected outputs.

## Definition of done

A reviewer can clone the project, follow the README, start it, discover each capability, reproduce the example results, and understand what is intentionally out of scope.

## Reflection questions

1. Which logic belongs in `logic.py`, and which belongs in `server.py`?
2. Why is the metrics validation duplicated neither blindly nor only in the description?
3. What permissions would change if this helper were modified to read local model files?
4. How would you test the resource separately from the tool calls?

**Extension — only after the core works:** replace the static resource with model metadata from a known, allow-listed local file. Do not accept an arbitrary path from the model.
