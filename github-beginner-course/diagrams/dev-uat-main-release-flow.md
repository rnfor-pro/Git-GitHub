# Diagram: DEV → UAT → MAIN Release Flow

---

## The Three-Branch Strategy

```
┌─────────────────────────────────────────────────────────────────────┐
│                    FEATURE DEVELOPMENT                              │
│                                                                     │
│   feature/user-login          feature/dark-mode                    │
│         │                           │                               │
│         │                           │                               │
│   ┌─────▼───────────────────────────▼──────────────────────────┐   │
│   │                          DEV                               │   │
│   │                                                            │   │
│   │   Latest code from all developers                         │   │
│   │   May have bugs — integration testing happens here        │   │
│   │   Represents: "What developers are working on"            │   │
│   └─────────────────────────────┬──────────────────────────────┘   │
│                                 │ PR (after integration testing)    │
│   ┌─────────────────────────────▼──────────────────────────────┐   │
│   │                          UAT                               │   │
│   │                                                            │   │
│   │   Stable version for testing                               │   │
│   │   QA team and stakeholders verify here                    │   │
│   │   Represents: "What is being tested before release"       │   │
│   └─────────────────────────────┬──────────────────────────────┘   │
│                                 │ PR (after QA sign-off)            │
│   ┌─────────────────────────────▼──────────────────────────────┐   │
│   │                         MAIN                               │   │
│   │                                                            │   │
│   │   Production-ready code                                    │   │
│   │   Protected — only updated via approved PRs                │   │
│   │   Represents: "What is live in production"                │   │
│   └────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Normal Release Flow (Step by Step)

```
1. Developer creates feature branch from DEV
   git switch dev
   git pull
   git switch -c feature/my-feature

2. Developer works on feature and commits

3. Developer opens PR:  feature/my-feature → dev
   (Code reviewed, approved, merged)

4. After testing in DEV environment, team opens PR: dev → uat
   (QA team tests in UAT)

5. After QA sign-off, team opens PR: uat → main
   (Goes to production)
```

---

## Hotfix Flow (Urgent Production Bug)

```
┌─────────────────────────────────────────────────────────────────────┐
│                         HOTFIX WORKFLOW                             │
│                                                                     │
│   MAIN ────────────────────────────────────────────────►           │
│     │                                                               │
│     │  Bug discovered in production!                                │
│     │                                                               │
│     └── hotfix/fix-payment-crash                                    │
│               │                                                     │
│               │  (developer makes urgent fix)                       │
│               │                                                     │
│               └── PR reviewed and approved (emergency)              │
│               │                                                     │
│               ▼                                                     │
│   MAIN ◄── merge hotfix ──────────────────────────────────────►    │
│                │                                                    │
│                │  IMPORTANT: Sync fix back!                         │
│                │                                                    │
│                ├──► UAT  (merge main into uat)                     │
│                │                                                    │
│                └──► DEV  (merge main into dev)                     │
│                                                                     │
│   If you do NOT sync back:                                          │
│   ✗ The bug will return when UAT is next promoted to MAIN          │
│   ✗ DEV will diverge from production                               │
└─────────────────────────────────────────────────────────────────────┘
```

### Hotfix Commands

```bash
# Start from latest production code
git switch main
git pull

# Create hotfix branch
git switch -c hotfix/fix-payment-crash

# Make the fix, commit, push
git add .
git commit -m "Hotfix: resolve payment crash on empty cart"
git push -u origin hotfix/fix-payment-crash

# Open PR to main, get emergency approval, merge

# Sync back to UAT
git switch uat
git pull
git merge main
git push

# Sync back to DEV
git switch dev
git pull
git merge main
git push
```

---

## Environment Summary

| Branch | Environment | Audience | Stability |
|--------|------------|---------|-----------|
| `dev` | Development | Developers | Low — may have bugs |
| `uat` | User Acceptance Testing | QA / Stakeholders | Medium — should be functional |
| `main` | Production | End users / Customers | High — must be stable |

---

## Note: Many Workflows Exist

This DEV/UAT/MAIN workflow is one common pattern in enterprise and DevOps teams. You may also encounter:

- **GitHub Flow** — Simpler: just `main` + feature branches. Common in startups and open source.
- **GitFlow** — More formal structure with `develop`, `release`, `hotfix` branches.
- **Trunk-Based Development** — Very short-lived branches, many small merges to `main`.

Adapt to what your team uses. The principles (isolation, review, protected main) apply to all of them.
