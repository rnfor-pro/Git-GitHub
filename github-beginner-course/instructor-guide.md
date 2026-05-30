# Instructor Guide: Git and GitHub for Beginners

This guide is written for you to teach from directly. Use it during live class, Zoom sessions, or workshops. Each module includes what to say, what to demo, where students get stuck, and how to explain tricky concepts simply.

---

## Before Class Starts

**Pre-class checklist:**
- [ ] Share the course repository link with students
- [ ] Ask students to complete [setup-guide.md](setup-guide.md) before Day 1 if possible
- [ ] Have your own terminal and GitHub account ready to demo
- [ ] Create a class GitHub organization (optional but recommended)
- [ ] Prepare a class repository for the final project

**Technology setup:**
- Screen share your terminal in a large font (minimum 18pt)
- Keep a browser open to GitHub alongside your terminal
- Have the command cheatsheet open for reference

---

## Module 1: Introduction to Git and GitHub (30 min)

### What to Say

_"Before we touch any commands, I want to make sure we understand what problem Git solves and why every developer, DevOps engineer, and IT professional uses it daily."_

_"Has anyone ever saved a file called 'final_REAL_v2.docx'? That right there is the problem. Git solves this."_

**Walk through the analogy:**
_"Git is like a time machine for your project. Every time you commit, you are taking a photograph of your entire project at that moment. You can always go back to any photo."_

**Git vs GitHub distinction — say this clearly:**
_"Git is the tool on your computer. GitHub is the website. Git works without internet. GitHub needs internet. They are not the same thing."_

### Questions to Ask Students

- "What do you think would happen if two people edited the same file at the same time without Git?"
- "Has anyone used a 'Save History' feature in Google Docs? Git does something similar but much more powerful."
- "What do you think 'version control' means?"

### Key Analogies for This Module

- Git = time machine
- Commit = checkpoint / photograph
- Repository = a project folder with memory
- Branch = a safe side road
- Pull request = asking your team to review before merging

### Where Students Get Confused

- Mixing up Git and GitHub — be firm and repeat: "Git = your computer, GitHub = the website"
- Thinking they need to understand everything before starting — reassure them that it clicks after the labs

---

## Module 2: Setup (45 min)

### What to Demo

1. Open your terminal
2. Run `git --version` — explain the output
3. Run `git config --global user.name "Your Name"`
4. Run `git config --global user.email "your_email@example.com"`
5. Run `git config --global --list` — show students what it looks like

### What Students Should Do

Immediately after your demo, have every student run:
```bash
git --version
git config --global user.name "Their Name"
git config --global user.email "their_email@example.com"
git config --global --list
```

Do not move on until every student has confirmed their config.

### Where Students Get Stuck

- **Windows students opening the wrong terminal:** Make it very clear they must open Ubuntu (WSL), not Command Prompt or PowerShell.
- **Git not found after install:** Have them close and reopen the terminal, then try again.
- **Wrong email:** Ask them: "What email did you use for GitHub?" They should use the same one.

### Timing

- 10 min: Talk through setup concepts
- 30 min: Students work through Labs 01 and 02
- 5 min: Verify everyone is configured

---

## Module 3: SSH Keys (30 min)

### What to Say

_"GitHub used to let you type your username and password every time you pushed code. They stopped allowing that in 2021 for security reasons. Now you use SSH keys — and once it is set up, you never have to type a password again."_

_"Think of SSH keys like a padlock and key. You give GitHub the padlock — the public key. You keep the key — the private key — on your computer. When you connect, GitHub uses the padlock to verify you are who you say you are."_

**Critical rule to emphasize:**
_"Your private key — the file without .pub at the end — never leaves your computer. Never paste it anywhere. Never email it. If someone has your private key, they can pretend to be you."_

### What to Demo

1. Run `ssh-keygen -t ed25519 -C "your_email@example.com"`
2. Press Enter for all prompts (default location, no passphrase)
3. Run `cat ~/.ssh/id_ed25519.pub` — show the output
4. Open GitHub → Settings → SSH and GPG keys → New SSH key
5. Paste the public key — explain: "This is the padlock we are giving GitHub"
6. Click Add SSH key
7. Run `ssh -T git@github.com` — show the success message

