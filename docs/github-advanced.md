---
layout: page
title: "Advanced GitHub Features"
permalink: /github-advanced/
nav_order: 9
---

## GitHub Pages
GitHub Pages lets you publish your site directly from a repository branch. For scientific projects, this is a great way to host documentation, tutorials, or lab project portals without extra server setup.

### Quick steps
1. Create a branch named `gh-pages` or use `main`.
2. Open your repository Settings > Pages.
3. Select the branch and folder to publish.
4. Commit your site files and wait for deployment.

---

## GitHub Actions
GitHub Actions allows you to automate workflows like testing, building the site, or deploying updates whenever code is pushed.

### Useful ideas for this guide
* Build the Jekyll site automatically on every push.
* Run markdown link checks.
* Deploy the generated site to GitHub Pages.

### Example workflow
Use `.github/workflows/pages.yml` as a starting point.

---

## Why it matters
Automating builds and deployment saves time, prevents human error, and keeps your documentation up to date with every code change.
