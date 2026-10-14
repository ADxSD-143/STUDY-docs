# 03 — Tools, Resources, and Prompts

**Estimated time:** 25–35 minutes  
**Prerequisite:** [02 — Host, client, and server](02-host-client-server.md)

An MCP server can expose different kinds of capabilities. Start with three common primitives and the question each one answers.

## 1. Tools — “Do something”

A tool is a callable operation. The model may decide to request it, while the host can enforce policies and user approval.

Examples:
- calculate precision/recall from supplied values;
- classify a short text;
- query an allow-listed database view;
- run a safe health check.

Tools can have side effects, so the implementation must validate inputs and restrict dangerous operations.

## 2. Resources — “Give me context”

A resource exposes data for an application to read and include as context.

Examples:
- model card or model metadata;
- project documentation;
- database schema;
- a permitted configuration summary.

Think “readable source of information.” A resource should not unexpectedly perform a destructive action just because it is read.

## 3. Prompts — “Use this reusable template”

A prompt is a reusable template that helps structure an interaction.

Examples:
- “Review this classification report for likely data leakage.”
- “Explain this repository's test failure.”
- “Summarize this model card using the standard project template.”

A prompt is not a trained model; it is a named, reusable instruction template.

## 4. Decision table

| Scenario | Best starting point | Why |
|---|---|---|
| Calculate a score from input numbers | Tool | It performs a computation |
| Read the project model card | Resource | It supplies context |
| Reuse a structured code-review instruction | Prompt | It is a template |
| Delete a database table | Usually do not expose casually | High-impact side effect needs strong authorization and safeguards |

A useful shorthand is **tool = action, resource = context, prompt = template**. This is a memory aid, not a substitute for reading the actual interface requirements.

## 5. How a server declares a capability

In the Python SDK, decorators can register functions as MCP capabilities. The exact API is SDK-version-sensitive; later lessons pin and verify the setup used by this course.

Illustrative shape:

```python
@mcp.tool()
def count_words(text: str) -> int:
    """Count whitespace-separated words."""
    return len(text.split())
```

**Line-by-line meaning**
- `@mcp.tool()` registers the function as a tool with the server object named `mcp`.
- `count_words` is the function clients will be able to discover by its exposed name.
- `text: str` communicates the expected input type.
- `-> int` communicates the output type.
- The docstring explains what the tool does; descriptive documentation helps a model choose correctly.

The code is not standalone: it assumes `mcp` has already been created using the SDK. The full runnable setup is in Lesson 04.

## 6. Design names and descriptions well

Prefer:
- `summarize_model_metrics`: clear operation name.
- “Return accuracy, precision, recall, and F1 for the provided predictions and labels.”: explicit description.

Avoid:
- `do_stuff`: vague.
- “Use me”: no useful intent or constraints.

A good description explains what the capability does, required inputs, output, and important limitations. Do not hide permission requirements in an ambiguous description.

## Checkpoint

Classify each as a **tool**, **resource**, or **prompt**:
1. Fetch the README content of an allowed repository.
2. Run a text-classification function on supplied text.
3. Reuse a standard template for explaining an error log.
4. Read a model's metadata document.

Then explain why a tool that sends an email needs more care than a tool that only counts words.
