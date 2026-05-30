# Quiz 01: Git and GitHub Basics

**Covers:** Modules 1–3 (Introduction, Setup, SSH)  
**Format:** Multiple choice, True/False, Short answer  
**Estimated Time:** 10 minutes

---

## Section A: Multiple Choice

**1. What is Git?**

a) A website where you store and share code  
b) A tool installed on your computer that tracks changes to files  
c) A programming language  
d) A type of terminal  

---

**2. What is GitHub?**

a) A version control tool that runs locally  
b) A Linux terminal  
c) A website that hosts Git repositories and adds collaboration features  
d) A replacement for Git  

---

**3. Which command checks your Git version?**

a) `git status`  
b) `git --version`  
c) `git check`  
d) `git info`  

---

**4. Which command sets your Git username?**

a) `git user.name "Your Name"`  
b) `git config --global user.name "Your Name"`  
c) `git set name "Your Name"`  
d) `git username "Your Name"`  

---

**5. What is a repository?**

a) A backup of your desktop  
b) A website where developers chat  
c) A folder that Git tracks, including the full history of every change  
d) A type of SSH key  

---

**6. Which file do you add to GitHub when setting up SSH?**

a) The private key (`id_ed25519`)  
b) The public key (`id_ed25519.pub`)  
c) Both files  
d) Neither — GitHub uses passwords  

---

**7. What does `git config --global` mean?**

a) The config applies only to the current project  
b) The config applies to all Git projects on your computer  
c) The config is shared with your team on GitHub  
d) The config resets after every session  

---

## Section B: True or False

**8.** Git and GitHub are the same thing. ___

**9.** Your private SSH key should be added to GitHub. ___

**10.** You only need to run `git config --global user.name` once per computer. ___

**11.** Git requires internet access to function. ___

**12.** `ssh -T git@github.com` is used to test your SSH connection. ___

---

## Section C: Short Answer

**13.** In your own words, explain the difference between Git and GitHub. (2–3 sentences)

**14.** What would happen if you configured your Git email differently from your GitHub account email?

**15.** Why does GitHub require SSH keys instead of passwords?

---

## Answer Key

| # | Answer |
|---|--------|
| 1 | b |
| 2 | c |
| 3 | b |
| 4 | b |
| 5 | c |
| 6 | b |
| 7 | b |
| 8 | False |
| 9 | False |
| 10 | True |
| 11 | False (Git works offline; GitHub needs internet) |
| 12 | True |

**Short answer notes:**  
- Q13: Key point — Git is a local tool; GitHub is a website. Git can work without GitHub.  
- Q14: Commits may not be linked to the GitHub account; some features (like contribution graphs) may not work correctly.  
- Q15: GitHub deprecated passwords in 2021 for security. SSH keys are more secure and do not require typing credentials on every push.
