# Glossary: Git and GitHub Terms

Every term you need to know, explained simply.

---

**Branch**  
A separate line of development inside a repository. Think of it like a copy of the road where you can safely build and test a new feature without breaking the main road. When your work is ready, you merge it back.

**Branch Protection**  
Rules you apply to important branches (like `main`) to prevent accidents. For example: require a pull request before merging, require at least one approval, and block direct pushes.

**CI/CD**  
Continuous Integration / Continuous Deployment. Automated processes that test and deploy your code when changes are merged. GitHub Actions is a common CI/CD tool that integrates directly with GitHub.

**Clone**  
Copying a remote repository from GitHub down to your local computer. `git clone` creates a full local copy, including all history.

**Collaborator**  
A person who has been given direct access to a specific repository. Collaborators can push code and manage the repo depending on their permission level.

**Commit**  
A saved snapshot of your changes. Every commit is a checkpoint in your project's history. You can always go back to any commit.

**Commit Hash**  
A unique identifier (a long string of letters and numbers) automatically assigned to every commit. You can use the short version (first 7 characters) to reference a specific commit.

**Commit Message**  
A short description you write when making a commit. A good commit message explains what changed and why. Example: `Add login validation to signup form`.

**Conflict**  
A situation where two people changed the same part of the same file in different ways, and Git cannot automatically decide which version to keep. You have to resolve it manually.

**Fetch**  
Downloading changes from the remote repository without automatically applying them to your local branch. Use `git fetch` when you want to see what changed remotely before merging.

**Feature Branch**  
A branch created specifically for developing a new feature. Named clearly, like `feature/user-login`. Merged into `dev` or `main` via a pull request when complete.

**.gitignore**  
A file that tells Git which files or folders to ignore. For example, you can tell Git to ignore `node_modules/`, `.env` files, and other files that should not be committed.

**Git**  
A free, open-source version control tool that runs on your computer. It tracks every change made to your project files over time. Think of it as a time machine for your code.

**GitHub**  
A website that hosts Git repositories in the cloud. It adds collaboration features like pull requests, issues, actions, and organizations. GitHub is where your team shares code.

**Merge**  
Combining the changes from one branch into another. Usually happens after a pull request is approved. Git tries to merge automatically but may need your help if there are conflicts.

**Main Branch**  
The primary branch of a repository, typically named `main` (or `master` in older repos). This is the production-ready code. It is usually protected to prevent direct pushes.

**Organization**  
A GitHub account type used by companies and teams. Organizations can have multiple repositories, teams, and members with different access levels. Similar to a company workspace.

**Origin**  
The default name Git gives to the remote repository you cloned from or linked to. When you push, you are usually pushing to `origin`.

**Outside Collaborator**  
A person who is not a member of a GitHub organization but has been given access to one or more specific repositories within that organization.

**Pull**  
Downloading and applying remote changes to your local branch in one step. `git pull` = fetch + merge.

**Pull Request (PR)**  
A way to propose merging your changes from one branch into another on GitHub. Team members review the changes, leave comments, and approve before the merge happens. The professional way to contribute code.

**Push**  
Uploading your local commits to the remote repository on GitHub. Makes your changes visible to your team.

**README.md**  
A Markdown file typically placed at the root of a repository. GitHub displays it on the repository's main page. It describes the project, how to set it up, and how to use it.

**Remote Repository**  
The version of your repository hosted online (usually on GitHub). Multiple people can access and push to it. It is the shared "source of truth" for your project.

**Repository (Repo)**  
A folder that Git is tracking. It contains your project files plus the full history of every change ever made. Like a project folder with memory.

**Local Repository**  
The copy of the repository on your own computer. You make changes here before pushing them to the remote repository.

**Reviewer**  
A team member assigned to examine a pull request and give feedback. They can approve, request changes, or comment.

**SSH Key**  
A pair of cryptographic keys used to authenticate securely without a password. Your private key stays on your computer; your public key is added to GitHub. Like a key and lock pair.

**Staging Area**  
The middle step between editing files and committing. Files you `git add` go into the staging area. Think of it like a shopping cart — you pick what you want to commit before checking out.

**Status Check**  
An automated test or pipeline that must pass before a pull request can be merged. Configured with CI/CD tools. Prevents broken code from reaching `main`.

**Working Directory**  
The folder on your computer where you edit files. Git can see what changed here, but changes are not tracked until you stage and commit them.
