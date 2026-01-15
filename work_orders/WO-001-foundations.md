---
id: WO-001
title: Project Foundations & Seed Format
status: ready
priority: 1
tags: [foundations, format]
created_at: 2025-01-15
---

# WO-001: Project Foundations & Seed Format

## Objective
Establish the foundational structure, define the canonical seed format, and specify what makes a repo "reverse-seedable."

## Tasks

### Seed Format
- [ ] Define seed file format (markdown structure, frontmatter schema)
- [ ] Create seed template file
- [ ] Include source repo reference structure (GitHub URL, version, commit)
- [ ] Define customization hooks syntax ({{PLACEHOLDERS}})
- [ ] Create example seed as reference implementation

### Reverse-Seed Requirements
- [ ] Define what makes a repo "reverse-seedable"
- [ ] Document minimum repo requirements (README, docs, config)
- [ ] Create repo profile YAML schema
- [ ] Define extraction metadata format

### Supporting Schemas
- [ ] Define profession YAML schema
- [ ] Define workflow YAML schema
- [ ] Set up directory structure conventions

## Seed Format Spec (Draft)

```markdown
---
id: seed-id
name: Seed Name
source:
  repo: github.com/org/repo
  version: v1.2.3
  commit: abc123
workflow: client-feedback-approvals
profession: marketing-agency
outcome: "Clients can review and approve creative work without email chaos"
oss_tool: tool-name
deployment: docker | railway | vps | local
---

# [Seed Name]

## The Outcome
[What the user will have when done]

## Before You Start
- [ ] Prerequisite 1
- [ ] Prerequisite 2

## Your Context
[Questions to customize - these become {{PLACEHOLDERS}}]

- What is your company name? → {{COMPANY_NAME}}
- What services do you offer? → {{SERVICES}}

## The Prompt

---
[The actual mega-prompt for Claude Code goes here]
---

## Expected Result
[Description + optional screenshots]

## Customization Ideas
[Common add-ons users request]
```

## Reverse-Seedable Repo Criteria

A repo is reverse-seedable if it has:
1. **Clear deployment method** - Docker, npm, or documented setup
2. **Configuration surface** - Env vars, config files, or settings UI
3. **Documentation** - README explains what it does
4. **Active maintenance** - Recent commits, responsive issues
5. **Permissive license** - MIT, Apache, etc.

## Acceptance Criteria

- Seed template is documented and usable
- One complete example seed exists (from a real repo)
- Reverse-seedable criteria documented
- All schemas defined
- Directory conventions documented
