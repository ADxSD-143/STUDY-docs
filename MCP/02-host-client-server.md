# 02 — Host, Client, and Server

**Estimated time:** 20 minutes  
**Prerequisite:** [01 — What MCP is](01-what-is-mcp.md)

These three words describe different responsibilities. Keep them separate.

## 1. The roles

**Host** — the AI application the user interacts with. It coordinates the model and its connections to MCP servers. Examples could include an AI-enabled IDE or desktop assistant.

**Client** — the MCP-speaking component inside the host. It handles communication with a particular server. A host may use a separate client connection for each server.

**Server** — the program that offers capabilities. It might expose a function, project documentation, or a reusable prompt. The server does not have to be an AI model.

## 2. Everyday analogy

Think about ordering from a restaurant through a delivery app:
- **Host:** the delivery app you use.
- **Client:** the app component that communicates with the restaurant's ordering system.
- **Server:** the restaurant ordering system that accepts the request and returns the result.

This is only an analogy. Actual MCP communication follows a protocol, not a human conversation.

## 3. Trace a realistic request

You ask an AI coding assistant: “How many rows are in my training dataset?”

1. The **host** interprets the user request and coordinates the model.
2. An MCP **client** discovers that a connected server provides a dataset-summary tool.
3. The model/host decides whether to call the tool, subject to the host's policies and permissions.
4. The **client** sends the MCP request.
5. The **server** runs the Python code that reads the permitted dataset summary.
6. The result returns to the host, where it can be shown to the user or used as context.

The server should not be assumed to have access to your files automatically. Access exists only if its implementation and runtime permissions provide it.

## 4. Role diagram

```text
User
  |
  v
Host (AI application + orchestration)
  |
  v
MCP Client  <---- protocol messages ---->  MCP Server
                                             |
                                             v
                                  Python function / API / data
```

The AI model normally sits under the host's orchestration. MCP defines the connection to server capabilities; it does not dictate how the host must reason.

## 5. Keep application logic separate

A clean design keeps the actual calculation in a normal Python function and uses a thin MCP layer to expose it. This makes the code easier to test and reuse from a CLI, FastAPI, or a unit test.

```python
def dataset_row_count(rows: list[dict]) -> int:
    """Business logic: count supplied records."""
    return len(rows)
```

**Meaning and use:** This function has no dependency on MCP. That is good architecture: protocol code should not be mixed unnecessarily into core application logic.

## Checkpoint

1. Which component offers tools and resources?
2. Which component maintains MCP communication from inside the host?
3. Can one host connect to multiple MCP servers?
4. Why is it useful to keep core Python logic independent of MCP?

**Common trap:** Calling the server “the AI.” A server may be a small utility process that exposes a few functions, with no model inside it.
