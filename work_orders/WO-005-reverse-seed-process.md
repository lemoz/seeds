---
id: WO-005
title: Reverse-Seed Process
status: ready
priority: 1
tags:
  - core
  - reverse-seed
  - process
created_at: 2025-01-15
goal: "Build the first real working seed by reverse-seeding Cal.com patterns into a scheduling seed. Prove the concept: run the seed with Claude Code or Codex, answer 5 questions, get a deployed scheduling app."
acceptance_criteria:
  - seeds/scheduling/client-booking.md exists as a complete seed
  - "Seed contains: project DNA, customization hooks, multi-target deployment configs"
  - "Seed includes deployment logic for: local Docker, Railway, Fly.io"
  - Running the seed with a coding agent produces a working project structure
  - "Generated project includes: booking page, availability config, calendar integration patterns, database schema"
  - Seed is self-contained — no network needed during generation (only for deployment)
  - docs/reverse-seed-process.md updated with lessons learned from this first extraction
  - "Test report documenting: generation time, file count, deployment success/failure"
stop_conditions:
  - If the seed exceeds 500 lines, compress or split into modular sections and document the approach
  - If certain Cal.com patterns cant be generalized, document as limitations
  - If deployment to a target fails, document the failure and continue with other targets
estimate_hours: 10
updated_at: 2026-02-15
---
# WO-005: Reverse-Seed Process

## Objective

Create the process for extracting "DNA" from OSS projects into self-contained generative seeds.

**Key insight:** Seeds don't link to repos. Seeds ARE the code - encoded as a generative prompt that Claude Code unpacks.

## What Changed

Previous approach (WRONG):
- Analyze repo → Create instructions to clone and configure it
- Requires network to fetch repo
- Dependent on external repos

New approach (CORRECT):
- Analyze repo → Extract essential patterns and architecture
- Encode patterns into generative prompt
- Seed generates fresh code from scratch
- No network needed to build (only for deployment)

## Tasks

### Define Extraction Methodology
- [ ] Document what "DNA" means (patterns, schemas, architecture)
- [ ] Define what to extract vs what to leave behind
- [ ] Create extraction checklist

### Extract Scheduling DNA
- [ ] Study Cal.com architecture (we have it cloned at repos/cal.com)
- [ ] Extract database schema patterns (not exact copy)
- [ ] Extract API structure patterns
- [ ] Extract availability calculation logic
- [ ] Extract booking flow patterns
- [ ] Document deployment requirements

### Create Generative Seed
- [ ] Write scheduling seed that generates fresh code
- [ ] Include full project structure
- [ ] Include Prisma schema
- [ ] Include API routes
- [ ] Include core components
- [ ] Add multi-target deployment configs

### Test End-to-End
- [ ] Run seed with Claude Code in empty directory
- [ ] Verify all files generated correctly
- [ ] Test local Docker deployment
- [ ] Verify generated code works

## What DNA Extraction Means

We're NOT copying code. We're extracting:

| Extract | Don't Copy |
|---------|------------|
| Data model patterns | Exact table structures |
| API endpoint structure | Implementation details |
| Core algorithms (availability calc) | UI components verbatim |
| Architecture decisions | Vendor-specific code |
| Deployment requirements | Exact config values |

**Example - Database:**
- Extract: "Need User, EventType, Booking, Availability tables with these relationships"
- Don't copy: Cal.com's exact Prisma schema with their field names

**Example - Availability:**
- Extract: "Calculate open slots by subtracting bookings from availability windows"
- Don't copy: Cal.com's exact implementation

## Seed Output Format

The scheduling seed should:

1. **Ask context questions**
   - Company name, brand color, timezone, working hours

2. **Generate complete project**
   - Next.js 14 app with App Router
   - Prisma schema with PostgreSQL
   - API routes for availability, bookings, event types
   - Basic UI components
   - Docker, Railway, Fly.io configs

3. **Offer deployment choice**
   - Local Docker
   - Railway
   - Fly.io
   - Other (ask for platform)

4. **Deploy and return URL**

## Success Criteria

- [ ] Seed generates working scheduling app without network
- [ ] Generated code is clean, not copied
- [ ] Multi-target deployment works
- [ ] End-to-end test passes (seed → running URL)
