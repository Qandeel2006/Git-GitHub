<div align="center">

# 🌱 Git & GitHub for Beginners

**A simple, complete guide to version control — from zero to confident.**

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

</div>

---

## 📌 What Even Is Git & GitHub?

| | 🛠️ Git | ☁️ GitHub |
|---|---|---|
| **What it is** | A tool that tracks changes to your files | A website that stores your Git projects online |
| **Runs where** | On your computer | In the cloud |
| **Needs internet?** | ❌ No | ✅ Yes |
| **In one line** | Your project's "save history" | Your project's online home |

> 💡 Think of Git like the **"undo history"** of a video game save file — and GitHub like **cloud storage** for that save file, where friends can also help you play.

---

## 🎯 Why Bother Learning This?

- 🧑‍💻 **Every tech job expects it** — it's the #1 tool for coding collaboration.
- 💾 **Never lose work** — every version is saved, forever recoverable.
- 🧪 **Experiment safely** — try new ideas on a branch without breaking your main project.
- 🌍 **Build a portfolio** — your GitHub profile is basically your coding resume.
- 🤝 **Work with others** — teams use it to combine code without chaos.

---

## ⚙️ Step 1: Install & Set Up Git

**Install:**
- 🪟 Windows → [git-scm.com](https://git-scm.com)
- 🍎 Mac → `brew install git`
- 🐧 Linux → `sudo apt install git`

**Tell Git who you are** (do this once):
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

**Check it worked:**
```bash
git --version
```

---

## 🧠 Step 2: Understand the 3 Key Zones

```
📁 Working Directory  →  📋 Staging Area  →  💾 Repository
    (you edit files)      (git add)            (git commit)
```

| Term | Meaning |
|---|---|
| **Repository (repo)** | A project folder tracked by Git |
| **Commit** | A saved snapshot with a message |
| **Branch** | A separate line of work, like a parallel universe of your project |
| **Remote** | The GitHub copy of your repo |

---

## 🚀 Step 3: The Core Daily Commands

This is 90% of what you'll ever use:

```bash
git init                      # start tracking a new project
git status                    # see what's changed
git add .                     # stage all changes
git commit -m "message"       # save a snapshot
git push                      # send it to GitHub
git pull                      # get latest changes from GitHub
```

> 📝 **Golden rule:** `add` → `commit` → `push`. Repeat forever.

---

## 📤 Step 4: Uploading Your First Project

```bash
cd my-project              # go into your project folder
git init                   # start Git tracking
git add .                  # stage everything
git commit -m "Initial commit"

# Create an empty repo on GitHub.com first, then:
git remote add origin https://github.com/username/repo-name.git
git branch -M main
git push -u origin main
```

✅ After this first setup, future updates are just:
```bash
git add .
git commit -m "what I changed"
git push
```

---

## 🌿 Step 5: Branching (Working Without Fear)

Branches let you build new features without touching your working code.

```bash
git branch                    # list branches
git checkout -b new-feature   # create + switch to a new branch
git checkout main             # switch back to main
git merge new-feature         # bring your branch's work into main
```

> 🧩 Think of `main` as your finished, stable project — and branches as your "draft" workspace.

---

## 🔄 Step 6: Getting Code From Others

| Action | What it does | Command |
|---|---|---|
| **Clone** | Download a full copy of any repo | `git clone <url>` |
| **Fork** | Copy someone's repo to *your* GitHub account (done on the website) | — |
| **Pull Request (PR)** | Ask to merge your changes into someone else's project | Done on GitHub after pushing your branch |

**Typical open-source flow:**
```
Fork → Clone your fork → Create a branch → Make changes → Push → Open a Pull Request
```

---

## 🧯 Step 7: "Oh No, I Made a Mistake" Fixes

| Problem | Fix |
|---|---|
| Staged the wrong file | `git restore --staged filename` |
| Want to discard changes in a file | `git restore filename` |
| Want to undo last commit but keep changes | `git reset --soft HEAD~1` |
| Need to reverse a commit that's already pushed | `git revert <commit-hash>` |

⚠️ Avoid `git reset --hard` unless you're 100% sure — it deletes work permanently.

---

## 🙈 Step 8: Ignoring Files You Don't Want Tracked

Create a `.gitignore` file in your project root:
```
node_modules/
.env
*.log
.DS_Store
```

Anything listed here Git will never track or upload — perfect for secrets, dependencies, and junk files.

---

## 🧰 Handy Extras

| Command | What it does |
|---|---|
| `git log --oneline` | See commit history, condensed |
| `git diff` | See exactly what changed |
| `git stash` | Temporarily "shelve" changes without committing |
| `git remote -v` | See which GitHub repo you're connected to |
| `git tag v1.0` | Mark a version milestone |

---

## 🏆 GitHub Features Worth Knowing

| Feature | What it's for |
|---|---|
| **Issues** | Track bugs & to-dos |
| **Pull Requests** | Propose & review code changes |
| **Actions** | Automate testing/deployment |
| **Pages** | Host a free website from your repo |
| **Codespaces** | Code in the cloud, no setup needed |

---

## 📋 Cheat Sheet (Print This)

```bash
git init                 # start a repo
git clone <url>          # copy a repo locally
git status                # check current state
git add .                 # stage everything
git commit -m "msg"       # save snapshot
git push                  # upload to GitHub
git pull                  # download latest
git branch                # list branches
git checkout -b <name>    # new branch
git merge <branch>        # combine branches
git log --oneline         # view history
```

---

<div align="center">

### 🎉 That's really it.

Learn `add`, `commit`, `push`, `pull`, and `branch` well — everything else you'll pick up as you need it.

</div>