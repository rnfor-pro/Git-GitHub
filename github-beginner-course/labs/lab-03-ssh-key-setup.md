# Lab 03: SSH Key Setup

**Estimated Time:** 20 minutes  
**Prerequisites:** Labs 01 and 02 complete  

---

## Objective

Generate an SSH key pair and add the public key to GitHub so you can push and pull code securely.

## What You Will Learn

- What SSH keys are and how they work
- How to generate an SSH key
- How to add your public key to GitHub
- How to test your SSH connection

---

## Background: Why SSH?

GitHub stopped accepting plain passwords for pushing code in 2021. Instead, you use SSH — a secure authentication method.

You will generate two files:
- **Private key** (`id_ed25519`) — stays on your computer, never shared
- **Public key** (`id_ed25519.pub`) — you give this to GitHub

> ⚠️ **Never share your private key.** If someone gets it, they can access GitHub as you.

---

## Step-by-Step Instructions

### Step 1: Generate Your SSH Key

In your terminal, run:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Replace the email with the one you used for GitHub.

When prompted:
- **"Enter file in which to save the key"** → Press Enter (use the default location)
- **"Enter passphrase"** → Press Enter (no passphrase for now)
- **"Enter same passphrase again"** → Press Enter

**Expected output:**
```
Generating public/private ed25519 key pair.
Your identification has been saved in /home/yourname/.ssh/id_ed25519
Your public key has been saved in /home/yourname/.ssh/id_ed25519.pub
```

> **If ed25519 is not supported** (rare, older systems), use RSA instead:
> ```bash
> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```
> Then replace `id_ed25519` with `id_rsa` in the steps below.

### Step 2: View Your Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

You will see a long string starting with `ssh-ed25519`. **Copy the entire line** — from `ssh-ed25519` all the way to the end (which should be your email address).

> **Tip:** Click at the start of the line, hold Shift, click at the end, then copy. Or right-click and Copy All in some terminals.

### Step 3: Add the Public Key to GitHub

1. Go to [github.com](https://github.com) and sign in
2. Click your **profile picture** (top right) → **Settings**
3. In the left sidebar, click **SSH and GPG keys**
4. Click **New SSH key**
5. In the **Title** field, type something descriptive: `WSL Ubuntu` or `My Laptop`
6. In the **Key** field, paste the public key you copied
7. Click **Add SSH key**
8. Confirm your GitHub password if prompted

[Instructor Screenshot Placeholder: GitHub SSH keys page with "New SSH key" button highlighted]

### Step 4: Test the Connection

```bash
ssh -T git@github.com
```

If this is your first time connecting to GitHub via SSH, you may see:

```
The authenticity of host 'github.com' can't be established.
Are you sure you want to continue connecting (yes/no)?
```

Type `yes` and press Enter.

**Expected success output:**
```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

If you see your username, you are connected.

---

## Common Mistakes

| Problem | Cause | Fix |
|---------|-------|-----|
| `Permission denied (publickey)` | Public key not added to GitHub | Redo Steps 3–4 |
| Copied the wrong file | Copied `id_ed25519` (private) instead of `.pub` | Run `cat ~/.ssh/id_ed25519.pub` and copy again |
| Only copied part of the key | Multi-line paste | Try `cat` output and copy carefully from start to end |
| `No such file or directory` | Key generation failed | Re-run Step 1 |

---

## Checkpoint Questions

1. Which file did you add to GitHub — the private key or the public key?
2. What is the command to display your public key?
3. What does the success message look like after running `ssh -T git@github.com`?

---

## Completion Checklist

- [ ] SSH key pair generated (`id_ed25519` and `id_ed25519.pub` exist in `~/.ssh/`)
- [ ] Public key added to GitHub under SSH keys
- [ ] `ssh -T git@github.com` shows your username in the success message
