# Workflow Scoring Rubric

Score each workflow 1-5 on six criteria. Threshold for seed development: 20+ out of 30.

## Criteria

### 1. Pain Severity (1-5)
How much does this problem hurt?

| Score | Description |
|-------|-------------|
| 1 | Minor annoyance, workarounds exist |
| 2 | Noticeable friction, occasional complaints |
| 3 | Regular frustration, costs time weekly |
| 4 | Significant pain, costs hours/money weekly |
| 5 | Critical blocker, major revenue/time loss |

### 2. Frequency (1-5)
How often does this workflow occur?

| Score | Description |
|-------|-------------|
| 1 | Yearly or less |
| 2 | Monthly |
| 3 | Weekly |
| 4 | Multiple times per week |
| 5 | Daily or continuous |

### 3. OSS Availability (1-5)
Does good open source software exist for this?

| Score | Description |
|-------|-------------|
| 1 | Nothing exists, would need full custom build |
| 2 | Partial solutions exist, major gaps |
| 3 | Decent options exist, need significant customization |
| 4 | Good options exist, need moderate tailoring |
| 5 | Excellent OSS exists, just needs configuration |

### 4. AI Tailorability (1-5)
Can Claude Code meaningfully customize this?

| Score | Description |
|-------|-------------|
| 1 | Requires deep domain expertise AI lacks |
| 2 | Significant manual configuration required |
| 3 | AI can handle most customization with guidance |
| 4 | AI excels at this type of configuration |
| 5 | Perfect fit for AI-driven setup and customization |

### 5. Standalone Value (1-5)
Does this work without complex integrations?

| Score | Description |
|-------|-------------|
| 1 | Requires 5+ integrations to be useful |
| 2 | Requires 3-4 integrations |
| 3 | Requires 1-2 integrations |
| 4 | Optional integrations enhance but not required |
| 5 | Fully standalone, immediately useful |

### 6. Skill Match (1-5)
Can this be solved in hours with Claude Code?

| Score | Description |
|-------|-------------|
| 1 | Weeks of work, complex architecture |
| 2 | Days of work, significant complexity |
| 3 | Day of work, moderate complexity |
| 4 | Half day, straightforward |
| 5 | Few hours, well-defined scope |

## Scoring Template

```yaml
profession:
workflow:
outcome:
current_pain:
oss_candidates: []
scores:
  pain_severity:
  frequency:
  oss_availability:
  ai_tailorability:
  standalone_value:
  skill_match:
total:
qualifies: # true if >= 20
```
