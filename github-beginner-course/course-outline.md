# Course Outline: Git and GitHub for Beginners

---

## Module 1: Introduction to Git and GitHub (30 min)

**Learning Goals:** Understand what Git is, what GitHub is, and why they exist.

- The problem Git solves: tracking changes, avoiding "final_v2_REAL_FINAL.docx"
- What version control means in plain language
- Git vs GitHub — the key difference
- Key vocabulary: repository, commit, branch, pull request
- Real-world DevOps context: why every team uses Git

**Lab:** None — concepts only  
**Quiz:** Quiz 01 (after this module)

---

## Module 2: Setup (45 min)

**Learning Goals:** Install Git, configure identity, understand the terminal.

- Create a GitHub account
- Install Git (Windows WSL, Mac, Linux)
- Open and use the terminal
- Configure username and email
- Verify installation

**Lab:** Lab 01 — Create GitHub Account  
**Lab:** Lab 02 — Install and Configure Git

---

## Module 3: Authentication with SSH (30 min)

**Learning Goals:** Generate SSH keys and connect GitHub securely.

- What SSH keys are and why GitHub uses them
- Generate an SSH key (ed25519)
- Add the public key to GitHub
- Test the SSH connection
- Common SSH mistakes

**Lab:** Lab 03 — SSH Key Setup

---

## Module 4: Repositories (30 min)

**Learning Goals:** Create, clone, and understand repositories.

- What a repository is
- Local vs remote repositories
- Create a repository on GitHub
- Clone a repository locally
- Understand `origin` and remote references

**Lab:** Lab 04 — Create and Clone Repository

---

## Module 5: Git's Three Main Areas (45 min)

**Learning Goals:** Understand working directory, staging, and commits.

- The three areas: working directory, staging area, local repository
- How files move through Git
- `git status`, `git add`, `git commit`
- Reading commit history: `git log`, `git log --oneline`
- Viewing differences: `git diff`

**Lab:** Lab 05 — Working Directory, Staging, and Commits

---

## Module 6: Pushing and Pulling (30 min)

**Learning Goals:** Sync local and remote repositories.

- What the remote repository is
- `git push` and `git pull`
- `git fetch` — what makes it different from pull
- `git remote -v`
- How to stay in sync with your team

**Lab:** Lab 06 — Push to GitHub

---

## Module 7: Branching (45 min)

**Learning Goals:** Create and manage branches confidently.

- What branches are and why teams use them
- Create, switch, rename, and delete branches
- Modern commands: `git switch`, `git switch -c`
- Push a branch to GitHub
- Understanding HEAD and branch pointers

**Lab:** Lab 07 — Branches

---

## Module 8: Pull Requests (45 min)

**Learning Goals:** Create, review, and merge pull requests on GitHub.

- What a pull request is and why teams use them
- Create a pull request on GitHub
- Add a description and assign a reviewer
- Leave and respond to review comments
- Approve and merge a pull request
- Delete a branch after merging

**Lab:** Lab 08 — Pull Requests  
**Quiz:** Quiz 03 (after this module)

---

## Module 9: GitHub Organizations and Collaboration (30 min)

**Learning Goals:** Understand how teams are organized in GitHub.

- What a GitHub organization is
- Organization members vs repository collaborators vs outside collaborators
- Teams and access levels
- Inviting members and collaborators
- Principle of least privilege

**Lab:** Lab 10 (conceptual, partial demo)

---

## Module 10: Branch Protection and Team Rules (30 min)

**Learning Goals:** Configure branch protection rules on GitHub.

- Why `main` should be protected
- Require a pull request before merging
- Require approvals and dismiss stale approvals
- Require status checks
- Prevent direct push to `main`

**Lab:** Lab 09 — Branch Protection

---

## Module 11: Beginner Team Workflow (30 min)

**Learning Goals:** Follow a real DevOps release workflow.

- Feature branch workflow
- DEV → UAT → MAIN release flow
- Hotfix branch workflow
- Where CI/CD pipelines fit in
- Diagram walkthrough

**Lab:** Lab 10 — Team Collaboration Workflow

---

## Module 12: VS Code and GitHub (30 min)

**Learning Goals:** Use VS Code for everyday Git tasks.

- Clone a repository in VS Code
- Create and switch branches
- Stage, commit, and push from the UI
- Pull and sync changes
- When to use the terminal vs VS Code UI

---

## Module 13: Final Project (60 min)

**Learning Goals:** Apply all skills end-to-end.

- Clone → branch → edit → commit → push → pull request → merge
- Write a professional commit message and PR description
- Request and respond to a review
- Grade: 100 points

**Lab:** Final Project

---

## Suggested Teaching Schedules

### 1-Day Intensive (8 hours)

| Time | Content |
|------|---------|
| 9:00–9:30 | Module 1: Introduction |
| 9:30–10:15 | Module 2: Setup (Labs 01, 02) |
| 10:15–10:30 | Break |
| 10:30–11:00 | Module 3: SSH (Lab 03) |
| 11:00–11:30 | Module 4: Repositories (Lab 04) |
| 11:30–12:15 | Module 5: Three Areas (Lab 05) |
| 12:15–1:00 | Lunch |
| 1:00–1:30 | Module 6: Push/Pull (Lab 06) |
| 1:30–2:15 | Module 7: Branches (Lab 07) |
| 2:15–3:00 | Module 8: Pull Requests (Lab 08) |
| 3:00–3:15 | Break |
| 3:15–3:45 | Module 9–10: Orgs and Protection |
| 3:45–4:15 | Module 11–12: Workflow and VS Code |
| 4:15–5:00 | Module 13: Final Project |

---

### 2-Day Workshop

**Day 1:** Modules 1–7 (Labs 01–07) + Quizzes 01 and 02  
**Day 2:** Modules 8–13 (Labs 08–10, Final) + Quiz 03 and Final Review

---

### 4-Week Part-Time Course

| Week | Modules | Labs | Assessment |
|------|---------|------|-----------|
| Week 1 | 1, 2, 3 | Labs 01, 02, 03 | Quiz 01 |
| Week 2 | 4, 5, 6 | Labs 04, 05, 06 | Quiz 02 |
| Week 3 | 7, 8 | Labs 07, 08 | Quiz 03 |
| Week 4 | 9, 10, 11, 12, 13 | Labs 09, 10, Final | Final Project |
