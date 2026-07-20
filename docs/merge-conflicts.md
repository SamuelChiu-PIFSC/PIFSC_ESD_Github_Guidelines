---
layout: page
title: "7. Handling Merge Conflicts"
permalink: /merge-conflicts/
nav_order: 7
---

# Merge Conflicts

## Why Do Merge Conflicts Happen?

A merge conflict is **not a crash or a bug**. It is simply a safety feature.

Git is incredibly smart at merging files automatically. If Scientist A edits the top of a script and Scientist B edits the bottom of the same script, Git will seamlessly stitch their changes together.

However, Git has one golden rule: **It will never blindly overwrite code.** A merge conflict happens when Git loses the ability to decide which line of code is the "correct" one. This occurs when two people (or two branches) modify the exact same line of the exact same file, or when one person deletes a file that another person is currently editing.

Instead of guessing which scientist's work is more important, Git pauses the merge, leaves your files completely safe, and says: *"Human, please look at this line and tell me which version to keep."*

---

## The Anatomy of a Conflict Marker

When a conflict happens, Git will pause and modify the affected file. When you open that script in RStudio, you will see highly visible conflict markers injected directly into your code:

```r
<<<<<<< HEAD
# This is the code currently on your active branch
data <- read_csv("data/raw_data_v2.csv")
=======
# This is the code on the branch you are trying to pull/merge in
data <- read_csv("data/cleaned_data.csv")
>>>>>>> origin/main
```

### How to read this:
* `<<<<<<< HEAD`: Marks the start of the changes made on your current branch.
* `=======`: The dividing line. Everything above this line is your version; everything below it is their version.
* `>>>>>>> origin/main`: Marks the end of the conflicting changes, showing the name of the incoming branch (e.g., the main branch on GitHub).

---

## How to Resolve a Merge Conflict

Resolving a conflict is just a matter of cleaning up a text file. Teach your lab mates this 4-step process:

### Step 1: Open and Locate
Open the conflicted file in RStudio. Search for `<<<<<<<` to jump straight to the problem area.

### Step 2: Talk to Your Lab Mate (The Scientific Choice)
Look at both versions of the code. Decide which line is correct for your analysis.
* Do you need your line?
* Do you need their line?
* Do you need a combination of both?

### Step 3: Clean up the Code
Manually edit the file to look exactly how you want it to look. **Crucially, delete all the Git conflict markers** (`<<<<<<<`, `=======`, and `>>>>>>>`).

Using the example above, if you decided that the cleaned data path was the correct one, you would edit the script until it looks like this:

```r
# Resolved code: We are using the cleaned dataset moving forward
data <- read_csv("data/cleaned_data.csv")

```

### Step 4: Stage and Commit the Resolution
Once the markers are gone and the file is saved, you have to tell Git that the crisis is over. In your terminal or RStudio Git pane, stage and commit the file:

```r
# 1. Stage the resolved file
git add data_loader.R

# 2. Check status to see that the conflict is cleared
git status

# 3. Finalize the merge with a commit
git commit -m "Fix: resolve merge conflict in data path, keeping cleaned data version"
```

---

## 💡 Pro-Tips for Scientists to Avoid Conflicts

While conflicts are easy to fix, preventing them saves time. Give your lab these three rules:

1. **Communicate:** If two people are working on the exact same statistical model or figure script, talk to each other before you start coding for the day.
2. **Pull Frequently:** Run `git pull` every morning before you type a single line of code. The closer your local branch is to the main branch, the less likely you are to encounter a conflict.
3. **Keep Commits Small:** Don't wait three weeks to commit a massive 500-line script change. Commit small, logical chunks of work so Git can merge them incrementally.