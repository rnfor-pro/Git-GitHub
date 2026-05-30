# Quiz 02: Git Commands

**Covers:** Modules 4–6 (Repositories, Three Areas, Push/Pull)  
**Format:** Multiple choice, Fill in the blank, Match the command  
**Estimated Time:** 10 minutes

---

## Section A: Multiple Choice

**1. What does `git clone` do?**

a) Creates a new empty repository  
b) Downloads a remote repository to your computer  
c) Uploads your local repository to GitHub  
d) Copies a file within the repository  

---

**2. After editing a file, which command shows you what changed before you stage it?**

a) `git status`  
b) `git log`  
c) `git diff`  
d) `git show`  

---

**3. You edited `README.md` and want to stage ONLY that file. Which command is correct?**

a) `git add .`  
b) `git add --all`  
c) `git add README.md`  
d) `git commit README.md`  

---

**4. What does `git status` show?**

a) Your full commit history  
b) The differences between commits  
c) Which files have changed, are staged, or are untracked  
d) A list of remote repositories  

---

**5. What is the purpose of the staging area?**

a) A place to permanently save your changes  
b) A temporary holding area where you choose what to include in the next commit  
c) The remote copy of your repository  
d) A backup location on GitHub  

---

**6. Which command sends your local commits to GitHub?**

a) `git pull`  
b) `git fetch`  
c) `git upload`  
d) `git push`  

---

**7. What is the difference between `git pull` and `git fetch`?**

a) They are the same command  
b) `git pull` downloads and applies changes; `git fetch` only downloads them  
c) `git fetch` downloads and applies changes; `git pull` only downloads them  
d) `git pull` is used for branches; `git fetch` is used for files  

---

**8. What does `git remote -v` show?**

a) Your commit history  
b) A list of all files in the repo  
c) The remote repository names and URLs  
d) Branches in the remote repository  

---

## Section B: Fill in the Blank

Complete each command:

**9.** To stage all changed files: `git ___ .`

**10.** To commit staged files with a message: `git ___ -m "Your message"`

**11.** To view compact one-line commit history: `git log ___`

**12.** To see the remote URL: `git remote ___`

**13.** To download changes from GitHub without merging: `git ___`

---

## Section C: Match the Command

Match each command on the left to its description on the right.

| Command | Description |
|---------|-------------|
| A. `git status` | 1. Creates a local copy of a remote repo |
| B. `git add .` | 2. Saves a snapshot of staged changes |
| C. `git commit -m "msg"` | 3. Shows files that are modified, staged, or untracked |
| D. `git clone <url>` | 4. Stages all changed files |
| E. `git log --oneline` | 5. Shows a compact list of past commits |

---

## Answer Key

**Multiple Choice:**

| # | Answer |
|---|--------|
| 1 | b |
| 2 | c |
| 3 | c |
| 4 | c |
| 5 | b |
| 6 | d |
| 7 | b |
| 8 | c |

**Fill in the Blank:**

| # | Answer |
|---|--------|
| 9 | `add` |
| 10 | `commit` |
| 11 | `--oneline` |
| 12 | `-v` |
| 13 | `fetch` |

**Match the Command:**

| A | B | C | D | E |
|---|---|---|---|---|
| 3 | 4 | 2 | 1 | 5 |
