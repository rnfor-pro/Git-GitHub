# Setup Guide: Git, Terminal, and SSH

This guide walks you through everything you need to do before the first lab. Follow the section for your operating system.

---

## Part 1: Install Git

### Windows Users (Using WSL)

Windows does not come with Git or a Linux terminal built in. We use **WSL (Windows Subsystem for Linux)** with Ubuntu to get a proper terminal environment.

**Step 1: Install WSL**

Open PowerShell as Administrator and run:

```powershell
wsl --install
```

This installs WSL and Ubuntu automatically. If this does not work on your version of Windows, visit: https://learn.microsoft.com/en-us/windows/wsl/install

**Step 2: Restart your computer**

After installation completes, restart your machine.

**Step 3: Open Ubuntu**

Search for "Ubuntu" in the Start menu and open it. The first time it launches, it will ask you to create a Linux username and password. Choose something simple — this is separate from your Windows login.

**Step 4: Update your package list**

```bash
sudo apt update
```

You will be prompted for your Linux password.

**Step 5: Install Git**

```bash
sudo apt-get install git -y
```

**Step 6: Verify the installation**

```bash
git --version
```

You should see something like: `git version 2.43.0`

---

### Mac Users

**Step 1: Check if Git is already installed**

Open Terminal (search for it in Spotlight) and run:

```bash
git --version
```

If Git is installed, you will see a version number. You are done.

If Git is not installed, macOS will prompt you to install Xcode Command Line Tools. Click **Install** and follow the prompts.

Alternatively, install Git directly from: https://git-scm.com/download/mac

**Step 2: Verify**

```bash
git --version
```

---

### Linux Users (Ubuntu/Debian)

```bash
sudo apt update
sudo apt-get install git -y
git --version
```

---

## Part 2: Configure Git

Now tell Git who you are. Git attaches your name and email to every commit you make.

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

> Use the same email address you will use for your GitHub account.

**Verify your configuration:**

```bash
git config --global user.name
git config --global user.email
git config --global --list
```

---

## Part 3: Set Up SSH Keys

SSH keys let you connect to GitHub securely without typing a password every time.

Think of it like a key and lock:
- Your **private key** stays on your computer (never share it)
- Your **public key** goes to GitHub (safe to share)

### Step 1: Generate your SSH key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When prompted:
- **File location:** Press Enter to use the default (`~/.ssh/id_ed25519`)
- **Passphrase:** Press Enter for no passphrase (recommended for beginners)

> If you get an error saying ed25519 is not supported, use this RSA fallback instead:
> ```bash
> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```

### Step 2: Display your public key

```bash
cat ~/.ssh/id_ed25519.pub
```

(If you used RSA: `cat ~/.ssh/id_rsa.pub`)

You will see a long string starting with `ssh-ed25519` or `ssh-rsa`. **Copy the entire line.**

### Step 3: Add the public key to GitHub

1. Go to [github.com](https://github.com) and sign in
2. Click your profile picture → **Settings**
3. In the left menu, click **SSH and GPG keys**
4. Click **New SSH key**
5. Give it a title like: `My Laptop` or `WSL Ubuntu`
6. Paste your public key into the **Key** box
7. Click **Add SSH key**

[Instructor Screenshot Placeholder: GitHub SSH key settings page showing the "New SSH key" button]

### Step 4: Test the SSH connection

```bash
ssh -T git@github.com
```

Expected output:

```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

If you see this message, your SSH setup is working correctly.

---

## Important Rules About SSH Keys

| Rule | Why It Matters |
|------|---------------|
| Never share your private key | It is like your password — keep it secret |
| Your public key is safe to share | GitHub needs it to verify your identity |
| Your private key file has no `.pub` extension | `id_ed25519` = private, `id_ed25519.pub` = public |
| Generate a new key if you switch computers | Each device should have its own key |

---

## Common Setup Problems

**Problem:** `git: command not found`  
**Fix:** Git is not installed. Go back to Part 1.

**Problem:** `Permission denied (publickey)`  
**Fix:** Your SSH key is not added to GitHub, or the wrong key is being used. See [troubleshooting-guide.md](troubleshooting-guide.md).

**Problem:** `ssh-keygen: command not found`  
**Fix:** On Windows, make sure you are running this inside WSL/Ubuntu, not Command Prompt or PowerShell.

**Problem:** You see `WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED`  
**Fix:** Run `ssh-keygen -R github.com` and then try again.
