# Git Tutorial

A practical guide to using Git for version control in this project.

## What Is Git?

Git is a distributed version control system that tracks changes to files over time. It lets you:

- Save snapshots of your project at any point
- Revert to previous versions if something breaks
- Collaborate with others without overwriting each other's work
- Work on new features in isolation using branches

## Installation

### Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install git
```

### macOS

```bash
# Git comes with Xcode Command Line Tools
xcode-select --install

# Or install via Homebrew
brew install git
```

### Windows

Download the installer from [git-scm.com](https://git-scm.com/download/win), or use:

```powershell
winget install Git.Git
```

### Verify Installation

```bash
git --version
```

## Initial Setup

Configure your identity (used in commit messages):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@umich.edu"
```

## Getting This Project

Clone the repository to your local machine:

```bash
git clone https://github.com/MichiganDataScienceTeam/W26-MDST-Project_Heart-Failure-Survival-Analysis.git
cd W26-MDST-Project_Heart-Failure-Survival-Analysis
```

This creates a local copy of the entire project, including its full history.

## Core Concepts

### The Three Areas

Git tracks files across three areas:

```
Working Directory  -->  Staging Area  -->  Repository
   (your files)       (ready to commit)   (saved history)
       |                    |                   |
   git add ───────>    git commit ──────>   permanent
```

- **Working directory**: the files you see and edit
- **Staging area** (index): a draft of your next commit
- **Repository** (`.git/`): the complete history of commits

### Commits

A commit is a snapshot of all tracked files at a point in time. Each commit has:

- A unique hash (e.g., `9dc958d`)
- An author and timestamp
- A message describing what changed
- A pointer to its parent commit(s)

## Essential Commands

### Checking Status

```bash
# See which files are modified, staged, or untracked
git status

# See what you've changed but haven't staged yet
git diff

# See what's staged and ready to commit
git diff --staged
```

### Staging and Committing

```bash
# Stage a specific file
git add Week1.ipynb

# Stage multiple files
git add Week1.ipynb Week2.ipynb

# Stage all changes (use with caution)
git add .

# Commit staged changes with a message
git commit -m "Add data exploration notebook"
```

Write commit messages that explain **why** you made the change, not just what changed.

Good: `"Fix outlier filtering to exclude impossible age values"`
Bad: `"Updated code"`

### Viewing History

```bash
# View commit history
git log

# Compact one-line format
git log --oneline

# Show the last 5 commits
git log --oneline -5

# See what changed in a specific commit
git show 9dc958d
```

### Undoing Changes

```bash
# Discard changes to a file in your working directory
git checkout -- Week1.ipynb

# Unstage a file (keep the changes, just remove from staging)
git restore --staged Week1.ipynb

# Amend the last commit message (only if you haven't pushed yet)
git commit --amend -m "Better commit message"
```

## Working with Remotes

A remote is a copy of the repository hosted elsewhere (e.g., on GitHub).

```bash
# See configured remotes
git remote -v

# Download latest changes from GitHub (doesn't modify your files)
git fetch origin

# Download and merge latest changes into your current branch
git pull origin main

# Upload your commits to GitHub
git push origin main
```

### Typical Workflow

```bash
# 1. Pull latest changes before you start working
git pull origin main

# 2. Make your changes (edit notebooks, code, etc.)

# 3. Check what changed
git status

# 4. Stage your changes
git add Week3.ipynb

# 5. Commit
git commit -m "Complete K-Means clustering analysis"

# 6. Push to GitHub
git push origin main
```

## Branching

Branches let you work on features or experiments without affecting the main codebase.

```bash
# Create and switch to a new branch
git checkout -b feature/add-random-forest

# List all branches (* marks the current one)
git branch

# Switch between branches
git checkout main

# Merge a branch into main
git checkout main
git merge feature/add-random-forest

# Delete a branch after merging
git branch -d feature/add-random-forest
```

### Branch Naming Conventions

Use descriptive names with a prefix:

- `feature/add-pca-analysis` - new functionality
- `fix/correct-correlation-plot` - bug fixes
- `docs/update-readme` - documentation changes

## Handling Merge Conflicts

Conflicts happen when two branches modify the same lines. Git marks them like this:

```
<<<<<<< HEAD
your changes
=======
their changes
>>>>>>> feature-branch
```

To resolve:

1. Open the conflicting file
2. Choose which version to keep (or combine them)
3. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Stage and commit the resolved file

```bash
git add resolved_file.py
git commit -m "Resolve merge conflict in analysis code"
```

## The `.gitignore` File

The `.gitignore` file tells Git which files to ignore. This project's `.gitignore` excludes:

```
venv/               # Virtual environment (large, system-specific)
__pycache__/        # Python bytecode cache
.ipynb_checkpoints/ # Jupyter auto-saves
*.pyc               # Compiled Python files
.env                # Environment variables / secrets
```

Never commit virtual environments, compiled files, secrets, or large data files that can be downloaded separately.

## Common Issues and Fixes

### "I committed something I shouldn't have"

```bash
# Remove a file from tracking but keep it on disk
git rm --cached secrets.env
echo "secrets.env" >> .gitignore
git commit -m "Stop tracking secrets file"
```

### "I need to see what a file looked like before"

```bash
# Show a file from a specific commit
git show abc1234:Week1.ipynb
```

### "I want to temporarily save my work without committing"

```bash
# Stash your changes
git stash

# Restore stashed changes later
git stash pop
```

### "I'm getting 'permission denied' when pushing"

You likely need to set up SSH keys or a personal access token. See [GitHub's authentication docs](https://docs.github.com/en/authentication).

## Quick Reference

| Command | What It Does |
| --- | --- |
| `git clone <url>` | Copy a remote repository locally |
| `git status` | Show changed/staged/untracked files |
| `git add <file>` | Stage a file for the next commit |
| `git commit -m "msg"` | Save staged changes as a commit |
| `git push` | Upload commits to the remote |
| `git pull` | Download and merge remote changes |
| `git log --oneline` | View commit history (compact) |
| `git diff` | Show unstaged changes |
| `git branch` | List branches |
| `git checkout -b <name>` | Create and switch to a new branch |
| `git merge <branch>` | Merge a branch into the current one |
| `git stash` | Temporarily shelve changes |

## Further Reading

- [Pro Git Book](https://git-scm.com/book/en/v2) (free, comprehensive)
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Oh My Git!](https://ohmygit.org/) (interactive game to learn Git)
