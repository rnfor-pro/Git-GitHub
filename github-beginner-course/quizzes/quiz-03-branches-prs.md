# Quiz 03: Branches and Pull Requests

**Covers:** Modules 7–10 (Branches, PRs, Organizations, Branch Protection)  
**Estimated Time:** 12 minutes

---

## Section A: Multiple Choice

**1. What is a branch in Git?**

a) A copy of a file  
b) A separate line of development in the repository  
c) A type of commit  
d) A connection to a remote repository  

---

**2. Which command creates a new branch AND switches to it in one step?**

a) `git branch feature/new`  
b) `git switch feature/new`  
c) `git switch -c feature/new`  
d) `git create feature/new`  

---

**3. You are on the `main` branch and run `git switch -c feature/login`. Where are your existing commits?**

a) Only on `feature/login`  
b) Only on `main`  
c) On both branches  
d) They are deleted  

---

**4. What command pushes a new local branch to GitHub for the first time?**

a) `git push`  
b) `git push -u origin feature/login`  
c) `git send feature/login`  
d) `git upload origin feature/login`  

---

**5. What is a pull request?**

a) A Git command that downloads changes  
b) A request to merge changes from one branch into another, with team review  
c) A way to delete a branch  
d) A command that pushes to main  

---

**6. Where do pull requests happen?**

a) In the terminal  
b) In VS Code  
c) On the GitHub website  
d) In the `.git` folder  

---

**7. Why should you delete a branch after it is merged?**

a) To free up disk space on GitHub  
b) To keep the repository tidy and avoid confusion with old branches  
c) It is required by Git — otherwise it breaks  
d) So that the commit history is deleted  

---

**8. What does "Require approvals" in branch protection mean?**

a) The branch owner must approve every file before committing  
b) A set number of team members must approve the PR before it can be merged  
c) GitHub automatically approves PRs after 24 hours  
d) Only admins can merge  

---

**9. Which of the following is a good branch name?**

a) `mychanges`  
b) `fix`  
c) `feature/add-user-login`  
d) `NEW_CODE_12_FINAL`  

---

**10. In a DEV → UAT → MAIN workflow, where should a developer's feature branch be merged first?**

a) `main`  
b) `uat`  
c) `dev`  
d) `hotfix`  

---

## Section B: True or False

**11.** A pull request can be created before pushing the branch to GitHub. ___

**12.** Branch protection rules can be applied to prevent direct pushes to `main`. ___

**13.** An outside collaborator is a full member of the GitHub organization. ___

**14.** After a hotfix is merged to `main`, you should sync the fix back to `dev` and `uat`. ___

**15.** `git switch` and `git checkout` perform the same branch-switching action. ___

---

## Section C: Short Answer

**16.** Describe the typical pull request workflow in 4–5 steps.

**17.** A developer pushes a hotfix directly to `main` without a pull request. The branch is not protected. What are two risks of this approach?

**18.** What is the difference between an organization member and an outside collaborator?

---

## Answer Key

**Multiple Choice:**

| # | Answer |
|---|--------|
| 1 | b |
| 2 | c |
| 3 | c |
| 4 | b |
| 5 | b |
| 6 | c |
| 7 | b |
| 8 | b |
| 9 | c |
| 10 | c |

**True or False:**

| # | Answer |
|---|--------|
| 11 | False — branch must be pushed first |
| 12 | True |
| 13 | False — outside collaborators are not org members |
| 14 | True |
| 15 | True |

**Short Answer Notes:**

**Q16 expected steps:**
1. Create a feature branch
2. Make changes and commit
3. Push branch to GitHub
4. Open a pull request with description and assign reviewer
5. Get approval, merge, delete branch

**Q17 expected risks (any two):**
- No code review — bugs may go unnoticed
- No automated tests required to pass
- History shows a direct commit to main with no context
- If something breaks, no clear PR trail to trace the change

**Q18:** An organization member belongs to the GitHub organization and inherits access via teams. An outside collaborator is not an org member — they are added to specific repositories only and do not have access to other org resources.
