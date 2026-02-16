---
id: WO-005
title: Reverse-Seed Process
status: you_review
priority: 1
tags:
  - core
  - reverse-seed
  - process
created_at: 2025-01-15
goal: |
  Create the reverse-seed extraction process that analyzes OSS projects and
  extracts their "DNA" into self-contained generative seeds. The seed must
  be able to generate similar software from scratch WITHOUT network access
  or cloning any repos. Test by creating a scheduling seed from Cal.com patterns.
acceptance_criteria:
  - docs/reverse-seed-process.md documents the full extraction methodology
  - A working scheduling seed exists at seeds/examples/scheduling-seed.md
  - The seed can generate a complete project structure when run
  - The seed includes multi-target deployment (local Docker, Railway, Fly.io)
  - The seed does NOT require cloning Cal.com or any external repo
  - Test: Running the seed with Claude Code produces working files
stop_conditions:
  - If unclear what "DNA" to extract vs copy, escalate with examples
  - If generated seed is too large (>500 lines), escalate to discuss compression
  - If certain patterns can't be generalized, document as limitation
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
