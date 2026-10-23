# Unit 2 – Student Hands-On Script

## Git, GitHub & the Command Line

---

## Purpose of this hands-on

In this hands-on, you will:

- Create a GitHub account (if you do not already have one)
- Create an **empty** repository on GitHub (a remote repository)
- Create a simple local project on your computer
- Initialise Git locally, make commits, then push to GitHub
- Practise the basic workflow: **edit → diff → commit → push**

This unit focuses on publishing a local project to GitHub.
More advanced Git topics (branching, merging, conflicts) are covered later.

---

## Prerequisites

Before starting, confirm you have:

- Git installed
  Run: `git --version`
- VS Code installed
- A terminal open (Terminal on macOS, PowerShell/Terminal on Windows)
- Internet access

---

## Ground rules for today

- Go slowly and do not skip steps.
- If you get an error, stop and read it. Do not guess.
- The HTML content quality does not matter today. The goal is Git and GitHub.

---

## Part 1 — Create a GitHub account (only if you do not already have one)

### Goal

Have a GitHub account you can log into.

### Steps

1. Open GitHub in your browser:
   - [https://github.com](https://github.com)

2. Click **Sign up**
3. Enter:
   - Email address
   - Username (public)
   - Password

4. Complete the verification steps
5. Choose the **Free** plan
6. Finish setup and log in

### Checkpoint

You are logged in and can see your GitHub dashboard.

---

## Part 2 — Create an empty remote repository on GitHub

### Goal

Create a GitHub repository that is completely empty (so we can push our local project into it cleanly).

### Steps

1. In GitHub, click **+** (top right) → **New repository**
2. Repository name:
   - `unit2-git-practice`

3. Visibility:
   - **Public**

4. Important: leave the repository empty
   Do **not** add:
   - README
   - Licence
   - `.gitignore`

5. Click **Create repository**

### Checkpoint

You can see the repository page and it shows an “empty repository” setup screen.

---

## Part 3 — Command line navigation (slow and careful)

### Goal

Create a project folder and make sure everyone is working in the correct place.

### Key commands (read these before typing)

- `pwd` → shows where you are right now (Print Working Directory)
- `ls` → lists what is inside the current folder
- `cd` → changes folder (moves you into another directory)

Nothing is being saved online yet. You are only navigating your computer.

### Steps

1. Check where you are:

   ```bash
   pwd
   ```

2. See what is in this folder:

   ```bash
   ls
   ```

3. Create a new folder:

   ```bash
   mkdir unit2-git-practice
   ```

4. Move into it:

   ```bash
   cd unit2-git-practice
   ```

5. Confirm your location:

   ```bash
   pwd
   ```

### Checkpoint

- Your terminal path ends with `unit2-git-practice`
- No one has errors before moving on

---

## Part 4 — Create the project file (keep it simple)

### Goal

Create a single HTML file we can track with Git.

### Steps

1. Create the file:

   ```bash
   touch index.html
   ```

   If `touch` does not work on your system, create the file in VS Code instead (File → New File → Save as `index.html`).

2. Open the folder in VS Code:

   ```bash
   code .
   ```

3. Open `index.html` and paste the following:

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <title>Unit 2 Git Practice</title>
     </head>
     <body>
       <h1>Hello GitHub</h1>
       <p>This file will be tracked using Git.</p>
     </body>
   </html>
   ```

4. Save the file.

### Checkpoint

- You can see `index.html` in VS Code
- The file is saved (no unsaved dot in the tab)

---

## Part 5 — Initialise Git locally (what this actually means)

### Goal

Turn your folder into a Git repository.

### Explain before typing

When you run `git init`, Git creates a hidden `.git` folder.
That folder contains the project’s version history and tracking metadata.
If you delete `.git`, you remove the project’s Git history.

### Steps

1. Initialise Git:

   ```bash
   git init
   ```

2. Check the status:

   ```bash
   git status
   ```

### Checkpoint

- Git is initialised
- `git status` shows `index.html` as an untracked file (or similar)

---

## Part 6 — First commit (a commit is a snapshot)

### Goal

Create the first saved snapshot of your project.

### Explain before typing

A commit is a snapshot of your project at a point in time.
A good commit message describes the intent, not just the action.

### Steps

1. Stage the file (prepare it for the commit):

   ```bash
   git add .
   ```

2. Commit with a message:

   ```bash
   git commit -m "Initial project structure"
   ```

3. View your commit history:

   ```bash
   git log --oneline
   ```

### Checkpoint

- You can see one commit in `git log --oneline`
- `git status` shows a clean working tree

---

## Part 7 — Modify the file and commit again (show the diff)

### Goal

Practise checking changes before committing.

### Steps

1. In VS Code, edit `index.html`:
   - Change the heading text
   - Add a second paragraph underneath the first

   Example:

   ```html
   <h1>Hello GitHub (updated)</h1>
   <p>This file will be tracked using Git.</p>
   <p>This is my second commit.</p>
   ```

2. Save the file.

3. Check status:

   ```bash
   git status
   ```

4. View the exact changes:

   ```bash
   git diff
   ```

   Read the output:
   - Lines starting with `+` were added
   - Lines starting with `-` were removed

5. Stage and commit:

   ```bash
   git add .
   git commit -m "Update page content"
   ```

### Checkpoint

- `git log --oneline` shows two commits
- `git status` is clean after the commit

---

## Part 8 — Connect your local repo to GitHub (local vs remote)

### Goal

Link your local Git repository to the remote GitHub repository.

### Key idea (say it out loud)

- Local repository = your computer
- Remote repository = GitHub
- Git is the tool; GitHub is the platform
- Git is not the same thing as GitHub

### Steps

1. On GitHub, open your repository page (`unit2-git-practice`)
2. Copy the repository HTTPS URL (it ends in `.git`)
3. In your terminal (inside the project folder), add the remote:

   ```bash
   git remote add origin <PASTE_REPOSITORY_URL>
   ```

4. Verify the remote is set:

   ```bash
   git remote -v
   ```

### Checkpoint

- `git remote -v` shows `origin` with fetch and push URLs

---

## Part 9 — Push to GitHub (first upload)

### Goal

Upload your commits to GitHub.

### Steps

1. Ensure your default branch is called `main`:

   ```bash
   git branch -M main
   ```

2. Push and set upstream:

   ```bash
   git push -u origin main
   ```

3. If prompted, complete authentication.
4. Refresh your GitHub repository page in the browser.

### Checkpoint

- You can see your files on GitHub
- You can see at least two commits on GitHub

---

## Part 10 — Practise the workflow again (edit → diff → commit → push)

### Goal

Repeat the cycle to build confidence.

### Steps

1. Edit `index.html` again (small change is enough)
2. Save the file
3. Check changes:

   ```bash
   git status
   git diff
   ```

4. Stage and commit:

   ```bash
   git add .
   git commit -m "Refine page content"
   ```

5. Push:

   ```bash
   git push
   ```

### Checkpoint

- GitHub shows the latest commit and updated file content

---

## Part 11 — Verification checklist (do not skip)

Confirm all of the following:

- Your GitHub repository exists and is accessible
- The repository contains your `index.html`
- There are at least **two commits** visible on GitHub
- Your local project still works and matches what you see online

If anything does not match, stop here and ask for help.

---

## Optional extension (extra practice)

### Goal

Add a second file and repeat the full workflow.

### Steps

1. Create a new file:

   ```bash
   touch about.html
   ```

2. Add basic HTML to it (keep it simple), save it
3. Check and commit:

   ```bash
   git status
   git diff
   git add .
   git commit -m "Add about page"
   ```

4. Push:

   ```bash
   git push
   ```

### Checkpoint

`about.html` appears on GitHub.

---

## Recap

By the end of this hands-on, you should be able to:

- Explain local vs remote repositories
- Explain what a commit is (a snapshot)
- Read `git status` and `git diff` with confidence
- Publish a local project to GitHub and keep it updated