# 05 — Tests, CI, and Code Review

## The regression-test loop

```text
Reproduce bug
   -> add test for expected behavior
   -> verify test fails for the right reason
   -> implement focused fix
   -> verify new test passes
   -> run relevant existing tests
   -> run lint/type/format checks
   -> inspect final diff
```

A test that passes before the fix may not be testing the bug. When possible, show that the new test fails before the fix and passes afterward.

## Types of checks

- **Unit test:** tests a small function or component.
- **Integration test:** checks how components work together.
- **External/integration test:** may require network, credentials, or services; inspect project markers and setup before running.
- **Lint:** flags code-quality/style issues.
- **Formatter:** applies consistent formatting.
- **Type check:** checks static type expectations.
- **CI:** executes automated checks in the project's configured environment.

Use the exact commands documented by the repository. Example for a pytest project:

```powershell
python -m pytest
```

Runs pytest in the active Python environment. The summary reports passed, failed, skipped, or errored tests. A missing pytest module usually indicates an environment/dependency issue; read setup instructions before changing code.

Example syntax check:

```powershell
python -m py_compile path/to/module.py path/to/test_module.py
```

Compiles the named Python files to check syntax. Successful execution normally prints nothing and exits successfully. This **does not** prove runtime behavior, API correctness, or test assertions.

## Mocking external APIs

Unit tests should usually not depend on a live external service unless the project explicitly defines an external/integration test. Mocking lets a test provide a controlled response or exception so behavior is repeatable.

Test success, empty results, missing fields, invalid input, and upstream failure where relevant. Assert meaningful output, not merely that the function returned something.

## When CI fails

1. Open the failing workflow/job.
2. Read the first meaningful error and surrounding context.
3. Identify whether it is a code failure, dependency/runtime mismatch, missing secret, network issue, formatting issue, or flaky test.
4. Reproduce locally if possible.
5. Fix the cause rather than deleting a valid test.
6. Run the relevant checks and push the fix.
7. Confirm the new CI run completes.

Do not claim a check passed if it was not run or was skipped.

## PR description template

```markdown
## Problem
What behavior or issue does this address?

## Solution
What changed, and why is this approach appropriate?

## Testing
- Command:
- Result:

## Notes / limitations
Any remaining limitations or environment-dependent checks.
```

Use issue references and sign-off conventions required by the repository. Keep the PR focused. If a maintainer requests changes, update the same branch, retest, and push.

## Final diff checklist

- [ ] Only relevant files changed.
- [ ] No secrets, generated files, or unrelated formatting changes.
- [ ] Tests cover the new/changed behavior.
- [ ] Error paths and edge cases were considered.
- [ ] Documentation matches implementation.
- [ ] Commands and outputs in the PR description are truthful.
