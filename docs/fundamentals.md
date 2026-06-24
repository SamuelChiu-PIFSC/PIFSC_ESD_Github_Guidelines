---
layout: page
title: "Git & GitHub Fundamentals"
permalink: /fundamentals/
nav_order: 3
---

# Git & GitHub Fundamentals

Welcome to the core knowledge base for version control. Think of version control as a time machine and a safety net for your research. Instead of duplicating files and creating chaotic naming systems (like `analysis_v1.R`, `analysis_v2_final.R`), a Version Control System (VCS) tracks changes to a single set of files over time, taking "snapshots" of your project whenever you tell it to.

---

## 1. Git vs. GitHub

Understanding your environment starts with distinguishing the tool on your machine from the platform on the web.

* **Git:** The software application running locally on your computer that tracks the history of your files.
* **GitHub:** An online, cloud-based hosting platform for Git repositories.

### Why Do We Separate Git and GitHub?
Git handles the tracking, while GitHub handles the sharing. To use a simple analogy: Git is like the Microsoft Word application on your laptop; GitHub is like OneDrive or SharePoint where you store, back up, and share those documents with lab mates.

---

## 2. Repositories vs. Standard Cloud Folders

Managing code requires a different infrastructure than managing standard office documents.

* **A Local Folder:** A standard directory on your operating system.
* **A Repository ("Repo"):** A project folder that has been initialized with Git, which creates a hidden `.git` ledger folder inside it.

### Why Not Use OneDrive, Google Drive, or Dropbox?
Cloud storage tools are built to sync the current state of files. If a lab mate overwrites a formula in your script, or if a sync error occurs, older code can be permanently lost or corrupted. Furthermore, automated cloud storage cannot merge simultaneous edits intelligently. 

Git allows multiple researchers to work on the exact same script at the same time, keeping a clear, chronological, and immutable audit trail. When you publish a paper, you can point reviewers to the exact repository snapshot used to generate your figures, ensuring computational reproducibility.

---

## 3. The Local File Life Cycle

Files inside an active Git repository move through three distinct local states before being saved permanently.

* **Modified:** You have changed a file on your computer, but Git hasn’t officially logged it yet.
* **Staged:** You have marked a modified file to be included in your next snapshot (putting it in the "waiting room").
* **Committed:** The snapshot of your staged files is securely saved into your local Git database.



### Why Is There a Separate Staging and Committing Step?
Staging (`git add`) is like picking out the specific items you want to pack into a box. Committing (`git commit`) is taping the box shut and labeling it. This two-step process allows you to group related changes together deliberately, rather than saving every minor typo as a separate, chaotic entry in your project's history.

---

## 4. Writing Commit Messages

Every time you commit changes, you are required to attach a short text summary.

* **Bad Messages:** `fixed code`, `updated script.R`, `working copy`
* **Good Messages:** `Fix: adjust baseline threshold to 0.05 to match Smith et al. (2022) protocol in file xyz.R`

### Why Do Commit Messages Matter?
A good commit message explains *why* a change was made, not just *what* was changed. In a research or lab context, this serves as documentation for your future self and external reviewers, explaining the scientific or programmatic rationale behind modifications weeks or months after they occurred.

---

## 5. Moving Changes: Fetch, Pull, and Push

Interacting with remote lab code requires explicit instructions to safely move file histories between your computer and the cloud.

* **Fetch vs. Pull:** `git fetch` downloads the latest history from GitHub without changing your local files so you can see what others have done. `git pull` downloads that history and immediately forces a merge into your working files.
* **Upstream Flags:** The command `git push --set-upstream` is used when pushing a newly created local branch to GitHub for the first time.

### Why Do We Structure Syncing This Way?
Using `git fetch` gives you a safe window to inspect incoming updates before altering your active environment. Regarding upstream flags, your computer must explicitly link your local branch to a corresponding tracker branch on the cloud. Once this link is established, you only need to type a simple `git push` or `git pull` for the rest of that branch's lifespan.

---

## 6. Branching & Isolation

Instead of everyone editing the primary codebase, Git relies on independent lines of development called branches.

### Why Do We Use Branches Instead of Working on Main?
Working directly on the main branch is like multiple scientists editing the master copy of a lab protocol simultaneously on the exact same whiteboard. It leads to data overwrites and broken scripts. Creating a branch generates a safe, isolated copy of the code where you can test a new package or experiment with a statistical model without disrupting the working code your lab mates are actively relying on.

---

## 7. Code Reviews & Pull Requests (PRs)

When your branch work is complete, it undergoes an official integration phase on GitHub known as a Pull Request.

### Why Are Pull Requests Essential for Labs?
A Pull Request acts as a structured "peer-review" system for our lab's code. It generates a dedicated web page showing your teammates exactly which lines of code were modified. They can comment on specific lines, suggest structural improvements, and run automated tests before the code is merged into the master branch, maintaining high software and scientific standards.

---

## 8. Handling Merge Conflicts

Occasionally, automated syncing pauses when two distinct histories collide on the same line of code.

### Why Do Merge Conflicts Happen and How Do We Fix Them?
A merge conflict happens when two people edit the exact same line of the exact same file on different branches, leaving Git unable to know which version to keep. Git will pause the process and highlight the conflict markers directly inside your file. To resolve it safely without losing work, you simply open the file, evaluate both code options, delete the version you do not want along with Git's temporary tracking markers, and make a clean commit.

To prevent your isolated branch from falling too far behind while others make updates, you should periodically run `git merge main` within your branch to safely integrate their changes incrementally.

---

## 9. File Exclusion with .gitignore

Not every file generated on your local workstation should be tracked or shared publicly on the web.

* **The `.gitignore` File:** A plain text file located at the root of your repository where you explicitly list the names of files, extensions, or folders that Git should completely ignore.

### Why Must We Explicitly Exclude Certain Files?
Git is engineered for tracking text files (scripts and code), not data assets or secure metadata. There are specific categories of files that must never be committed to Git:
* **Large Raw Datasets:** Storing multi-gigabyte files (like raw sequencing data or high-resolution imagery) bloats the repository size, slows down execution speeds, and causes synchronization errors.
* **Temporary System and Cache Files:** Files automatically created by your computer (like Windows `.Thumbs.db` or Python `__pycache__`) cause unnecessary clutter.
* **Credentials and Secrets:** Hardcoding passwords, API tokens, or cloud access keys creates severe security vulnerabilities if pushed to cloud spaces.

---

## Next Steps
Now that you understand our baseline environmental definitions, please review our core guardrails and workflows before cloning any repositories:

1. Proceed to **[Project Workflows]({{ site.baseurl }}/workflows/)** to see how data moves between the Cloud, your local Sandbox, and the Network Archive.
2. Review **[Cybersecurity Boundaries & Do Nots]({{ site.baseurl }}/cybersecurity/)** to understand our compliance rules regarding network shares, credentials, and large datasets.