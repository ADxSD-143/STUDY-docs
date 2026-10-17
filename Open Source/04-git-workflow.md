# 04 — Git Workflow Reference

The detailed real walkthrough and the remote-permission mistake from the first practice PR are documented in [github.md](../../github.md). This page is the reusable quick reference.

## Standard workflow

```text
Fork upstream on GitHub
  -> clone your fork
  -> create a feature branch
  -> inspect repository and edit
  -> review diff
  -> stage intended files
  -> commit
  -> push branch to fork
  -> open PR against upstream
```

## Commands, purpose, and expected behavior

```powershell
git --version
```
Shows the installed Git version. If the command is not recognized, install Git for Windows or fix PATH, then reopen the terminal.

```powershell
git clone https://github.com/OWNER/REPO.git
cd REPO
```
Clones the URL into a local folder and enters it. Replace the placeholders with the correct repository URL and folder name.

```powershell
git remote -v
```
Shows fetch/push URLs. For a typical fork workflow, `origin` should point to your fork, not to the upstream repository where you lack write access.

```powershell
git switch -c feat/short-description
git branch --show-current
```
Creates and switches to a branch, then prints its name. Use a name consistent with the project's conventions.

```powershell
git status
git diff
git diff --staged
```
- `git status`: current branch and changed files.
- `git diff`: unstaged changes.
- `git diff --staged`: staged changes that will go into the next commit.

Review the diff before staging and again before committing. It should contain only intended changes.

```powershell
git add path/to/file.py
git status
git commit -m "Fix concise description"
git push -u origin feat/short-description
```
Stages one selected file, checks status, commits the staged snapshot, and pushes the branch while setting its upstream tracking branch. Exact commands and sign-off requirements vary by project; follow its instructions.

## Safe habits

- Never use `git add .` without first checking what changed.
- Never commit API keys, tokens, passwords, or private keys.
- Do not force-push a shared branch unless you understand the consequences and the project workflow requires it.
- Before using `git commit --amend` or force-push, confirm whether the branch is shared and follow maintainer guidance.
- Do not push to upstream unless you have permission and the project explicitly uses that workflow.
- Check the PR's base repository/branch and head repository/branch before submitting.

## Troubleshooting: permission denied on push

If GitHub says you do not have permission:
1. Run `git remote -v`.
2. Check whether `origin` points to your fork.
3. Verify that you are authenticated as the correct account.
4. Fix the URL only if it is actually wrong; do not confuse an authentication problem with a remote URL problem.

The first-contribution guide records the exact incident and fix: [GitHub & Git: First Open-Source Contribution](../../github.md).
