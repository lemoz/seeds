# Reverse-Seed Process

How to extract the "DNA" from an OSS project and create a self-contained generative seed.

## Overview

The reverse-seed process analyzes a working open source project and extracts the essential patterns, architecture, and logic needed for Claude Code to generate a similar application from scratch.

**Important:** We're not creating instructions to clone a repo. We're extracting the DNA so Claude Code can grow fresh code.

```
OSS Project → Analyze → Extract DNA → Encode as Seed → Generative Prompt
```

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

## The Extraction Process

### Step 1: Study the Project

Clone and explore the OSS project:
- Read README and docs
- Understand the problem it solves
- Run it locally to see how it works

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
