# Instructor Guide: Git and GitHub for Beginners

This guide is written for you to teach from directly during live class or Zoom. Each module includes what to say, what to demo, suggested answers to every student question, and where students commonly get stuck — including Git Bash notes where relevant.

---

## Before Class Starts

**Pre-class checklist:**
- [ ] Share the course repository link with students
- [ ] Ask students to complete the setup guide before Day 1 if possible
- [ ] Have your own terminal and GitHub account ready to demo
- [ ] Create a class GitHub organization (optional but recommended)
- [ ] Prepare a class repository for the final project

**Technology setup:**
- Screen share your terminal in a large font (minimum 18pt)
- Keep a browser open to GitHub alongside your terminal

---

## Module 1: Introduction to Git and GitHub (30 min)

### What to Say

_"Before we touch any commands, I want to make sure we understand what problem Git solves and why every developer, DevOps engineer, and IT professional uses it daily."_

_"Has anyone ever saved a file called 'final_REAL_v2.docx'? That right there is the problem. Git solves this."_

_"Git is like a time machine for your project. Every time you commit, you are taking a photograph of your entire project at that moment. You can always go back to any photo."_

_"Git is the tool on your computer. GitHub is the website. Git works without internet. GitHub needs internet. They are not the same thing."_

---

### Questions to Ask Students — With Suggested Answers

**"What do you think would happen if two people edited the same file at the same time without Git?"**

> The second person to save would overwrite the first person's changes without either of them knowing. You would lose work with no way to recover it. In a team of 5 or 10, this becomes unmanageable very quickly. Git solves this by tracking who changed what and when, and it can merge different people's changes together automatically in most cases.

---

**"Has anyone used the Save History or Version History feature in Google Docs? How is Git similar — and different?"**

> Google Docs saves a version every time you make a change automatically. Git is similar in that it keeps a full history — but Git gives you control. You decide when to save a version (commit), you write a message explaining what changed, and you can work on separate "copies" (branches) without affecting the main document. Git also works for any type of file, not just documents — code, config files, infrastructure scripts, everything.

---

**"What do you think 'version control' means?"**

> Version control means tracking every change made to a set of files over time so that you can see what changed, who changed it, when, and why — and go back to any earlier version if needed. Think of it as a complete audit trail for your project.

---

### Where Students Get Confused

- Mixing up Git and GitHub — be firm and repeat: "Git = your computer, GitHub = the website"
- Thinking they need to understand everything before starting — reassure them it clicks after the labs

---

## Module 2: Setup (45 min)

### What to Demo

```bash
git --version
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
git config --global --list
```

Do not move on until every student has confirmed their config.

### Git Bash Note

Students on Windows may have **Git Bash** installed instead of WSL/Ubuntu. **Git Bash works fine** for everything in this course. It provides a Unix-like terminal and comes bundled with Git. If a student has Git Bash and it is working, there is no need to switch them to WSL mid-class.

