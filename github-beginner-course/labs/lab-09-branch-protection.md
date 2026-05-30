# Lab 09: Branch Protection

**Estimated Time:** 25 minutes  
**Prerequisites:** GitHub repository, instructor or organization admin access  

---

## Objective

Apply branch protection rules to the `main` branch so that no one can push directly to it.

## What You Will Learn

- Why `main` should be protected
- How to apply branch protection rules in GitHub
- What rules are most important for beginner teams
- How branch protection affects the PR workflow

---

## Why Protect `main`?

Without protection:
- A developer can push broken code directly to `main`
- Production could go down
- There is no peer review

With branch protection:
- Only pull requests can update `main`
- At least one person must review and approve
- Automated tests (if configured) must pass

In real DevOps teams, protected branches are standard. You will be expected to know how to configure and work within them.

---

## Step-by-Step Instructions

### Step 1: Go to Repository Settings

1. Open your repository on GitHub
2. Click the **Settings** tab
3. In the left sidebar, click **Branches**

[Instructor Screenshot Placeholder: GitHub repository Settings → Branches page]

### Step 2: Add a Branch Protection Rule

Click **Add branch protection rule** (some GitHub versions show "Add ruleset" — the options are similar).

### Step 3: Set the Branch Name Pattern

In the **Branch name pattern** field, type:
```
main
```

This will apply the rules to the `main` branch.

### Step 4: Configure Protection Rules

Enable the following settings by checking the boxes:

---

**✅ Require a pull request before merging**

This prevents anyone from pushing directly to `main`. All changes must come through a pull request.

Sub-options to also enable:

- **Require approvals:** Set to `1` (at least one person must approve before merging)
- **Dismiss stale pull request approvals when new commits are pushed:** If someone pushes new commits after an approval, the approval is removed and a new one is required.

---

**✅ Require status checks to pass before merging** *(optional for now)*

If you have CI/CD set up (like GitHub Actions running tests), checks must pass before a merge is allowed. You can skip this for now if no CI/CD is configured.

---

**✅ Require branches to be up to date before merging**

The feature branch must include all recent commits from `main` before it can be merged.

---

**✅ Do not allow bypassing the above settings**

Even administrators cannot bypass these rules. This is important for consistency.

---

### Step 5: Save the Rules

Scroll down and click **Create** (or **Save changes**).

[Instructor Screenshot Placeholder: Branch protection rule settings page with rules enabled]

---

## Part B: Test Your Protection Rules

### Step 6: Try to Push Directly to Main

On your local machine:

```bash
git switch main
echo "Direct push test" >> README.md
git add README.md
git commit -m "Test direct push to main"
git push
```

**Expected result:** GitHub rejects the push.

```
remote: error: GH006: Protected branch update failed for refs/heads/main.
remote: error: At least 1 approving review is required by reviewers with write access.
To git@github.com:your-username/git-practice.git
 ! [remote rejected] main -> main (protected branch hook declined)
error: failed to push some refs to 'git@github.com:your-username/git-practice.git'
```

The protection is working.

### Step 7: Undo the Local Commit

Since the push was rejected, reset your local state:

```bash
git reset --hard origin/main
```

> **Warning:** `git reset --hard` deletes any uncommitted local changes. Use it carefully. Here it is safe because we want to undo the test commit.

---

## Part C: The Correct Flow with Protection

Now that `main` is protected, the only way to update it is through a pull request:

1. Create a feature branch
2. Make changes and commit
3. Push the feature branch
4. Open a pull request
5. Get approval
6. Merge

This is the workflow you will use for the rest of the course and in your professional career.

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| "I cannot push to main anymore!" | That is correct — create a feature branch instead |
| PR cannot be merged — "approval required" | Ask your reviewer to approve in the PR |
| PR cannot be merged — "branch out of date" | Run `git pull origin main` on your feature branch, then push again |

---

## Checkpoint Questions

1. What happens when you try to push directly to a protected `main` branch?
2. What does "Dismiss stale approvals" mean?
3. Why would a company enable "Require status checks"?
4. Can administrators bypass branch protection if "Do not allow bypassing" is enabled?

---

## Completion Checklist

- [ ] Branch protection rule created for `main`
- [ ] "Require a pull request before merging" is enabled
- [ ] "Require approvals" is set to at least 1
- [ ] Tested: direct push to `main` was rejected
- [ ] Local state reset after failed push test
