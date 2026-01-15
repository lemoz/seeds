---
id: WO-004
title: OSS Catalog & GitHub Evaluation
status: ready
priority: 1
tags: [oss, github, catalog, research]
created_at: 2025-01-15
---

# WO-004: OSS Catalog & GitHub Evaluation

## Objective
Build a curated catalog of GitHub repos suitable for reverse-seeding, with evaluation criteria and repo profiles.

## Why Priority 1

The reverse-seed approach depends on finding good repos. This workstream:
- Feeds directly into WO-003 (pilot needs repos)
- Establishes the GitHub discovery methodology
- Creates reusable evaluation criteria

## Tasks

### Evaluation Framework
- [ ] Define repo quality criteria (stars, maintenance, docs, etc.)
- [ ] Define reverse-seed-ability criteria
- [ ] Create repo evaluation scorecard
- [ ] Document GitHub search strategies

### Repo Profiling
- [ ] Create repo profile YAML template
- [ ] Document deployment method categories
- [ ] Create customization surface taxonomy

### Initial Catalog
- [ ] Research OSS options per category (see below)
- [ ] Evaluate top 3 repos per category
- [ ] Create profiles for 50+ repos
- [ ] Tag repos by workflow fit

## OSS Categories & Candidates

### Project Management
- Plane (plane.so) - Modern, Jira alternative
- Focalboard - Mattermost's Trello/Notion alternative
- Vikunja - Todoist alternative
- OpenProject - Enterprise PM
- Taiga - Agile PM

### CRM
- Twenty - Modern CRM, Salesforce alternative
- EspoCRM - Flexible CRM
- Monica - Personal CRM

### Documentation/Wiki
- Outline - Modern team wiki
- BookStack - Simple wiki
- Wiki.js - Powerful wiki
- Docmost - Notion alternative

### Dashboards/BI
- Metabase - SQL dashboards
- Superset - Apache BI tool
- Grafana - Monitoring dashboards
- Evidence - Code-based BI

### Forms/Surveys
- Formbricks - Typeform alternative
- Typebot - Conversational forms
- Heyform - Form builder

### Scheduling
- Cal.com - Calendly alternative
- Easy!Appointments - Booking system
- Rallly - Meeting polls

### File Management
- Nextcloud - Full suite
- Seafile - File sync

### Invoicing
- Invoice Ninja - Full invoicing
- Crater - Laravel invoicing
- SolidInvoice - Simple invoicing

### Signing/Documents
- Documenso - DocuSign alternative
- OpenSign - E-signatures

### Communication
- Chatwoot - Intercom alternative
- Papercups - Live chat

## Repo Evaluation Scorecard

### Quality Signals (1-5 each)
| Criterion | What to Check |
|-----------|---------------|
| Stars | >1k = 5, >500 = 4, >100 = 3, >50 = 2, <50 = 1 |
| Maintenance | Commits in last month? Last 3 months? |
| Documentation | README quality, setup guides, API docs |
| Community | Issues response time, Discord/forum activity |
| License | MIT/Apache = 5, GPL = 3, Proprietary = 1 |

### Reverse-Seed-Ability (1-5 each)
| Criterion | What to Check |
|-----------|---------------|
| Deployment clarity | Docker? One-command setup? |
| Config surface | Env vars? Config files? Settings UI? |
| Customization depth | Themes? Plugins? Code extensibility? |
| Dependency simplicity | How many external services needed? |
| Documentation | Can AI understand setup from docs? |

**Threshold:** 35+ out of 50 to include in catalog

## Repo Profile Template

```yaml
id: repo-slug
name: Display Name
github: org/repo
url: https://github.com/org/repo
website: https://tool.com
license: MIT

# Scores
quality:
  stars: 5
  maintenance: 4
  documentation: 4
  community: 3
  license: 5
  total: 21

reverse_seedability:
  deployment: 5
  config_surface: 4
  customization: 4
  dependencies: 4
  ai_parseable: 4
  total: 21

overall: 42

# Metadata
category: project-management
deployment_methods: [docker, railway, vps]
config_files: [.env, config.yml]
customization_hooks:
  - branding (logo, colors)
  - fields (custom properties)
  - workflows (automation rules)

# Workflow fit
workflows:
  - project-task-tracking
  - team-collaboration

# Notes
notes: |
  Best for teams wanting a Jira alternative.
  Strong API, good plugin ecosystem.
```

## Acceptance Criteria

- Evaluation scorecard documented
- 50+ repos profiled
- Each category has 2-3 top picks identified
- Repo profile template finalized
- Search strategies documented
