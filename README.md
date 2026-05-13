---
title: root README.md file
last updated: 5/13/2026
tags: documentation, update, taxonomy, rules, project
summary: brief description of organization knowledge hub along with repository rules
---

# knowledge-hub

Repository to team information. Also serves as a testbed for Github Organization features, allowing the team to hit the ground running with the class project.

## Taxonomy
- personal-research/
  - ryan/
  - rayen/
  - nicolas/
  - austin/
  - apurva/
- unnamed-project/
  - front-end/
  - back-end/
  - README.md
- AGENTS.md
- README.md
- CODEOWNERS

## Update Model
- Collected personal research information must go in one of subfolders within 'personal-research'.
  - The contents of these subfolders is not structured.
- Project folders must be located at repository root.
- Project folders must contain a 'README.md' file for general project information.
- Project folders must contain a subfolder for every large submodule.
  - A large submodule is defined as a component, technical or otherwise, that requires its own unique set of documentation material (e.g. 'front-end').
- Project documentation must be located within the appropriate subfolder.
  - Documentation may only be composed of '.gitkeep', '.md' and '.svg' files.
- Pull Requests adhere to the following requirements before approval:
  - Code owner review is required.
  - CI checks must be passed.
- All files and folders beside 'README.md', 'AGENTS.md', '.gitkeep' and 'CODEOWNERS' must adhere to kebab-case.
- All '.md' files must have a YAML frontmatter with the following entries (e.g. 'README.md'):
  - title
  - last-updated
  - tags
  - summary


## Branching Rules
- The use of feature branches is mandatory. 
- All branches must come have main as the origin. 

## Ownership Model
- Ownership is strict; every team member may only make changes to their assigned files or have a code owner review their changes.