### Where Students Get Stuck

- **Running ssh-keygen on Windows PowerShell:** They must be in WSL/Ubuntu
- **Copying the wrong file:** They sometimes try to copy `id_ed25519` (private) instead of `id_ed25519.pub` (public). Stress the `.pub` extension.
- **SSH -T fails:** Usually they pasted only part of the public key. Have them redo the copy step carefully.

---

## Module 4: Repositories (30 min)

### What to Say

_"A repository is just a folder that Git is watching. Everything inside that folder — every file, every subfolder — is tracked. Git remembers the full history of every change."_

_"There are two types. The local repository is the copy on your computer. The remote repository is the copy on GitHub. They stay in sync when you push and pull."_

### What to Demo

1. Create a new repository on GitHub (show the UI)
2. Copy the SSH clone URL
3. In your terminal: `git clone git@github.com:your-username/your-repo.git`
4. `cd` into the folder
5. `ls -la` — show the `.git` folder
6. Explain: "That `.git` folder is where Git stores all the history. Do not delete it."

### Key Point

_"When you clone, GitHub automatically becomes your 'origin' — the default remote. When you push, you push to origin. When you pull, you pull from origin."_

---

## Module 5: Three Areas (45 min)

### This Is the Most Important Module

Spend extra time here. Students who understand working directory → staging → commit understand Git.

### What to Say

_"Git does not automatically save every change you make. You have to tell it what to save and when. This is a good thing — it gives you control."_

Draw this on screen or a whiteboard:
```
Working Directory → Staging Area → Local Repo → Remote
     (edit)           (git add)    (git commit)  (git push)
```

**Staging area analogy:**
_"Think of the staging area like a shopping cart. You are walking through the store — that's your working directory. You put items in your cart — that's git add. When you go to checkout, that's git commit. The items are saved and paid for."_

### What to Demo

```bash
# Create a file
echo "Hello Git" > hello.txt

# Check status
git status           # shows hello.txt as untracked (red)

# Stage it
git add hello.txt

# Check status again
git status           # shows hello.txt as staged (green)

# Commit it
git commit -m "Add hello.txt with greeting"

# Check log
git log --oneline    # shows the commit
```

### Where Students Get Stuck

- Forgetting to `git add` before committing — "nothing to commit" error
- Using vague commit messages — address this with the commit message examples template
- Not understanding what staging is for — use the shopping cart analogy again

---

## Module 6: Push and Pull (30 min)

### What to Demo

```bash
git push
# If first push of a new branch:
git push -u origin branch-name

# Pull before starting new work
git pull
```

**Key point to stress:**
_"Always pull before you start working. This is how you make sure you have the latest code from your team. A common beginner mistake is forgetting to pull, making changes, and then getting confused when pushing fails."_

---

## Module 7: Branches (45 min)

### What to Say

_"Now we get to one of the most powerful features of Git. Branches."_

_"Imagine your project is a road. The main branch is the main road — it is stable, production-ready. When you want to add something new, you build a side road. You do your work there. When it is done and approved, you connect it back to the main road."_

### What to Demo

```bash
# See current branch
git branch

# Create and switch to a new branch
git switch -c feature/add-about-page

# Confirm you switched
git status   # or git branch

# Make a change
echo "About page content" > about.txt
git add .
git commit -m "Add about page placeholder"

# Push branch to GitHub
git push -u origin feature/add-about-page
```

### Explain Modern vs Old Syntax

_"You will see two styles of branch commands in the wild. Both work:"_

| Modern (preferred) | Older (still common) |
|--------------------|---------------------|
| `git switch branch-name` | `git checkout branch-name` |
| `git switch -c new-branch` | `git checkout -b new-branch` |

_"I will teach you both because you will definitely see `git checkout` in documentation and Stack Overflow answers."_

---

## Module 8: Pull Requests (45 min)

### What to Say

_"Everything we have done so far has been terminal commands. Pull requests happen in the browser on GitHub. This is where team collaboration really happens."_

_"A pull request is you saying to your team: 'I finished this feature. Here are my changes. Can someone please review them before we add them to the main project?'"_

### What to Demo

