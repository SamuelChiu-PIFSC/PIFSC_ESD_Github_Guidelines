# PIFSC ESD GitHub Guidelines

This repository hosts a Jekyll-based documentation site built with the `just-the-docs` theme. It is intended to collect PIFSC-specific GitHub best practices, workflows, and reference material in a simple static site.

## What this directory contains

- `index.md` — the site homepage, currently showing the Overview content.

- `docs/` — the main documentation pages for the site.
  - `docs/getting-started.md` — a Getting Started guide placeholder.
  - `docs/overview.md` — the full project overview content (hidden from sidebar navigation).
  - `docs/cybersecurity.md` — GitHub security guidance and safe practices.
  - `docs/project-workflows.md` — recommended project workflows for repository management.
  - `docs/merge-conflicts.md` — guidance on handling merge conflicts safely.
  - `docs/noaa-requirements.md` — NOAA-specific requirements for GitHub projects.
  - `docs/cli-cheatsheet.md` — terminal-based Git cheat sheet.
  - `docs/rstudio-cheatsheet.md` — RStudio-specific Git workflow cheat sheet.
  - `docs/github-advanced.md` — advanced GitHub features like Pages and Actions.
  - `docs/category-archive.md` — a hidden archive page used for site structure or category reference.

- `_config.yml` — Jekyll site configuration and Just the Docs settings.
- `Gemfile` — Ruby gem dependencies for building the site.
- `_sass/` — custom Sass styling overrides used by the site theme.
- `_site/` — generated site output created after building locally.

## Purpose of this repository

The site is a lightweight documentation hub for NOAA GitHub usage. It is organized into a homepage plus topic pages that appear in the navigation sidebar. The current structure is designed to support:

- an introductory Getting Started guide,
- project workflow recommendations,
- security best practices,
- merge conflict handling,
- NOAA compliance requirements,
- Git cheat sheets for both the command line and RStudio,
- and an advanced GitHub features reference page.

## How to update content

Edit the Markdown files in the repository, especially the files under `docs/`. Each page uses Jekyll front matter to control page metadata, such as `title`, `permalink`, and `nav_order`.

If you want to change navigation order, update `nav_order` values in the front matter of the pages.

## Local development

From the repository root:

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open the local server, usually at `http://127.0.0.1:4000`, to preview the site.

## Building the site

The generated static site files are written to `_site/` by Jekyll. If you need to inspect the published HTML output, look in that directory after a successful build.

## Notes

- This repository is not a generic Just the Docs template anymore; it is customized for NOAA GitHub guidelines.
- The site navigation order is controlled by each page's `nav_order` front matter value.
- The homepage is served from `index.md`, while most content pages live under `docs/`.

## Disclaimer
This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an ‘as is’ basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.
