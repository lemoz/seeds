---
id: WO-2026-006
title: Quality Gates — CI Verification & Auto-Deprecation
goal: Build CI verification pipeline that tests seeds on every commit. Auto-deprecate seeds that fail generation or deployment. Quality badges for seed trust levels.
context: []
acceptance_criteria:
  - GitHub Actions workflow that validates seed format on PR
  - "Seed generation test: run seed in dry-run mode, verify file output structure"
  - "Deployment target validation: verify deployment configs are syntactically correct"
  - "Auto-deprecation: seeds that fail 3 consecutive CI runs get flagged"
  - "Trust badges: official, verified, community tiers"
  - "Scoring dashboard: generation success rate per seed"
  - docs/quality-gates.md documenting the verification process
non_goals: []
stop_conditions:
  - If dry-run seed testing requires actual LLM calls, use cached/mocked outputs for CI
  - Start with format validation only, add generation testing in a follow-up if complex
priority: 2
tags:
  - quality
  - ci
  - infrastructure
estimate_hours: 8
status: ready
created_at: 2026-02-15
updated_at: 2026-02-15
depends_on:
  - WO-005
era: v1
---
## Notes
- 
