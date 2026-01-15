# Scoring Rubrics

Two rubrics: one for evaluating **workflows** (what to build seeds for) and one for evaluating **repos** (what to reverse-seed).

---

# Part 1: Workflow Scoring Rubric

Score each workflow 1-5 on six criteria. Threshold for seed development: **20+ out of 30**.

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

## Workflow Scoring Template

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

---

# Part 2: Repo Scoring Rubric

Score each GitHub repo 1-5 on ten criteria. Threshold for reverse-seeding: **35+ out of 50**.

## Quality Signals (1-5 each)

### 1. Stars / Popularity
| Score | Description |
|-------|-------------|
| 1 | <50 stars |
| 2 | 50-100 stars |
| 3 | 100-500 stars |
| 4 | 500-1000 stars |
| 5 | >1000 stars |

### 2. Maintenance Activity
| Score | Description |
|-------|-------------|
| 1 | No commits in 6+ months |
| 2 | Commits in last 6 months |
| 3 | Commits in last 3 months |
| 4 | Commits in last month |
| 5 | Active weekly commits |

### 3. Documentation Quality
| Score | Description |
|-------|-------------|
| 1 | Minimal/no README |
| 2 | Basic README only |
| 3 | README + some docs |
| 4 | Good docs, setup guides |
| 5 | Excellent docs, tutorials, API reference |

### 4. Community Health
| Score | Description |
|-------|-------------|
| 1 | No community activity |
| 2 | Some issues, rarely addressed |
| 3 | Active issues, slow response |
| 4 | Responsive maintainers |
| 5 | Thriving community (Discord, forum, etc.) |

### 5. License
| Score | Description |
|-------|-------------|
| 1 | Proprietary or no license |
| 2 | Restrictive license |
| 3 | GPL (copyleft) |
| 4 | LGPL, MPL |
| 5 | MIT, Apache, BSD (permissive) |

## Reverse-Seed-Ability (1-5 each)

### 6. Deployment Clarity
| Score | Description |
|-------|-------------|
| 1 | Complex, undocumented setup |
| 2 | Manual multi-step process |
| 3 | Documented but complex |
| 4 | Docker or simple setup |
| 5 | One-command deployment |

### 7. Configuration Surface
| Score | Description |
|-------|-------------|
| 1 | Hard-coded, no config |
| 2 | Minimal config options |
| 3 | Config files exist |
| 4 | Env vars + config files |
| 5 | Rich config + settings UI |

### 8. Customization Depth
| Score | Description |
|-------|-------------|
| 1 | No customization possible |
| 2 | Basic theming only |
| 3 | Some extensibility |
| 4 | Plugins or themes system |
| 5 | Fully extensible (API, plugins, themes) |

### 9. Dependency Simplicity
| Score | Description |
|-------|-------------|
| 1 | 5+ external services required |
| 2 | 3-4 external services |
| 3 | 1-2 external services |
| 4 | Optional external services |
| 5 | Self-contained, no dependencies |

### 10. AI Parseability
| Score | Description |
|-------|-------------|
| 1 | AI cannot understand structure |
| 2 | Poorly organized, hard to parse |
| 3 | Standard structure, some gaps |
| 4 | Clean structure, good patterns |
| 5 | Excellent structure, AI-friendly |

## Repo Scoring Template

```yaml
repo:
github_url:
category:

quality:
  stars:
  maintenance:
  documentation:
  community:
  license:
  subtotal:

reverse_seedability:
  deployment:
  config_surface:
  customization:
  dependencies:
  ai_parseability:
  subtotal:

total:
qualifies: # true if >= 35

notes:
```