1. Push a feature branch (from previous demo)
2. Go to the GitHub repository page
3. Show the "Compare & pull request" banner
4. Click it, show the diff
5. Write a meaningful title and description
6. Assign yourself or a student as reviewer
7. Click Create pull request
8. Show how to leave a comment
9. Show how to approve and merge

### Discussion Question

Ask students: _"Why do you think code review is important? What kinds of mistakes might a reviewer catch?"_

---

## Module 9: Organizations (30 min)

### What to Say

_"Up to now we have been working with personal repositories — `github.com/yourname/project`. In the real world, companies use organizations — `github.com/companyname/project`."_

### Demo or Show Screenshots

- Create an organization or show an existing one
- Show how teams are structured within an org
- Show how to invite someone to an org
- Explain the difference between org member, repo collaborator, and outside collaborator

**Key principle to teach:**
_"Least privilege. Give people only the access they need. Not everyone needs admin access. Not everyone needs write access to every repo."_

---

## Module 10: Branch Protection (30 min)

### What to Say

_"Now that you know what branches and pull requests are, let's talk about enforcing good habits for your whole team."_

_"Without branch protection, a developer could push directly to main, break production, and nobody would know until users start complaining. Branch protection rules prevent this."_

### What to Demo (GitHub UI)

1. Go to Repository → Settings → Branches
2. Click "Add branch protection rule" (or "Add ruleset" in newer GitHub)
3. Set branch name pattern: `main`
4. Enable: Require a pull request before merging
5. Enable: Require approvals (set to 1)
6. Enable: Dismiss stale approvals
7. Enable: Require status checks to pass
8. Show: the result — now no one can push directly to main

[Instructor Screenshot Placeholder: Branch protection rules settings]

---

## Module 11: DEV/UAT/MAIN Workflow (30 min)

### What to Say

_"This is how many real companies structure their releases. You will see this in job descriptions and on day one of your DevOps role."_

Refer to the [`diagrams/dev-uat-main-release-flow.md`](diagrams/dev-uat-main-release-flow.md) diagram during this module.

**Walk through the flow:**
1. Developer creates a feature branch from DEV
2. Work is completed, PR is opened to DEV
3. After testing in DEV, a PR is opened to UAT
4. QA tests in UAT
5. After UAT sign-off, a PR is opened to MAIN
6. Code goes to production

**Then cover hotfixes:**
_"What happens when production has a critical bug? You cannot wait for the normal flow. You create a hotfix branch from MAIN, fix the bug fast, merge it to MAIN, and then sync the fix back to UAT and DEV."_

---

## Grading Rubric for Final Project

| Criteria | Points |
|----------|--------|
| Correct branch name (`feature/firstname-lastname-profile`) | 10 |
| README.md updated with name and intro | 15 |
| New file added inside `dir1/` folder | 15 |
| Meaningful commit message (not "update" or "changes") | 15 |
| Branch pushed to GitHub successfully | 15 |
| Pull request created with description | 20 |
| Professional communication in PR comments | 10 |
| **Total** | **100** |

---

## Suggested Homework

**After Module 5 (commits):**
Create a personal practice repository. Add 3 files with different content. Make 3 separate commits with meaningful messages. Push to GitHub.

**After Module 7 (branches):**
Create two feature branches. Make changes in each. Push both to GitHub. Do NOT merge yet.

**After Module 8 (pull requests):**
Open a pull request for one of your branches. Write a proper description. Review a classmate's PR if possible.

---

## Common Questions Students Ask

**"What is the difference between git pull and git fetch?"**  
_"Pull = fetch + merge. Fetch only downloads. Pull downloads and applies the changes to your branch immediately. In most daily work, you use pull."_

**"When should I commit?"**  
_"Commit when you finish a logical unit of work. Not after every line, not once a week. Think: 'If I had to explain this commit to a teammate, does the message make sense?'"_

**"Do I have to use the terminal? Can I just use VS Code?"**  
_"Yes, you can use VS Code for most tasks. But learn the terminal commands first. They are universal — they work on any machine, in any CI/CD pipeline, and in job interviews."_

**"What if I push to main by accident?"**  
_"Raise your hand. We will fix it together. It happens. The important thing is to stop and ask instead of making it worse."_
