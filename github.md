# GitHub & Git: First Open-Source Contribution

A practical, beginner-friendly record of my first contribution using the **First Contributions** repository. This guide documents the full workflow from forking a repository to getting a Pull Request merged.

- **Contributor:** Aditya Narayan 
- **GitHub:** https://github.com/ADxSD-143
- **Practice repository:** https://github.com/firstcontributions/first-contributions
- **My fork:** https://github.com/ADxSD-143/first-contributions
- **Merged Pull Request:** https://github.com/firstcontributions/first-contributions/pull/126562
- **Shell:** Windows PowerShell
- **Local folder used:** `D:\\open source\\first-contributions`

> Note: This was a beginner practice contribution (adding a contributor entry). The workflow is useful Git/GitHub practice, but meaningful GSoC contributions usually involve useful code, tests, documentation improvements, or bug fixes in a project's actual codebase.

---

## 1. Git and GitHub: The basic idea

- **Git** is a version-control tool that tracks changes in files.
- **GitHub** hosts Git repositories online and provides collaboration features such as Pull Requests.
- **Fork**: your own GitHub copy of another repository.
- **Clone**: download a repository to your computer.
- **Branch**: an independent line of work, so changes can be prepared without changing `main`.
- **Stage**: choose the changes that will go into the next commit.
- **Commit**: save a named checkpoint of staged changes.
- **Push**: upload local commits/branches to a remote repository.
- **Pull Request (PR)**: propose that maintainers merge your branch into the original project.
- **Merge**: integrate the PR changes into the target branch.

Typical workflow:

```text
Original repository
       |
       | Fork on GitHub
       v
Your GitHub fork
       |
       | Clone to computer
       v
Local repository
       |
       | Create branch -> edit files -> stage -> commit
       v
Local branch
       |
       | Push
       v
Branch on your GitHub fork
       |
       | Open Pull Request
       v
Original repository maintainers review and merge
```

## 2. One-time checks

Open PowerShell and check that Git is installed:

```powershell
git --version
```

If this prints a Git version, Git is available. If PowerShell says the command is not recognized, install Git for Windows and reopen PowerShell.

Set your Git commit identity if you have not already configured it:

```powershell
git config --global user.name "Aditya Narayan Laha"
git config --global user.email "YOUR_GITHUB_NOREPLY_OR_COMMIT_EMAIL"
```

Replace the email placeholder with the email you want recorded in commits. Do not paste passwords, personal access tokens, or other credentials into commands or public files.

Check the current configuration:

```powershell
git config --global user.name
git config --global user.email
```

## 3. Fork the repository on GitHub

1. Open https://github.com/firstcontributions/first-contributions.
2. Click **Fork**.
3. Create the fork under your own account, `ADxSD-143`.
4. The fork should be available at https://github.com/ADxSD-143/first-contributions.

Forking is done on the GitHub website; it is not a terminal command.

## 4. Clone your fork

In the original attempt, I initially typed a malformed command:

```powershell
git clonehttps://github.com/firstcontributions/first-contributions.git
```

It failed because there was no space between `clone` and the URL. The correct form has a space. For this workflow, clone **your fork**:

```powershell
cd "D:\\open source"
git clone https://github.com/ADxSD-143/first-contributions.git
cd first-contributions
```

Explanation:

- `cd "D:\\open source"` moves PowerShell into the parent folder. Quotes are needed because the path contains a space.
- `git clone URL` downloads the repository and creates a local folder.
- `cd first-contributions` moves into the local repository.

Check the current folder and repository status:

```powershell
Get-Location
git status
```

## 5. Create a separate branch

```powershell
git switch -c add-aditya-narayan-laha
```

This creates and switches to a new branch. The `-c` option means create.

For older Git versions, the equivalent command is:

```powershell
git checkout -b add-aditya-narayan-laha
```

Confirm the branch:

```powershell
git branch --show-current
```

Expected output:

```text
add-aditya-narayan-laha
```

## 6. Edit the file

Open this file in VS Code or another text editor:

```text
D:\\open source\\first-contributions\\Contributors.md
```

Add your entry in the appropriate place among the existing entries, following the file's formatting. For this practice contribution, the line was:

```markdown
- [Aditya Narayan Laha](https://github.com/ADxSD-143)
```

Save the file with `Ctrl+S`.

Before staging, inspect what changed:

```powershell
git status
git diff -- Contributors.md
```

- `git status` shows modified, staged, and untracked files.
- `git diff -- Contributors.md` displays the unstaged changes in that file.

Always check the diff before committing. Stage only intended changes.

## 7. Stage the change

```powershell
git add Contributors.md
git status
```

The first command stages the selected file. The second confirms that it appears under **Changes to be committed**.

For more control over individual parts of changes, use interactive staging:

```powershell
git add -p
```

