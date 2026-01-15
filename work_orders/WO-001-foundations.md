---
id: WO-001
title: Project Foundations & Seed Format
status: ready
priority: 1
tags: [foundations, format]
created_at: 2025-01-15
goal: |
  Create the canonical seed file format, templates, and schemas that will be used
  for all seeds in the project. This includes the seed markdown template,
  profession YAML schema, workflow YAML schema, and repo profile YAML schema.
acceptance_criteria:
  - seeds/templates/seed-template.md exists with complete structure
  - professions/schema.yml defines profession YAML format
  - professions/workflows-schema.yml defines workflow YAML format
  - repos/schema.yml defines repo profile YAML format
  - One example seed exists at seeds/examples/example-seed.md
  - All schemas are valid YAML with comments explaining each field
stop_conditions:
  - If unclear on what fields a schema should have, escalate with proposed options
  - If example seed requires a real repo, use Cal.com (calcom/cal.com) as reference
---

# WO-001: Project Foundations & Seed Format

## Objective
Establish the foundational structure, define the canonical seed format, and specify what makes a repo "reverse-seedable."

## Tasks

### Seed Format
- [ ] Define seed file format (markdown structure, frontmatter schema)
- [ ] Create seed template file at seeds/templates/seed-template.md
- [ ] Include source repo reference structure (GitHub URL, version, commit)
- [ ] Define customization hooks syntax ({{PLACEHOLDERS}})
- [ ] Create example seed as reference implementation

### Schemas
- [ ] Create professions/schema.yml - profession definition format
- [ ] Create professions/workflows-schema.yml - workflow definition format
- [ ] Create repos/schema.yml - repo profile format for reverse-seeding

### Directory Structure
- [ ] Create seeds/templates/ directory
- [ ] Create seeds/examples/ directory
- [ ] Document directory conventions in README or docs

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
