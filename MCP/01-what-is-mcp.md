# 01 — What Is MCP?

**Estimated time:** 20–30 minutes  
**Prerequisite:** Basic Python functions and JSON.

## 1. The problem, in plain language

Imagine you build an AI assistant for your college project. It needs to answer questions about a dataset, inspect a model's metrics, search project documentation, and perhaps trigger a safe backend action.

Without a common integration pattern, every AI application and every tool may need its own custom connection code. One integration might expect a REST endpoint, another a Python function, and another a custom JSON format. Repeating these integrations is tedious and makes tools harder to reuse.

**Model Context Protocol (MCP)** is an open protocol that standardizes how an AI application discovers and interacts with capabilities provided by external systems. Those capabilities can include callable tools, readable context, and reusable prompts.

Think of MCP as a **standard connector contract**, not as the intelligence itself.

## 2. Real-life intuition

Imagine a universal USB standard:
- A laptop is the AI application.
- A device provides a capability.
- The connector standard defines how they communicate.

MCP is not literally USB and the analogy is imperfect, but the idea is useful: a shared protocol reduces the need for every pair of systems to invent a completely separate connection method.

Another example: a restaurant's menu tells a customer what they can order and what information each order needs. MCP servers similarly describe what they offer, and an MCP client can discover those offerings through the protocol.

## 3. What MCP is — and is not

| MCP is | MCP is not |
|---|---|
| A standard way for AI applications to connect to external capabilities | An LLM or a trained model |
| A protocol with defined request/response behavior | A guarantee that an answer is correct |
| A way to expose tools, resources, and prompts | A replacement for Python, FastAPI, databases, or model code |
| A reusable integration boundary | Permission to expose every local file or database action |

**Important distinction:** MCP standardizes the connection. Your function still does the real work. If a Python function calculates an F1 score, MCP can make that function discoverable and callable by a compatible client; MCP does not calculate the F1 score by itself.

## 4. A tiny before-and-after example

Suppose you already have this ordinary Python function:

```python
def count_words(text: str) -> int:
    """Count whitespace-separated words."""
    return len(text.split())

print(count_words("MCP connects AI to tools"))
```

**Expected output**
```text
5
```

**Meaning**
- `def` defines a normal Python function.
- `text: str` says the input is expected to be a string.
- `-> int` documents the expected return type.
- `text.split()` splits the string on whitespace.
- `len(...)` counts the resulting pieces.

There is no MCP here. This function works in an ordinary Python program.

MCP becomes useful when you want an MCP-compatible AI application to discover this operation and request it through the standardized protocol. A later lesson will show the server wrapper.

## 5. Where MCP fits your goals

| Your area | Example capability to expose |
|---|---|
| AI/ML | Read model metadata or call a controlled inference function |
| NLP | Run a text-cleaning or classification function |
| Backend | Query an allow-listed endpoint or retrieve a service status |
| RAG | Retrieve permitted document snippets or collection metadata |
| Open source | Make project information or safe developer utilities available to an AI host |

You do **not** need MCP for every function. If a normal Python call solves the problem inside one program, keep it simple. MCP matters when another compatible application needs a standardized way to discover and use that capability.

## 6. The request in one sentence

A client discovers a capability made available by a server, then requests it using MCP's defined message format; the server executes the relevant implementation and returns a result.

You do not need to memorize the protocol's message format yet. First understand the roles, then the details will make sense.

## Checkpoint — answer before moving on

1. A model is the same thing as MCP. True or false? Explain.
2. You have a Python function that cleans text. Does MCP replace that function?
3. Give one case where MCP is useful and one where a normal Python call is enough.
4. In your own words, what problem does a shared protocol solve?

**Common trap:** Saying “MCP makes the AI smarter.” More accurately, MCP can give an AI application a standardized path to outside context or actions. The quality of reasoning still depends on the model, context, implementation, and safeguards.

## Lesson complete when

You can explain MCP without using the phrase “it is an AI model,” and you can distinguish a normal Python function from the protocol that exposes it.
