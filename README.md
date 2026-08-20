# UF Neurology Resident Handbook

## Table of Contents

- [Project Overview](#project-overview)
- [How This Site Is Built](#how-this-site-is-built)
- [How to Contribute](#how-to-contribute)
- [Repository Structure](#repository-structure)
- [Core Files](#core-files)
- [Closing Note](#closing-note)

## Project Overview

This repository contains the source code for the UF Neurology Resident Handbook, a practical living document written by and for neurology residents.  

It is deliberately designed as a living document. Content is expected to change as evidence updates, institutional protocols evolve, and residents contribute improvements.

## How This Site Is Built

The site is built with Quarto, a tool that turns simple text files into a clean, searchable website.

Currently the Quarto files are rendered on a computer running RStudio. Those files are then mirrored in this GitHub repository. GitHub takes the finished files and publishes them on the internet as a regular website (HTML pages).

GitHub also makes it easy for anyone to suggest improvements or corrections by opening a pull request. You make your edits on GitHub in a separate copy of the source file, then the pull request is sent to the root administrator, who will review them. If the changes look good, the root administrator merges them into the main handbook.

Luis Silva is the current root administrator. He maintains the master files on his local computer and edits them using RStudio, the environment he is most familiar with. Quarto also supports Python and Julia, so future administrators can work in the language they prefer.

Invitations for section editors have been sent. The current editorial team is listed below.

| Section                        | Editor          |
|--------------------------------|-----------------|
| **Editor in Chief**            | Dr. Wilson      |
| Neurological Examination       | TBD             |
| Vascular                       | TBD             |
| Neurocritical Care             | Dr. Maciel      |
| Epilepsy                       | TBD             |
| Neuromuscular                  | TBD             |
| Neuroimmunology                | TBD             |
| Neurotology                    | TBD             |
| Headache                       | TBD             |
| Emergencies                    | Dr. da Silva    |
| Procedures (Lumbar Puncture)   | TBD             |
| **New Sections**               |                 |
| Movement Disorders             | Dr. Almeida     |
| Sleep                          | TBD             |
| Neuro-ophthalmology            | TBD             |
| Behavioral Neurology           | TBD             |

## How to Contribute

Anyone can contribute to the handbook. To do this you only need a free GitHub account.

After creating an account, you can open any page, click the pencil icon to edit the file directly in your browser, make your changes, and then submit a pull request. The root administrator will review the suggestion and, if everything looks good, merge it into the main handbook.

Small corrections such as typos, outdated information, or broken links are especially welcome and can usually be accepted quickly.

### Contribution Workflow

```mermaid
flowchart TD
    A[Resident wants to improve a page] --> B[Creates GitHub account]
    B --> C[Edits file in browser]
    C --> D[Submits Pull Request]
    D --> E[Luis reviews PR]
    E --> F{Needs section editor?}
    F -->|Yes| G[Discusses with editor]
    F -->|No| H[Final edits on computer]
    G --> H
    H --> I[Renders with Quarto]
    I --> J[Pushes to main]
    J --> K[Website updates]
```


## Repository Structure

The repository is deliberately simple. Source pages are kept in the `qmd/` directory; images are kept in `images/`. 
The `_quarto.yml` file controls site-wide settings such as the navigation menus and the output directory. 

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


## Closing Note

Thank you for taking the time to read this and for considering a contribution.
This handbook exists because residents decided it should. Every correction, every clarified note, and every new section makes it more useful for the next person on call.
Whether you fix a single typo or help build an entire new section, you are part of keeping this resource alive and accurate for the whole residency.
