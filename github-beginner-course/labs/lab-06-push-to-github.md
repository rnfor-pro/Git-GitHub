# Lab 06: Push to GitHub

**Estimated Time:** 20 minutes  
**Prerequisites:** Labs 01–05 complete  

---

## Objective

Push your local commits to GitHub and verify your work is visible in the browser.

## What You Will Learn

- How to push commits to a remote repository
- How to pull changes from a remote repository
- The difference between `git push`, `git pull`, and `git fetch`
- How to check remote status

---

## Step-by-Step Instructions

### Step 1: Check Your Local Status

```bash
git status
git log --oneline
```

You should see the commits from Lab 05. They exist locally but are not on GitHub yet.

### Step 2: Push Your Commits

```bash
git push
```

**Expected output:**
```
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (8/8), 726 bytes | 726.00 KiB/s, done.
Total 8 (delta 1), reused 0 (delta 0), pack-reused 0
To git@github.com:your-username/git-practice.git
   3e2f1d0..d3f1a2b  main -> main
```

### Step 3: Verify on GitHub

1. Go to [github.com](https://github.com) and open your `git-practice` repository
2. You should see your new files (`notes.txt`, `file1.txt`, `file2.txt`)
3. Click on **Commits** to see the history — it should match your `git log`

[Instructor Screenshot Placeholder: GitHub repository page showing new files after push]

---

## Part B: Simulate Pulling Changes

In a team, your teammates push changes while you are working. You need to pull their changes to stay in sync.

### Step 4: Edit README on GitHub (Simulating a Teammate's Change)

1. On your GitHub repository page, click on `README.md`
2. Click the **pencil icon** (Edit this file)
3. Add a line of text at the bottom: `Updated from GitHub browser.`
4. Scroll down, write a commit message: `Update README from browser`
5. Click **Commit changes**

This simulates a teammate pushing a change.

### Step 5: Pull the Change Locally

In your terminal:

```bash
git pull
```

**Expected output:**
```
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
...
Updating d3f1a2b..f7a3c12
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

### Step 6: Verify the Change

```bash
cat README.md
```

You should see the text you added on GitHub, now on your local machine.

---

## Understanding git fetch vs git pull

| Command | What it does |
|---------|-------------|
| `git fetch` | Downloads changes from the remote but does NOT apply them to your branch |
| `git pull` | Downloads changes AND applies them to your current branch |
| `git pull` | Is equivalent to `git fetch` + `git merge` |

**When to use fetch:**  
When you want to see what changed on the remote before deciding whether to merge.

```bash
git fetch
git log --oneline origin/main   # see remote commits before applying
git pull                         # merge when ready
```

**In most daily work:** just use `git pull`.

---

## Check Remote Info

```bash
git remote -v
```

Shows the remote name and URL for fetch and push.

---

## Common Mistakes

| Problem | Fix |
|---------|-----|
| `rejected — remote contains work you do not have` | Run `git pull` first, then `git push` |
| Push goes to wrong branch | Check `git status` to confirm which branch you are on |
| Nothing appears on GitHub after push | Confirm you are pushing the right branch: `git push -u origin main` |

---

## Checkpoint Questions

1. After committing locally, what command sends your changes to GitHub?
2. What is the difference between `git pull` and `git fetch`?
3. What does `git remote -v` show?
4. Why is it important to `git pull` before starting new work?

---

## Completion Checklist

- [ ] `git push` ran successfully
- [ ] New files are visible in the GitHub repository
- [ ] Simulated a teammate change by editing README on GitHub
- [ ] `git pull` brought the change down to your local machine
- [ ] `git remote -v` confirms the correct remote URL
