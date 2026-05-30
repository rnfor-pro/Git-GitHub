# Lab 02: Install and Configure Git

**Estimated Time:** 20 minutes  
**Prerequisites:** Lab 01 complete, terminal access  

---

## Objective

Install Git on your computer and configure it with your name and email.

## What You Will Learn

- How to install Git on your operating system
- How to configure your identity in Git
- How to verify your setup

---

## Step-by-Step Instructions

### Step 1: Open Your Terminal

- **Windows:** Open the Ubuntu app (WSL). If it is not installed, follow [setup-guide.md](../setup-guide.md) first.
- **Mac:** Open Terminal (search with Spotlight: Cmd + Space, type "Terminal")
- **Linux:** Open your preferred terminal

### Step 2: Check If Git Is Already Installed

```bash
git --version
```

**If you see a version number** (e.g., `git version 2.43.0`) → Git is installed. Skip to Step 4.

**If you see an error** → Go to Step 3.

### Step 3: Install Git

**Windows (WSL/Ubuntu):**
```bash
sudo apt update
sudo apt-get install git -y
```

**Mac:** If prompted, install Xcode Command Line Tools. Or visit https://git-scm.com/download/mac

**Linux:**
```bash
sudo apt update
sudo apt-get install git -y
```

After installation, verify:
```bash
git --version
```

### Step 4: Configure Your Name

```bash
git config --global user.name "Your Full Name"
```

Replace `Your Full Name` with your actual name. Include the quotes.

### Step 5: Configure Your Email

```bash
git config --global user.email "your_email@example.com"
```

Use the same email address you used to create your GitHub account.

### Step 6: Verify Your Configuration

```bash
git config --global --list
```

Expected output:
```
user.name=Your Full Name
user.email=your_email@example.com
```

You can also check individual values:
```bash
git config --global user.name
git config --global user.email
```

---

## Understanding What You Did

The `--global` flag means this configuration applies to every Git project on your computer. You only need to run these config commands once per computer.

Every commit you make will include your name and email as the author. This is how your team knows who made which change.

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Forgetting the quotes around the name | Re-run the command with quotes |
| Using a different email than GitHub | Re-run with the correct email |
| Running commands in the wrong terminal (Windows CMD instead of WSL) | Open Ubuntu and run again |

---

## Checkpoint Questions

1. What command verifies your Git version?
2. Why does it matter that your Git email matches your GitHub account email?
3. What does `--global` mean in a Git config command?

---

## Completion Checklist

- [ ] `git --version` returns a version number
- [ ] `git config --global user.name` returns your name
- [ ] `git config --global user.email` returns your email
- [ ] Email matches your GitHub account
