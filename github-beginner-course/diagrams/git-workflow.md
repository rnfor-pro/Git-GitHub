# Diagram: Git File Workflow

This diagram shows how files move through Git's three areas on their way to the remote repository.

---

## The Four Stages

```
┌─────────────────────────────────────────────────────────────────────┐
│                         YOUR COMPUTER                               │
│                                                                     │
│  ┌──────────────┐    git add    ┌──────────────┐    git commit      │
│  │   Working    │ ────────────► │   Staging    │ ─────────────────► │
│  │  Directory   │               │    Area      │                    │
│  │              │               │              │                    │
│  │ (You edit    │               │ (Files ready │                    │
│  │  files here) │               │  to commit)  │                    │
│  └──────────────┘               └──────────────┘                    │
│                                                                     │
│         git restore <file>              git restore --staged <file> │
│         (undo edits)                    (unstage a file)            │
│                                                                     │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │                    Local Repository                          │   │
│  │                                                              │   │
│  │   commit 1 → commit 2 → commit 3 → commit 4                │   │
│  │   (Full history of all commits stored here)                 │   │
│  └──────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
                             │                    ▲
                             │  git push          │  git pull / git fetch
                             ▼                    │
┌─────────────────────────────────────────────────────────────────────┐
│                         GITHUB (Remote)                             │
│                                                                     │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │                   Remote Repository                          │   │
│  │                                                              │   │
│  │   commit 1 → commit 2 → commit 3 → commit 4                │   │
│  │   (Shared copy — your team sees this)                       │   │
│  └──────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
```

---

## The Commands at Each Step

| Step | Command | What It Does |
|------|---------|-------------|
| Edit → Stage | `git add <file>` or `git add .` | Moves changes to the staging area |
| Stage → Local Repo | `git commit -m "message"` | Saves a permanent snapshot |
| Local → Remote | `git push` | Uploads your commits to GitHub |
| Remote → Local | `git pull` | Downloads and applies remote changes |
| Remote → Local (no apply) | `git fetch` | Downloads remote changes without merging |

---

## How to Check Where You Are

```bash
git status   # Shows what is staged, unstaged, and untracked
git diff     # Shows changes not yet staged
git diff --staged  # Shows changes that are staged but not committed
git log --oneline  # Shows your commit history
```

---

## The Analogy

| Git Area | Real-Life Analogy |
|----------|------------------|
| Working Directory | Your desk — files are spread out, you are working on them |
| Staging Area | Shopping cart — you have decided what you want, not checked out yet |
| Local Repository | Receipt — your purchase is saved and recorded |
| Remote Repository | The store's inventory system — everyone can see it |
