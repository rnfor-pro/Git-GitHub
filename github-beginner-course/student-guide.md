# Student Guide: Git and GitHub for Beginners

Welcome. This guide is your companion throughout the course. Read it alongside the labs, and refer back to it whenever you need a clear explanation.

---

## Module 1: What Are Git and GitHub?

### The Problem Git Solves

You have probably seen folder structures like this:

```
project/
├── report.docx
├── report_v2.docx
├── report_FINAL.docx
├── report_FINAL_REAL.docx
└── report_FINAL_REAL_USE_THIS_ONE.docx
```

This is how people try to manage changes without a proper tool — and it is a nightmare. If you work with a team, it gets even worse.

**Git solves this problem** by tracking every change you make over time. You can always go back to any previous version. You can work on new features without breaking what already works. And your whole team can work together without overwriting each other's work.

> **Remember:** Git is like a time machine for your project.

### Git vs GitHub

These two words sound similar but they are different things:

| | Git | GitHub |
|--|-----|--------|
| **What it is** | A tool installed on your computer | A website |
| **What it does** | Tracks changes to files locally | Stores your code online and adds collaboration tools |
| **Needs internet?** | No | Yes |
| **Made by** | Linus Torvalds (2005) | Microsoft (acquired 2018) |

Think of it this way: **Git is the engine. GitHub is the garage where you park and share the car.**

---

## Module 2: Setup

See [setup-guide.md](setup-guide.md) for the full installation walkthrough.

### What You Are Setting Up

When you configure Git, you are telling it who you are:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Every commit you make will be signed with this name and email. Use the same email you signed up to GitHub with.

> **Checkpoint:** Run `git config --global --list`. You should see your name and email listed.

---

## Module 3: SSH Keys

### Why SSH?

GitHub needs to know it is really you when you push code. Instead of asking for a password every time, it uses SSH keys — a pair of files that prove your identity securely.

- **Private key:** Stays on your computer. Never share this.
- **Public key:** You give this to GitHub. It is safe to share.

Think of it like a padlock you ship to someone. They lock something with it. Only you have the key to open it.

> **Common mistake:** Never paste your private key anywhere. The private key file has no `.pub` at the end.

---

## Module 4: Repositories

### What Is a Repository?

A **repository** (or repo) is a folder that Git is tracking. It contains your project files and the entire history of every change ever made to them.

> Think of a repository as a project folder with a built-in memory.

### Local vs Remote

| | Local Repository | Remote Repository |
|--|-----------------|------------------|
| Where | Your computer | GitHub |
| Who can see it | Just you | Your team |
| How to sync | `git push` / `git pull` | — |

### Cloning a Repository

When you clone a repo, you download the entire project — all files and all history — to your computer.

```bash
git clone git@github.com:username/repo-name.git
```

After cloning, you have a full copy on your machine. The remote on GitHub is automatically linked as `origin`.

---

## Module 5: Git's Three Main Areas

This is one of the most important concepts in the whole course. Understanding these three areas will make everything else make sense.

```
Working Directory  →  Staging Area  →  Local Repository  →  Remote Repository
   (your files)        (git add)        (git commit)           (git push)
```

### 1. Working Directory

This is the folder where you edit your files normally. Git can see what you change here, but it does not track anything until you tell it to.

### 2. Staging Area

When you are ready to tell Git "remember this change," you add files to the staging area. Think of it like a shopping cart — you pick what you want before you check out.

```bash
git add filename.txt    # add one file
git add .               # add everything that changed
```

### 3. Local Repository

When you commit, Git takes a snapshot of everything in the staging area and saves it permanently in the local repository.

```bash
git commit -m "Add homepage layout"
```

> **Common mistake:** Forgetting to write a meaningful commit message. "update" or "changes" tells your team nothing. Write what you actually did.

### Checking Where You Are

```bash
git status
```

Run `git status` constantly. It shows you:
- What files have changed (red = not staged)
- What is staged and ready to commit (green)
- Whether you are ahead or behind the remote

> **Try it yourself:** Edit a file, run `git status`. Then run `git add .` and `git status` again. Notice the difference.

---

## Module 6: Pushing and Pulling

### git push

After committing locally, `git push` sends your commits to GitHub so your team can see them.

```bash
git push
```

If it is a brand-new branch you are pushing for the first time:

```bash
git push -u origin branch-name
```

### git pull

Before starting new work, always pull to get the latest changes from your teammates.

```bash
git pull
```

### git fetch vs git pull

| | `git fetch` | `git pull` |
|--|------------|-----------|
| What it does | Downloads changes from remote | Downloads AND applies changes |
| Changes your files? | No | Yes |
| When to use | When you want to check what changed first | When you want to stay up to date |

> **Real-world DevOps note:** Many teams require you to `git pull` before starting work every morning to avoid working on outdated code.

---

## Module 7: Branches

### What Is a Branch?

Imagine your project is a road. The `main` branch is the main road. When you want to add something new, you build a side road — a **branch** — where you can work safely without disrupting traffic.

When your work is done and tested, you merge the side road back into the main road.

