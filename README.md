# UF Neurology Resident Handbook

## Table of Contents

- [Project Overview](#project-overview)
- [How This Site Is Built with Quarto](#how-this-site-is-built-with-quarto)
- [Core Files](#core-files)
- [Repository Structure](#repository-structure)
- [Local Development and Editing](#local-development-and-editing)
- [How This Site Is Hosted on GitHub](#how-this-site-is-hosted-on-github)
- [Recommended Workflow](#recommended-workflow)
- [Contributing](#contributing)

## Project Overview

This repository contains the source code for the UF Neurology Resident Handbook, a practical living document written by and for neurology residents. The handbook gathers high-yield clinical notes, admission orders, consult templates (often called “dot phrases”), grading scales, and management algorithms, organized by subspecialty. The goal is to provide a single, easily searchable, mobile-friendly reference that residents can use on the wards or in clinic.

The site is generated entirely from plain-text Markdown files using Quarto, an open-source publishing system designed for scientific and technical content. Because the source is simple Markdown, any resident can open a file, make an edit, and see the change appear on the live website after a short publishing cycle.

## How This Site Is Built with Quarto

Quarto is the engine that turns a collection of Markdown files into a polished website. Each clinical page is a `.qmd` file—ordinary Markdown with an optional YAML header at the top that supplies the page title and category. When you run the Quarto render command, the system reads every `.qmd` file, converts the Markdown into HTML, applies the site-wide theme and custom styles, builds the navigation bar from the project configuration, and writes the finished pages into an output folder.

The project is configured as a “website” rather than a book or a single document. This means Quarto automatically creates a multi-page site with a shared navigation bar, a search box, and consistent styling across all pages. Features such as tabsets (used for the Modified Fisher scale examples), callout boxes, tables, and fenced code blocks for copy-paste notes are all native Quarto constructs and require no extra plugins.

Because Quarto produces static HTML, the resulting site can be hosted anywhere. We chose GitHub Pages because it is free, version-controlled, and tightly integrated with the same repository that holds the source files.

## Core Files

| File / Folder       | Purpose |
|---------------------|---------|
| `_quarto.yml`       | Project configuration (navbar, theme, output directory, search, repo links) |
| `styles.css`        | Custom CSS that gives the site its distinctive look (hero boxes, code blocks, mobile tweaks) |
| `index.qmd`         | Homepage |
| `about.qmd`         | About page |
| `qmd/`              | All clinical content organized by topic |
| `images/`           | Figures, CT examples, etc. |
| `docs/`             | Generated website (this is what GitHub Pages serves) |

## Repository Structure

The repository is deliberately simple. Source content lives in the root and in the `qmd/` directory; images are kept in `images/`. The `_quarto.yml` file controls site-wide settings such as the navigation menus and the output directory. After rendering, Quarto places every finished HTML page, CSS file, and asset into the `docs/` folder. That folder is the only thing GitHub Pages needs to serve the public website. Everything inside `docs/` is generated and should never be edited by hand—any manual change will be overwritten on the next render.

## Local Development and Editing

To work on the handbook you need Quarto and Git installed on your computer. After cloning the repository, the most useful command is `quarto preview`. This starts a local web server and watches every source file; as soon as you save a change, the browser refreshes automatically. You can therefore write a new section, adjust a table, or tweak the CSS and see the result instantly without publishing anything.

When you are satisfied with the changes, run `quarto render`. This rebuilds the entire site into the `docs/` folder. You then commit both the source files and the newly generated `docs/` folder and push to the main branch. The push is what triggers the public update.

Editing a clinical page is straightforward. Open the corresponding `.qmd` file, change the text, add or replace images by placing them in the `images/` folder and referencing them with ordinary Markdown image syntax, and save. Tabsets, callouts, and code blocks follow standard Quarto conventions and are documented in the Quarto documentation if you need a reminder of the exact syntax.

## How This Site Is Hosted on GitHub

The handbook is published using GitHub Pages, GitHub’s free static-site hosting service. The key design decision that makes this work cleanly is the line in `_quarto.yml` that sets `output-dir: docs`. This tells Quarto to place every generated HTML file, stylesheet, and image into a folder named `docs` at the root of the repository.

GitHub Pages is then configured (under Settings → Pages) to treat the `/docs` folder on the `main` branch as the source of the public website. When a visitor goes to the site, GitHub simply serves the static files that live inside that folder. There is no server-side processing, no database, and no continuous-integration runner required beyond the ordinary `git push`.

The publishing workflow is therefore very direct. A resident edits one or more `.qmd` files, runs `quarto render` locally, commits both the source changes and the freshly generated contents of the `docs/` folder, and pushes to `main`. Within one to two minutes GitHub detects the new commit, updates the Pages site, and the revised handbook becomes publicly visible. Because the source files and the published HTML live in the same repository, every page on the live site can offer “Edit this page,” “View source,” and “Report an issue” buttons that link straight back to the corresponding file on GitHub.

This arrangement has several practical advantages. Version control is automatic: every change to the handbook is recorded in the Git history. Collaboration is simple: anyone with write access can improve a page and the result appears for everyone after a single push. Rollback is equally easy—if a change introduces an error, the previous commit can be restored and the site reverts immediately. Finally, because the output is pure static HTML, the site is fast, secure, and requires essentially zero ongoing maintenance.

## Recommended Workflow

The cleanest way to maintain the handbook is to treat one computer as the single place where the final version is prepared and pushed. All editing, Quarto rendering, and testing happen locally on that computer. When the changes are ready, they are pushed from the computer to the `main` branch on GitHub, and the live website updates automatically.

Other residents who want to contribute open a Pull Request instead of pushing directly to `main`. The maintainer reviews the proposed changes, can pull the branch to the local computer for testing if needed, makes any final adjustments, and then merges the pull request. After the merge, a simple `git pull` on the local computer brings everything back into perfect sync.

This workflow keeps the repository clean, avoids almost all merge conflicts, and ensures that the live site only updates when the maintainer has verified the result. It also gives the maintainer full control over quality while still allowing the whole residency to contribute safely through pull requests.

## Contributing

Anyone with access to the repository can improve the handbook. The preferred method is to open a Pull Request with the proposed changes. The maintainer will review the contribution, make any necessary edits on the local computer, and merge it. Small factual corrections or typo fixes can also be submitted as pull requests.

The design philosophy remains deliberate simplicity: plain Markdown, a single configuration file, one custom stylesheet, and a static hosting model. This keeps the barrier to contribution low while still producing a professional, searchable, and mobile-friendly resource for the residency.
