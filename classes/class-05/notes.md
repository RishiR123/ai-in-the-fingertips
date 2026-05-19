# Class 5 Notes: AI and GitHub — Git, Commands, and Versioning Basics

---

## 1. What Is Version Control and Why Does It Matter?

Imagine you are writing an assignment. You save it as:
- `assignment.docx`
- `assignment_final.docx`
- `assignment_final_v2.docx`
- `assignment_FINAL_USE_THIS.docx`

This is manual version control — and it is chaotic. Now imagine doing this with thousands of files across a team of 20 engineers, all editing the same code at the same time.

**Version control** is a system that automatically tracks every change ever made to every file in a project — who changed it, when, and what exactly changed. You can go back to any point in history instantly.

**Git** is the most widely used version control system in the world. It was created by **Linus Torvalds** (the creator of Linux) in 2005.

**GitHub** is a website that hosts your Git repositories online — so your code is backed up, shareable, and collaborative.

> **Analogy**: Git is like Google Docs' version history, but for code — and far more powerful.

---

## 2. Key Concepts Before We Touch the Terminal

### Repository (Repo)
A folder that Git is tracking. Everything inside it — files, subfolders, history — is part of the repo.

### Commit
A snapshot of your project at a specific point in time. Think of it as a save point in a video game. Each commit has:
- The changes made
- A message describing what changed
- A timestamp and author

### Branch
A separate line of development. The default branch is called `main`. You create branches to work on features without affecting the main code.

### Remote
A copy of your repo hosted online (on GitHub). Your local machine has the local repo; GitHub has the remote repo.

---

## 3. Installing Git

