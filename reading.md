# Git & GitHub Learning Notes

## Table of Contents
- [What is Git?](#what-is-git)
- [What is GitHub?](#what-is-github)
- [Understanding Remote](#understanding-remote)
- [Basic Workflow](#basic-workflow)
- [The Three Areas in Git](#the-three-areas-in-git)
- [Git Configuration](#git-configuration)
- [File Tracking Status](#file-tracking-status)
- [Common Commands](#common-commands)
- [Working with Remote Repositories](#working-with-remote-repositories)
- [Pulling Updates](#pulling-updates)

---

## What is Git?

**Git** is a Version Control System (VCS) - a tool to track changes in your code (history, deletions, additions, commits, etc.)

Think of Git as a **time machine for your project** - it records what changed, who changed it, and when.

---

## What is GitHub?

**GitHub** is a software application/website where developers store and manage their code using Git.

🔗 [https://www.github.com](https://www.github.com)

It's a **cloud hosting platform for Git repositories**.

---

## Understanding Remote

### What does "Remote" mean in Git?

In Git, a **remote** means a version of the repository that is stored somewhere else - online (GitHub, GitLab, BitBucket, etc.)

**Key Difference:**
- **Git** = Local tool → Local repo → Stays on your computer
- **GitHub** = Remote service that stores Git repos online → Remote repos live on the internet

---

## Basic Workflow

### File Changes Process

**md** = markdown  
**change** = do

Changes follow a **2-step process:**
1. **Change** → Add
2. **Changes final** → Commit

### Commit Process

```
Changes → Snapshot → Saved in History
```

---

## The Three Areas in Git

Every file in Git goes through three stages:

| Stage | Description | Command |
|-------|-------------|---------|
| **Working Directory** | Your local folder where you edit files | `git status` shows what's changed |
| **Staging Area** | Where you prepare (select) files to include in your next snapshot | `git add file.txt` |
| **Repository (Local)** | Where Git permanently saves your snapshot (commit) | `git commit -m "message"` |

---

## Git Configuration

### User Naming + Emails (Account in Action)

When you make a commit in Git, Git stores who made the changes:

```
Author: Muhammad Nouman Hafeez <noumanhafeez.nh11@gmail.com>
Date:   Sat Oct 05 2025 ...
```

These details come from the **Git Configuration**.

### Configuration Types:
1. **Global** → Once → For all projects
2. **Local** → Per Project

---

### Setting Configuration Globally

Open Git Bash and type:

```bash
git config --global user.name "Muhammad Nouman Hafeez"
git config --global user.email "noumanhafeez.nh11@gmail.com"
```

Now, every future commit from your system will show your name and email.

### Verifying Settings

Run these commands:

```bash
git config --global user.name
git config --global user.email
```

**Or do it with 1 command:**

```bash
git config --global --list
```

**What you will see:**
```
user.name=Muhammad Nouman Hafeez
user.email=noumanhafeez.nh11@gmail.com
```

---

### Setting Configuration Locally (Per Project)

Run above commands **without** `--global`:

```bash
git config user.name "Nouman Work"
git config user.email "nouman@company.com"
```

This will apply to the current working repo only.

---

### Where These Are Stored?

Git saves your configuration in text files:

| Scope | File | Applies To |
|-------|------|------------|
| **Global** | `~/.gitconfig` | All repos for your user |
| **Local** | `.git/config` | Only the current repo |

You can even open `.gitconfig` in Notepad to view or edit it manually.

---

### Other Useful Global Settings

```bash
# Set your default branch name to main
git config --global init.defaultBranch main

# Set your preferred text editor (for commit messages)
git config --global core.editor "code --wait"     # for VS Code
# or "notepad" or "nano" etc.

# Enable colored output for better readability
git config --global color.ui auto

# Make Git remember your GitHub login credentials
git config --global credential.helper store
```

---

## File Tracking Status

### Git File Tracking Status Lifecycle

Every file in a Git repo can be in one of these **4 states:**

| State | Meaning | Typical Git Symbol |
|-------|---------|-------------------|
| **Untracked (U)** | New file, not yet added to Git | `??` or `A` (after adding) |
| **Modified (M)** | File changed after last commit | `M` |
| **Staged (A / M)** | File added to staging area (ready to commit) | `A` (Added) or `M` (Modified and staged) |
| **Unmodified** | No changes since last commit | `—` (nothing shown) |

---

### Status Symbols Explained

| Symbol | Meaning | Example Output | Description |
|--------|---------|----------------|-------------|
| `??` | Untracked | `?? newfile.txt` | File not added to Git yet |
| `A` | Added (staged new file) | `A newfile.txt` | New file added to staging area |
| `M` | Modified | `M script.py` | File changed since last commit |
| `M` (first column) | Staged modification | `M script.py` | File changes staged and ready to commit |
| `M` (second column) | Unstaged modification | ` M script.py` | File changed but not staged yet |
| `D` | Deleted | `D oldfile.txt` | File deleted from working directory |
| `R` | Renamed | `R100 oldname → newname` | File renamed |
| `C` | Copied | `C100 fileA → fileB` | File copied |
| `U` | Unmerged / conflict | `U file.txt` | Merge conflict during merge/pull |

---

### Cheat Sheet

| Symbol | Meaning | Staging? | Description |
|--------|---------|----------|-------------|
| `??` | Untracked | ❌ | New file not tracked yet |
| `A` | Added | ✅ | File added to Git |
| `M` | Modified | ⚠️ / ✅ | File content changed |
| `D` | Deleted | ✅ | File removed |
| `R` | Renamed | ✅ | File renamed |
| `C` | Copied | ✅ | File copied |
| `U` | Unmerged | ❌ | Merge conflict |

---

### Quickly Check File Statuses

```bash
git status -s
```

**Example:**

```
M  index.html      # modified & staged
 M style.css       # modified but not staged
?? new.txt         # untracked
```

---

## Common Commands

### Creating a New Project

```bash
# Creating a new project
mkdir MyProject
cd MyProject

# Initializing git
git init

# Creating a file
echo "Hello Git" > file.txt

# Check what's happening
git status
```

### Staging and Committing

```bash
# Stage the file
git add .              # add all files
git add file.txt       # only add the specific file

# Commit (save the snapshot)
git commit -m "Initial Commit"

# See the history
git log
```

---

## Working with Remote Repositories

### Connecting a Local Repo to GitHub

**Step 1:** Create an empty repo on GitHub with the repo name, description, tags, collaborators, then connect it with Git.

**Step 2:** Link your local repo to GitHub

```bash
git remote add origin https://github.com/username/reponame.git
```

**Step 3:** Push your local commits to GitHub

```bash
git push -u origin main
```

---

### How to Check Remote Servers

To check which remote servers your local Git repo is connected to:

```bash
git remote -v
```

**`-v`** = verbose = shows more details (the URLs)

**Example:**

Let's say we connected a local repo to GitHub using:

```bash
git remote add origin https://github.com/noumanic/MyRepo.git
```

Now type:

```bash
git remote -v
```

We will see something like:

```
origin  https://github.com/noumanic/MyRepo.git (fetch)
origin  https://github.com/noumanic/MyRepo.git (push)
```

---

### What the Output Means

| Part | Meaning |
|------|---------|
| `origin` | This is the name (alias) of your remote repo. Default name is always `origin`. |
| `fetch` | The URL used when you download (pull) changes from GitHub. |
| `push` | The URL used when you upload (push) changes to GitHub. |
| `URL` | The actual web address of your GitHub repo. |

---

### Why & When to Use It?

| Situation | Why use it |
|-----------|------------|
| After cloning a repo | To check which remote repo it's linked to. |
| After adding a remote | To confirm you added the correct GitHub link. |
| If your push/pull isn't working | To debug and ensure your remote URL is correct. |
| When working with multiple remotes | To see all remotes (e.g., `origin`, `upstream`). |

---

### Managing Remotes

**Disconnect a remote:**

```bash
git remote remove origin
```

**Update/change the remote URL:**

```bash
git remote set-url origin <new-URL>
```

---

## Pulling Updates

### What is `git pull`?

```bash
git pull
```

**Translation:** Hey Git, go to the remote repo (GitHub), get the latest commits and merge them into my local copy.

It's a shortcut for 2 commands:

1. `git fetch` — Download changes from remote
2. `git merge` — Combine them into your branch

**So:**

```
git pull = git fetch + git merge
```

---

### When You Use `git pull`?

1. You already have a local copy of a repo.
2. You want to update your local repo with the latest version from GitHub.

---

### Case 1: Already Have a Local Copy / Already Cloned GitHub Repo

```bash
git clone https://github.com/noumanic/MyRepo.git
cd MyRepo
```

Now if someone (either you, or anyone else in the contributors, or any user) makes changes, you can get the latest version by running:

```bash
git pull origin main
```

- `origin` → The remote repo (GitHub repo)
- `main` → Branch specified (usually it is `main` or `master`)

**Note:** `master` was the old name, now it is `main`.

---

### Understanding Default Branch Names

By default, when we do:

```bash
git init
```

Git initializes a new empty repo → It requires/needs to create a default branch to start with → By default → `master` branch

Now Git changes the default branch (`master`) into the `main` branch.

**Check Git Configuration:**

```bash
git config --global init.defaultBranch
```

- Returns nothing → `master` branch
- Returns `main` → `main` branch

**Setting to main:**

```bash
git config --global init.defaultBranch main
```

So now, future `git init` → default branch → `main` branch

**Renaming a branch to main:**

```bash
git branch -m main
```

---

### Case 2: You Made Local Repo First, Then Connected GitHub Later

```bash
mkdir MyRepo
cd MyRepo
git init
# ... add files, commit etc.
git remote add origin https://github.com/noumanic/MyRepo.git
```

To get updates from GitHub later:

```bash
git pull origin main
```

If it is your first pull, you might need to set up tracking:

```bash
git pull --set-upstream origin main
```

---

## Pulling Other People's Public Repos

### Option 1: Just Clone It (If You Want to Copy to Explore or Learn)

```bash
git clone https://github.com/someuser/project-name.git
```

Later, if the original repo updates:

```bash
cd project-name
git pull origin main
```

**Note:** You can see updates but can't push unless you have permission.

---

### Option 2: Fork → Clone → Pull Updates (For Contributing)

If you want to contribute to someone's repo:

**1. Fork it on GitHub** (your own copy under your account).

**2. Clone your fork:**

```bash
git clone https://github.com/yourusername/project-name.git
cd project-name
```

**3. Work locally, commit, and push to your fork.**

**4. If the original repo gets new updates,** you can link it as `upstream`:

```bash
git remote add upstream https://github.com/originaluser/project-name.git
git fetch upstream
git merge upstream/main
```

**Or simply:**

```bash
git pull upstream main
```

---

## Visual Flow

### git pull Visual Flow

```
GitHub (remote repo) 
    ↓
git fetch (downloads new commits) 
    ↓
git merge (combines with your local branch) 
    ↓
Your local folder updated
```

---

## In Short

```
Working Directory  →  Staging Area  →  Local Repository  →  GitHub (Remote)
   (edit files)        (git add)         (git commit)         (git push)
```

---

**Happy Learning! 🚀**