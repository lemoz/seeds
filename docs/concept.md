# Seeds - Project Concept

## Vision

Seeds enable anyone with Claude Code or Codex to deploy a customized version of any open source project for their specific workflow in minutes, not weeks.

**The core innovation:** A reverse-seed process that can analyze any GitHub repo and extract a deployment prompt - turning the entire OSS ecosystem into a library of launchable solutions.

## Core Principles

### 1. Workflows, Not Tools
Instead of "deploy Metabase" → "I need to see which customers are about to churn"
Instead of "set up Cal.com" → "I need clients to self-schedule without back-and-forth"

### 2. Adapt, Don't Create
Claude Code excels at customization, not greenfield development. Seeds give it a working codebase to tailor, not a blank slate to fill.

### 3. Leverage, Don't Build
Millions of OSS projects already exist. We don't build software - we build the bridge to existing software.

## The Two-Way Conversion

```
GitHub Repo  ⟷  Seed Prompt
```

**Forward (Deploy):** Seed prompt + user context → Claude Code → Customized deployment

**Reverse (Extract):** GitHub repo → Reverse-seed process → Seed prompt

This bidirectional flow is the key insight. Any repo can become a seed.

## How It Works

### Reverse-Seed Process

```
1. GitHub OSS Repo
   │
   ▼
2. Analyze repo structure, dependencies, config points
   │
   ▼
3. Extract deployment instructions
   │
   ▼
4. Identify customization hooks
   │
   ▼
5. Generate seed prompt with {{PLACEHOLDERS}}
   │
   ▼
6. Seed ready for users
```

### User Flow

```
1. User has a workflow problem
   │
   ▼
2. Search/browse seeds by outcome
   │
   ▼
3. Find: "Launch [OSS Project] for your needs"
   │
   ▼
4. Provide context (profession, specifics, preferences)
   │
   ▼
5. Run seed prompt with Claude Code
   │
   ▼
6. Working customized solution
```

## What a Seed Contains

1. **Source reference** - GitHub repo URL, version/commit
2. **Deployment instructions** - How to get it running
3. **Customization map** - What can be tailored and how
4. **Context prompts** - Questions to ask the user
5. **Tailoring instructions** - How Claude Code should customize

## Target Audience

Anyone capable of running Claude Code or Codex. The seed removes:
- "What should I build?" → We match workflows to proven OSS
- "How do I describe it?" → We provide the prompt
- "Will this work?" → The OSS is already battle-tested

## Scaling Strategy

### Old Approach (Manual)
Write prompts for 1000 workflows = years of work

### New Approach (Reverse-Seed)
1. Map 50 professions × 20 workflows = 1000 workflow targets
2. Find best OSS repo for each workflow
3. Run reverse-seed process on each repo
4. 1000 seeds in weeks, not years

## Product Vision

**"Launch [Open Source Project] for Your Needs"**

A searchable catalog where users:
1. Describe their workflow/outcome
2. See matching OSS options
3. Click to get a customized deployment prompt
4. Run with Claude Code
5. Have a working solution

## Success Metrics

- 1000+ seeds published
- 50+ professions covered
- 2000+ workflows mapped
- Reverse-seed process works on 90%+ of target repos
