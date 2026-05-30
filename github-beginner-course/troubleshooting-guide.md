# Troubleshooting Guide: Common Git and GitHub Problems

Use this guide when something goes wrong. Find your error, read the explanation, and follow the fix.

---

## 1. `git: command not found`

**What it means:** Git is not installed on your system, or your terminal cannot find it.

**Why it happens:**
- Git was never installed
- On Windows, you are running Command Prompt instead of WSL/Ubuntu

**How to fix it:**
- Mac/Linux: Follow the installation steps in [setup-guide.md](setup-guide.md)
- Windows: Open Ubuntu from the Start menu (not Command Prompt or PowerShell), then install Git:
  ```bash
  sudo apt-get install git -y
  ```

---

## 2. `Permission denied (publickey)`

**What it means:** GitHub rejected your connection because it could not verify your identity.

**Why it happens:**
- Your SSH key has not been added to GitHub
- You are using a different key than the one registered in GitHub
- You generated a key but forgot to add the public key

**How to fix it:**

Step 1 — Check which key you have:
```bash
ls ~/.ssh/
```
You should see `id_ed25519` and `id_ed25519.pub` (or `id_rsa` and `id_rsa.pub`).

Step 2 — Display and copy your public key:
```bash
cat ~/.ssh/id_ed25519.pub
```

Step 3 — Add it to GitHub:
Go to GitHub → Settings → SSH and GPG keys → New SSH key → paste and save.

Step 4 — Test:
```bash
ssh -T git@github.com
```

---

## 3. Wrong GitHub Email Configured

**What it means:** Your commits will show a different email than your GitHub account, and some features may not work correctly.

**Why it happens:** You ran `git config` with the wrong email, or used a personal email when your GitHub account uses a work email.

**How to fix it:**
```bash
git config --global user.email "correct_email@example.com"
git config --global user.email   # verify it is correct now
```

> Existing commits cannot be changed easily. Going forward, new commits will use the corrected email.

---

## 4. Pushed to the Wrong Branch

**What it means:** You committed and pushed to `main` (or another branch) when you should have used a feature branch.

**Why it happens:** You forgot to create or switch to a feature branch before working.

**How to fix it (if you have not opened a PR yet):**

Option 1 — If your changes are small and the branch is not protected:
Talk to your instructor or team lead before doing anything.

Option 2 — Create the right branch now (moves your commits there):
```bash
git branch feature/my-fix    # create the correct branch at current state
git switch main               # go back to main
git reset --hard origin/main  # ⚠️ resets main to match remote (deletes local changes on main)
git switch feature/my-fix     # your work is safely on this branch
```

> **Warning:** `git reset --hard` deletes local changes. Make sure you have created the correct branch first.

---

## 5. `nothing to commit, working tree clean`

**What it means:** Git sees no changes to commit. Everything is already committed and in sync.

**Why it happens:**
- You already committed your changes
- You forgot to save your file before running `git status`
- You are looking in the wrong folder

**How to fix it:**
- Save your files and run `git status` again
- Check you are in the right project folder: `pwd` and `ls`
- If you already committed, move to your next step (push)

---

## 6. `Repository not found`

**What it means:** Git cannot find the repository at the URL you provided.

**Why it happens:**
- The URL is wrong (typo)
- You do not have access to the repository
- The repository has been deleted or renamed

**How to fix it:**
- Copy the URL directly from the GitHub repository page (green Code button)
- Make sure you are using the SSH URL format: `git@github.com:username/repo.git`
- Ask the repository owner to check your access

---

## 7. `Authentication failed`

**What it means:** GitHub rejected your login credentials.

**Why it happens:**
- You are using HTTPS with a password instead of an SSH key
- GitHub no longer accepts account passwords for HTTPS — it requires a Personal Access Token or SSH

**How to fix it:**
- Switch to SSH: Use the SSH clone URL (`git@github.com:...`) instead of HTTPS (`https://github.com/...`)
- To update an existing remote:
  ```bash
  git remote set-url origin git@github.com:username/repo.git
  ```

---

## 8. `remote origin already exists`

**What it means:** You tried to add a remote named `origin` but one already exists.

**Why it happens:** You already ran `git remote add origin` previously.

**How to fix it:**

Check what remote is set:
```bash
git remote -v
```

If it is wrong, update it:
```bash
git remote set-url origin git@github.com:username/repo.git
```

If you want to remove and re-add:
```bash
git remote remove origin
git remote add origin git@github.com:username/repo.git
```

---

## 9. `rejected — remote contains work that you do not have locally`

**What it means:** The remote repository has commits that your local copy does not have. Git refuses to push to avoid losing those changes.

**Why it happens:** Someone else pushed changes after you last pulled, or you have two computers with different states.

**How to fix it:**
```bash
git pull
# resolve any conflicts if prompted
git push
```

---

## 10. Merge Conflict

**What it means:** Two branches changed the same part of a file differently. Git cannot automatically decide which version is correct.

**Why it happens:** Two developers edited the same line of code, or changes were made to the same file in both the source and target branch.

**How to fix it:**

Step 1 — Git marks the conflict in the file:
```
<<<<<<< HEAD
Your version of the line
=======
The other branch's version
>>>>>>> feature/some-branch
```

Step 2 — Open the file and decide which version to keep (or combine them).

Step 3 — Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).

Step 4 — Stage the resolved file:
```bash
git add <filename>
```

Step 5 — Complete the merge:
```bash
git commit -m "Resolve merge conflict in filename"
```

---

## 11. Accidentally Committed to `main`

**What it means:** You made a commit directly on the `main` branch when you should have used a feature branch.

**Why it happens:** You forgot to create or switch to a feature branch.

**How to fix it (before pushing):**

Step 1 — Create the correct branch at the current point:
```bash
git branch feature/my-fix
```

Step 2 — Reset main back to match the remote:
```bash
git switch main
git reset --hard origin/main
```

Step 3 — Switch to your feature branch and continue:
```bash
git switch feature/my-fix
```

> If you already pushed to `main` and main is protected, ask your instructor or team lead immediately.

---

## 12. Branch Not Visible on GitHub

**What it means:** You created a branch locally but it does not appear on GitHub.

**Why it happens:** You have not pushed the branch yet.

**How to fix it:**
```bash
git push -u origin your-branch-name
```

After this, the branch will appear on GitHub.

---

## 13. Pull Request Shows No Changes

**What it means:** Your pull request appears empty — no files changed.

**Why it happens:**
- You opened the PR against the wrong base branch
- Your branch does not have any commits that differ from the target branch
- You forgot to push your latest commit

**How to fix it:**
- Check the base branch in the PR is correct (should be `main` or `dev`, not your own branch)
- Run `git log --oneline` locally and confirm your commits are there
- Run `git push` to make sure your latest commit is on GitHub
- Close the current PR and open a new one with the correct base branch

---

*If your problem is not listed here, ask your instructor or search the exact error message on Stack Overflow or the GitHub documentation.*
