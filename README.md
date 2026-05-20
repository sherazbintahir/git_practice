# 📘 Git & GitHub — Complete Reference Guide

A professional, structured reference covering Git version control and GitHub collaboration workflows — from first commit to team-based CI/CD.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Core Concepts](#core-concepts)
- [Essential Commands](#essential-commands)
- [Daily Workflow](#daily-workflow)
- [Branching & Merging](#branching--merging)
- [Collaboration](#collaboration)
- [Stashing](#stashing)
- [Git Ignore](#git-ignore)
- [Security Best Practices](#security-best-practices)
- [Mental Model](#mental-model)

---

## Overview

This repository serves as a practical, production-ready reference for Git and GitHub. It covers version control fundamentals, branching strategies, team collaboration flows, and security standards used in real projects.

**Who this is for:** Developers who want a single clean reference — no filler, all signal.

---

## Core Concepts

| Term | Description |
|------|-------------|
| **Git** | Tracks code changes locally |
| **GitHub** | Stores Git projects online |
| **Repository** | Project folder tracked by Git |
| **Commit** | Saved snapshot of code state |
| **Branch** | Isolated work area |
| **Main Branch** | Stable default project branch |
| **Clone** | Download remote repo locally |
| **Push** | Upload commits to GitHub |
| **Pull** | Fetch latest changes from GitHub |
| **Remote** | Online repo connection |
| **Staging** | Prepare files before committing |
| **Pull Request (PR)** | Request to merge code into main |
| **Merge** | Combine branch changes |
| **Conflict** | Same line changed in two branches |
| **Stash** | Temporary storage for uncommitted changes |
| **Tag** | Mark a specific version/release |

---

## Essential Commands

### Setup & Init
```bash
git init                        # Initialize Git in folder
git remote add origin <url>     # Connect local repo to GitHub
git remote -v                   # Show connected remotes
git branch -M main              # Rename branch to main
```

### Status & Logs
```bash
git status                      # Show all current changes
git status -s                   # Short status (U=untracked, A=added, M=modified, D=deleted)
git log                         # Full commit history
git log --oneline               # Condensed commit history
git log -p                      # Detailed diff per commit
```

### Stage & Commit
```bash
git add .                       # Stage all changes
git commit -m "message"         # Commit staged changes
```

### Push & Pull
```bash
git push                        # Upload commits to remote
git push origin <branch>        # Push specific branch
git pull                        # Fetch + merge latest changes
git pull origin main            # Pull from main branch explicitly
git fetch                       # Fetch without merging
git merge origin/main           # Merge fetched remote changes
```

### Cloning
```bash
git clone <url>                 # Copy remote repo locally
```

---

## Daily Workflow

```
1. git pull                     ← Always start here
2. git switch -c feature/name   ← Create working branch
3. [make changes]
4. git status                   ← Review changes
5. git add .                    ← Stage files
6. git commit -m "clear message"
7. git push origin feature/name ← Push branch
8. Open Pull Request on GitHub
9. Review → Merge PR
10. git switch main && git pull  ← Sync local main
```

---

## Branching & Merging

### Branch Operations
```bash
git branch                      # List branches
git branch <name>               # Create branch
git switch <name>               # Switch to branch
git switch -c <name>            # Create and switch
git branch -d <name>            # Delete merged branch
git branch -D <name>            # Force delete branch
```

### Merge
```bash
# Switch to target branch first
git switch main
git merge <branch>
```

**Merge types:**
- **Fast-forward merge (FFM)** — No divergence in main; pointer moves forward cleanly
- **3-way merge** — Both branches have changes; Git creates a merge commit

### Conflict Resolution
When conflict occurs, Git marks the file:
```
<<<<<<< HEAD
your changes
=======
incoming changes
>>>>>>> feature/branch
```
1. Edit file — keep desired changes, remove markers
2. `git add <file>`
3. `git commit`

---

## Collaboration

### As Collaborator
```bash
git clone <repo-url>
git switch -c feature/your-feature
# make changes
git add .
git commit -m "feature: description"
git push -u origin feature/your-feature
# open Pull Request on GitHub
```

### As Admin (Reviewing & Merging)
```bash
git fetch
git switch feature/branch        # Review incoming changes
git switch main
git merge feature/branch
git push origin main
```

### After Merge — Collaborator Syncs
```bash
git switch main
git fetch
git pull
```

---

## Stashing

Temporarily save work without committing:

```bash
git stash                       # Save uncommitted changes
git stash list                  # View all stashes
git stash apply                 # Re-apply latest stash
git stash clear                 # Remove all stashes
```

---

## Git Ignore

Create `.gitignore` in project root to exclude files/folders from tracking:

```gitignore
# Dependencies
node_modules/

# Environment variables
.env
.env.local

# Build output
dist/
build/

# OS files
.DS_Store
Thumbs.db

# Secrets
secrets.json
*.key
```

> **Rule:** If it should never reach GitHub, it belongs in `.gitignore`.

---

## Security Best Practices

| Rule | Reason |
|------|--------|
| Never commit `.env` | Protects API keys and credentials |
| Use `.gitignore` | Prevents accidental secret uploads |
| Use GitHub Secrets | Stores private values for CI/CD safely |
| Keep client repos private | Protects proprietary data |
| Use `.env.example` | Documents config without exposing values |
| Enable 2FA on GitHub | Adds login security layer |
| Review diffs before push | Catches sensitive data before it's public |
| Protect main branch | Prevents direct unreviewed pushes |

---

## Mental Model

```
Your Machine (Local)          GitHub (Remote)
─────────────────────         ───────────────────
Working Directory             main branch
      ↓ git add
Staging Area                  feature branches
      ↓ git commit
Local Commits                 Pull Requests
      ↓ git push    ────────→ Merged Code
      ← git pull   ←──────── Updated Main
```

| Local | Remote Equivalent |
|-------|-------------------|
| Working directory | Your laptop |
| `git commit` | Save point |
| `git push` | Send online |
| `git pull` | Bring back |
| Branch | Safe work area |
| Stash | Temp change storage |
| Conflict | Manual decision point |

---

## File Status Codes (git status -s)

| Code | Meaning |
|------|---------|
| `U` | Untracked |
| `A` | Added (staged) |
| `M` | Modified |
| `D` | Deleted |
| `R` | Renamed |

---

## Previous Commits

```bash
git checkout HEAD~1             # Go back 1 commit
git checkout HEAD~2             # Go back 2 commits
```

---

> Built for developers who move fast and want a reliable reference — not a tutorial.
> With ❤
