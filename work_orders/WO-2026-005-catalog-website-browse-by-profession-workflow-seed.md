---
id: WO-2026-005
title: Catalog Website — Browse by Profession, Workflow, Seed
goal: Build the browsable catalog website — the front door to Seeds. Static site generated from YAML/markdown data. Users browse by profession → workflow → seed → copy and run.
context: []
acceptance_criteria:
  - Static site at seeds.dandelion.industries (or localhost for now)
  - Homepage with search and profession grid
  - Profession page listing all workflows with scores
  - Workflow page showing available seeds with metadata
  - "Seed detail page with: description, requirements, copy-to-clipboard, deployment targets"
  - Dark theme, clean design, mobile-friendly
  - Site generated programmatically from professions/ and seeds/ YAML/markdown files
  - Build script that regenerates site when data changes
  - No backend — pure static HTML/CSS/JS
non_goals: []
stop_conditions:
  - If profession data from WO-002 is incomplete, build with available data and placeholder pages
  - Keep it simple — no frameworks unless justified. Plain HTML + CSS + vanilla JS preferred.
priority: 1
tags:
  - website
  - catalog
  - frontend
estimate_hours: 12
status: ready
created_at: 2026-02-15
updated_at: 2026-02-15
depends_on:
  - WO-002
era: v0
---
## Notes
- 