The only difference students will notice:
- File paths use forward slashes (`/`) like Linux, not backslashes (`\`)
- SSH key generation works the same way
- All Git commands are identical

> If a student opens Command Prompt or PowerShell and Git is not found there, direct them to open Git Bash from the Start menu instead. That is all they need to do.

---

### Questions to Ask Students — With Suggested Answers

**"Why do you think Git needs your name and email? What would happen if you skipped this step?"**

> Git attaches your name and email to every commit you make. This is how your team knows who made which change. If you skip it, your commits will show up with a blank or wrong author. On GitHub, your commits may not be linked to your account, which means your contribution history will not be tracked. You should always use the same email you registered with on GitHub.

---

### Where Students Get Stuck

- **Windows students opening the wrong terminal:** If they do not have Git Bash, direct them to open Ubuntu (WSL). If they do have Git Bash, that is perfectly fine to use.
- **Git not found after install:** Have them close and reopen the terminal, then try again.
- **Wrong email:** Ask them: "What email did you use for GitHub?" They should use the same one.

---

## Module 3: SSH Keys (30 min)

### What to Say

_"GitHub stopped accepting plain passwords for pushing code in 2021. Now you use SSH keys — and once it is set up, you never have to type a password again."_

_"Think of it like a padlock and key. You give GitHub the padlock — the public key. You keep the key — the private key — on your computer. GitHub uses the padlock to confirm it is really you."_

_"The file without .pub at the end is your private key. It never leaves your computer. Never paste it anywhere. Never email it. If someone has it, they can act as you on GitHub."_

### What to Demo

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
# Press Enter for all prompts
cat ~/.ssh/id_ed25519.pub
# Copy the output, paste into GitHub → Settings → SSH keys → New SSH key
ssh -T git@github.com
```

---

### Git Bash SSH Note

**SSH key generation works in Git Bash exactly the same as in WSL or Mac Terminal.** The commands are identical and the keys are saved in the same `~/.ssh/` location. If a student is using Git Bash, they do not need WSL for this step.

> The only situation where Git Bash may behave slightly differently is if a student has an old version of Git for Windows. In that case, update Git for Windows from git-scm.com and the issue usually resolves.

---

### Questions to Ask Students — With Suggested Answers

**"Why does GitHub use SSH keys instead of just a username and password?"**

> Passwords can be guessed, phished, or reused across sites. SSH keys are cryptographic — mathematically extremely hard to break. They also cannot be phished the way a password form can. GitHub made this change in 2021 because too many accounts were being compromised through weak or reused passwords. SSH keys are the industry standard for secure, passwordless server authentication.

---

**"What would happen if someone got hold of your private key?"**

> They could connect to GitHub as you — push code, access private repositories, delete branches, everything your account can do. This is why the private key is treated like a password, or actually more carefully than a password, since it cannot be changed the same way. If your private key is ever exposed, you should delete the corresponding public key from GitHub immediately and generate a new key pair.

---

### Where Students Get Stuck

- **Copying the wrong file:** They sometimes copy `id_ed25519` (private) instead of `id_ed25519.pub` (public). Always stress: the file with `.pub` is the one that goes to GitHub.
- **`ssh -T` fails:** Usually they pasted only part of the public key. Have them go back to `cat ~/.ssh/id_ed25519.pub`, copy the full line carefully, and re-add it in GitHub settings.
- **"It says 'Are you sure you want to continue connecting?'":** This is normal on first connection. They type `yes` and press Enter. GitHub's fingerprint gets added to their `known_hosts` file and they will not see this again.

---

## Module 4: Repositories (30 min)

### What to Say

_"A repository is just a folder that Git is watching. Everything inside — every file, every subfolder — is tracked. Git remembers the full history of every change ever made."_

_"Local means on your computer. Remote means on GitHub. They stay in sync when you push and pull."_

_"When you clone, GitHub automatically becomes your 'origin' — the default remote. When you push, you push to origin. When you pull, you pull from origin."_

### What to Demo

```bash
git clone git@github.com:your-username/your-repo.git
cd your-repo
ls -la        # show the .git folder
git remote -v # show origin
```

---

### Questions to Ask Students — With Suggested Answers

**"What do you think is inside the `.git` folder? Why should you never delete it?"**

> The `.git` folder is where Git stores the entire history of the project — every commit, every branch, every author, every timestamp. The files in your working directory are just the current state. If you delete `.git`, you lose all that history. The folder stays hidden (starts with a dot) because you never need to touch it directly — Git manages it for you.

---

## Module 5: Three Areas (45 min)

### This Is the Most Important Module

Spend extra time here. Students who understand working directory → staging → commit understand Git at its core.

### What to Say

_"Git does not automatically save every change you make. You decide what gets saved and when. This is a good thing — it gives you full control."_

Draw this flow on screen:
```
Working Directory → Staging Area → Local Repo → Remote
     (edit)           (git add)    (git commit)  (git push)
```

_"Think of the staging area like a shopping cart. You walk through the store — that is your working directory, where you make changes. You put items in your cart — that is git add. When you check out, that is git commit. The purchase is saved permanently."_

### What to Demo

```bash
echo "Hello Git" > hello.txt
git status           # untracked, shown in red
git add hello.txt
git status           # staged, shown in green
git commit -m "Add hello.txt with greeting"
git log --oneline
```

---

### Questions to Ask Students — With Suggested Answers

**"Why do you think Git has a staging area at all? Why not just commit everything you changed?"**

> The staging area gives you fine-grained control. Imagine you changed five files while working — three are part of the feature you finished, one is an experiment you are not ready to share, and one is a typo fix unrelated to your feature. The staging area lets you commit those three files together with one clear message, commit the typo fix separately with its own message, and leave the experiment out entirely. Without staging, you would have to commit everything at once, which makes the history messy and harder to understand later.

---

**"What do you think happens to your changes if you forget to commit before switching branches?"**

> Git will try to carry your uncommitted changes with you when you switch. If those changes conflict with the other branch, Git will warn you and may refuse to switch. If there is no conflict, the changes follow you to the new branch — which can be confusing because you might commit them there by mistake. The safe habit is: always commit or stash your changes before switching branches.

---

### Where Students Get Stuck

- Forgetting `git add` before committing — they see "nothing to commit" and get confused. Remind them: edit → add → commit, every time.
- Writing vague commit messages like "update" — address this directly. Show the commit message examples.
- Not understanding why staging exists — use the shopping cart analogy a second time if needed.

---

## Module 6: Push and Pull (30 min)

### What to Demo

```bash
git push
git push -u origin branch-name   # first push of a new branch

git pull   # always pull before starting new work
```

_"Always pull before you start working. A common beginner mistake is forgetting to pull, making changes, and then getting a rejected push because the remote has newer commits."_

---

### Questions to Ask Students — With Suggested Answers

**"What do you think would happen if two people push changes to the same branch at the same time?"**

> The second person's push will be rejected by Git. Git will tell them the remote has changes they do not have locally. They need to pull first, which merges the remote changes into their local branch. If two people changed different parts of the code, Git merges automatically. If they changed the same lines, there will be a merge conflict that needs to be resolved manually. This is one of the main reasons teams use feature branches — it reduces the chance of two people working on the same code at the same time.

---

**"What is the difference between git pull and git fetch?"**

> `git fetch` downloads the latest changes from GitHub to your machine but does not apply them to your current branch. Your files stay as they are. `git pull` does both — it fetches and then automatically merges the remote changes into your current branch. In daily work, most developers use `git pull`. You would use `git fetch` when you want to inspect what changed before deciding to merge — for example, checking if a teammate's work will cause a conflict before you pull it in.

---

## Module 7: Branches (45 min)

### What to Say

_"Branches are one of the most powerful features of Git. Imagine your project is a road. Main is the main road — stable and reliable. When you want to add something new, you build a side road. You do your work there. When it is done and approved, you merge it back."_

### What to Demo

```bash
git branch
git switch -c feature/add-about-page
git status
echo "About page content" > about.txt
git add .
git commit -m "Add about page placeholder"
git push -u origin feature/add-about-page
```

Also show both syntaxes:

| Modern (preferred) | Older (still common) |
|--------------------|---------------------|
| `git switch branch-name` | `git checkout branch-name` |
| `git switch -c new-branch` | `git checkout -b new-branch` |

_"You will see `git checkout` constantly in documentation and on Stack Overflow. Both work. I will teach you both."_

---

### Questions to Ask Students — With Suggested Answers

**"Why do you think we use a naming convention like `feature/user-login` instead of just `login`?"**

> In a busy repository with ten developers, you might have dozens of branches. Clear naming tells you immediately what the branch is for, what type of change it is (feature, fix, hotfix), and roughly who owns it. A name like `login` tells you nothing. A name like `feature/user-login` tells you it is a new feature and it is about user login. Many teams also include a ticket number: `feature/JIRA-123-user-login`. This makes it easy to search, filter, and understand the state of a project at a glance.

---

**"What do you think happens to the `main` branch while you are working on your feature branch?"**

> Nothing — that is the point. Your feature branch is completely independent. If your teammates merge other changes into `main` while you are working, your branch is unaffected. You will eventually need to bring those changes into your branch before merging (via `git pull origin main` on your branch), but you do that on your own schedule. This isolation is exactly why branches exist.

---

### Where Students Get Stuck

- Working on `main` when they think they are on a feature branch. Emphasize: always check `git status` before editing files. The first line shows your current branch.
- Forgetting `-u` on the first push of a new branch. Explain: the `-u` links your local branch to the remote one so future pushes and pulls work without specifying the remote and branch name each time.

---

## Module 8: Pull Requests (45 min)

### What to Say

_"Everything so far has been terminal commands. Pull requests happen in the browser on GitHub. This is where team collaboration really happens."_

_"A pull request is you saying: 'I finished this feature. Here are my changes. Can someone please review them before we add them to the main project?'"_

### What to Demo

1. Push a feature branch
2. Go to GitHub, show the "Compare & pull request" banner
3. Write a title and description
4. Assign a reviewer
5. Create the PR, show the diff view
6. Leave a comment, show how to approve
7. Merge and delete the branch

---

### Questions to Ask Students — With Suggested Answers

**"Why do you think code review is important? What kinds of mistakes might a reviewer catch?"**

> A reviewer catches things the author cannot see because they are too close to their own work. Common catches include: bugs or edge cases the author did not think of, security issues like hardcoded passwords or exposed API keys, code that does not follow team conventions, changes that break something in a different part of the codebase, and simple things like typos in user-facing messages. Beyond bugs, code review is also how knowledge spreads through a team — junior developers learn from senior feedback, and everyone stays aware of what is changing in the codebase.

---

**"What do you think would happen if a team merged every pull request without review?"**

> You would lose the safety net. Bugs would reach production faster, security vulnerabilities would slip through, and code quality would decline over time because no one is checking that standards are being followed. In regulated industries — banking, healthcare, government — code review is often legally required as part of audit compliance. Even outside those industries, teams that skip code review typically spend more time fixing bugs in production than teams that review carefully.

---

### Where Students Get Stuck

- Opening a PR with no description — remind them that the reviewer has no context. A blank description forces the reviewer to read all the code from scratch just to understand the intent.
- PR shows no changes — usually they forgot to push their latest commit, or the base branch is wrong. Check `git log --oneline` and `git push` first.

---

## Module 9: Organizations (30 min)

### What to Say

_"Up to now we have worked with personal repositories. In the real world, companies use organizations — a shared workspace where multiple repositories, teams, and members are managed in one place."_

_"Least privilege: give people only the access they need to do their job, nothing more. A contractor writing frontend code should not have admin access to your infrastructure repo."_

---

### Questions to Ask Students — With Suggested Answers

**"Why would a company use an organization instead of just having everyone work from personal accounts?"**

> Personal accounts are not manageable at scale. If an employee leaves, you would have to go into every repository and remove them individually. With an organization, you remove them from the org once and they lose access to everything. Organizations also let you create teams — for example, a Frontend team with read access to all repos and write access to the UI repo only. You get centralized billing, audit logs, security policies, and the ability to enforce two-factor authentication across everyone. It is the difference between managing a single house and managing an entire building.

---

**"What is the difference between a repository collaborator and an outside collaborator?"**

> A repository collaborator is added directly to a specific repo and gets access to that repo based on their permission level. An outside collaborator is someone who is not a member of the GitHub organization — typically a contractor, a partner, or a temporary contributor — who has been given access to one or more specific repositories. Outside collaborators do not inherit any organization-level permissions or team access. The distinction matters for auditing: you want to know who has access to what, and at what level, especially in security-sensitive environments.

---

## Module 10: Branch Protection (30 min)

### What to Say

_"Now that you know what branches and pull requests are, let's talk about enforcing these habits for the whole team — automatically."_

_"Without protection, anyone can push directly to main, break production, and nobody knows until users start complaining. Branch protection rules make good workflow mandatory, not optional."_

### What to Demo (GitHub UI)

1. Repository → Settings → Branches
2. Add branch protection rule, pattern: `main`
3. Enable: Require a pull request before merging
4. Enable: Require approvals (set to 1)
5. Enable: Dismiss stale approvals
6. Enable: Require status checks to pass (explain what this is even if not configured)
7. Save and test — show that a direct push is now rejected

---

### Questions to Ask Students — With Suggested Answers

**"What do you think 'dismiss stale approvals' means and why would a team use it?"**

> It means that if a PR already has an approval and then the author pushes new commits, the approval is automatically removed. The reviewer has to look again and re-approve. Teams use this because an approval covers the code as it was at the time of review. If someone adds three new files after being approved, those files were never reviewed. Dismissing stale approvals prevents the workaround of getting approval on a small change and then sneaking in larger changes before merging.

---

**"Could a company choose to protect UAT and DEV branches the same way as main?"**

> Yes, and many do. You might require one approval to merge to DEV, two approvals to merge to UAT, and two approvals plus passing CI/CD checks to merge to MAIN. The strictness of protection usually increases as you move closer to production. Some teams protect MAIN very tightly but leave DEV more open so developers can move faster. The right balance depends on the team size, the risk tolerance, and whether there are compliance or regulatory requirements.

---

## Module 11: DEV/UAT/MAIN Workflow (30 min)

### What to Say

_"This is how many real companies structure their releases. You will see this workflow on day one of a DevOps job."_

Walk through the flow:
1. Developer creates a feature branch from DEV
2. PR opened to DEV — reviewed and merged
3. After integration testing in DEV, PR opened to UAT
4. QA team tests in UAT
5. After sign-off, PR opened to MAIN — goes to production

_"What happens when production has a critical bug and you cannot wait? You create a hotfix branch from MAIN, fix it fast, merge back to MAIN, and then sync the fix into UAT and DEV so it does not get overwritten next release."_

---

### Questions to Ask Students — With Suggested Answers

**"Why does a hotfix start from MAIN and not from DEV?"**

> Because you want to fix exactly what is running in production. DEV may have half-finished features, experimental changes, or code that is not tested yet. If you branch off DEV, your hotfix will include all of that unreviewed work when you merge it back to MAIN — potentially making the situation worse. Starting from MAIN means you get a clean, stable starting point. You fix the one thing that is broken and nothing else changes.

---

**"Why is it important to sync the hotfix back to DEV and UAT after merging to MAIN?"**

> If you do not, the bug still exists in DEV and UAT. The next time those branches are promoted to MAIN — which could be the very next release — the bug comes back. Syncing ensures that all branches stay consistent with what is in production. This is one of the most commonly forgotten steps in hotfix workflows.

---

## Grading Rubric for Final Project

| Criteria | Points |
|----------|--------|
| Correct branch name (`feature/firstname-lastname-profile`) | 10 |
| README.md updated with name and intro | 15 |
| New file added inside `dir1/` folder | 15 |
| Meaningful commit message (not "update" or "changes") | 15 |
| Branch pushed to GitHub successfully | 15 |
| Pull request created with proper description | 20 |
| Professional communication in PR comments | 10 |
| **Total** | **100** |

---

## Suggested Homework

**After Module 5:** Create a personal practice repository. Add 3 files. Make 3 separate commits with meaningful messages. Push to GitHub.

**After Module 7:** Create two feature branches. Make changes in each. Push both. Do not merge yet.

**After Module 8:** Open a pull request. Write a full description. Review a classmate's PR if possible.

---

## Common Questions Students Ask

**"Do I need WSL if I have Git Bash?"**
No. Git Bash is a fully valid environment for this course. All Git commands and SSH commands work the same way. Only direct students to WSL if they have neither Git Bash nor WSL and need to install something from scratch.

**"When should I commit?"**
Commit when you finish a logical unit of work. Not after every line, not once a week. A good test: if you had to describe this commit to a teammate in one sentence, can you? If yes, commit. If not, keep working.

**"Do I have to use the terminal? Can I just use VS Code?"**
You can use VS Code for most daily tasks. But learn the terminal commands first — they are universal, they work in CI/CD pipelines, on servers, in job interviews, and in any environment where VS Code is not available.

**"What if I push to main by accident?"**
Stop immediately and raise your hand. Do not try to fix it yourself by force-pushing or resetting — that can make it much worse, especially on a shared repo. We will fix it together.

**"What is a commit hash?"**
A commit hash is the unique ID Git assigns to every commit — a long string of letters and numbers like `a3f1b2c`. You can use the short version (first 7 characters) to reference a specific commit. It is how Git tracks history precisely. You will sometimes need it when reverting, cherry-picking, or resetting to a specific point.
