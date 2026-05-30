# Lab 04: Create and Clone a Repository

**Estimated Time:** 25 minutes  
**Prerequisites:** Labs 01–03 complete (SSH configured)  

---

## Objective

Create a new repository on GitHub and clone it to your local computer.

## What You Will Learn

- How to create a repository on GitHub
- What cloning means
- How to clone a repository using SSH
- What `origin` is
- How the local and remote repos relate to each other

---

## Part A: Create a Repository on GitHub

### Step 1: Go to Your GitHub Profile

Log in to [github.com](https://github.com).

### Step 2: Create a New Repository

Click the **+** button in the top right corner → **New repository**.

Fill in the details:
- **Repository name:** `git-practice` (or any name you like)
- **Description:** `My first Git practice repository`
- **Visibility:** Public (or Private — your choice)
- **Initialize this repository with:** Check ✅ **Add a README file**
- Leave the other options as defaults

Click **Create repository**.

[Instructor Screenshot Placeholder: GitHub "Create a new repository" form]

### Step 3: Copy the SSH Clone URL

On your new repository page, click the green **Code** button.

Make sure **SSH** is selected (not HTTPS). You should see a URL that looks like:
```
git@github.com:your-username/git-practice.git
```

Click the copy icon to copy this URL.

---

## Part B: Clone the Repository

### Step 4: Open Your Terminal

Open your terminal (WSL/Ubuntu on Windows, Terminal on Mac/Linux).

Navigate to where you want to store your projects. A common location is your home folder:

```bash
cd ~
```

Or create a projects folder:
```bash
mkdir projects
cd projects
```

### Step 5: Clone the Repository

```bash
git clone git@github.com:your-username/git-practice.git
```

Replace `your-username` with your actual GitHub username.

**Expected output:**
```
Cloning into 'git-practice'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
Receiving objects: 100% (3/3), done.
```

### Step 6: Navigate Into the Repository

```bash
cd git-practice
```

### Step 7: Explore the Repository

```bash
ls -la
```

You will see:
- `README.md` — the file you initialized on GitHub
- `.git/` — the hidden folder where Git stores all history

```bash
git status
```

Expected output:
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### Step 8: Check the Remote

```bash
git remote -v
```

Expected output:
```
origin  git@github.com:your-username/git-practice.git (fetch)
origin  git@github.com:your-username/git-practice.git (push)
```

**What is `origin`?**  
`origin` is the default name Git gives to the remote repository you cloned from. When you push or pull without specifying a remote, Git uses `origin`.

---

## Understanding What Happened

When you cloned the repo:
1. Git downloaded the full repository history
2. Git created a local folder called `git-practice`
3. Git automatically linked your local repo to the GitHub remote as `origin`
4. Git checked out the `main` branch

---

## Common Mistakes

| Problem | Fix |
|---------|-----|
| Using the HTTPS URL instead of SSH | Click Code → SSH → copy that URL |
| Cloning into the wrong folder | Use `cd` to navigate first, then clone |
| `Permission denied` error | SSH key not set up — complete Lab 03 first |

---

## Checkpoint Questions

1. What does `git clone` do?
2. What is `origin`?
3. What is the `.git` folder for?
4. What command shows you what remote repository is connected to your local repo?

---

## Completion Checklist

- [ ] Repository created on GitHub with a README
- [ ] Repository cloned to your computer using the SSH URL
- [ ] `cd` into the repository folder
- [ ] `git status` shows "nothing to commit, working tree clean"
- [ ] `git remote -v` shows the `origin` remote URL
