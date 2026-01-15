---
# Unique seed id (kebab-case).
id: seed-id
# Human-friendly seed name.
name: Seed Name
# Source repo reference for the seed.
source:
  # GitHub repo URL used as the base.
  repo: https://github.com/org/repo
  # Release tag or version string.
  version: v1.2.3
  # Commit SHA for the source used.
  commit: abc1234
# Workflow id this seed supports.
workflow: workflow-id
# Profession id this seed targets.
profession: profession-id
# Outcome statement for the user.
outcome: "What the user will have when done"
# Short OSS tool name.
oss_tool: tool-name
# Deployment method: docker | railway | vps | local.
deployment: docker
# Seed lifecycle status: draft | active | deprecated.
status: draft
---

# [Seed Name]

## The Outcome
[Describe the concrete result the user will have when finished.]

## Before You Start
- [ ] Prerequisite 1
- [ ] Prerequisite 2

## Your Context
Answer these to customize the seed. Use placeholders like {{COMPANY_NAME}}.

- What is your company name? -> {{COMPANY_NAME}}
- What services do you offer? -> {{SERVICES}}

## The Prompt

---
[The actual mega-prompt for Claude Code goes here.]
---

## Expected Result
[Describe what should be visible or working when done. Add screenshots if useful.]

## Customization Ideas
[Common add-ons users request after the first deploy.]
