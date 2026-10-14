# 09 — Security and Safe Tool Design

**Estimated time:** 30 minutes  
**Prerequisite:** [03 — Tools, resources, and prompts](03-tools-resources-prompts.md)

MCP can make operations available to an AI application. Availability is not the same as permission. Safe servers restrict what can be called and validate every input.

## 1. The main risks

**Over-broad access:** a tool reads any file or queries any database table when it only needed one approved document.

**Prompt injection:** external content (a README, issue, webpage, or retrieved document) contains instructions that try to manipulate the model into taking an action. Treat retrieved content as untrusted data, not authority.

**Side effects:** a tool posts a comment, sends an email, changes a record, or deploys code. These actions need stronger controls than a read-only lookup.

**Secret leakage:** logs, tool results, or error messages accidentally return API keys, tokens, or personal data.

**Confused authorization:** the MCP server trusts the model to choose an authorized target rather than checking the caller's actual permissions.

## 2. Practical design rules

- Expose the smallest set of capabilities needed.
- Prefer read-only tools first.
- Validate types, ranges, lengths, identifiers, and allowed values on the server.
- Use allow-lists for files, commands, endpoints, and query targets.
- Reuse backend authentication and authorization; never use a tool wrapper to bypass them.
- Keep secrets in environment or secret-management configuration, not source code or tool output.
- Make errors useful without revealing internal paths, credentials, stack traces, or sensitive records.
- Require user confirmation or an explicit authorization step for impactful actions where appropriate.
- Log enough for debugging and auditing without logging secrets.
- Set timeouts and resource limits. Consider rate limiting for network-facing services.
- Treat tool output as data that may be incomplete or malicious.

## 3. Unsafe vs safer design

**Unsafe design:** `run_shell(command: str)` executes any command the model supplies.

Why it is unsafe: the input can perform arbitrary operations with the server process's permissions.

**Safer learning design:** a narrow tool such as `get_service_status()` that returns a pre-defined status. If a command must be run, use a small allow-list of fixed operations with validated arguments and appropriate permissions.

Do not expose arbitrary SQL, unrestricted filesystem reads, or unrestricted shell commands as a beginner exercise.

## 4. A small validation example

```python
def normalize_user_text(text: str) -> str:
    """Validate a small text input and trim surrounding whitespace."""
    if not isinstance(text, str):
        raise TypeError("text must be a string")
    if len(text) > 2_000:
        raise ValueError("text must be 2000 characters or fewer")
    return text.strip()
```

**Meaning**
- The type check makes the expected input explicit.
- The length limit prevents unexpectedly large inputs from flowing further into the application.
- `strip()` removes whitespace at the beginning and end.
- A real system should align limits with the application requirements and handle these errors at the protocol boundary.

Input validation does not by itself make a tool secure. Authorization and least privilege are separate requirements.

## Checkpoint

1. Why is a read-only tool usually easier to secure than a tool that changes production data?
2. Why should retrieved README text not be treated as trusted instructions?
3. What is the difference between validation and authorization?
4. Name two things that should never appear in ordinary logs.
