# Diagram: Branch and Pull Request Workflow

---

## Branch Lifecycle

```
main branch (protected)
│
│   ◄── only updated via Pull Request ──►
│
├── commit A ── commit B ── commit C
│                                  │
│                     ┌────────────┘
│                     │
│              [Developer creates feature branch]
│
│              feature/user-login
│              │
│              ├── commit D  (add login form)
│              ├── commit E  (add validation)
│              └── commit F  (add tests)
│
│              [Developer pushes branch to GitHub]
│              [Developer opens Pull Request]
│
│              ┌─────────────────────────────┐
│              │       PULL REQUEST          │
│              │  feature/user-login → main  │
│              │                             │
│              │  Reviewer: @instructor      │
│              │  Status: ✅ Approved        │
│              └─────────────────────────────┘
│
│              [PR is merged]
│
├── commit A ── commit B ── commit C ── merge commit (D+E+F)
│
│              [feature/user-login branch deleted]
```

---

## Pull Request Workflow (Step by Step)

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│  1. Start on main (or dev)                                      │
│     git switch main                                             │
│     git pull                                                    │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  2. Create a feature branch                                     │
│     git switch -c feature/my-feature                           │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  3. Make changes and commit                                     │
│     (edit files)                                                │
│     git add .                                                   │
│     git commit -m "Add my feature"                              │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  4. Push branch to GitHub                                       │
│     git push -u origin feature/my-feature                      │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  5. Open Pull Request on GitHub                                 │
│     → Choose base branch (main or dev)                         │
│     → Write description                                         │
│     → Assign reviewer                                           │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  6. Review Process                                              │
│     → Reviewer reads changes                                    │
│     → Leaves comments                                           │
│     → You respond or make fixes                                 │
│     → Reviewer approves ✅                                      │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  7. Merge the PR                                                │
│     → Click "Merge pull request"                                │
│     → Delete the branch on GitHub                              │
│                                                                 │
│         ↓                                                       │
│                                                                 │
│  8. Clean up locally                                            │
│     git switch main                                             │
│     git pull                                                    │
│     git branch -d feature/my-feature                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Branch Naming Convention

```
feature/   → new functionality       feature/user-login
fix/       → bug fixes               fix/broken-search
hotfix/    → urgent production fix   hotfix/payment-crash
student/   → student project work    feature/jane-smith-profile
```

---

## Why This Matters

Without branches:
```
main ← developer A pushes broken code → PRODUCTION IS DOWN
```

With branches and PRs:
```
main (protected) ← only approved PRs ← reviewed and tested code
```