### On Windows
1. Go to [git-scm.com](https://git-scm.com)
2. Download the Windows installer
3. Run it — keep all default settings
4. Open **Git Bash** (installed alongside Git) to run Git commands

### On Mac
Open Terminal and run:
```bash
git --version
```
If Git is not installed, Mac will prompt you to install it automatically via Xcode Command Line Tools. Click Install.

Alternatively, if you have Homebrew:
```bash
brew install git
```

### On Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install git
```

### Verify the Installation
```bash
git --version
```
You should see something like: `git version 2.43.0`

---

## 4. First-Time Setup — Tell Git Who You Are

Git needs to know your name and email so it can label your commits correctly. Do this once after installing:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Verify it worked:
```bash
git config --list
```

---

## 5. Creating a GitHub Account

1. Go to [github.com](https://github.com)
2. Click **Sign Up**
3. Choose a username — this is your public identity as a developer, pick something professional
4. Verify your email address
5. You now have a GitHub account

---

## 6. The Core Git Workflow — The 5 Commands You Will Use Daily

90% of your daily Git usage comes down to these five commands:

```
git init       → Start tracking a folder with Git
git add        → Stage changes (select what to include in the next commit)
git commit     → Save a snapshot with a message
git push       → Send commits to GitHub
git pull       → Get the latest changes from GitHub
```

Let's walk through each one.

---

## 7. Starting a New Project — Step by Step

### Step 1: Create a folder and initialise Git

```bash
mkdir my-project
cd my-project
git init
```

`git init` creates a hidden `.git` folder inside your project — this is where Git stores all its tracking information. Do not delete it.

You will see: `Initialized empty Git repository in .../my-project/.git/`

---

### Step 2: Create a file

```bash
# On Mac/Linux:
echo "# My First Project" > README.md

# On Windows (Git Bash):
echo "# My First Project" > README.md
```

Or just create a file manually in any text editor.

---

### Step 3: Check what Git sees

```bash
git status
```

Output:
```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
```

`Untracked` means Git sees the file but is not yet tracking changes to it.

---

### Step 4: Stage the file

```bash
git add README.md
```

To stage everything at once:
```bash
git add .
```

Run `git status` again — the file is now under **"Changes to be committed"** (shown in green).

**What is staging?**
Staging is like putting items into a box before sealing it. You decide exactly what goes into the next commit. This lets you commit some changes but not others.

---

### Step 5: Commit the snapshot

```bash
git commit -m "Initial commit: add README"
```

The `-m` flag lets you write the message inline. Always write a message that describes *what changed and why* — not just "update" or "fix".

Good commit messages:
- `Add navigation bar to homepage`
- `Fix login bug when email has uppercase letters`
- `Update README with installation steps`

Bad commit messages:
- `stuff`
- `fix`
- `asdfgh`

---

## 8. Connecting to GitHub and Pushing

### Step 1: Create a new repository on GitHub
1. Go to github.com → click the **+** button → **New repository**
2. Give it a name (e.g. `my-project`)
3. Leave it empty — do NOT add a README (you already have one locally)
4. Click **Create repository**

GitHub will show you a page with setup instructions. Look for the section that says **"push an existing repository from the command line"**.

### Step 2: Link your local repo to GitHub

```bash
git remote add origin https://github.com/your-username/my-project.git
```

`origin` is just a nickname for the GitHub URL. You can call it anything, but `origin` is the convention.

### Step 3: Push your commits to GitHub

```bash
git push -u origin main
```

`-u` sets the upstream — after this, you can just type `git push` without specifying the branch every time.

You will be asked to log in to GitHub. Use your GitHub username and a **Personal Access Token** (not your password — GitHub stopped accepting passwords for this).

**To create a Personal Access Token**:
GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic) → Generate new token → give it `repo` permission → copy it and save it somewhere safe.

---

## 9. The Daily Loop — After the First Setup

Once your repo is connected to GitHub, your daily workflow is:

```bash
# 1. Make changes to files

# 2. See what changed
git status

# 3. Stage the changes
git add .

# 4. Commit with a message
git commit -m "Describe what you changed"

# 5. Push to GitHub
git push
```

That is it. Do this every time you finish a meaningful chunk of work.

---

## 10. Pulling — Getting Changes from GitHub

If you work on multiple computers or collaborate with someone else, you need to get their changes before you start working:

```bash
git pull
```

This fetches the latest commits from GitHub and merges them into your local repo.

**Rule**: Always `git pull` before you start working. Always `git push` when you are done.

---

## 11. Viewing History

See all your commits:
```bash
git log
```

For a cleaner one-line view:
```bash
git log --oneline
```

Output:
```
a3f92c1 Fix typo in hero section
7d1bc44 Add scroll animation to sections
2ab9669 Initial commit: add README
```

Each line shows the **commit hash** (a unique ID) and the message.

---

## 12. Undoing Things — The Safety Net

### Undo changes to a file before staging
```bash
git restore filename.txt
```
This throws away all unsaved changes to that file and resets it to the last commit.

### Unstage a file (remove from staging area without losing changes)
```bash
git restore --staged filename.txt
```

### See exactly what changed in a file
```bash
git diff
```
Lines with `+` are additions. Lines with `-` are deletions.

---

## 13. Branches — Working Without Breaking Things

A branch lets you work on a new feature or experiment without touching the main code.

```bash
# Create a new branch
git branch feature-navbar

# Switch to it
git checkout feature-navbar

# Shortcut — create AND switch in one command
git checkout -b feature-navbar
```

Now you are on the `feature-navbar` branch. Any commits you make here do not affect `main`.

When you are done:
```bash
# Switch back to main
git checkout main

# Merge your branch into main
git merge feature-navbar
```

---

## 14. Cloning — Downloading an Existing Repo

To download any GitHub repository to your computer:

```bash
git clone https://github.com/username/repository-name.git
```

This creates a folder with all the files and the full history. You can then make changes and push back (if you have permission).

---

## 15. The .gitignore File

Sometimes there are files you never want Git to track — API keys, passwords, large files, auto-generated folders.

Create a file called `.gitignore` in your project root and list what to ignore:

```
# Example .gitignore

node_modules/        # Dependencies folder (huge, auto-generated)
.env                 # Environment variables (secrets!)
*.log                # Log files
.DS_Store            # Mac system files
```

Git will completely ignore anything listed here — it will never show up in `git status` or get committed.

> **Important**: Never commit API keys or passwords to GitHub. Even if you delete them later, the history still contains them. Add `.env` to `.gitignore` from day one.

---

## 16. AI + GitHub — How They Work Together

This course is about AI, so here is how Git and GitHub connect to the AI tools you are learning:

| AI Tool | How GitHub Is Involved |
|---------|----------------------|
| **GitHub Copilot** | Reads your open files and repo context to suggest code completions inline |
| **Cursor** | AI code editor that understands your entire repo — all files, not just the one open |
| **Claude Code / ChatGPT** | You paste code from your repo, get suggestions, paste back — Git tracks every change |
| **Vibe coding (Bolt, v0)** | Generated code gets pasted into files and committed — Git keeps a history of every AI-generated version |
| **Open source AI projects** | Cloned from GitHub — LLaMA, Stable Diffusion, and thousands of AI tools live on GitHub |

When you vibe code a site with AI, Git lets you:
- Save the AI-generated version as a commit
- Try changes, and roll back if they break something
- Share your project as a public GitHub repo for your portfolio

---

## Quick Reference Card

```
SETUP
git config --global user.name "Name"     Set your name
git config --global user.email "email"   Set your email

START
git init                                  Start tracking a folder
git clone <url>                           Download a repo from GitHub

DAILY WORKFLOW
git status                                See what has changed
git add .                                 Stage all changes
git add <file>                            Stage one file
git commit -m "message"                   Save a snapshot
git push                                  Send to GitHub
git pull                                  Get latest from GitHub

HISTORY
git log                                   Full commit history
git log --oneline                         Compact history
git diff                                  See exact changes

UNDO
git restore <file>                        Discard unsaved changes
git restore --staged <file>               Unstage a file

BRANCHES
git branch <name>                         Create a branch
git checkout <name>                       Switch to a branch
git checkout -b <name>                    Create and switch
git merge <name>                          Merge branch into current
```

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Repository** | A folder tracked by Git — contains all files and their full history |
| **Commit** | A saved snapshot of the project at a point in time |
| **Staging area** | Where you prepare changes before committing |
| **Branch** | A separate line of development — keeps experiments away from main code |
| **Remote** | The online copy of your repo (on GitHub) |
| **Clone** | Downloading a remote repo to your local machine |
| **Push** | Sending local commits to GitHub |
| **Pull** | Getting the latest commits from GitHub |
| **.gitignore** | A file listing what Git should never track |
| **Merge** | Combining changes from one branch into another |

---

[Back to Class 5](README.md) | [Back to Course Index](../../README.md)
