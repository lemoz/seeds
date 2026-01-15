---
id: WO-006
title: GitHub OSS Discovery
status: ready
priority: 1
tags: [github, discovery, research]
created_at: 2025-01-15
---

# WO-006: GitHub OSS Discovery

## Objective
Create a systematic approach to finding the best GitHub repos for each workflow. This feeds the reverse-seed pipeline.

## Tasks

### Search Strategy
- [ ] Document GitHub search techniques
- [ ] Create search query templates per workflow type
- [ ] Identify alternative discovery sources (awesome lists, alternatives.to, etc.)
- [ ] Build workflow → search query mapping

### Evaluation Process
- [ ] Apply repo scoring rubric
- [ ] Create quick-filter checklist (before deep evaluation)
- [ ] Document red flags to skip repos
- [ ] Establish minimum viable repo criteria

### Discovery for Pilot
- [ ] Find 3 candidate repos for each of the 5 pilot workflows
- [ ] Score each candidate
- [ ] Select winner for each workflow
- [ ] Document selection rationale

### Tooling (Optional)
- [ ] Consider GitHub API automation
- [ ] Consider search result caching
- [ ] Consider repo metadata extraction scripts

## GitHub Search Strategies

### Direct Search
```
# By topic
topic:project-management stars:>500

# By description keywords
"client portal" in:description stars:>100

# By language + topic
language:typescript topic:dashboard

# Self-hosted tag
topic:self-hosted topic:crm
```

### Alternative Sources
- **Awesome Lists**: github.com/awesome-selfhosted/awesome-selfhosted
- **Alternatives.to**: Find OSS alternatives to commercial tools
- **Product Hunt**: Search for open source launches
- **Hacker News**: "Show HN" posts for OSS tools
- **Reddit**: r/selfhosted, r/opensource

### Workflow → Search Mapping

| Workflow | Search Queries |
|----------|----------------|
| Client feedback/approvals | "review approval" "feedback portal" "client proofing" |
| Project/task tracking | topic:project-management topic:kanban topic:tasks |
| Client dashboard/portal | "client portal" "customer dashboard" topic:dashboard |
| Knowledge base | topic:wiki topic:knowledge-base topic:documentation |
| Performance reporting | topic:analytics topic:dashboard "business intelligence" |

## Quick-Filter Checklist

Before deep evaluation, check:

- [ ] **Stars**: >100 minimum (ideally >500)
- [ ] **Last commit**: Within 6 months
- [ ] **License**: Permissive (MIT, Apache, BSD)
- [ ] **README**: Exists and explains what it does
- [ ] **Docker**: Has Dockerfile or docker-compose

If any fail → skip and move to next candidate.

## Red Flags (Auto-Skip)

- No commits in 12+ months (abandoned)
- No license file (legal risk)
- README is empty or just project name
- Requires paid services to function
- Written in obscure language
- No English documentation
- More issues than stars (problematic)

## Pilot Workflow Discovery

### 1. Client Feedback/Approvals (Score: 27)

| Candidate | GitHub | Stars | Notes |
|-----------|--------|-------|-------|
| TBD | | | |
| TBD | | | |
| TBD | | | |

### 2. Project/Task Tracking (Score: 26)

| Candidate | GitHub | Stars | Notes |
|-----------|--------|-------|-------|
| Plane | makeplane/plane | 20k+ | Jira alternative |
| Focalboard | mattermost/focalboard | 15k+ | Trello/Notion alt |
| Vikunja | go-vikunja/vikunja | 3k+ | Todoist alt |

### 3. Client Dashboard/Portal (Score: 26)

| Candidate | GitHub | Stars | Notes |
|-----------|--------|-------|-------|
| TBD | | | |
| TBD | | | |
| TBD | | | |

### 4. Knowledge Base (Score: 25)

| Candidate | GitHub | Stars | Notes |
|-----------|--------|-------|-------|
| Outline | outline/outline | 20k+ | Modern wiki |
| BookStack | BookStackApp/BookStack | 12k+ | Simple wiki |
| Wiki.js | requarks/wiki | 20k+ | Powerful wiki |

### 5. Performance Reporting (Score: 25)

| Candidate | GitHub | Stars | Notes |
|-----------|--------|-------|-------|
| Metabase | metabase/metabase | 35k+ | SQL dashboards |
| Evidence | evidence-dev/evidence | 3k+ | Code-based BI |
| Superset | apache/superset | 55k+ | Full BI suite |

## Acceptance Criteria

- GitHub search strategies documented
- Quick-filter checklist created
- 15 candidate repos identified (3 per pilot workflow)
- Each candidate scored against rubric
- 5 winning repos selected for reverse-seeding
