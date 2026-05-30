# Lab 10: Team Collaboration Workflow

**Estimated Time:** 30 minutes  
**Prerequisites:** Labs 01–09 complete  

---

## Objective

Understand how GitHub Organizations work and practice a real team workflow using DEV, UAT, and MAIN branches.

## What You Will Learn

- What GitHub Organizations are
- The difference between organization members, repository collaborators, and outside collaborators
- How to invite members to an organization and repository
- The DEV → UAT → MAIN release workflow
- How hotfix branches work

---

## Part A: GitHub Organizations

### What Is a GitHub Organization?

A GitHub **organization** is a shared account for a team or company. Instead of:
```
github.com/yourname/project
```
An organization looks like:
```
github.com/companyname/project
```

Organizations allow companies to:
- Group multiple repositories in one workspace
- Create teams with different access levels
- Manage members centrally
- Apply security policies across all repos

### Types of Access

| Role | Who They Are | What They Can Access |
|------|-------------|---------------------|
| **Organization Owner** | Admin of the whole org | Everything |
| **Organization Member** | Belongs to the org | Depends on team settings |
| **Repository Collaborator** | Added directly to a specific repo | Only that repo |
| **Outside Collaborator** | Not in the org, added to specific repos | Only repos they are added to |

### Principle of Least Privilege

> Give people only the access they need to do their job — nothing more.

A contractor who writes frontend code should not have admin access to your production database repository. A junior developer should not be able to push directly to `main`.

---

## Part B: How to Invite Members

### Invite Someone to an Organization

1. Go to your organization on GitHub
2. Click **People** in the top navigation
3. Click **Invite member**
4. Enter the person's GitHub username or email
5. Select their role: **Member** or **Owner**
6. Click **Send invitation**

[Instructor Screenshot Placeholder: GitHub organization People tab with "Invite member" button]

### Invite Someone to a Repository

1. Go to the repository → **Settings** → **Collaborators**
2. Click **Add people**
3. Enter the person's GitHub username
4. Select a permission level:
   - **Read** — view and clone only
   - **Write** — push branches and open PRs
   - **Admin** — full repo control

[Instructor Screenshot Placeholder: Repository Collaborators settings page]

### Key Difference

- **Organization-level access:** Managed via Teams. Member gets access to all repos the team has access to.
- **Repository-level access:** Direct access to one specific repo. Used for outside contractors or partners.

---

## Part C: DEV → UAT → MAIN Release Workflow

### The Three-Branch Strategy

Most professional teams use at least three long-lived branches:

| Branch | Purpose | Who Merges Here |
|--------|---------|----------------|
| `dev` | Integration of all features. May have bugs. | Developers via PR |
| `uat` | Stable version for testing and QA sign-off | Dev lead via PR from dev |
| `main` | Production. Always stable. | Release manager via PR from uat |

Feature branches are created off `dev`. New features go to `dev` first.

### Step-by-Step Simulation

**Step 1: Create the three branches**

On your repository, create `dev` and `uat` branches on GitHub:

1. Go to your repository
2. Click the branch dropdown
3. Type `dev` and click "Create branch: dev"
4. Repeat for `uat`

Or in the terminal:
```bash
git switch main
git switch -c dev
git push -u origin dev

git switch main
git switch -c uat
git push -u origin uat
```

**Step 2: Create a feature branch off dev**

```bash
git switch dev
git switch -c feature/add-team-section
```

**Step 3: Make changes and commit**

```bash
echo "Team section: Alice, Bob, Carol" >> README.md
git add .
git commit -m "Add team section to README"
git push -u origin feature/add-team-section
```

**Step 4: Open PR from feature/add-team-section → dev**

On GitHub, create a pull request:
- Base: `dev`
- Compare: `feature/add-team-section`

Get it approved and merged.

**Step 5: Open PR from dev → uat**

After testing in `dev`, open a PR:
- Base: `uat`
- Compare: `dev`

This represents promoting the code to the testing environment.

**Step 6: Open PR from uat → main**

After QA sign-off, promote to production:
- Base: `main`
- Compare: `uat`

---

## Part D: Hotfix Workflow

### When Production Has a Critical Bug

You cannot wait for the normal `feature → dev → uat → main` flow. You need to fix it now.

**Hotfix process:**

```bash
# 1. Start from main (production code)
git switch main
git pull

# 2. Create a hotfix branch
git switch -c hotfix/fix-login-crash

# 3. Make the fix
echo "Fix: corrected login validation" >> README.md
git add .
git commit -m "Hotfix: resolve login crash on empty password"
git push -u origin hotfix/fix-login-crash
```

4. Open a PR from `hotfix/fix-login-crash` → `main`
5. Get emergency approval and merge
6. **Sync the fix back to UAT and DEV:**

```bash
# Merge main into uat
git switch uat
git merge main
git push

# Merge main into dev
git switch dev
git merge main
git push
```

> **Why sync back?** If you do not, the same bug will return when UAT or DEV is next promoted to MAIN.

---

## Part E: The Complete Picture

```
feature/my-feature
        ↓ PR
       dev  ←── integration, latest work
        ↓ PR
       uat  ←── testing, QA sign-off
        ↓ PR
      main  ←── production

HOTFIX PATH:
      main → hotfix/critical-fix → PR → main → sync to uat → sync to dev
```

---

## Note: This Is One Workflow

There are many Git branching strategies. This DEV/UAT/MAIN approach is common in enterprise DevOps environments. Other teams use:
- **GitHub Flow:** Just `main` + feature branches (simpler, common in startups)
- **GitFlow:** More complex with `develop`, `release`, `hotfix` branches
- **Trunk-based development:** Very frequent small merges to `main`

The important thing is to understand the principles, then adapt to what your team uses.

---

## Checkpoint Questions

1. What is the difference between an organization member and an outside collaborator?
2. Why does a hotfix start from `main` instead of `dev`?
3. Why is it important to sync a hotfix back to `dev` and `uat` after merging to `main`?
4. What does "least privilege" mean and why does it matter?

---

## Completion Checklist

- [ ] Understand the difference between organization member, repo collaborator, and outside collaborator
- [ ] Know how to invite someone to an organization or repository
- [ ] Created `dev` and `uat` branches
- [ ] Practiced the feature → dev → uat → main PR flow (at least partially)
- [ ] Understand the hotfix workflow and why you sync back
