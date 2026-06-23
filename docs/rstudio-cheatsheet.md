---
layout: page
title: "RStudio Git Cheatsheet"
permalink: /rstudio-cheatsheet/
nav_order: 8
---

> 📌 **Prerequisite:** Make sure you are in the correct RStudio Project (`.Rproj`) linked to your GitHub repository. Your Git controls live in the **Git Pane** (usually located in the top-right quadrant of RStudio next to the Environment and History tabs).

---

## 1. Add (Stage) & Commit Your Changes
*Think of staging as packing a box, and committing as sealing and labeling it.*

1. Look at the **Git Pane**. You will see a list of files that have been modified, deleted, or newly created.
2. **Add (Stage):** Check the box under the **Staged** column next to the files you want to save.
3. Click the **Commit** button (with the little clock icon) at the top of the Git Pane. A new window will pop up.
4. Review your changes in the bottom half of the window (green lines are additions, red lines are deletions).
5. Type a clear, concise message in the **Commit message** box on the right.
6. Click the **Commit** button below your message. Close the success dialog box.

---

## 2. Push Changes to GitHub
*Sending your local snapshots up to the cloud so your lab mates can see them.*

1. In the same popup window (or back in the main Git Pane), look at the top-right corner.
2. Click the green **Push arrow (Up)**.
3. A dialog box will appear showing the progress. Once it says `To github.com:...`, your code is safely online. Close the window.

---

## 3. Pull Changes from GitHub
*Downloading your lab mates' latest work into your local RStudio environment.*

1. Before you start working for the day, go to the **Git Pane**.
2. Click the blue **Pull arrow (Down)**.
3. RStudio will download any new commits. If your files update automatically in your file viewer, the pull was successful.

---

## 4. Work on a Branch & Merge it
*Creating an isolated workspace so you don't break the lab's primary working code.*

### Step A: Create and switch to a new branch
1. In the Git Pane, look at the top right corner where it says `main` or `master`. Next to it, click the **New Branch** button (purple icon with two squares).
2. Type a name for your branch (e.g., `feature-plots` or `yourname-analysis`).
3. Leave *"Sync branch with remote"* checked.
4. Click **Create**. RStudio automatically switches you onto this new branch.
5. Make your changes, then Stage, Commit, and Push using Steps 1 and 2 above.

### Step B: Merge your branch back into Main
Once your branch work is complete and tested, you want to bring it back to the master copy. While you can do this locally, the safest best practice for a lab is to do this via GitHub so team members can review it:

1. Go to your repository page on **GitHub.com**.
2. You will see a yellow banner saying your branch has recent pushes. Click **Compare & pull request**.
3. Write a brief description of what you did and click **Create pull request**.
4. Once reviewed (or if you are working alone), click the green **Merge pull request** button, then click **Confirm merge**.

---

## 5. Pull from Main onto your Branch
If your lab mates updated the main branch while you were working on your isolated branch, use this to bring their updates into your branch so you don't fall behind.

Because RStudio’s Git pane doesn't have a direct "merge main into branch" button, you will use the **Terminal tab** (located right next to your Console tab at the bottom left of RStudio):

1. Save and commit any open work on your current branch first.
2. Open the **Terminal tab** in RStudio.
3. Type the following command to download the latest updates from GitHub:
   * Command A: git fetch origin
4. Type this command to pull the latest main code directly into your active branch:
   * Command B: git merge origin/main

If there are no conflicts, your branch is now perfectly up to date with the rest of the lab! (If RStudio flags a conflict, open the affected file, choose which code to keep, delete the conflict markers, and make a standard commit).