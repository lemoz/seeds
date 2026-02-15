# Profession Mapping Methodology (WO-002)

This document defines the repeatable method used to map professions to workflows for the Seeds catalog.

## Sector Taxonomy

All professions must be assigned to exactly one sector from this canonical list:

1. Professional Services
2. Food & Hospitality
3. Health & Wellness
4. Education
5. Creative
6. Retail
7. Construction & Trades
8. Nonprofit
9. Tech

## Profession Selection Rules

1. Target exactly 50 professions for this work order.
2. Keep coverage balanced across all nine sectors.
3. Include only professions with at least five identifiable software workflows.
4. If a profession has fewer than five valid workflows, replace it with another profession in the same sector.
5. Favor professions where software addresses recurring operational pain, not theoretical edge cases.

## Workflow Discovery Rules

For each profession:

1. List the recurring jobs done daily, weekly, monthly, or quarterly.
2. Keep only workflows where software can remove bottlenecks, errors, delays, or manual rework.
3. Discard workflows that are mostly offline/manual with low software leverage.
4. Select 5-15 workflows per profession.
5. Describe each workflow with concrete operational language.

## Scoring Method

Each workflow must include:

- `complexity_score` (1-5): effort to ship a usable seed implementation.
- `seedability_score` (1-5): suitability for OSS + AI-assisted tailoring.
- `rubric_scores` aligned to `rubric/scoring.md`:
  - `pain_severity`
  - `frequency`
  - `oss_availability`
  - `ai_tailorability`
  - `standalone_value`
  - `skill_match`
  - `total`

The rubric `total` is the sum of the six rubric criteria (max 30).

## Priority Seeding Rule

The top 10 highest-scoring workflows across the full catalog are flagged:

- `priority_seed: true`

All other workflows are:

- `priority_seed: false`

Tie-break order for selecting the top 10:

1. Higher `rubric_scores.total`
2. Higher `seedability_score`
3. Higher `rubric_scores.pain_severity`
4. Higher `rubric_scores.frequency`

## File Format Contract

Each profession is stored as one YAML file in `professions/` and follows `professions/schema.yml`:

- Profession-level metadata (`id`, `name`, `sector`, `summary`, `description`, `workflow_count_estimate`, `tags`, `status`)
- `workflows` array with 5-15 items
- Every workflow includes:
  - `name`
  - `description`
  - `pain_point`
  - `frequency`
  - `complexity_score`
  - `seedability_score`
  - `rubric_scores`
  - `priority_seed`