### Why Teams Use Branches

- Everyone can work at the same time without breaking each other's work
- Experiments are isolated — if your feature does not work, just delete the branch
- `main` stays clean and stable

### Branch Commands

```bash
# See all branches
git branch

# Create a new branch
git branch feature/login-page

# Switch to it
git switch feature/login-page

# Create and switch in one step (recommended)
git switch -c feature/login-page

# Push your branch to GitHub for the first time
git push -u origin feature/login-page
```

> **Remember:** After creating a branch, make sure you are ON it before you start making changes. Run `git status` — it shows your current branch at the top.

> **Common mistake:** Working on `main` when you think you are on a feature branch. Always check with `git status` or `git branch` before editing files.

---

## Module 8: Pull Requests

### What Is a Pull Request?

A **pull request (PR)** is how you ask your team to review your changes before they are merged into the main branch. It is not a Git command — it happens on GitHub in the browser.

> Think of a PR as saying: "Hey team, I finished this feature. Can someone check it before we add it to the project?"

### Why PRs Matter

- Your teammates catch mistakes before they reach production
- You build a record of what changed and why
- It is a professional habit in every real DevOps and engineering team

### The Pull Request Workflow

1. Push your branch to GitHub
2. Go to the repository on GitHub
3. Click **Compare & pull request**
4. Write a description of what you changed and why
5. Assign a reviewer
6. Wait for feedback
7. Make any requested changes, push again
8. Get approval → merge → delete the branch

[Instructor Screenshot Placeholder: GitHub Pull Request creation page]

> **Checkpoint:** Can you explain what a pull request is to someone who has never used Git? Try explaining it in two sentences.

---

## Module 9: Organizations and Collaboration

### What Is a GitHub Organization?

A GitHub **organization** is a shared workspace for a team or company. Instead of a personal repository (`github.com/yourname/project`), an org looks like `github.com/companyname/project`.

Organizations let companies:
- Manage multiple repositories in one place
- Set team-level access permissions
- Control who can see or change what

### Types of Access

| Role | Access |
|------|--------|
| **Organization member** | Belongs to the org; access depends on their team |
| **Repository collaborator** | Has direct access to a specific repository |
| **Outside collaborator** | Not an org member, but has access to specific repos |

> **Real-world DevOps note:** The principle of least privilege: give people only the access they need to do their job, nothing more.

---

## Module 10: Branch Protection

### Why Protect `main`?

Without protection, anyone on your team could push directly to `main` and accidentally break production. Branch protection rules prevent this.

### Common Protection Rules

| Rule | What It Does |
|------|-------------|
| Require pull request before merging | No one can push directly to `main` |
| Require approvals | At least 1 (or more) people must approve the PR |
| Dismiss stale approvals | If new commits are pushed, old approvals are removed |
| Require status checks | Automated tests must pass before merging |
| Require branch to be up to date | Your branch must include the latest `main` changes before merging |

**How to apply these in GitHub:**  
Repository → Settings → Branches → Add branch protection rule (or Ruleset)

[Instructor Screenshot Placeholder: GitHub Branch Protection settings page]

---

## Module 11: Team Workflow — DEV, UAT, MAIN

### The Real-World Release Workflow

Many companies use a branching strategy that looks like this:

```
Feature Branch
      ↓
    DEV  (development — latest features, may be unstable)
      ↓
    UAT  (testing — ready for QA/stakeholders to test)
      ↓
   MAIN  (production — what customers see)
```

- **Feature branches** are where developers do their daily work
- **DEV** is merged into regularly and may have bugs — it is where everything comes together first
- **UAT** is more stable — used for testing before release
- **MAIN** is always production-ready

### Hotfix Workflow

If a bug is discovered in production, you cannot wait for the normal flow:

```
MAIN → Hotfix Branch → fix the bug → PR → merge back to MAIN
                                       → also merge back to UAT and DEV
```

> **Important:** After a hotfix, always sync the fix back to UAT and DEV, or those branches will be missing the fix and it will come back.

---

## Module 12: VS Code and GitHub

VS Code has built-in Git integration. You can stage, commit, push, and pull without using the terminal.

### Basic VS Code Git Actions

1. Open the **Source Control** panel (the branch icon in the left sidebar)
2. Changed files appear listed — click `+` to stage them
3. Type a commit message at the top and click the checkmark to commit
4. Use `...` menu → Push to push your commits
5. Use `...` menu → Pull to get the latest changes

> Use the terminal for complex tasks and VS Code UI for everyday stage/commit/push when you are comfortable.

---

## Quick Reference: Analogies

| Git Concept | Real-Life Analogy |
|-------------|-------------------|
| Repository | A project folder with memory |
| Commit | A photograph / checkpoint |
| Staging area | Shopping cart before checkout |
| Branch | A side road where you work safely |
| Pull request | Asking for a code review before merging |
| Remote repository | The shared online copy |
| Merge | Combining your side road back into the main road |
| Clone | Downloading a full copy to your computer |
| Git | A time machine for your project |
| GitHub | The garage where you park and share the car |
