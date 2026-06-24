---
layout: page
title: "Cybersecurity & Git 'Do Nots'"
permalink: /cybersecurity/
nav_order: 4
---

# Cybersecurity; What *NOT* to do

## The Golden Rule of GitHub
Assume that **anything you commit to Git is permanent**, and **anything you push to GitHub can be seen by the entire world**. Even if your repository is currently private, security practices must remain strict to prevent catastrophic accidental leaks.

---

## 🚫 The "Do Nots" (Critical Safeguards)

### 1. NEVER Commit Raw Patient or Participant Data
* **The Risk:** Violating legal frameworks like HIPAA, GDPR, or institutional IRB protocols.
* **Do Not:** Stage or commit files containing names, dates of birth, medical IDs, genomic sequences linked to identities, or sensitive survey responses.
* **The Fix:** Strip all Personal Identifiable Information (PII) *before* bringing data into your project folder, or use a `.gitignore` file to ensure the data never leaves your local machine.

### 2. NEVER Commit Credentials, Passwords, or API Keys
* **The Risk:** Attackers use automated bots to scan GitHub constantly for exposed keys. If you commit a lab database password or a cloud computing API key, it will be stolen within minutes—potentially costing your lab thousands of dollars or compromising secure infrastructure.
* **Do Not:** Hardcode passwords directly into your scripts (e.g., `dbConnect(..., password = "LabPassword123")`).
* **The Fix:** Use environment variables (like an `.Renviron` file) to store credentials locally, and add that file to your `.gitignore`.

### 3. NEVER Commit Large Binary Files or Whole Databases
* **The Risk:** While not strictly a security risk, committing giant files (like a 2GB `.csv`, `.sqlite`, or `.fastq` file) will bloat the repository, slowing down everyone's `git pull` and `git push` to a crawl, and can cause GitHub to reject your pushes entirely.
* **Do Not:** Push raw imagery, massive spreadsheets, or heavy data backups.
* **The Fix:** Code should point to data stored on a secure institutional server or a dedicated data repository, not track the data inside Git.

---

## 🔒 Best Practices for Lab Security

### 👥 Account Security
* **Enforce Two-Factor Authentication (2FA):** Every member of the lab must enable 2FA on their GitHub accounts. If a lab mate's password is breached, 2FA prevents attackers from gaining access to your lab’s private code.
* **Use SSH Keys or Personal Access Tokens (PATs):** Never type your actual GitHub password into RStudio or the terminal. Use secure SSH keys or scoped PATs to authenticate your machine.

### 🛠️ Defensive Git Habits
* **Always run `git status` before you commit:** Make it a habit to check exactly what files are about to be staged. This catches accidental additions of data files or notes containing sensitive information before they are locked into history.
* **The Danger of `git add .`:** Be highly cautious with `git add .` (stage everything). It is the number one way scientists accidentally commit hidden data files or system configuration files they didn't mean to share.

---

## 🚨 What to do if someone leaks sensitive data

If someone accidentally pushes a password, API key, or sensitive dataset to GitHub, **do not just delete the file and make a new commit.** Because Git tracks history, the file will still exist in the previous commits, and anyone can look back in time to find it.

1. **Rotate the credential immediately:** If an API key or password was exposed, consider it compromised. Change the password or delete the API key immediately on the service provider's website.
2. **Notify the repository administrator:** Do not try to quietly fix it. The history needs to be rewritten using specialized tools (like `git-filter-repo` or BFG Repo-Cleaner) to completely purge the file from the repository’s entire history.