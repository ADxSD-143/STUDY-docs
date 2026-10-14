# 00 — MCP Roadmap and Study Workflow

## Outcome

By the end, you should be able to explain MCP to another developer, build a small Python MCP server, inspect and test its capabilities, connect a client, safely expose a useful AI/ML or backend function, and make sense of an MCP open-source repository.

## Prerequisites

You already have the essential starting point if you can:
- Read basic Python functions and imports.
- Understand JSON objects such as `{"text": "hello"}`.
- Recognize that a backend function receives input and returns output.

You do **not** need to learn an LLM from scratch or pay for an LLM API to learn the protocol.

## Learning sequence

| Stage | Learn | Proof that you understand it |
|---|---|---|
| 1. Mental model | Why MCP, what it is not | Explain it with a real-life analogy |
| 2. Architecture | Host, client, server | Trace one request through the components |
| 3. Capabilities | Tools, resources, prompts | Choose the right primitive for a scenario |
| 4. First server | Python SDK and type hints | Run a tiny local server |
| 5. Developer workflow | Inspector, logs, errors | Call a tool and interpret the result |
| 6. AI/ML integration | Wrap existing functions | Expose a harmless model-info or inference function |
| 7. Client basics | Discover and call a capability | Write or inspect a simple client |
| 8. Transport | stdio and Streamable HTTP | Choose a suitable transport for a use case |
| 9. Reliability | Validation, permissions, secrets | Explain what must not be exposed blindly |
| 10. Open source | Read issues, tests, docs, versions | Find a small, bounded contribution |
| 11. Capstone | ML helper server | Demonstrate and document it |

## Study routine

For each lesson:
1. Read only the current lesson.
2. Explain the main idea in your own words.
3. Run the code if the lesson includes code.
4. Answer the checkpoint without looking back.
5. Fix misunderstandings before moving forward.

## Scope guard

MCP's core mental model is small. Learn the three capabilities and a basic server before reading transport details. Do not confuse learning more terminology with making progress.

## Version note

The MCP specification and SDKs evolve. Treat code as version-sensitive: check the official Python SDK's current first-steps page and release line before installing. If an existing project pins an older SDK, follow its pinned version rather than mixing APIs.

## Checkpoint

1. What practical ability should you have at the end of this track?
2. Why should you avoid starting with advanced protocol internals?
3. What should you verify before using a copied SDK example?
