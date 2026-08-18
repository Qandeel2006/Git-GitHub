# Git & GitHub — Complete Guide

A full reference covering what Git and GitHub are, how they work, every core feature, and the exact commands/procedures to use them — for both personal projects and professional workflows.

---

## Table of Contents

1. [What is Git?](#1-what-is-git)
2. [What is GitHub?](#2-what-is-github)
3. [Git vs GitHub — The Difference](#3-git-vs-github--the-difference)
4. [Why Git/GitHub Matter (Personally & Professionally)](#4-why-gitgithub-matter)
5. [Installing & Configuring Git](#5-installing--configuring-git)
6. [Core Concepts](#6-core-concepts)
7. [Basic Workflow Commands](#7-basic-workflow-commands)
8. [Branching](#8-branching)
9. [Merging & Rebasing](#9-merging--rebasing)
10. [Working with Remotes (GitHub)](#10-working-with-remotes-github)
11. [Cloning vs Forking](#11-cloning-vs-forking)
12. [Uploading a New Project to GitHub (Step-by-Step)](#12-uploading-a-new-project-to-github-step-by-step)
13. [Pull Requests](#13-pull-requests)
14. [Resolving Merge Conflicts](#14-resolving-merge-conflicts)
15. [.gitignore](#15-gitignore)
16. [Stashing](#16-stashing)
17. [Tags & Releases](#17-tags--releases)
18. [Undoing Things](#18-undoing-things)
19. [Viewing History & Inspecting](#19-viewing-history--inspecting)
20. [GitHub-Specific Features](#20-github-specific-features)
21. [Common Git Workflows](#21-common-git-workflows)
22. [Quick Command Cheat Sheet](#22-quick-command-cheat-sheet)

---

## 1. What is Git?

**Git** is a free, open-source **version control system (VCS)**. It tracks changes to files over time, so you can:
- See the full history of every change made to a project
- Revert to a previous version if something breaks
- Work on new features without affecting the main working code
- Collaborate with others without overwriting each other's work

Git runs **locally on your computer** — it doesn't require the internet to function. It was created by Linus Torvalds (creator of Linux) in 2005.

## 2. What is GitHub?

**GitHub** is a **cloud-based hosting platform** for Git repositories. It adds a web interface and collaboration tools on top of Git, including:
- Remote storage for your repositories (backup + access from anywhere)
- Pull requests, code review, and team collaboration tools
- Issue tracking, project boards, and wikis
- GitHub Actions (automation/CI-CD)
- A public portfolio of your work, visible to employers and collaborators

**GitLab** and **Bitbucket** are similar alternatives to GitHub — same underlying Git, different hosting platform.

## 3. Git vs GitHub — The Difference

| | Git | GitHub |
|---|---|---|
| What it is | Software/tool | Website/service |
| Where it runs | Locally on your machine | In the cloud |
| Requires internet | No | Yes (for remote features) |
| Purpose | Version control | Hosting + collaboration on top of Git |

You can use Git without GitHub (fully local). You cannot use GitHub without Git.

## 4. Why Git/GitHub Matter

**Professionally:**
- It's the industry standard — virtually every software job expects Git proficiency.
- Enables teams to collaborate on the same codebase without conflict or chaos.
- Your GitHub profile acts as a public portfolio — recruiters check it.
- Essential for open-source contribution, which builds real-world credibility.
- Powers CI/CD pipelines (automated testing/deployment) via GitHub Actions.

**Personally:**
- Keeps a safe, versioned backup of your projects (nothing is truly lost).
- Lets you experiment freely using branches, without breaking your main project.
- Makes it easy to track progress and revisit "why did I make this change" months later.
- Useful even for non-code projects: notes, configs, documentation.

## 5. Installing & Configuring Git

**Install:**
- Windows: download from [git-scm.com](https://git-scm.com)
- Mac: `brew install git` (or comes pre-installed)
- Linux: `sudo apt install git` (Debian/Ubuntu) or `sudo dnf install git` (Fedora)

**Check installation:**
```bash
git --version
```

**Set your identity (required before your first commit):**
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Check your config:**
```bash
git config --list
```

## 6. Core Concepts

| Term | Meaning |
|---|---|
| **Repository (repo)** | A project folder tracked by Git |
| **Commit** | A saved snapshot of your changes, with a message |
| **Branch** | An independent line of development |
| **Working directory** | Your actual project files on disk |
| **Staging area (index)** | A holding area for changes before committing |
| **HEAD** | Pointer to your current branch/commit |
| **Remote** | A version of your repo hosted elsewhere (e.g., GitHub) |
| **Clone** | A local copy of a remote repository |
| **Fork** | Your own copy of someone else's repository on GitHub |
| **Pull Request (PR)** | A request to merge your changes into another branch/repo |

**The three states of a file in Git:**
```
Working Directory  →  Staging Area  →  Repository (committed)
     (edit)              (git add)         (git commit)
```

## 7. Basic Workflow Commands

**Initialize a new repository:**
```bash
git init
```

**Check status of your files (what's changed, staged, untracked):**
```bash
git status
```

**Stage changes (add to staging area):**
```bash
git add filename.txt        # stage one file
git add .                   # stage everything in current directory
git add folder/             # stage a whole folder
```

**Commit staged changes (save a snapshot):**
```bash
git commit -m "Write a clear, short message describing the change"
```

**Stage and commit in one step (only for already-tracked files):**
```bash
git commit -am "message"
```

**View commit history:**
```bash
git log
git log --oneline           # condensed view
```

## 8. Branching

Branches let you work on features/fixes independently without touching the main codebase.

```bash
git branch                        # list branches
git branch new-feature            # create a branch
git checkout new-feature          # switch to that branch
git checkout -b new-feature       # create AND switch in one step
git switch new-feature            # modern alternative to checkout
git branch -d new-feature         # delete a branch (after merging)
git branch -D new-feature         # force-delete (even if not merged)
```

**Common convention:** `main` (or `master`) is the stable/production branch. Feature work happens on branches like `feature/login-page` or `fix/navbar-bug`.

## 9. Merging & Rebasing

**Merging** combines changes from one branch into another, keeping full history:
```bash
git checkout main
git merge new-feature
```

**Rebasing** replays your branch's commits on top of another branch, creating a cleaner, linear history:
```bash
git checkout new-feature
git rebase main
```

<div class="note">

**When to use which:** Merge is safer and preserves exact history — good for shared/team branches. Rebase creates a cleaner history — good for your own local branches before pushing, but avoid rebasing commits others have already pulled.

</div>

## 10. Working with Remotes (GitHub)

**Link a local repo to a GitHub repo:**
```bash
git remote add origin https://github.com/username/repo-name.git
```

**View configured remotes:**
```bash
git remote -v
```

**Push local commits to GitHub:**
```bash
git push origin main              # push branch "main" to remote "origin"
git push -u origin main           # -u sets upstream, so future pushes just need "git push"
```

**Pull latest changes from GitHub into your local repo:**
```bash
git pull origin main
```

**Fetch changes without merging them (just check what's new):**
```bash
git fetch origin
```

## 11. Cloning vs Forking

**Clone** — download a full copy of a repository (yours or someone else's) to your machine:
```bash
git clone https://github.com/username/repo-name.git
```

**Fork** — create your own copy of someone else's repo *under your GitHub account* (done via the GitHub website, not the command line). Used when you want to contribute to a project you don't have write access to.

**Typical open-source contribution flow:** Fork → Clone your fork → Create a branch → Make changes → Push to your fork → Open a Pull Request to the original repo.

## 12. Uploading a New Project to GitHub (Step-by-Step)

**Starting from a local project folder:**

```bash
# 1. Navigate into your project folder
cd my-project

# 2. Initialize Git
git init

# 3. Stage all files
git add .

# 4. Make your first commit
git commit -m "Initial commit"

# 5. Create a new empty repository on GitHub.com (via the website — do NOT initialize with a README if you already have local files)

# 6. Link your local repo to the GitHub repo
git remote add origin https://github.com/username/repo-name.git

# 7. Rename branch to main (if needed)
git branch -M main

# 8. Push your code to GitHub
git push -u origin main
```

After this, any future changes just need:
```bash
git add .
git commit -m "Description of changes"
git push
```

## 13. Pull Requests

A **Pull Request (PR)** is how you propose merging changes from one branch (or fork) into another — used heavily in team and open-source workflows.

**Typical steps:**
1. Push your branch to GitHub: `git push origin feature-branch`
2. Go to the repository on GitHub — it will show a prompt to "Compare & pull request"
3. Add a title and description explaining your changes
4. Reviewers comment, request changes, or approve
5. Once approved, the PR is merged into the target branch (often `main`)

PRs are where **code review** happens — a core part of professional software development.

## 14. Resolving Merge Conflicts

A conflict happens when Git can't automatically combine changes (e.g., two people edited the same line differently).

**When it happens, Git marks the file like this:**
```
<<<<<<< HEAD
Your current changes
=======
Incoming changes
>>>>>>> branch-name
```

**To resolve:**
1. Open the file and manually edit it to keep the correct content
2. Remove the `<<<<<<<`, `=======`, `>>>>>>>` markers
3. Stage the resolved file: `git add filename`
4. Complete the merge: `git commit`

## 15. .gitignore

A `.gitignore` file tells Git which files/folders to **never track** (e.g., secrets, dependencies, build files).

**Example `.gitignore`:**
```
node_modules/
.env
*.log
__pycache__/
.DS_Store
dist/
```

Create it in your project root before your first commit for best results.

## 16. Stashing

Temporarily save uncommitted changes without committing them — useful when you need to switch branches quickly.

```bash
git stash                 # save current changes
git stash list             # view stashed changes
git stash pop               # reapply the most recent stash and remove it from the list
git stash apply             # reapply without removing from the list
git stash drop               # delete a stash
```

## 17. Tags & Releases

Tags mark specific points in history — typically used for version releases (e.g., `v1.0.0`).

```bash
git tag v1.0.0                       # create a tag
git tag                              # list tags
git push origin v1.0.0               # push a specific tag
git push origin --tags               # push all tags
```

On GitHub, tags can be turned into formal **Releases** with changelogs and downloadable files via the repo's "Releases" section.

## 18. Undoing Things

| Situation | Command |
|---|---|
| Unstage a file (keep changes) | `git restore --staged filename` |
| Discard changes in a file | `git restore filename` |
| Undo last commit, keep changes staged | `git reset --soft HEAD~1` |
| Undo last commit, unstage changes | `git reset --mixed HEAD~1` |
| Undo last commit, discard changes entirely | `git reset --hard HEAD~1` ⚠️ irreversible |
| Create a new commit that reverses a previous one | `git revert <commit-hash>` |

<div class="warn">

`git reset --hard` permanently deletes uncommitted work — use `git revert` instead if the commit has already been pushed/shared, since it preserves history.

</div>

## 19. Viewing History & Inspecting

```bash
git log                      # full commit history
git log --oneline --graph    # visual branch history
git show <commit-hash>       # details of a specific commit
git diff                     # unstaged changes vs last commit
git diff --staged            # staged changes vs last commit
git blame filename           # who changed each line, and when
```

## 20. GitHub-Specific Features

| Feature | Purpose |
|---|---|
| **Issues** | Track bugs, tasks, and feature requests |
| **Projects (Boards)** | Kanban-style task management |
| **Actions** | Automate testing, building, and deployment (CI/CD) |
| **Wiki** | Project documentation pages |
| **Discussions** | Community Q&A, separate from Issues |
| **GitHub Pages** | Free static website hosting directly from a repo |
| **Codespaces** | Cloud-based dev environment in the browser |
| **Security/Dependabot alerts** | Flags vulnerable dependencies automatically |

## 21. Common Git Workflows

**Feature Branch Workflow (most common in teams):**
```
main
 └── feature/login-page   → work here → PR → merge into main
 └── fix/navbar-bug       → work here → PR → merge into main
```

**Daily solo workflow:**
```bash
git pull                       # get latest changes
# ... make edits ...
git add .
git commit -m "message"
git push
```

## 22. Quick Command Cheat Sheet

```bash
git init                          # start a new repo
git clone <url>                   # copy a remote repo locally
git status                        # see current state
git add <file>                    # stage a file
git add .                         # stage everything
git commit -m "message"           # save a snapshot
git push                          # send commits to remote
git pull                          # get latest from remote
git branch                        # list branches
git checkout -b <name>            # create + switch branch
git merge <branch>                # merge a branch into current one
git log --oneline                 # view history
git diff                          # see unstaged changes
git stash                         # temporarily save changes
git remote -v                     # view linked remotes
git tag <name>                    # mark a version point
```

---

*This guide covers Git/GitHub fundamentals through professional workflows — from your first `git init` to pull requests and CI/CD.*