Review the prompts carefully; only stage changes you intend to include.

## 8. Commit the staged change

```powershell
git commit -m "Add Aditya Narayan Laha to Contributors list"
```

A commit records the staged changes with a message. A successful commit typically reports the number of files changed and insertions/deletions.

Check the latest commit:

```powershell
git log -1 --oneline
git status
```

## 9. Inspect the remote before pushing

```powershell
git remote -v
```

A remote is a nickname for a Git repository URL. `origin` is commonly used for the repository that was cloned.

### Important error encountered: pushing to the original repository

The first push failed with:

```text
ERROR: Permission to firstcontributions/first-contributions.git denied to ADxSD-143.
fatal: Could not read from remote repository.
```

The remote output showed:

```text
origin  git@github.com:firstcontributions/first-contributions.git (fetch)
origin  git@github.com:firstcontributions/first-contributions.git (push)
```

That meant `origin` pointed to the upstream/original repository, where I did not have permission to push. Contributors normally push to **their own fork**, then open a PR to the original repository.

### Fix the remote URL

```powershell
git remote set-url origin https://github.com/ADxSD-143/first-contributions.git
git remote -v
```

After the fix, both fetch and push URLs should be:

```text
https://github.com/ADxSD-143/first-contributions.git
```

This changes the local `origin` URL. It does not grant access to the original repository; it correctly directs the push to your fork.

## 10. Push the branch to your fork

```powershell
git push -u origin add-aditya-narayan-laha
```

- `git push` uploads commits to the remote.
- `origin` is the remote name.
- `add-aditya-narayan-laha` is the branch to upload.
- `-u` sets the upstream tracking branch, which makes future pushes from this branch simpler.

A successful push reports that the new branch was created on your fork. GitHub may also print a link to open a Pull Request.

## 11. Open a Pull Request

For this contribution, GitHub provided this PR link:

https://github.com/ADxSD-143/first-contributions/pull/new/add-aditya-narayan-laha

Before creating the PR, verify:

- **Base repository:** `firstcontributions/first-contributions`
- **Base branch:** `main`
- **Head repository:** `ADxSD-143/first-contributions`
- **Compare branch:** `add-aditya-narayan-laha`

Example title:

```text
Add Aditya Narayan Laha to Contributors list
```

Review the changed-files tab to ensure the PR contains only the changes you intended. Then select **Create pull request**.

## 12. Verify the result

The practice Pull Request was merged successfully:

- **PR:** [#126562 — Add Aditya Narayan Laha to Contributors list](https://github.com/firstcontributions/first-contributions/pull/126562)
- **Status:** Merged
- **Target branch:** `main`

A merged PR means the contribution was integrated into the original repository. Keep the PR link as a record of the completed workflow.

## 13. Quick command reference

Run commands from inside the repository unless a step says otherwise.

| Goal | Command |
|---|---|
| Check Git installation | `git --version` |
| Move to a folder | `cd "D:\\open source"` |
| Clone a repository | `git clone https://github.com/OWNER/REPO.git` |
| Enter the repository | `cd REPO` |
| Check working-tree state | `git status` |
| Check current branch | `git branch --show-current` |
| Create and switch branch | `git switch -c BRANCH_NAME` |
| Inspect unstaged changes | `git diff` |
| Stage a specific file | `git add FILE_NAME` |
| Stage selected hunks interactively | `git add -p` |
| Commit staged changes | `git commit -m "Meaningful message"` |
| See latest commit | `git log -1 --oneline` |
| List remote URLs | `git remote -v` |
| Change a remote URL | `git remote set-url origin URL` |
| Push a branch and set upstream | `git push -u origin BRANCH_NAME` |

## 14. Troubleshooting checklist

**Push permission denied**
1. Run `git remote -v`.
2. Verify that `origin` points to your fork, not the original repository.
3. If needed, set it with `git remote set-url origin https://github.com/YOUR-USERNAME/REPO.git`.
4. Retry the push.

**Path contains spaces**
Use quotes, for example:

```powershell
cd "D:\\open source"
```

**Git says there is nothing to commit**
Run `git status`. Make sure the file was saved, and stage the intended changes with `git add FILE_NAME`.

**Authentication is requested**
Complete GitHub's supported browser or credential-manager authentication flow. Never put passwords or tokens directly in the remote URL or this document.

**Before opening a PR**
Run `git status`, inspect `git diff` before staging, and review the final PR diff on GitHub.

---

## 15. What to practise next

This first exercise taught the mechanics of collaborating through GitHub. The next step toward GSoC is to choose an actual open-source project, read its contribution guidelines, reproduce a bug or understand a small issue, make a targeted fix, add/update tests where appropriate, and submit a clear PR with evidence that the change works.

Do not choose projects only because competition appears low. Build a record of thoughtful, reviewable contributions in a project whose language and problem domain match your interests.
