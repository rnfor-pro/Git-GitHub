# Final Review Questions

**Covers:** All modules  
**Use for:** End-of-course review, final project prep, or self-assessment  
**Estimated Time:** 20 minutes

---

## Part 1: Core Concepts

1. Explain the difference between Git and GitHub in one sentence each.

2. What are the three areas in Git's workflow? Briefly describe what happens in each one.

3. What is a commit? What information does Git store with every commit?

4. What is the difference between `git pull` and `git fetch`?

5. Why do teams use branches? What problem do branches solve?

6. What is a pull request? Why is it important in a professional environment?

7. What is branch protection? Name three rules you can apply.

8. What is the difference between an organization member and an outside collaborator?

---

## Part 2: Commands

Write the correct command for each task:

9. Check the current state of your repository.

10. Stage all changed files.

11. Commit staged changes with the message "Add login feature".

12. Push a brand new branch called `feature/profile` to GitHub.

13. Create and immediately switch to a new branch called `feature/about`.

14. View commit history in compact, one-line format.

15. Download changes from GitHub without applying them.

16. Check which remote URLs are configured.

17. Delete a local branch called `feature/done` (safely).

---

## Part 3: Workflow Scenarios

**Scenario A:**  
You just cloned a repository and want to start working on a new feature called "dark mode." Describe every step from cloning to opening a pull request.

**Scenario B:**  
A critical bug is found in production (on `main`). Your team uses DEV → UAT → MAIN branches. Walk through the hotfix process step by step.

**Scenario C:**  
You committed and pushed 3 files but forgot to include a fourth file. The PR is not merged yet. How do you add the missing file to the same PR?

**Scenario D:**  
Your pull request was reviewed and the reviewer left two comments requesting changes. Walk through how you respond.

---

## Part 4: True or False

18. `git add .` stages all changed files in the current directory. ___

19. You should use `git reset --hard` frequently to undo mistakes. ___

20. Your private SSH key should be added to GitHub. ___

21. A feature branch should typically be created from `main` (or `dev`) and not from another feature branch. ___

22. `git log --oneline` shows less detail than `git log` but is easier to read. ___

23. Deleting a merged branch removes the commits from the repository history. ___

24. Branch protection rules can require at least one review approval before merging. ___

---

## Answer Key

### Part 1

1. Git is a local tool that tracks file changes. GitHub is a website that hosts Git repositories and adds collaboration features.

2. **Working directory** — where you edit files. **Staging area** — where you add files before committing (`git add`). **Local repository** — where commits are permanently saved (`git commit`).

3. A commit is a snapshot of your staged changes saved with a unique hash, an author name and email, a timestamp, and a commit message.

4. `git pull` downloads and applies changes. `git fetch` downloads only — it does not change your working files or branch.

5. Branches isolate new work so multiple developers can work without interfering with each other or breaking `main`.

6. A pull request is a proposal to merge one branch into another, with team review. It ensures code is reviewed and approved before it reaches production.

7. Any three of: Require PR before merging, require approvals, dismiss stale approvals, require status checks, require branch to be up to date, prevent bypassing rules.

8. Organization member belongs to the org and gets access through team settings. Outside collaborator is not an org member — they have direct access only to specific repositories.

---

### Part 2

| # | Answer |
|---|--------|
| 9 | `git status` |
| 10 | `git add .` |
| 11 | `git commit -m "Add login feature"` |
| 12 | `git push -u origin feature/profile` |
| 13 | `git switch -c feature/about` |
| 14 | `git log --oneline` |
| 15 | `git fetch` |
| 16 | `git remote -v` |
| 17 | `git branch -d feature/done` |

---

### Part 3 (Suggested Answers)

**Scenario A:**
1. `git clone git@github.com:org/repo.git`
2. `cd repo`
3. `git switch -c feature/dark-mode`
4. Make changes, save files
5. `git add .`
6. `git commit -m "Add dark mode toggle to settings"`
7. `git push -u origin feature/dark-mode`
8. Open GitHub → Compare & pull request → fill in description → assign reviewer → Create PR

**Scenario B:**
1. `git switch main && git pull`
2. `git switch -c hotfix/fix-crash`
3. Make the fix
4. `git add . && git commit -m "Hotfix: resolve login crash"`
5. `git push -u origin hotfix/fix-crash`
6. Open PR to `main`, get emergency approval, merge
7. Sync: merge `main` into `uat`, then `main` into `dev`

**Scenario C:**
1. Add the missing file: `git add missing-file.txt`
2. `git commit -m "Add missing file to complete login feature"`
3. `git push`
4. The PR on GitHub will automatically update with the new commit

**Scenario D:**
1. Read each comment carefully
2. If unclear, reply in the PR asking for clarification
3. Make the requested changes locally
4. `git add . && git commit -m "Address review: update error message wording"`
5. `git push`
6. Reply in the PR comments: "Updated — please take another look"
7. Wait for re-approval

---

### Part 4

| # | Answer |
|---|--------|
| 18 | True |
| 19 | False — use it only as a last resort; it permanently deletes changes |
| 20 | False — only the public key (`.pub`) goes to GitHub |
| 21 | True |
| 22 | True |
| 23 | False — deleting a branch does not delete the commits; history is preserved |
| 24 | True |
