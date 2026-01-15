# Seeds - Project Concept

## Vision

Seeds are **self-contained generative prompts** that, when run with Claude Code, produce a fully working, deployed application customized for the user's needs.

**No network required to build. No external repos to clone. The seed IS the code.**

## Core Principles

### 1. Self-Contained
The seed contains everything needed to generate the project. It doesn't link to external repos - it encodes the essential "DNA" of the software that Claude Code unpacks into working files.

### 2. End-to-End
A seed takes the user from nothing to a running URL:
```
Seed Prompt → Generate Code → Choose Deployment → Running Software
```

### 3. Multi-Target Deployment
Every seed asks: "Where do you want to deploy?"
- Local (Docker on your machine)
- Railway
- Fly.io
- Render
- DigitalOcean
- AWS/GCP

### 4. Workflows, Not Tools
Seeds are organized by outcome:
- "I need clients to self-schedule" → Scheduling seed
- "I need to track projects" → Project management seed
- "I need a client portal" → Portal seed

## What a Seed Contains

1. **Project DNA**
   - Essential code patterns and structure
   - Key files encoded in the prompt
   - Database schemas
   - API structures

2. **Customization Hooks**
   - {{COMPANY_NAME}}, {{BRAND_COLOR}}, etc.
   - User answers questions, values get injected

3. **Multi-Target Deployment Configs**
   - docker-compose.yml (local)
   - railway.json (Railway)
   - fly.toml (Fly.io)
   - Dockerfile (universal)

4. **Deployment Logic**
   - Prompts user for target
   - Handles deployment to chosen platform
   - Returns working URL

## How Seeds Work

### User Flow
```
1. User finds seed for their workflow
   ↓
2. User runs seed with Claude Code
   ↓
3. Seed asks context questions
   - Company name?
   - Brand colors?
   - etc.
   ↓
4. Claude Code generates all project files
   ↓
5. Seed asks: "Where do you want to deploy?"
   - Local Docker
   - Railway
   - Fly.io
   - etc.
   ↓
6. Claude Code deploys to chosen target
   ↓
7. User gets URL to running software
```

### What Happens Inside
```
Seed Prompt (contains project DNA)
    ↓
Claude Code "unpacks" the DNA
    ↓
Generates: /src, /config, /docker, etc.
    ↓
Injects {{PLACEHOLDERS}} with user values
    ↓
Generates deployment config for chosen target
    ↓
Deploys (local docker-compose up OR railway up OR fly deploy)
    ↓
Returns URL
```

## The Reverse-Seed Process

To create a seed, we analyze an existing OSS project and extract its DNA:

### Input
- A working open source project (e.g., Cal.com)

### Extraction
1. **Identify core architecture** - What makes this app work?
2. **Extract essential patterns** - Key code structures, schemas, APIs
3. **Map configuration surface** - What can be customized?
4. **Capture deployment requirements** - What services does it need?
5. **Encode into generative prompt** - Compress into seed format

### Output
A self-contained seed that can regenerate a similar app without needing the original repo.

**Important:** The seed doesn't recreate the exact OSS project. It captures the *essence* and *patterns* that let Claude Code generate a similar solution. This avoids licensing issues and creates truly bespoke software.

## Seed vs. Original Repo

| Aspect | Original Repo | Seed Output |
|--------|---------------|-------------|
| Source | Clone from GitHub | Generated from DNA |
| Dependencies | Exact versions | Fresh, current |
| Customization | Fork and modify | Built-in from start |
| Deployment | Figure it out | Choose target, done |
| Network | Required | Only for deployment |
| Licensing | Bound to original | Fresh code |

## Target Audience

Anyone with Claude Code or Codex who wants working software for their workflow without:
- Learning to code
- Understanding deployment
- Managing infrastructure
- Reading documentation

## Success Metrics

- Seeds published: 1000+
- Professions covered: 50+
- Deployment targets supported: 5+
- Time from seed to running URL: < 30 minutes
- Success rate (seed → working deployment): > 90%
