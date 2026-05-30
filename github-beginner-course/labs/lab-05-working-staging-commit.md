# Lab 05: Working Directory, Staging, and Commits

**Estimated Time:** 30 minutes  
**Prerequisites:** Lab 04 complete, inside your `git-practice` repo  

---

## Objective

Practice the core Git workflow: make changes, stage them, and commit them.

## What You Will Learn

- How Git tracks changes in the working directory
- How to use `git status`
- How to stage files with `git add`
- How to commit with `git commit`
- How to view commit history with `git log`
- How to see changes with `git diff`

---

## The Three Areas — Quick Reminder

```
Working Directory  →  Staging Area  →  Local Repository
   (you edit)         (git add)         (git commit)
```

---

## Step-by-Step Instructions

### Step 1: Make Sure You Are in the Right Place

```bash
pwd       # should show your git-practice directory
git status  # should show "nothing to commit, working tree clean"
```

### Step 2: Create a New File

```bash
echo "# My Notes" > notes.txt
```

This creates a file called `notes.txt` with the heading `# My Notes`.

### Step 3: Check Status

```bash
git status
```

**Expected output:**
```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        notes.txt

nothing added to commit but untracked files present
```

> **What does "Untracked" mean?** Git sees the file but is not tracking it yet. You have to tell Git you want to include it.

### Step 4: Stage the File

```bash
git add notes.txt
```

### Step 5: Check Status Again

```bash
git status
```

**Expected output:**
```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   notes.txt
```

The file is now in the staging area (green means ready to commit).

### Step 6: Commit the File

```bash
git commit -m "Add notes.txt with initial heading"
```

**Expected output:**
```
[main abc1234] Add notes.txt with initial heading
 1 file changed, 1 insertion(+)
 create mode 100644 notes.txt
```

### Step 7: Check Status After Commit

```bash
git status
```

**Expected:**
```
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Your commit exists locally. You have not pushed it to GitHub yet — that comes in Lab 06.

---

## Part B: Make More Changes

### Step 8: Edit the File

Open `notes.txt` and add a line. You can use any text editor, or in the terminal:

```bash
echo "Git is a version control system." >> notes.txt
```

### Step 9: View the Difference

Before staging, check what changed:

```bash
git diff
```

**Expected output:**
```diff
diff --git a/notes.txt b/notes.txt
index abc1234..def5678 100644
--- a/notes.txt
+++ b/notes.txt
@@ -1 +1,2 @@
 # My Notes
+Git is a version control system.
```

Lines starting with `+` are additions. Lines starting with `-` are removals.

### Step 10: Stage and Commit

```bash
git add notes.txt
git commit -m "Add Git definition to notes"
```

---

## Part C: View Commit History

### Step 11: See All Commits

```bash
git log
```

You will see your commits with their full details.

### Step 12: One-Line View

```bash
git log --oneline
```

**Expected output (example):**
```
d3f1a2b Add Git definition to notes
abc1234 Add notes.txt with initial heading
3e2f1d0 Initial commit
```

Each line shows the commit hash (short version) and the commit message.

---

## Practice: Stage Multiple Files

### Step 13: Create Two More Files

```bash
echo "Hello World" > file1.txt
echo "Learning Git" > file2.txt
```

### Step 14: Stage Everything at Once

```bash
git add .
git status
```

> `git add .` stages all changed and new files in the current directory.

### Step 15: Commit Both

```bash
git commit -m "Add file1 and file2 for practice"
```

---

## Common Mistakes

| Mistake | Symptom | Fix |
|---------|---------|-----|
| Forgetting `git add` | `nothing to commit` error | Always `git add` before `git commit` |
| Using vague commit messages | Commit history is useless later | Write what changed and why |
| Committing the wrong files | Unwanted files in repo | Use `git add <specific-file>` instead of `git add .` |

---

## Checkpoint Questions

1. What is the difference between a file being "untracked" and "staged"?
2. What does `git diff` show you?
3. Why would you use `git add notes.txt` instead of `git add .`?
4. What does `git log --oneline` show that `git log` does not?

---

## Completion Checklist

- [ ] Created a new file and ran `git status` before adding
- [ ] Staged the file with `git add` and ran `git status` again
- [ ] Made a commit with a descriptive message
- [ ] Made a second change, used `git diff`, then staged and committed
- [ ] Viewed commit history with `git log --oneline`
