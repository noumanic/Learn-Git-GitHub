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

# Learn Git & GitHub

A comprehensive guide to understanding Git version control and GitHub collaboration.

## 📚 What's Inside

This repository contains step-by-step notes on:

- **Git Fundamentals** - Version control basics and workflow
- **GitHub Integration** - Remote repositories and collaboration
- **Configuration** - Setting up user credentials and preferences
- **File Tracking** - Understanding Git's staging and commit process
- **Remote Operations** - Push, pull, and sync with GitHub
- **Collaboration** - Working with forks and upstream repositories

## 🚀 Quick Start

### Initial Setup

```bash
# Configure your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default branch to main
git config --global init.defaultBranch main
```

### Basic Workflow

```bash
# Initialize a new repo
git init

# Stage changes
git add .

# Commit changes
git commit -m "Your message"

# Connect to GitHub
git remote add origin https://github.com/username/repo.git

# Push to GitHub
git push -u origin main
```

## 📖 Documentation

For detailed notes and explanations, see [`reading.md`](reading.md)

## 🎯 Key Concepts

| Concept | Description |
|---------|-------------|
| **Working Directory** | Your local files |
| **Staging Area** | Files ready to commit |
| **Repository** | Committed snapshots |
| **Remote** | GitHub copy of your repo |

## 🔧 Common Commands

```bash
git status          # Check current state
git log             # View commit history
git pull            # Get updates from GitHub
git push            # Send commits to GitHub
git remote -v       # View remote connections
```

## 📝 Author

**Muhammad Nouman Hafeez**  
📧 noumanhafeez.nh11@gmail.com

---

⭐ Star this repo if you find it helpful!