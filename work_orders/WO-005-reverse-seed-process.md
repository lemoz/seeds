---
id: WO-005
title: Reverse-Seed Process
status: ready
priority: 1
tags: [core, reverse-seed, process]
created_at: 2025-01-15
---

# WO-005: Reverse-Seed Process

## Objective
Define and build the process/tool that extracts a seed prompt from any GitHub repo. This is the core innovation of the project.

## Why Critical

Without a reliable reverse-seed process, we can't scale. This WO creates the engine that turns GitHub's OSS ecosystem into our seed library.

## Tasks

### Process Definition
- [ ] Document the reverse-seed workflow step-by-step
- [ ] Identify what information to extract from a repo
- [ ] Define the analysis checklist
- [ ] Create the output format specification

### Extraction Prompt
- [ ] Build the mega-prompt that analyzes a repo
- [ ] Include repo structure analysis
- [ ] Include dependency detection
- [ ] Include config surface mapping
- [ ] Include deployment method extraction
- [ ] Include customization hook identification

### Testing & Iteration
- [ ] Test on 3 diverse repos (simple, medium, complex)
- [ ] Document failure modes
- [ ] Refine prompt based on results
- [ ] Establish success criteria

### Documentation
- [ ] Write docs/reverse-seed-process.md
- [ ] Create example walkthrough
- [ ] Document edge cases and limitations

## Reverse-Seed Process (Draft)

### Input
- GitHub repo URL
- Target workflow/outcome context

### Steps

```
1. CLONE & SCAN
   - Clone repo (or analyze via GitHub API)
   - Identify key files: README, package.json, docker-compose, .env.example, etc.

2. UNDERSTAND PURPOSE
   - Extract: What does this tool do?
   - Extract: Who is it for?
   - Extract: What problems does it solve?

3. MAP DEPLOYMENT
   - Identify deployment method(s)
   - Document prerequisites
   - Extract setup commands
   - Note environment requirements

4. MAP CONFIGURATION
   - Find all config files
   - List environment variables
   - Identify settings surfaces
   - Document what each config controls

5. IDENTIFY CUSTOMIZATION HOOKS
   - Theming/branding options
   - Feature flags
   - Extensibility points (plugins, APIs)
   - Code modification opportunities

6. GENERATE SEED PROMPT
   - Combine all above into deployment prompt
   - Add {{PLACEHOLDERS}} for user context
   - Include customization instructions
   - Add expected outcome description
```

### Output
A complete seed file ready for publishing.

## Extraction Checklist

### Repository Analysis
- [ ] README.md content
- [ ] package.json / requirements.txt / go.mod (dependencies)
- [ ] docker-compose.yml or Dockerfile
- [ ] .env.example or config templates
- [ ] /docs folder contents
- [ ] License file

### Deployment Extraction
- [ ] Primary deployment method
- [ ] Alternative deployment options
- [ ] Required services (DB, Redis, etc.)
- [ ] Port configurations
- [ ] Volume/storage requirements

### Configuration Extraction
- [ ] All environment variables
- [ ] Config file locations
- [ ] Default values
- [ ] Required vs optional settings

### Customization Extraction
- [ ] Branding options (logo, colors, name)
- [ ] Feature toggles
- [ ] Integration points
- [ ] API availability
- [ ] Plugin/extension system

## Success Criteria

A reverse-seed is successful if:
1. The generated seed can deploy the tool via Claude Code
2. Customization placeholders are correctly identified
3. The seed works on first try 80%+ of the time
4. Time from repo URL to working seed < 30 minutes

## Test Repos

| Repo | Complexity | Why Selected |
|------|------------|--------------|
| Cal.com | Medium | Well-documented, Docker, lots of config |
| Outline | Medium | Clean structure, good docs |
| Formbricks | Simple | Straightforward setup |

## Acceptance Criteria

- Reverse-seed process documented end-to-end
- Extraction prompt created and tested
- 3 test repos successfully reverse-seeded
- Success rate documented
- Process refinements captured
