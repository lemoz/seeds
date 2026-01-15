# Seeds

Turn any GitHub repo into a launchable, customizable solution.

## What Is a Seed?

A **Seed** is a prompt extracted from an open source repo that enables anyone with Claude Code or Codex to deploy a tailored version for their specific needs.

```
GitHub Repo  ⟷  Seed Prompt
```

**Reverse-seed:** Analyze a repo → Extract deployment prompt
**Deploy:** Seed prompt + user context → Customized solution

## The Idea

Millions of OSS projects exist. Most people don't know:
- Which one solves their problem
- How to deploy it
- How to customize it for their situation

Seeds bridge that gap. We don't build software - we build the bridge to existing software.

## Example

**Workflow:** "I need clients to approve creative work without email chaos"

**Seed:** Extracts from a review/approval OSS tool, adds customization for agency context

**Result:** User runs seed with Claude Code → Gets branded client approval portal in hours

## How It Works

1. **Map workflows** - What do people in each profession need?
2. **Find OSS** - What GitHub repos solve these workflows?
3. **Reverse-seed** - Extract deployment + customization prompts
4. **Publish** - Searchable catalog by workflow/outcome
5. **Deploy** - User runs seed, gets tailored solution

## Structure

```
.
├── seeds/              # Published seeds by profession
│   ├── templates/      # Seed templates
│   └── examples/       # Example seeds
├── professions/        # Profession -> workflow mappings
├── repos/              # GitHub repo profiles for reverse-seeding
├── rubric/             # Scoring criteria (workflows + repos)
├── docs/               # Project documentation
└── work_orders/        # Project tracking
```

## Goals

- 1000+ seeds (via reverse-seeding OSS repos)
- 50+ professions mapped
- 2000+ workflows identified
- "Launch [OSS] for your needs" catalog

## Current Focus

1. Define reverse-seed process
2. Pilot with Marketing/Creative Agency workflows
3. Build first 5 seeds from real GitHub repos

## Work Orders

- WO-001: Project Foundations & Seed Format
- WO-002: Profession Mapping Framework
- WO-003: Pilot Profession - Marketing/Creative Agency
- WO-004: OSS Catalog & Evaluation
- WO-005: Reverse-Seed Process
- WO-006: GitHub OSS Discovery

## Docs

- [Concept](docs/concept.md) - Full vision and strategy
- [Reverse-Seed Process](docs/reverse-seed-process.md) - How to extract seeds from repos
- [Workflow Rubric](rubric/scoring.md) - How we evaluate workflows
