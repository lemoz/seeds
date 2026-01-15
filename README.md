# Seeds

Self-contained generative prompts that produce deployed, customized software.

## What Is a Seed?

A **Seed** is a prompt containing the "DNA" of a software application. When run with Claude Code:

1. It generates all project files from scratch
2. Customizes them for your specific needs
3. Asks where you want to deploy (local, Railway, Fly.io, etc.)
4. Deploys and gives you a working URL

**No network needed to build. No repos to clone. The seed IS the code.**

## How It Works

```
Run seed with Claude Code
         ↓
Answer context questions (company name, colors, etc.)
         ↓
Claude Code generates entire project
         ↓
"Where do you want to deploy?"
   • Local Docker
   • Railway
   • Fly.io
   • Render
         ↓
Claude Code deploys
         ↓
You get a URL to working software
```

## Example

**Workflow:** "I need clients to book meetings without email back-and-forth"

**Run the scheduling seed:**
```
> Company name? Acme Agency
> Brand color? #3B82F6
> Default meeting length? 30 minutes
> Where to deploy? Railway
```

**Result:** `https://acme-scheduling.up.railway.app` - branded booking page, live in 20 minutes.

## Creating Seeds (Reverse-Seed Process)

Seeds are created by analyzing existing OSS projects and extracting their "DNA":

1. Study an OSS project (e.g., Cal.com for scheduling)
2. Extract essential patterns, schemas, architecture
3. Encode into a generative prompt
4. Add customization hooks and deployment configs

The seed doesn't clone the original - it captures the *essence* so Claude Code can generate similar software fresh.

## Structure

```
seeds/
├── seeds/              # Published seeds by workflow
│   ├── templates/      # Seed format templates
│   └── examples/       # Example seeds
├── professions/        # Profession → workflow mappings
├── repos/              # OSS repos analyzed for DNA extraction
├── rubric/             # Scoring criteria
├── docs/               # Documentation
└── work_orders/        # Project tracking
```

## Goals

- 1000+ seeds covering common workflows
- 50+ professions mapped
- 5+ deployment targets (local, Railway, Fly.io, Render, cloud)
- < 30 min from seed to running URL
- > 90% success rate

## Docs

- [Concept](docs/concept.md) - Full vision and how seeds work
- [Reverse-Seed Process](docs/reverse-seed-process.md) - How to create seeds from OSS
- [Scoring Rubric](rubric/scoring.md) - How we evaluate workflows and repos
