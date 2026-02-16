# Profession Mapping Methodology (WO-002)

This document defines how profession workflow files are created consistently.

## Sector Model

Workflows are organized under these sectors:

- Professional Services
- Food & Hospitality
- Health & Wellness
- Education
- Creative
- Retail
- Construction & Trades
- Nonprofit
- Tech

Each profession file must set `sector` to one of the values above.

## Workflow Discovery Rules

1. Start with frequent, operations-critical workflows where software solves concrete pain.
2. Skip theoretical or low-frequency workflows that do not produce clear operational value.
3. Keep each profession between 5 and 15 workflows.
4. Use the stop condition: if a profession cannot produce 5 software-relevant workflows, replace it.

## Workflow Data Contract

Each workflow entry must include:

- `name`
- `description`
- `pain_point`
- `frequency`
- `complexity_score`
- `seedability_score`

Each workflow must also include `rubric_scores` based on `rubric/scoring.md`:

- `pain_severity`
- `frequency`
- `oss_availability`
- `ai_tailorability`
- `standalone_value`
- `skill_match`
- `total`
- `qualifies_for_seed`

## Priority Seeding Rule

The top 10 highest-scoring workflows across the catalog are flagged with:

```yaml
priority_seed: true
```

All other workflows use `priority_seed: false`.

## Validation Checklist

- 50 profession files are present (`professions/*.yml`, excluding schema templates).
- Every profession file has 5-15 workflows.
- Total workflow count across professions is at least 400.
- Exactly 10 workflows are flagged with `priority_seed: true`.
