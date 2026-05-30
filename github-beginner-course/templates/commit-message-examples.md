# Commit Message Examples

Good commit messages are one of the most important professional habits in software development. They help your team understand what changed, why it changed, and when it changed — without needing to read all the code.

---

## The Rule of Thumb

> If you showed your commit message to a teammate, would they know what you did without opening the files?

---

## ❌ Bad Commit Messages

These tell your team nothing useful:

```
update
fix
changes
stuff
test
asdf
wip
final
FINAL
final final
ok
done
```

**Why they are bad:**
- No information about what changed
- No way to search or filter history later
- Forces reviewers to open the files just to understand the commit

---

## ✅ Good Commit Messages

These are specific, clear, and written in present tense:

```
Add student profile section to README
Fix typo in installation instructions
Add calculator script for Git practice lab
Update branch protection documentation
Remove unused import from login.js
Rename variable for clarity in checkout flow
Create dir1 folder with intro file for final project
Add SSH key setup steps to setup guide
Fix broken link in lab-03 instructions
Update glossary with CI/CD definition
```

**Why they are good:**
- Say what was done (action verb first)
- Say what was affected
- Written in present tense ("Add" not "Added")
- Short enough to read at a glance

---

## Commit Message Format

For most beginner work, one line is fine:

```
<action verb> <what was changed>
```

Examples:
```
Add login page layout
Fix calculation error in total cost function
Update README with setup instructions
Remove outdated deployment notes
Rename config file to match new convention
```

---

## For More Complex Changes (Optional Multi-Line Format)

For complex changes, a title + body format is useful:

```
Add user authentication with SSH key support

- Implemented login flow using SSH public key verification
- Added error handling for invalid key format
- Updated documentation with authentication steps

Fixes issue #42
```

The first line is the subject (50 characters or less). After a blank line, you can add more detail.

---

## Quick Reference: Action Verbs to Use

| Verb | When to Use |
|------|------------|
| `Add` | New file, feature, or content |
| `Fix` | Correcting a bug or error |
| `Update` | Modifying existing content |
| `Remove` | Deleting a file or feature |
| `Rename` | Changing a name |
| `Refactor` | Restructuring without changing behavior |
| `Create` | Setting up a new structure or folder |
| `Resolve` | Fixing a merge conflict |
| `Improve` | Making something better |
| `Document` | Adding or updating docs |

---

## For This Course

Every commit you make in labs and the final project should:

1. Start with a capital letter
2. Use an action verb
3. Describe what specifically changed
4. Be under 72 characters

**Final project example:**
```
Add Jane Smith profile to README and create intro file in dir1
```

Not:
```
update
```
