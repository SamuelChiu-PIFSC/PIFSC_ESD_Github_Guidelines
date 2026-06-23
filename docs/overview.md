---
layout: single
title: "Overview: Git & GitHub Guide"
permalink: /overview/
---

## What is Version Control?
Think of version control as a **time machine** and a **safety net** for your research.

Traditionally, scientists track changes by duplicating files and creating chaotic naming systems (e.g., `analysis_v1.R`, `analysis_v2_final.R`, `analysis_v2_final_FOR_REAL.R`). This makes it incredibly difficult to know which file is actually the latest, what changed between versions, or how to revert to an older model if a new tweak breaks your code.

Version Control Systems (VCS) solve this by tracking changes to a single set of files over time. Instead of duplicating files, the system takes "snapshots" of your project whenever you tell it to. You can see exactly who changed what line of code, why they changed it, and seamlessly travel back in time to any previous state of your project.

---

## Conceptual Fundamentals (The "Why")

### What is the difference between Git and GitHub?
* **Git** is the actual software tool running locally on your computer that tracks the history of your files.
* **GitHub** is an online, cloud-based hosting platform for Git repositories. It allows you to share your local Git history with lab mates, collaborate on code, and back up your work.

> 💡 **Analogy:** Git is like the Microsoft Word application on your laptop; GitHub is like OneDrive or SharePoint where you store and share those Word documents.

### Why should a scientist use Git instead of cloud storage like OneDrive, Google Drive, or Dropbox?
Cloud storage tools are built to sync the current state of files. If a lab mate overwrites a formula in your script, or if a sync error occurs, older code can be permanently lost or corrupted. Furthermore, cloud storage cannot merge simultaneous edits intelligently. 

Git allows multiple researchers to work on the exact same script at the same time, keeping a clear, chronological log of every single line of code added or deleted.

### What is a repository ("repo"), and how does it differ from a regular folder on your computer?
A repository (or "repo") is just a regular project folder that has been initialized with Git. This initialization creates a hidden `.git` folder inside it. This hidden folder acts as a ledger, tracking every modification, deletion, and addition made to any file within that directory.

### How does using Git contribute to the reproducibility of scientific research?
Git provides a transparent, immutable audit trail for your data analysis. When you publish a paper, you can point reviewers to the exact snapshot of the code used to generate your figures and statistics, ensuring your computational methods are fully reproducible by other labs.

---

## The Core Git Workflow (The "How")

### What are the three local states of a file in Git?
* **Modified:** You have changed a file on your computer, but Git hasn't officially logged the changes into its history yet.
* **Staged:** You have marked a modified file to be included in your next snapshot. It is in the "waiting room."
* **Committed:** The snapshot of your staged files is securely saved into your local Git database.

[Image of Git file states lifecycle]

### What is the difference between staging a file and committing a file?
Staging (`git add`) is like picking out the specific items you want to pack into a box. Committing (`git commit`) is taping the box shut and labeling it. This two-step process allows you to group related changes together rather than saving every single minor typo as a separate entry in your project's history.

### What makes a "good" commit message in a research or lab context?
A good commit message explains **why** a change was made, not just what was changed.
* **Bad:** `fixed code` or `updated script.R`
* **Good:** `Fix: adjust baseline threshold to 0.05 to match Smith et al. (2022) protocol in file xyz.R`

### What is the difference between `git fetch` and `git pull`?
* `git fetch` downloads the latest history from GitHub to your computer, but it does not change any of your local files. It just lets you see what your lab mates have been up to.
* `git pull` downloads the latest history and immediately merges it into your local working files. It is the equivalent of running `git fetch` followed by `git merge`.

### What does `git push --set-upstream` actually do, and why do we only need to run it once per branch?
The first time you create a new branch locally and want to send it to GitHub, your computer needs to link your local branch to a corresponding branch on the cloud. The `--set-upstream` flag creates this link (or "tracking relationship"). Once established, you can just type `git push` or `git pull` for the rest of that branch's lifespan.

---

## Collaboration & Branching

### Why should each person work on their own branch instead of the main/master branch?
Working directly on the main branch is like multiple scientists editing the master copy of a lab protocol simultaneously on the same whiteboard. It leads to chaos. Creating a branch creates a safe, isolated copy of the code. You can test a new package or experiment with a statistical model without breaking the working code your lab mates are actively relying on.

### What is a Pull Request (PR), and how does it act as a "peer-review" system for our lab's code?
When you finish working on your branch and want to merge it back into the main lab code, you open a Pull Request on GitHub. A PR is a web page that shows your lab mates exactly what lines of code you changed. They can comment on specific lines, suggest improvements, and run tests. Once approved, the code is merged. This mirrors the scientific peer-review process.

### What is a "merge conflict," and what is the best way to resolve one without losing work?
A merge conflict happens when two people edit the exact same line of the exact same file on different branches, and Git doesn't know which version to keep. Git will pause the merge and highlight the conflict in your code. 

To resolve it, you simply open the file, look at both options, delete the code you don't want (along with Git's conflict markers), and make a new commit.

### How do you safely bring updates from the main repository into your personal branch?
While you are working on your isolated branch, your lab mates might update the main branch. To keep your branch from falling behind, you periodically switch to your branch and run `git merge main` (or pull from the remote main). This integrates their new work into your branch so you can ensure your code still works with their updates.

---

## Best Practices for Scientific Data & Code

### What is a `.gitignore` file, and why is it essential for managing data analyses?
A `.gitignore` file is a plain text file where you list the names of files or folders that Git should completely ignore. This prevents you from accidentally uploading files that don't belong on GitHub.

### What types of files should never be committed to Git?
* **Large raw datasets:** Git is designed for text files (code), not gigabytes of raw sequencing data, high-