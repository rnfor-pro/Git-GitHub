# Git Command Cheatsheet

A quick reference for every command covered in this course, grouped by task.

---

## Setup and Configuration

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git --version` | Shows the installed Git version | Verifying Git is installed |
| `git config --global user.name "Your Name"` | Sets your Git display name | First-time setup |
| `git config --global user.email "email@example.com"` | Sets your Git email | First-time setup |
| `git config --global --list` | Shows all your Git configuration | Checking your settings |

---

## Starting and Cloning Repositories

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git init` | Creates a new local Git repository in the current folder | Starting a new project locally |
| `git clone <repo-url>` | Downloads a remote repository to your computer | Getting a copy of an existing repo |
| `git remote -v` | Shows the remote repositories connected to your local repo | Checking what remote is configured |
| `git remote add origin <repo-url>` | Links your local repo to a remote repository | After `git init`, before first push |

---

## Checking Status and History

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git status` | Shows which files have changed, are staged, or are untracked | All the time — check this often |
| `git log` | Shows full commit history | Reviewing past commits |
| `git log --oneline` | Shows compact one-line commit history | Quick history overview |
| `git diff` | Shows changes not yet staged | Before staging, to review edits |
| `git diff --staged` | Shows changes already staged | Before committing, to review staged changes |

---

## Staging and Committing

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git add <file>` | Stages a specific file | Adding one file at a time |
| `git add .` | Stages all changed files in the current directory | Staging everything at once |
| `git commit -m "message"` | Creates a commit with a message | After staging your changes |

> **Beginner tip:** Write your commit messages in the present tense: "Add login form" not "Added login form."

---

## Pushing and Pulling

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git push` | Uploads commits to the remote repository | After committing, to share your work |
| `git push -u origin <branch-name>` | Pushes a new branch to GitHub for the first time | First time pushing a new branch |
| `git pull` | Downloads and applies remote changes to your local branch | Before starting new work, or to stay in sync |
| `git fetch` | Downloads remote changes without applying them | When you want to check remote changes first |

> **Difference between pull and fetch:** `git pull` = fetch + merge. `git fetch` only downloads; it does not change your working files.

---

## Branching

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git branch` | Lists all local branches | Checking which branch you are on |
| `git branch <branch-name>` | Creates a new branch | Starting new work |
| `git switch <branch-name>` | Switches to an existing branch | Moving to a different branch |
| `git switch -c <branch-name>` | Creates and switches to a new branch | Shortcut for create + switch |
| `git checkout <branch-name>` | Same as `git switch` (older syntax) | Used in many existing guides |
| `git checkout -b <branch-name>` | Same as `git switch -c` (older syntax) | Used in many existing guides |
| `git branch -d <branch-name>` | Deletes a branch (safe — warns if unmerged) | After a branch is merged |
| `git branch -D <branch-name>` | Force-deletes a branch | ⚠️ Only if you are sure; cannot undo |
| `git branch -m old-name new-name` | Renames a branch | Fixing a branch name typo |
| `git push -u origin <branch-name>` | Publishes a local branch to GitHub | After creating a branch locally |

> **Modern vs older syntax:** `git switch` and `git switch -c` are the modern commands. `git checkout` is older but still widely used in companies. Both work.

---

## Undoing Changes

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git restore <file>` | Discards changes to a file (not staged) | Undoing edits you do not want |
| `git restore --staged <file>` | Unstages a file (keeps the changes) | When you staged the wrong file |
| `git revert <commit-hash>` | Creates a new commit that undoes a past commit | Safe way to undo a commit |
| `git reset --hard <commit-hash>` | ⚠️ Resets to a past commit and deletes all changes after it | Last resort — permanently deletes local changes |

> **Warning:** `git reset --hard` is destructive. It cannot be undone. Do not use it unless you are sure and have discussed with your team.

---

## Viewing Remote Information

| Command | What It Does | When to Use It |
|---------|-------------|----------------|
| `git remote -v` | Shows the remote name and URL | Verifying your remote is set correctly |
| `git branch -r` | Lists remote branches | Seeing what branches exist on GitHub |
| `git branch -a` | Lists all branches (local and remote) | Full branch overview |

---

## Quick Reference: The Most Common Flow

```bash
# 1. Get the latest from GitHub
git pull

# 2. Create a new branch for your work
git switch -c feature/my-feature

# 3. Make changes to your files
# (edit files in your editor)

# 4. Check what changed
git status

# 5. Stage your changes
git add .

# 6. Commit with a good message
git commit -m "Add my feature"

# 7. Push your branch to GitHub
git push -u origin feature/my-feature

# 8. Go to GitHub and open a Pull Request
```
