# Lab 08: Pull Requests

**Estimated Time:** 30 minutes  
**Prerequisites:** Labs 01–07 complete, branch pushed to GitHub  

---

## Objective

Create a pull request on GitHub, review it, and merge it into `main`.

## What You Will Learn

- What a pull request is and why it is used
- How to create a pull request
- How to add a description and assign a reviewer
- How to leave and respond to review comments
- How to approve and merge a pull request
- How to delete a branch after merging

---

## What Is a Pull Request?

A **pull request (PR)** is a proposal to merge changes from one branch into another. It is done through the GitHub website, not the terminal.

The workflow:
1. You push a feature branch
2. You open a pull request to merge it into `main`
3. A teammate reviews your changes
4. They approve (or request changes)
5. You merge
6. The branch is deleted

Pull requests are how professional teams review each other's code before it reaches production. It is one of the most important skills in this course.

---

## Step-by-Step Instructions

### Step 1: Make Sure Your Branch Is Pushed

Open your terminal. Make sure you are on `feature/add-contact-info` from Lab 07.

```bash
git status
git log --oneline
```

If the branch is not pushed yet:
```bash
git push -u origin feature/add-contact-info
```

### Step 2: Open a Pull Request on GitHub

1. Go to your repository on GitHub
2. You should see a yellow banner: **"feature/add-contact-info had recent pushes"** with a **Compare & pull request** button
3. Click **Compare & pull request**

If you do not see the banner, click the **Pull requests** tab → **New pull request** → select your branch.

[Instructor Screenshot Placeholder: GitHub banner showing "Compare & pull request" button]

### Step 3: Fill In the Pull Request Details

You will see a form with two text fields.

**Title:** Write a clear, descriptive title.  
Example: `Add contact information file`

**Description:** Explain what you changed and why. Use the template in [`templates/pull-request-template.md`](../templates/pull-request-template.md) as a guide. For this lab, write at least:

```
## Summary
Added a contact.txt file with my email address.

## What Changed
- New file: contact.txt

## Why This Change Is Needed
Adds contact information to the project.

## How I Tested It
Created the file, committed, and pushed. No errors.
```

### Step 4: Assign a Reviewer

On the right side of the PR form:
- Click **Reviewers** → search for your instructor's username (or a classmate's)
- Assign them as a reviewer

[Instructor Screenshot Placeholder: Pull request form with Reviewers section highlighted]

### Step 5: Create the Pull Request

Click **Create pull request**.

You are now on the PR page. You can share this URL with your reviewer.

---

## Part B: Review a Pull Request

If you are reviewing a classmate's PR (or practicing as your own reviewer):

### Step 6: Open the Pull Request

Click the **Files changed** tab to see all the changes.

Lines shown in green (with `+`) are additions. Lines in red (with `-`) are removals.

### Step 7: Leave a Comment

Click on a specific line to leave a comment about it. For example: `Looks good! Consider adding a phone number too.`

Click **Add single comment** or **Start a review** if you have multiple comments.

### Step 8: Approve the Pull Request

After reviewing all changes, click **Review changes** → select **Approve** → click **Submit review**.

[Instructor Screenshot Placeholder: GitHub PR review dialog showing Approve option]

---

## Part C: Merge the Pull Request

### Step 9: Merge

On the PR page (as the PR author or a person with merge permission):

1. Click **Merge pull request**
2. Click **Confirm merge**

The branch is now merged into `main`.

### Step 10: Delete the Branch

After merging, GitHub shows a **Delete branch** button. Click it to remove the remote branch.

In your terminal, also clean up locally:

```bash
git switch main
git pull
git branch -d feature/add-contact-info
```

---

## Part D: Verify the Merge

```bash
git log --oneline
```

You should see the merge commit at the top. Your `contact.txt` changes are now on `main`.

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| PR shows no changes | Make sure your branch has commits that `main` does not have |
| Merging into the wrong base branch | On the PR form, check the "base" branch carefully before creating |
| Forgetting to delete the branch | Use the GitHub "Delete branch" button after merging |
| Vague PR title | Rewrite: be specific about what changed |

---

## Checkpoint Questions

1. What is the difference between a branch and a pull request?
2. Where do pull requests happen — in the terminal or on GitHub?
3. Why should you delete a branch after it is merged?
4. What does a reviewer do in a pull request?

---

## Completion Checklist

- [ ] Branch pushed to GitHub
- [ ] Pull request created with a meaningful title and description
- [ ] Reviewer assigned
- [ ] PR reviewed (comments left)
- [ ] PR approved and merged
- [ ] Branch deleted on GitHub and locally
- [ ] `git log --oneline` on `main` shows the merged commits
