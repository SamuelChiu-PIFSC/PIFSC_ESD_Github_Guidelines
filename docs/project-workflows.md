---
layout: page
title: "Project Workflows"
permalink: /project-workflows/
nav_order: 3
---

```text
[Start Project] ➔ Create Repo (GitHub) ➔ Clone to RStudio
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
    [Daily Loop]                [Syncing Loop]
    Create Branch               Fetch latest main
    Code, Stage & Commit        Merge origin/main into branch
    Push to GitHub              Resolve conflicts (if any)
    Open Pull Request           
    Merge to Main
            │
            ▼
[Publish Paper] ➔ Tag Code Version for Reproducibility
```

## Phase 1: Project Initialization (Done Once per Project)

Always create your repository on GitHub first. This sets up your `.gitignore` automatically and prevents local configuration errors.

1. Go to **GitHub.com** and click the green **New repository** button.
2. **Configure your repository:**
   * **Name:** Use lowercase and hyphens (e.g., `dietary-cohort-analysis`).
   * **Visibility:** *Private* for active lab work, *Public* for open-source publication.
   * **Initialization:** Check **Add a README file** and check **Add .gitignore** (select the **R** template from the dropdown).
3. Click **Create repository**, then click the green **Code** button and copy the **HTTPS URL**.
4. Open **RStudio**, go to **File ➔ New Project ➔ Version Control ➔ Git**.
5. Paste the URL. RStudio will autofill the folder name. Choose where to save it locally and click **Create Project**.

---

## Phase 2: The Daily Driver Workflow (Done for every new analysis or plot)

Never code directly on the `main` branch. Use this isolated branch workflow instead.

### Step 1: Prep and Branch
Before starting a new chunk of work, update your local project and isolate your workspace:

```bash
# Switch to main and pull the lab's latest changes
git checkout main
git pull

# Create and switch to your new feature branch
git checkout -b yourname/add-linear-models
```

### Step 2: The Code-Commit Loop
As you write your code throughout the day, save deliberate checkpoints:

```bash
# 1. Check what files you altered
git status

# 2. Stage the specific script you want to save
git add scripts/03_linear_models.R

# 3. Commit with a clear scientific reason
git commit -m "Analysis: implement log-transformed linear regressions for primary cohort"
```

A great rule of thumb: *Commit small and commit often.* 
Whenever you change something small, give it a commit. 

### Step 3: Share and Peer Review
When your code is ready and runs without errors, push it to the cloud for the lab to review:

```bash
# Push your branch to GitHub for the first time
git push --set-upstream origin yourname/add-linear-models
```

1. Go to GitHub.com, click Compare & pull request on the yellow banner.

2. Write a brief description of your findings/code changes, assign a lab mate to review it, and click **Create pull request**.

3. Once approved, click **Merge pull request** on GitHub.

## Phase 3: Keeping Up to Date (Done when lab mates update main)

If a colleague updates a data-cleaning script or fixes a bug on the main branch while you are still working on your isolated branch, use this process to bring their updates into your workspace.

1. Save and commit any active work on your branch so your workspace is clean.
2. Run the sync commands in your terminal:

```bash
# Download the latest repository updates from GitHub
git fetch origin

# Merge the cloud's updated main branch directly into your active branch
git merge origin/main
```

### If a merge conflict occurs:
1. Open the flagged file in RStudio.
2. Look for the text conflict markers: <<<<<<< HEAD vs >>>>>>> origin/main.
3. Discuss with your lab mate, delete the markers, keep the correct code lines, and save the file.
4. Finalize the fix by running these commands in your terminal:

```bash
# Stage the resolved file
git add scripts/conflicted_file.R

# Commit the resolution to complete the merge
git commit -m "Fix: resolve merge conflict with main branch updates"
```

## Phase 4: Archiving for Publication (Done when submitting a paper)

When your manuscript is ready for submission or has been accepted, create an immutable snapshot of your code so reviewers and external researchers can perfectly reproduce your figures.

1. Make sure all your final code is successfully merged into the main branch and pulled to your local machine.
2. In the terminal, create a permanent, annotated version tag:

```bash
git tag -a v1.0-publication -m "Code base used for manuscript submission to Nature Methods 2026"
```

3. Push the tag to GitHub:

```bash
git push origin v1.0-publication
```
On GitHub, this creates a clean, downloadable .zip file of your exact code at that precise second in time, which you can link directly in the "Data and Code Availability" section of your journal paper.