# 03 — Reading an Unfamiliar Codebase

## Goal

Understand the existing system before changing it. You do not need to understand every file; start with the path related to the issue.

## Exploration sequence

1. Read `README.md` to understand the project's purpose.
2. Read `CONTRIBUTING.md`, `AGENTS.md`, and local instructions if present.
3. Inspect the project layout and locate package/test directories.
4. Identify the supported language/runtime and package manager.
5. Find the relevant function or route.
6. Search for callers, helpers, and nearby tests.
7. Run the smallest relevant existing test or baseline check.
8. Record uncertainties before implementing.

## Useful commands

Run these from the repository root unless otherwise noted.

```powershell
Get-Location
git status
git branch --show-current
Get-ChildItem
```

- `Get-Location`: prints the current directory.
- `git status`: shows current branch and whether files have changed.
- `git branch --show-current`: prints the active branch.
- `Get-ChildItem`: lists files and folders in PowerShell.

**Expected result:** the current repository path, a clean or understood Git status, the branch name, and a file listing. If the folder is not the intended repository, stop and navigate to the correct directory before running project commands.

For Python repositories, also inspect `pyproject.toml`, `requirements.txt`, lockfiles, and test configuration if present. Do not assume every Python project uses the same package manager or test command.

## Trace a function

For a function, ask:
- Who calls it?
- What arguments does it receive?
- What does it return?
- What helpers or external services does it use?
- What can fail?
- What happens for missing, empty, malformed, or unexpected data?
- Which tests describe current behavior?

A useful mental model:

```text
Input
  -> validation
  -> core logic / helper calls
  -> error handling
  -> output formatting
  -> caller / test
```

## Baseline before edits

Run the project's documented tests before modifying code when setup permits. Record the command and result. This helps distinguish an existing failure from a regression introduced by your change.

If setup fails, capture the exact error and investigate environment/version instructions. Do not silently treat a failed test run as a passing baseline.

## Using AI to read code

Good prompts ask about specific evidence:
- “Explain this function line by line and identify its inputs, outputs, and failure paths.”
- “Trace where this helper is called and cite the relevant symbols/files.”
- “What tests should cover the empty-input and upstream-error cases for this function?”

Then verify the explanation in source code. AI may misunderstand stale docs or infer behavior that the code does not implement.

## Notes template

- Repository and branch:
- Runtime and package manager:
- Project instructions read:
- Relevant files:
- Existing helpers:
- Existing tests:
- Baseline command and output:
- Uncertainties:
- Next smallest investigation step:
