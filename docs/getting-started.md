---
layout: page
title: "Getting Started"
permalink: /getting-started/
nav_order: 2
---

# Getting Started: Account Setup & File Organization

Welcome to the team! This guide will get your environment set up and introduce you to the core folder organization strategies used across the agency. Following these patterns helps ensure your code integrates smoothly with automated workflows, prevents security conflicts, and keeps your workstation clean.

---

## 1. Creating Your GitHub Account

Before writing code, you need a centralized profile to track your contributions.

1. Go to [GitHub.com](https://github.com) and click **Sign Up**.
2. **Username Convention:** If creating a new account for work, we recommend a clean format such as `FirstnameLastname-NOAA` (e.g., `SamuelChiu-NOAA`) or your standard agency format.
3. **Email:** Use your official `.gov` email address. This ensures your code commits are automatically verified and linked to your organization profile.
4. **Security:** Enable Two-Factor Authentication (2FA) immediately via your account settings. This is mandatory for accessing our organization's repositories.

### Why Do We Setup Accounts This Way?
Using your official `.gov` email address automatically links your workstation identity to your online organization profile, ensuring proper verification. Furthermore, matching the recommended username convention presents a clean, standardized identity across our team's shared project lists, while strict 2FA implementation keeps public-facing government assets secure.

---

## 2. Setting Up Your Local Workspace

One of the biggest hurdles for beginners is lost or disorganized files. To fix this, software developers use a dedicated **Workspace root directory**.

### Step-by-Step Configuration
1. Open your file explorer and navigate to your user profile folder (e.g., `C:\Users\YourName\`).
2. Inside your **Documents** folder, create a brand-new folder named precisely **`Repositories`** (or `Development`).
3. Every time you clone a project from GitHub, make sure it lands inside this exact folder:  
   `C:\Users\YourName\Documents\Repositories\<project-name>`

### Why Do Computer Scientists Do This?
If you are used to saving files to the Desktop or scattered across randomly named folders, this setup might feel rigid. However, a standardized directory structure is a foundational engineering practice for three critical reasons:

* **Path Predictability & Automation:** Automated scripts, deployment tools, and local batch files frequently need to interact with your codebase. When everyone uses a predictable path structure (like `/Documents/Repositories/`), scripts can be shared across the entire team without needing to manually rewrite paths for every individual's machine.
* **Preventing Antivirus & Security Conflicts:** Enterprise security suites (like Trellix or Windows Defender) heavily monitor system directories, network shares, and temporary folders. Saving active code projects on a remote network share (like an SMB drive) or inside restricted system folders can cause aggressive file-locking bugs (`PermissionError 13`) that crash your code execution. Keeping repositories locally in your user workspace allows security software to scan them efficiently without breaking operations.
* **Preventing Environment Drift:** A single software project can contain hundreds of thousands of hidden configuration files, dependencies, and temporary cache directories. If these files intermingle with your personal downloads or desktop shortcuts, it becomes impossible to track changes accurately. Keeping them isolated ensures that what works on your machine will work exactly the same way when deployed to production.

---

## 3. Installing Git

To connect your local `Repositories` folder to GitHub, you need to install Git, the version control system that tracks your file changes.

### Step-by-Step Installation
1. Download the official installer from [git-scm.com](https://git-scm.com/download/win).
2. Run the `.exe` installer. You can safely accept the default settings for most options, but pay close attention to these two screens:
   * **Choosing the default editor:** Select an editor you are comfortable with (like VS Code, Notepad++, or Nano) if you want to avoid the default editor, Vim, which can be tricky for beginners.
   * **Adjusting your PATH environment:** Ensure **"Git from the command line and also from 3rd-party software"** is selected. This allows your tools (like VS Code or PowerShell) to use Git automatically.
3. Finish the installation and restart any open terminal windows.

### Verification
To verify that Git installed correctly, open a fresh terminal or PowerShell window and run:  
`git --version`

### Why Do We Choose These Installation Options?
Adjusting your PATH environment variable during installation registers Git globally with your operating system. This makes the tool accessible from any interface—whether you are working out of Command Prompt, PowerShell, or internal development tools like VS Code. Selecting a familiar default text editor also saves you from getting stuck in advanced command-line text editors like Vim during accidental terminal prompts.

---

## 4. First-Time Git Configuration

Before you start tracking files, you must tell Git who you are. This identity is attached to every piece of code you save (commit).

Run the following global username and global email config commands in your terminal, replacing the placeholder text with your actual name and official `.gov` email address.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@noaa.gov"

```

### Why Do We Configure This?
* **Accountability & Tracking:** Version control relies on knowing exactly who made what change and when. This configuration stamps your identity directly onto your work history.
* **GitHub Integration:** Using your official `.gov` email here ensures that your local work matches your online GitHub account profile, allowing GitHub to accurately link your local file saves to your cloud contributions.

---

## Next Steps
Now that your baseline environment is set up, please review our core guardrails and workflows before downloading any code:

1. Proceed to **Project Workflows** to see how data moves between the Cloud, your local Sandbox, and the Network Archive.
2. Review **Cybersecurity Boundaries & Do Nots** to understand our compliance rules regarding network shares, credentials, and large datasets.