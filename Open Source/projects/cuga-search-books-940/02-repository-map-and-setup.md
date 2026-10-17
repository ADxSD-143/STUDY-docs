# 02 — Repository Map and Setup

## Repository distinction

The issue lives in the `cuga-project/cuga-agent` issue tracker, but its implementation links point to the separate repository `cuga-project/cuga-apps`. Confirm the correct code repository before cloning.

- Issue: https://github.com/cuga-project/cuga-agent/issues/940
- Code: https://github.com/cuga-project/cuga-apps

## Files relevant to the issue

```text
cuga-apps/
└── cuga-apps/
    ├── mcp_servers/
    │   └── knowledge/
    │       └── server.py          # tool implementations and shared helpers
    └── tests/
        └── test_mcp_tools.py      # MCP tool tests
```

This layout comes from the issue's linked paths. Inspect the current default branch before assuming the structure is unchanged.

## Prerequisites from the issue

The issue's setup section specifies:
- Python 3.13 (it says CUGA does not support Python 3.14 yet).
- `uv` for environment setup.
- Minimum dependencies for the MCP server work: `mcp>=1.0,<2`, `httpx`, `pydantic`, and `pytest`.
- Internet access for a live Open Library API call.
- No paid AI API key is needed for this tool issue.

Follow the repository's current setup instructions first; these notes summarize the issue, not a successful local setup run.

## Example setup commands from the issue

Use a fork URL after creating your own fork. Run these in a terminal compatible with the commands below; the activation command shown is for a Unix-like shell.

```bash
git clone https://github.com/<your-username>/cuga-apps.git
cd cuga-apps/cuga-apps
uv venv --python 3.13 .venv
source .venv/bin/activate
uv pip install "mcp>=1.0,<2" httpx pydantic pytest
```

What each command does:
- `git clone`: downloads your fork.
- `cd cuga-apps/cuga-apps`: enters the nested app source folder used by the issue's commands.
- `uv venv --python 3.13 .venv`: creates a virtual environment using Python 3.13.
- `source .venv/bin/activate`: activates that environment in bash/zsh.
- `uv pip install ...`: installs the listed dependencies into the active environment.

Expected behavior: each command completes without an error and the virtual environment uses Python 3.13. These commands have **not** been executed by this documentation task. On Windows PowerShell, use the appropriate activation script for the environment created by `uv`; check the current `uv` documentation if needed.

The `mcp<2` constraint matters because the issue explicitly says the tool servers do not yet support MCP version 2. Do not remove the upper bound casually.

## Baseline checks before edits

1. Read current project setup and contribution instructions.
2. Inspect the two target files and nearby helpers/tests.
3. Run the documented baseline test command if the environment is set up.
4. Record the exact command, output, and any skipped external tests.
5. Do not start implementation until issue availability is confirmed.

## Investigation commands

```bash
git status
git branch --show-current
python --version
python -m py_compile mcp_servers/knowledge/server.py tests/test_mcp_tools.py
```

- `git status`: shows current branch and changed files.
- `git branch --show-current`: confirms the active branch.
- `python --version`: confirms which interpreter is active.
- `python -m py_compile ...`: checks syntax in the named files; successful execution usually prints nothing. It does not prove tests pass or API behavior is correct.

Run commands from the directory where those relative file paths exist. Verify the working directory before executing them.
