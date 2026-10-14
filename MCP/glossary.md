# MCP Glossary and Quick Revision

## Core terms

| Term | Plain-language meaning |
|---|---|
| MCP | A protocol for exchanging context and invoking capabilities between compatible AI applications and servers |
| Host | The AI application coordinating the model and connections |
| Client | The host component that speaks MCP to a specific server |
| Server | Program that exposes MCP capabilities |
| Tool | A callable operation that may perform a computation or action |
| Resource | Readable information offered as context |
| Prompt | A reusable prompt template |
| Transport | How protocol messages travel, for example stdio or Streamable HTTP |
| stdio | Local process communication over standard input/output |
| Streamable HTTP | MCP transport over HTTP |
| Schema | Structured description of expected input/output data |
| Validation | Checking that input follows rules |
| Authorization | Checking whether a caller is allowed to perform an action |
| Least privilege | Giving a component only the access it needs |
| Prompt injection | Malicious or misleading instructions embedded in content that a model reads |
| Inspector | A developer tool to explore and test a server's capabilities |

## One-line recall

- MCP standardizes the connection; it does not replace your application logic.
- Host coordinates, client communicates, server offers capabilities.
- Tool = action; resource = context; prompt = reusable template.
- Start with a local stdio server; only add remote transport when there is a real requirement.
- Validate input, check authorization, restrict side effects, and keep secrets out of outputs.
- Test business logic and protocol behavior separately.
- Verify SDK version before copying examples.

## Self-test

1. A server exposes a function that deletes records. Which security safeguards matter most?
2. You need to share model-card text as context. Which primitive is a natural fit?
3. What happens if a server prints diagnostic text to stdout while using stdio?
4. Why should your MCP wrapper call an existing, tested inference function?
5. Which official docs should you check when an API example fails?

## Official references

- [MCP architecture](https://modelcontextprotocol.io/docs/learn/architecture)
- [MCP specification](https://modelcontextprotocol.io/specification)
- [Official Python SDK](https://py.sdk.modelcontextprotocol.io/)
- [Python SDK first steps](https://py.sdk.modelcontextprotocol.io/get-started/first-steps/)
