---
layout: page
title: "9. Git Terminal Cheatsheet"
permalink: /cli-cheatsheet/
nav_order: 9
---

# Terminal Cheat Sheet

> 📌 **Prerequisite:** Open the **Terminal** tab in RStudio (located right next to the Console) or your system terminal. Make sure you are in your active project directory. You can type `pwd` to check your current directory location and `git status` to check the status of your workspace.

---

## 1. Add (Stage) & Commit
*Tell Git which files to track, then save a local snapshot.*

* **Stage a specific file:**
  * Command: `git add path/to/your/script.R`
  * *Note: If your terminal is already inside the same folder as the file, you only need to type the filename itself (e.g., `git add script.R`).*

* **Stage ALL modified and new files at once:**
  * Command: `git add .`
  * *⚠️ Warning: Staging all files at once via the dot operator can be risky. It makes it very easy to accidentally commit raw datasets, temporary workspace files, or cluttered logs that don't belong on GitHub.*

* **Commit your staged files with a message:**
  * Command: `git commit -m "Fix: adjust baseline threshold to 0.05 to match protocol"`

---

## 2. Push Changes
*Upload your local commits to GitHub.*

* **Standard push** (Use this if your branch already exists on GitHub):
  * Command: `git push`

* **First push of a brand new branch** (This links your local branch to the cloud):
  * Command: `git push --set-upstream origin your-branch-name`

---

## 3. Pull Changes
*Download and merge the latest changes from your lab mates on GitHub into your current active branch.*

* Command: `git pull`

---

## 4. Work on a Branch
*Isolate your work so you don't overwrite the main project code.*

* **Create and switch to a new branch:**
  * Command: `git checkout -b your-branch-name`

* **Switch back to an existing branch** (e.g., returning to `main`):
  * Command: `git checkout main`

* **List all local branches** (The branch marked with an asterisk `*` is your active workspace):
  * Command: `git branch`

---

## 5. Sync Main onto your Branch
*Bring your lab mates' newest updates from the main branch into your active personal feature branch.*

1. Make sure you are currently sitting on your personal feature branch (type `git branch` to check).
2. **Download the latest updates from GitHub** without altering your local files yet:
   * Command A: `git fetch origin`
3. **Merge the cloud's version of main** directly into your active branch:
   * Command B: `git merge origin/main`

---

## 6. The "Emergency" Commands
*Quick diagnostic tools when your workflow feels stuck.*

* **Check the current state of your repository:**
  * Command: `git status`
  * *Use this to see what branch you are currently on, which files have been modified, and what is sitting in the staging area.*

* **See a chronological log of recent commits:**
  * Command: `git log --oneline`

* **Undo a staging mistake** (If you accidentally ran `git add` on a file that should stay local):
  * Command: `git reset path/to/file.R`