# Lab 07: Branches

**Estimated Time:** 35 minutes  
**Prerequisites:** Labs 01–06 complete  

---

## Objective

Create, switch between, and manage branches. Push a branch to GitHub.

## What You Will Learn

- What branches are and why teams use them
- How to create a branch
- How to switch branches
- How to push a branch to GitHub
- How to rename and delete branches

---

## Why Branches?

Think of your project as a road. The `main` branch is the main highway — stable and reliable. When you want to add a new feature, you build a side road. You do your work there without touching the main road. When finished, you merge the side road back.

**Without branches:** Everyone edits the same files at the same time → chaos.  
**With branches:** Everyone works independently → merge when ready → organized.

---

## Step-by-Step Instructions

### Step 1: Check Your Current Branch

```bash
git branch
```

You should see:
```
* main
```

The `*` shows which branch you are currently on.

### Step 2: Create a New Branch

```bash
git branch feature/add-contact-info
```

This creates the branch but does NOT switch to it. Check:

```bash
git branch
```

```
  feature/add-contact-info
* main
```

You are still on `main`.

### Step 3: Switch to the New Branch

```bash
git switch feature/add-contact-info
```

**Expected:**
```
Switched to branch 'feature/add-contact-info'
```

Check again:
```bash
git branch
```
```
* feature/add-contact-info
  main
```

Now the `*` is on your new branch.

> **Shortcut:** You can create and switch in one command:
> ```bash
> git switch -c feature/add-contact-info
> ```
> Or in older syntax:
> ```bash
> git checkout -b feature/add-contact-info
> ```

### Step 4: Make Changes on the Branch

```bash
echo "Contact: student@example.com" > contact.txt
git add contact.txt
git commit -m "Add contact information file"
```

### Step 5: Check Your Status

```bash
git status
git log --oneline
```

Notice that `main` does not have this commit yet. The change only exists on your feature branch.

### Step 6: Verify main Is Unaffected

```bash
git switch main
cat contact.txt
```

You should get an error like `cat: contact.txt: No such file or directory` — because `contact.txt` was only added on the feature branch, not on `main`.

Switch back:
```bash
git switch feature/add-contact-info
```

---

## Part B: Push Your Branch to GitHub

### Step 7: Push the Branch

```bash
git push -u origin feature/add-contact-info
```

The `-u` flag sets `origin feature/add-contact-info` as the default tracking branch. After this, you can just run `git push` on future pushes.

**Expected output:**
```
Enumerating objects: 4, done.
...
To git@github.com:your-username/git-practice.git
 * [new branch]      feature/add-contact-info -> feature/add-contact-info
Branch 'feature/add-contact-info' set up to track remote branch 'feature/add-contact-info' from 'origin'.
```

### Step 8: Verify on GitHub

Go to your repository on GitHub. You should see a banner saying your branch was recently pushed. You can also click the **branches** dropdown to see your branch listed.

[Instructor Screenshot Placeholder: GitHub repository showing branch switcher with the new branch]

---

## Part C: Rename and Delete Branches

### Step 9: Rename a Branch

If you are on the branch you want to rename:
```bash
git branch -m new-name
```

To rename a branch you are not currently on:
```bash
git branch -m old-name new-name
```

### Step 10: Delete a Branch (After It Is Merged)

Safe delete — warns you if the branch has not been merged:
```bash
git branch -d feature/add-contact-info
```

Force delete — use carefully:
```bash
git branch -D feature/add-contact-info
```

> Do not delete your branch yet — you will need it for Lab 08.

---

## Understanding Branch Naming Conventions

Good branch names are descriptive and consistent. Common patterns:

| Type | Pattern | Example |
|------|---------|---------|
| New feature | `feature/short-description` | `feature/user-login` |
| Bug fix | `fix/short-description` | `fix/broken-header` |
| Hotfix | `hotfix/issue` | `hotfix/payment-crash` |
| Student profile | `feature/firstname-lastname-profile` | `feature/jane-smith-profile` |

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Editing files while on the wrong branch | Always check `git status` — it shows your current branch |
| Forgetting to switch after creating a branch | Use `git switch -c` to create and switch at once |
| Trying to push a branch without `-u` the first time | Use `git push -u origin branch-name` for new branches |
| Deleting a branch that is not merged | Use `-d` (safe), not `-D` (force), unless you are sure |

---

## Checkpoint Questions

1. What is the difference between `git branch feature/test` and `git switch -c feature/test`?
2. How do you see which branch you are currently on?
3. Why did `contact.txt` not exist when you switched back to `main`?
4. What does `-u` do in `git push -u origin branch-name`?

---

## Completion Checklist

- [ ] Created a new feature branch
- [ ] Switched to the branch
- [ ] Made a commit on the feature branch
- [ ] Verified that `main` does not have the change
- [ ] Pushed the branch to GitHub
- [ ] Branch appears in the GitHub UI
