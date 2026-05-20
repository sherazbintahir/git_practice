````markdown
# All About Git and GitHub

A practical learning repository for understanding **Git**, **GitHub**, version control, branching, merging, collaboration, and professional development workflows.

This repository is created for hands-on practice and quick revision of commonly used Git and GitHub concepts.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Initialize Git Repository](#initialize-git-repository)
3. [Git File Status Symbols](#git-file-status-symbols)
4. [Git Status](#git-status)
5. [Git Logs](#git-logs)
6. [Working with Previous Commits](#working-with-previous-commits)
7. [Branching](#branching)
8. [Deleting Branches](#deleting-branches)
9. [Merging](#merging)
10. [Merge Conflicts](#merge-conflicts)
11. [Stashing](#stashing)
12. [Git Ignore](#git-ignore)
13. [Collaboration](#collaboration)
14. [Collaborator Workflow](#collaborator-workflow)
15. [Admin Merge Workflow](#admin-merge-workflow)
16. [After Code Is Merged](#after-code-is-merged)
17. [GitHub Review: One-Line Explanations](#github-review-one-line-explanations)
18. [Basic Command Review](#basic-command-review)
19. [Daily Workflow Review](#daily-workflow-review)
20. [Security Review](#security-review)
21. [Simple Mental Model](#simple-mental-model)

---

## Introduction

Git is a version control system used to track changes in code.

GitHub is an online platform used to store Git repositories, collaborate with others, manage projects, and maintain code history.

This project covers the most important Git and GitHub concepts in a simple and practical way.

---

## Initialize Git Repository

To start tracking a project with Git, initialize a Git repository inside the project folder:

```bash
git init
````

This creates a hidden `.git` folder that stores the project history.

---

## Git File Status Symbols

When using short status, Git shows different symbols for file states.

| Symbol | Meaning        |
| ------ | -------------- |
| `U`    | Untracked file |
| `A`    | Added file     |
| `M`    | Modified file  |
| `D`    | Deleted file   |
| `R`    | Renamed file   |

---

## Git Status

Check the current state of your working directory:

```bash
git status
```

Check the short version of file status:

```bash
git status -s
```

This helps you understand which files are new, modified, deleted, or staged.

---

## Git Logs

Check commit history in one-line format:

```bash
git log --oneline
```

Check detailed commit history:

```bash
git log
```

Check commit history with file changes:

```bash
git log -p
```

Git logs help you review previous commits and understand project history.

---

## Working with Previous Commits

Move one commit back:

```bash
git checkout HEAD~1
```

Move two commits back:

```bash
git checkout HEAD~2
```

This is useful for checking previous versions of your project.

Note: When you checkout an old commit, you enter a detached HEAD state. To return to the latest main branch, use:

```bash
git switch main
```

---

## Branching

Branches allow you to work on new features or fixes without affecting the main code.

Create a new branch:

```bash
git branch <branch_name>
```

Example:

```bash
git branch feature1
```

Switch to a branch:

```bash
git switch <branch_name>
```

Example:

```bash
git switch feature1
```

Switch back to the main branch:

```bash
git switch main
```

Create and switch to a branch at the same time:

```bash
git switch -c <branch_name>
```

Example:

```bash
git switch -c feature1
```

---

## Deleting Branches

Delete a branch safely:

```bash
git branch -d <branch_name>
```

Example:

```bash
git branch -d feature1
```

Force delete a branch:

```bash
git branch -D <branch_name>
```

Example:

```bash
git branch -D feature1
```

Use force delete only when you are sure the branch is no longer needed.

---

## Merging

Merging is used to combine changes from one branch into another branch.

To merge a branch into `main`, first switch to the main branch:

```bash
git switch main
```

Then merge the required branch:

```bash
git merge <branch_name>
```

Example:

```bash
git merge feature/calc
```

### Fast Forward Merge

A fast forward merge happens when there are no new changes in the main branch. Git simply moves the main branch pointer forward.

### Three-Way Merge

A three-way merge happens when both branches have new changes. Git combines the changes from both branches.

---

## Merge Conflicts

A merge conflict happens when Git cannot automatically decide which changes should be kept.

Git shows conflict markers inside the affected file:

```text
<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> branch-name
```

To resolve a conflict:

1. Open the conflicted file.
2. Remove the conflict markers.
3. Keep the correct code.
4. Add the resolved file:

```bash
git add .
```

5. Commit the resolved conflict:

```bash
git commit -m "Resolve merge conflict"
```

After this, the merge is completed.

---

## Stashing

Stashing is used to temporarily save uncommitted changes.

Save current changes in stash:

```bash
git stash
```

Show all stashes:

```bash
git stash list
```

Apply the latest stash:

```bash
git stash apply
```

Clear all stashes:

```bash
git stash clear
```

Stashing is useful when you need to switch branches but do not want to commit incomplete work.

---

## Git Ignore

`.gitignore` is used to tell Git which files or folders should not be tracked.

Create a `.gitignore` file in the root directory of your project.

Example: ignore `node_modules`:

```gitignore
node_modules/
```

Example: ignore a specific file:

```gitignore
secret.txt
```

Common `.gitignore` example:

```gitignore
.env
node_modules/
venv/
__pycache__/
.DS_Store
*.log
```

This helps prevent unnecessary or sensitive files from being pushed to GitHub.

---

## Collaboration

GitHub allows multiple developers to work on the same project.

Clone a remote repository:

```bash
git clone <remote_repository_url>
```

Pull latest changes:

```bash
git pull
```

Push local changes:

```bash
git push
```

Add a remote repository:

```bash
git remote add origin <remote_repository_url>
```

Check connected remote repositories:

```bash
git remote -v
```

Remove a remote repository:

```bash
git remote remove origin
```

Fetch changes without merging:

```bash
git fetch
```

Merge remote main branch into your current branch:

```bash
git merge origin/main
```

Pull changes from main branch:

```bash
git pull origin main
```

Push changes to main branch:

```bash
git push origin main
```

Push changes to a specific branch:

```bash
git push origin <branch_name>
```

Create and switch to a branch:

```bash
git checkout -b <branch_name>
```

Switch to a branch:

```bash
git checkout <branch_name>
```

Merge a branch into the current branch:

```bash
git merge <branch_name>
```

---

## Collaborator Workflow

When you are added as a collaborator to someone else's repository, use this professional workflow:

```bash
git clone <repo_url>
cd <repo_folder>
git switch -c feature
```

Make your changes, then run:

```bash
git add .
git commit -m "Add new feature"
git push -u origin feature
```

After pushing your branch, open GitHub and create a Pull Request.

A Pull Request allows the repository owner or admin to review your changes before merging them into the main branch.

---

## Admin Merge Workflow

The admin or repository owner can review and merge the collaborator's branch.

Fetch latest changes:

```bash
git fetch
```

Switch to the collaborator's branch:

```bash
git switch feature
```

Check the changes.

Switch back to main:

```bash
git switch main
```

Merge the feature branch:

```bash
git merge feature
```

Push the updated main branch:

```bash
git push origin main
```

---

## After Code Is Merged

After your code is merged into the main branch, update your local main branch:

```bash
git switch main
git fetch
git pull origin main
```

This keeps your local project updated with the latest merged code.

---

# GitHub Review: One-Line Explanations

| Term           | Explanation                    |
| -------------- | ------------------------------ |
| Git            | Tracks code changes locally    |
| GitHub         | Stores Git projects online     |
| Repository     | Project folder on GitHub       |
| Repo           | Short name for repository      |
| Commit         | Saved version of code          |
| Branch         | Separate safe work area        |
| Main Branch    | Stable default project branch  |
| Clone          | Download repo to computer      |
| Push           | Upload changes to GitHub       |
| Pull           | Download latest GitHub changes |
| Remote         | Online repo connection         |
| Local          | Project on your computer       |
| Staging        | Prepare files for commit       |
| Pull Request   | Request to merge code          |
| Merge          | Combine branch changes         |
| Conflict       | Same line changed differently  |
| README.md      | Explains project clearly       |
| .gitignore     | Hides files from Git           |
| Issues         | Track bugs and tasks           |
| GitHub Actions | Automate project workflows     |
| CI/CD          | Test and deploy automatically  |
| Secrets        | Store private keys safely      |
| Releases       | Publish project versions       |
| Tags           | Mark specific versions         |
| Public Repo    | Visible to everyone            |
| Private Repo   | Visible to invited users       |
| Organization   | Team or company account        |
| Contributor    | Person adding project work     |
| License        | Rules for using code           |
| Star           | Save or appreciate repo        |
| Watch          | Get repo notifications         |
| Documentation  | Written project instructions   |
| Rollback       | Return to older version        |

---

# Basic Command Review

| Command                       | Explanation                 |
| ----------------------------- | --------------------------- |
| `git init`                    | Start Git in folder         |
| `git status`                  | Show current file changes   |
| `git status -s`               | Show short file status      |
| `git add .`                   | Stage all changed files     |
| `git commit -m "message"`     | Save staged changes         |
| `git push`                    | Upload commits online       |
| `git pull`                    | Download latest changes     |
| `git clone <url>`             | Copy repo locally           |
| `git branch`                  | Show project branches       |
| `git switch <branch>`         | Move to another branch      |
| `git switch -c <branch>`      | Create and enter branch     |
| `git merge <branch>`          | Combine branch into current |
| `git log`                     | Show commit history         |
| `git log --oneline`           | Show short commit history   |
| `git remote -v`               | Show connected remote repo  |
| `git remote add origin <url>` | Connect local to GitHub     |
| `git branch -M main`          | Rename branch to main       |
| `git fetch`                   | Get changes without merging |
| `git stash`                   | Save temporary changes      |

---

# Daily Workflow Review

| Step           | Explanation                     |
| -------------- | ------------------------------- |
| Pull first     | Get latest code changes         |
| Create branch  | Work safely separately          |
| Edit files     | Make project changes            |
| Check status   | See changed files               |
| Stage files    | Prepare files for saving        |
| Commit changes | Save meaningful project version |
| Push branch    | Upload work to GitHub           |
| Open PR        | Request merge review            |
| Review code    | Check before merging            |
| Merge PR       | Add changes to main             |
| Pull again     | Update local main branch        |

---

# Security Review

| Rule                      | Explanation                  |
| ------------------------- | ---------------------------- |
| Never upload `.env`       | Protect secret credentials   |
| Use `.gitignore`          | Block unwanted files         |
| Use GitHub Secrets        | Store private values safely  |
| Keep client repos private | Protect client project data  |
| Avoid API key leaks       | Prevent account misuse       |
| Use `.env.example`        | Show config without secrets  |
| Enable 2FA                | Add login protection         |
| Review before push        | Catch sensitive files early  |
| Ignore large folders      | Avoid unnecessary uploads    |
| Protect main branch       | Prevent direct risky changes |

---

# Simple Mental Model

| Concept      | Explanation              |
| ------------ | ------------------------ |
| Your laptop  | Local working place      |
| GitHub       | Online project storage   |
| Commit       | Code save point          |
| Push         | Send code online         |
| Pull         | Bring code back          |
| Branch       | Safe experiment area     |
| Pull Request | Review before merging    |
| README       | Project explanation page |
| .gitignore   | Do not upload list       |
| Stash        | Temporary change storage |
| Merge        | Combine completed work   |
| Conflict     | Manual decision needed   |

---

## Final Collaboration Flow

```text
Clone repo
Create branch
Make changes
Add changes
Commit changes
Push branch
Create pull request
Admin reviews
Admin merges
Collaborator pulls latest code
```

---

## Summary

This repository provides a practical overview of Git and GitHub, including version control, branching, merging, stashing, collaboration, and security basics.

The main goal is to build a strong foundation for working professionally with GitHub in real-world projects.

```
```
