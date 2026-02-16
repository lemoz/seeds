# Reverse-Seed Process

How to extract the "DNA" from an OSS project and create a self-contained generative seed.

## Overview

The reverse-seed process analyzes a working open source project and extracts the essential patterns, architecture, and logic needed for Claude Code to generate a similar application from scratch.

**Important:** We're not creating instructions to clone a repo. We're extracting the DNA so Claude Code can grow fresh code.

```
OSS Project → Analyze → Extract DNA → Encode as Seed → Generative Prompt
```

## DNA Definition (Contract)

For this project, "DNA" means reusable product patterns that survive implementation changes:

- **Architecture DNA**: app shape, boundary lines, and service decomposition.
- **Data DNA**: entity relationships, invariants, and indexing intent.
- **API DNA**: endpoint semantics, payload contracts, and auth model.
- **Workflow DNA**: user journeys and core algorithm steps.
- **Ops DNA**: runtime dependencies and deployment requirements.

DNA explicitly excludes exact upstream code, naming, and vendor-specific internals.

## What We Extract

### 1. Core Architecture
- Application structure (monolith, microservices, etc.)
- Key directories and their purposes
- How components connect

### 2. Database Schema
- Tables/collections and relationships
- Key fields and types
- Indexes and constraints

### 3. API Structure
- Endpoints and their purposes
- Request/response shapes
- Authentication patterns

### 4. Essential Business Logic
- Core workflows (scheduling, CRUD, etc.)
- Key algorithms
- State management patterns

### 5. Configuration Surface
- What can be customized
- Environment variables
- Feature flags

### 6. Deployment Requirements
- Required services (database, cache, etc.)
- Resource needs
- Network configuration

## Extraction Checklist

Use this checklist before writing a seed:

- [ ] Source context identified (repo snapshot, docs, architecture notes)
- [ ] 3-5 core entities and relationships documented
- [ ] 3-7 critical endpoints captured with input/output intent
- [ ] Core workflow algorithm written in implementation-agnostic steps
- [ ] Customization hooks identified (branding, business rules, integrations)
- [ ] Required runtime services documented
- [ ] At least 3 deployment targets specified
- [ ] "Extract vs Don't Copy" boundaries recorded
- [ ] Known limitations recorded for patterns that do not generalize cleanly

## The Extraction Process

### Step 1: Study the Project

Use a local source snapshot whenever possible:
- Read README and docs
- Understand the problem it solves
- Run it locally to see how it works

If the local source is unavailable, continue with documented architecture patterns and record the limitation in the seed notes. Do not block seed creation.

### Step 2: Map the Architecture

Document the structure:
```
/src
  /api         → REST endpoints
  /db          → Database models
  /services    → Business logic
  /ui          → Frontend components
/config        → Configuration files
/docker        → Container setup
```

### Step 3: Extract Database Schema

Capture the data model:
```sql
-- Core entities
users (id, email, name, created_at)
bookings (id, user_id, start_time, end_time, status)
event_types (id, name, duration, user_id)
```

### Step 4: Extract API Patterns

Document key endpoints:
```
POST /api/bookings     → Create booking
GET  /api/bookings/:id → Get booking
GET  /api/availability → Check available slots
```

### Step 5: Identify Customization Hooks

What should users be able to change?
- Branding (name, colors, logo)
- Business rules (hours, duration)
- Features (notifications, integrations)

### Step 6: Document Deployment Needs

What's required to run this?
- PostgreSQL database
- Redis cache (optional)
- SMTP for emails
- File storage for uploads

### Step 7: Encode as Generative Prompt

Transform extracted knowledge into a prompt that tells Claude Code how to generate similar software:

```markdown
## The Prompt

Build a scheduling application with these characteristics:

### Architecture
- Next.js 14 app with App Router
- PostgreSQL database via Prisma
- REST API under /api

### Database Schema
Generate these models:
- User: id, email, name, timezone, created_at
- EventType: id, title, duration, userId
- Booking: id, eventTypeId, startTime, endTime, attendeeEmail, status

### API Endpoints
- POST /api/event-types - Create event type
- GET /api/availability?date=X - Get available slots
- POST /api/bookings - Create booking

### Customization
Apply these values:
- Company: {{COMPANY_NAME}}
- Brand color: {{BRAND_COLOR}}
- Timezone: {{TIMEZONE}}

### Deployment
[Deployment instructions based on chosen target]
```

## Multi-Target Deployment

Every seed must support multiple deployment options:

### Local Docker
```yaml
# docker-compose.yml
services:
  app:
    build: .
    ports: ["3000:3000"]
  db:
    image: postgres:15
```

### Railway
```json
// railway.json
{
  "build": { "builder": "DOCKERFILE" },
  "deploy": { "startCommand": "npm start" }
}
```

### Fly.io
```toml
# fly.toml
[build]
  dockerfile = "Dockerfile"

[[services]]
  internal_port = 3000
```

## Seed Output Format

The final seed should:

1. **Ask context questions** - Gather customization values
2. **Generate all code** - Full project structure
3. **Ask deployment target** - Where to deploy
4. **Deploy** - Execute deployment to chosen target
5. **Return URL** - Provide access to running app

## Quality Checklist

Before publishing a seed:

- [ ] Seed generates working code without network
- [ ] All {{PLACEHOLDERS}} are documented
- [ ] At least 3 deployment targets supported
- [ ] Tested end-to-end (seed → running URL)
- [ ] Generated code is clean and maintainable
- [ ] No hardcoded secrets or URLs
- [ ] Database migrations included
- [ ] Basic error handling in place

## Example: Scheduling Seed DNA

**Source:** Analyzed from Cal.com patterns

**Extracted DNA:**
- Next.js + Prisma + PostgreSQL stack
- User → EventType → Booking data model
- Availability calculation algorithm
- iCal/Google Calendar integration pattern
- Timezone handling approach

**Seed generates:**
- Fresh Next.js 14 project
- Custom-branded booking page
- Admin dashboard for managing events
- API for integrations
- Deployment configs for local/Railway/Fly.io

**Seed does NOT:**
- Clone Cal.com
- Copy Cal.com code
- Require Cal.com license
- Depend on external repos

## Lessons Learned (WO-005, First Extraction)

Date: February 15, 2026

1. Availability logic generalized well when described as interval math (`windows - bookings`) instead of preserving framework-specific code paths.
2. Seed size pressure is real: once a seed approaches 500 lines, split into contract-style sections (questions, DNA, file requirements, deployment logic) instead of expanding full inline code for every file.
3. Deployment patterns transfer cleanly across projects when the seed includes both config files and execution commands for each target.
4. Calendar integrations should be extracted as adapter interfaces plus stubs first; full OAuth flows are not required for an MVP seed.
5. When local upstream source is missing, documenting assumptions and limitations is better than blocking the workflow.

### First-Extraction Limitations

- OAuth provider setup (Google/Outlook) is scaffolded as an adapter pattern, not end-to-end credential flow.
- Advanced routing patterns (round-robin, pooled teams) are intentionally excluded from the first scheduling seed.
