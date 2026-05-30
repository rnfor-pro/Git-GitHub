# Final Project: Git and GitHub Individual Project

**Estimated Time:** 45–60 minutes  
**Prerequisites:** All labs (01–10) complete  

---

## Overview

You will apply everything you have learned in this course to complete an end-to-end Git and GitHub workflow. This project simulates what you would do on your first day contributing to a real team repository.

---

## Project Requirements

You must:

1. Clone the class repository (your instructor will share the URL)
2. Create a branch using the naming convention: `feature/firstname-lastname-profile`
3. Update the `README.md` file to add your name and a short introduction
4. Create a new file inside a folder called `dir1/`
5. Stage and commit your changes with a meaningful commit message
6. Push your branch to GitHub
7. Open a pull request with a proper title and description
8. Assign your instructor (or a classmate, as directed) as a reviewer
9. Respond to any review comments professionally
10. Merge after approval

---

## Step-by-Step Instructions

### Step 1: Clone the Class Repository

Your instructor will share a repository URL. Clone it:

```bash
cd ~
git clone git@github.com:instructor-username/class-repo.git
cd class-repo
```

### Step 2: Create Your Branch

Use this exact naming pattern (replace with your actual name):

```bash
git switch -c feature/jane-smith-profile
```

Verify you are on the correct branch:

```bash
git status
```

### Step 3: Update README.md

Open `README.md` in VS Code or any editor. Find the **Student Profiles** section (or add one at the bottom if it does not exist) and add:

```markdown
## Student Profiles

### Jane Smith
Hi, I am Jane. I am learning DevOps and cloud computing. 
I completed this GitHub course and I am excited to use Git in real projects.
```

Save the file.

### Step 4: Create a File in `dir1/`

```bash
mkdir -p dir1
```

Create a file inside it:

```bash
echo "This file was created by Jane Smith as part of the Git course final project." > dir1/jane-smith.txt
```

You can add any content you like, but include at least:
- Your name
- What you learned in this course (2–3 sentences)

### Step 5: Check Status

```bash
git status
```

You should see two changes:
- `README.md` modified
- `dir1/jane-smith.txt` new file

### Step 6: Stage Your Changes

```bash
git add README.md dir1/jane-smith.txt
```

Or stage everything:

```bash
git add .
```

Check status again:

```bash
git status
```

Both files should appear in green (staged).

### Step 7: Commit with a Meaningful Message

```bash
git commit -m "Add Jane Smith profile and intro file to dir1"
```

Your commit message should:
- State what was done (not "update" or "changes")
- Be written in present tense
- Be specific enough that a teammate understands it without opening the files

### Step 8: Push Your Branch

```bash
git push -u origin feature/jane-smith-profile
```

**Expected output:**
```
To git@github.com:instructor-username/class-repo.git
 * [new branch]      feature/jane-smith-profile -> feature/jane-smith-profile
```

### Step 9: Open a Pull Request

1. Go to the class repository on GitHub
2. Click the banner: **Compare & pull request** (or go to Pull requests → New pull request)
3. Set:
   - **Base:** `main`
   - **Compare:** `feature/jane-smith-profile`

**Title:** `Add Jane Smith profile and intro file`

**Description:** Fill in the PR template from [`templates/pull-request-template.md`](../templates/pull-request-template.md):

```
## Summary
Added my student profile to README.md and created an intro file in dir1/.

## What Changed
- Updated README.md with student profile section
- Added dir1/jane-smith.txt with intro content

## Why This Change Is Needed
Final project submission for the Git and GitHub beginner course.

## How I Tested It
- Ran git status to confirm both files were staged
- Ran git log --oneline to confirm the commit was created
- Verified the branch appeared on GitHub after push

## Checklist
- [x] Branch follows naming convention
- [x] README.md updated
- [x] File created in dir1/
- [x] Commit message is meaningful
- [x] Branch pushed successfully
```

### Step 10: Assign a Reviewer

On the right side of the PR, click **Reviewers** and select your instructor or assigned reviewer.

### Step 11: Respond to Review Comments

If your reviewer leaves comments:
- Read them carefully
- Ask for clarification in the PR if you do not understand
- Make the requested changes locally, commit, and push:
  ```bash
  git add .
  git commit -m "Address review: fix commit message typo"
  git push
  ```
- Reply to the comment on GitHub to let the reviewer know you made the change

### Step 12: Merge After Approval

Once your PR is approved:
1. Click **Merge pull request**
2. Click **Confirm merge**
3. Click **Delete branch**

Also clean up locally:
```bash
git switch main
git pull
git branch -d feature/jane-smith-profile
```

---

## Grading Rubric

| Criteria | Points | Notes |
|----------|--------|-------|
| Correct branch name (`feature/firstname-lastname-profile`) | 10 | Must follow the exact pattern |
| README.md updated with name and introduction | 15 | Must include both name and intro text |
| New file created inside `dir1/` folder | 15 | File must be inside `dir1/`, not the root |
| Meaningful commit message | 15 | Not "update", "fix", or "changes" |
| Branch pushed to GitHub successfully | 15 | Branch must appear on GitHub |
| Pull request created with proper description | 20 | Must include all required template sections |
| Professional communication in PR comments | 10 | Polite, clear, responds to review if needed |
| **Total** | **100** | |

---

## Submission Checklist

- [ ] Branch name follows `feature/firstname-lastname-profile` pattern
- [ ] `README.md` updated with your name and introduction (at least 2 sentences)
- [ ] File created in `dir1/` with meaningful content
- [ ] `git status` was clean before committing
- [ ] Commit message clearly describes the change
- [ ] Branch pushed — visible on GitHub
- [ ] Pull request opened with proper title and description
- [ ] Reviewer assigned
- [ ] PR approved and merged
- [ ] Branch deleted after merge

---

## Common Final Project Mistakes

| Mistake | Prevention |
|---------|-----------|
| File created in root instead of `dir1/` | Run `mkdir -p dir1` first, then create file inside it |
| Branch name not following convention | Copy and paste the pattern: `feature/firstname-lastname-profile` |
| Vague commit message | Ask: "Would my teammate understand this without opening the files?" |
| PR opened against wrong base branch | Double-check: base should be `main`, compare should be your branch |
| Forgot to assign reviewer | Check the right sidebar of the PR |
| PR merged before approval | Wait for the green "Approved" status before merging |
