---
id: WO-006
title: GitHub OSS Discovery
status: you_review
priority: 1
tags:
  - github
  - discovery
  - research
created_at: 2025-01-15
goal: |
  Research and identify the best GitHub repos for the 5 pilot Marketing/Creative
  Agency workflows. For each workflow, find 2-3 candidate repos, evaluate them
  against the repo scoring rubric, and select the winner.
acceptance_criteria:
  - repos/candidates/ directory contains YAML profiles for 10-15 candidate repos
  - Each candidate has quality scores and reverse-seedability scores
  - Top repo selected for each of the 5 pilot workflows
  - Selection rationale documented for each choice
  - professions/marketing-agency/workflows.yml updated with selected repos
stop_conditions:
  - If no good OSS exists for a workflow, escalate with alternatives
  - If multiple repos score equally, escalate for human decision
  - If repo requires paid services to function, skip it
updated_at: 2026-01-22
---
# WO-006: GitHub OSS Discovery

## Objective
Create a systematic approach to finding the best GitHub repos for each workflow. This feeds the reverse-seed pipeline.

## Tasks

### Research Phase
- [ ] Search GitHub for repos matching each pilot workflow
- [ ] Check awesome-selfhosted list for candidates
- [ ] Verify each candidate meets minimum criteria (500+ stars, recent commits, permissive license)

### Evaluation Phase
- [ ] Score each candidate against repo rubric (rubric/scoring.md Part 2)
- [ ] Create YAML profile for each candidate in repos/candidates/
- [ ] Calculate totals and check against threshold (35+)

### Selection Phase
- [ ] Select winner for each workflow based on scores
- [ ] Document selection rationale
- [ ] Update professions/marketing-agency/workflows.yml with selections

## Pilot Workflows to Find Repos For

### 1. Client Feedback/Approvals (Score: 27)
**Need:** Clients review and approve creative work without email chaos
**Search terms:** "review approval" "feedback portal" "client proofing" "design review"
**Candidates to evaluate:**
- TBD (research needed)

### 2. Project/Task Tracking (Score: 26)
**Need:** Agency tracks projects, tasks, deadlines
**Search terms:** topic:project-management topic:kanban
**Candidates to evaluate:**
- Plane (makeplane/plane) - 20k+ stars, Jira alternative
- Focalboard (mattermost/focalboard) - 15k+ stars, Trello/Notion alt
- Vikunja (go-vikunja/vikunja) - 3k+ stars, Todoist alt

### 3. Client Dashboard/Portal (Score: 26)
**Need:** Clients see project status, deliverables, updates
**Search terms:** "client portal" "customer dashboard" topic:dashboard
**Candidates to evaluate:**
- TBD (research needed)

### 4. Knowledge Base (Score: 25)
**Need:** Internal wiki for SOPs, processes, documentation
**Search terms:** topic:wiki topic:knowledge-base topic:documentation
**Candidates to evaluate:**
- Outline (outline/outline) - 20k+ stars, modern wiki
- BookStack (BookStackApp/BookStack) - 12k+ stars, simple wiki
- Wiki.js (requarks/wiki) - 20k+ stars, powerful wiki

### 5. Performance Reporting (Score: 25)
**Need:** Dashboards showing marketing metrics/KPIs
**Search terms:** topic:analytics topic:dashboard "business intelligence"
**Candidates to evaluate:**
- Metabase (metabase/metabase) - 35k+ stars, SQL dashboards
- Evidence (evidence-dev/evidence) - 3k+ stars, code-based BI
- Superset (apache/superset) - 55k+ stars, full BI suite

## Repo Evaluation Criteria (from rubric/scoring.md)

### Quality (25 points max)
- Stars (1-5)
- Maintenance (1-5)
- Documentation (1-5)
- Community (1-5)
- License (1-5)

### Reverse-Seedability (25 points max)
- Deployment clarity (1-5)
- Config surface (1-5)
- Customization depth (1-5)
- Dependency simplicity (1-5)
- AI parseability (1-5)

**Threshold:** 35+ out of 50 to qualify

## Output Structure

```
repos/
└── candidates/
    ├── plane.yml
    ├── focalboard.yml
    ├── outline.yml
    ├── metabase.yml
    └── ...
```
