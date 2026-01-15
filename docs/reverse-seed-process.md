# Reverse-Seed Process

How to extract a seed prompt from any GitHub repository.

## Overview

The reverse-seed process analyzes a GitHub repo and generates a deployment prompt (seed) that Claude Code can use to deploy and customize that tool for any user.

```
GitHub Repo → Analysis → Seed Prompt
```

## The Process

### Step 1: Clone & Scan

Clone the repository and identify key files:

```bash
git clone https://github.com/org/repo
cd repo
```

**Key files to find:**
- `README.md` - Purpose and basic setup
- `package.json` / `requirements.txt` / `go.mod` - Dependencies
- `docker-compose.yml` / `Dockerfile` - Container setup
- `.env.example` - Environment variables
- `/docs` - Additional documentation
- `LICENSE` - Usage terms

### Step 2: Understand Purpose

Extract from README and docs:
- What does this tool do?
- Who is the target user?
- What problem does it solve?
- What are the main features?

### Step 3: Map Deployment

Document how to get it running:

| Question | Where to Find |
|----------|---------------|
| What's the primary deployment method? | README, docker-compose |
| What prerequisites are needed? | README, docs |
| What commands start the app? | README, package.json scripts |
| What ports does it use? | docker-compose, .env.example |
| What databases/services does it need? | docker-compose, README |

### Step 4: Map Configuration

Identify all configuration surfaces:

**Environment Variables** (from `.env.example`):
```
DATABASE_URL=         # Required - database connection
SECRET_KEY=           # Required - encryption key
SMTP_HOST=            # Optional - email sending
LOGO_URL=             # Optional - branding
```

**Config Files** (list all with their purpose):
```
config/default.yml    # Main app settings
config/features.yml   # Feature flags
```

### Step 5: Identify Customization Hooks

What can users change to make it their own?

| Category | Examples |
|----------|----------|
| Branding | Logo, colors, company name, favicon |
| Features | Enable/disable modules, feature flags |
| Fields | Custom properties, form fields |
| Integrations | API keys, webhooks, SSO |
| Workflows | Automation rules, notifications |

### Step 6: Generate Seed Prompt

Combine everything into a seed file:

```markdown
---
id: tool-name-seed
name: Tool Name for [Workflow]
source:
  repo: github.com/org/repo
  version: v1.0.0
workflow: the-workflow-slug
outcome: "What the user gets when done"
---

# Tool Name for [Workflow]

## The Outcome
[Clear description of end result]

## Before You Start
- [ ] Docker installed
- [ ] Domain name ready (optional)
- [ ] SMTP credentials (optional)

## Your Context
Answer these to customize:

- Company name? → {{COMPANY_NAME}}
- Primary color? → {{PRIMARY_COLOR}}
- Admin email? → {{ADMIN_EMAIL}}

## The Prompt

---
I need you to deploy [Tool Name] for my {{COMPANY_NAME}}.

**My context:**
- Company: {{COMPANY_NAME}}
- Branding: {{PRIMARY_COLOR}}
- Admin: {{ADMIN_EMAIL}}

**Deployment:**
[Paste deployment commands from Step 3]

**Configuration:**
[Paste key env vars from Step 4, with {{PLACEHOLDERS}}]

**Customizations:**
[List customization hooks from Step 5]

Please deploy this and customize it for my needs.
---

## Expected Result
[What they should see when done]
```

## Example: Reverse-Seeding Cal.com

### Input
- Repo: https://github.com/calcom/cal.com
- Workflow: Client self-scheduling

### Analysis

**Purpose:** Open-source Calendly alternative for scheduling meetings.

**Deployment:** Docker Compose with Postgres

**Key Config:**
- `NEXT_PUBLIC_WEBAPP_URL` - App URL
- `DATABASE_URL` - Postgres connection
- `CALENDSO_ENCRYPTION_KEY` - Security
- `NEXT_PUBLIC_APP_NAME` - Branding

**Customization Hooks:**
- App name and logo
- Available booking types
- Working hours defaults
- Email templates
- Integrations (Google, Zoom, etc.)

### Output Seed

```markdown
---
id: calcom-scheduling
name: Cal.com for Client Scheduling
source:
  repo: github.com/calcom/cal.com
  version: v3.0
workflow: client-self-scheduling
outcome: "Clients book meetings on your calendar without email back-and-forth"
---

# Cal.com for Client Scheduling

## The Outcome
A branded scheduling page where clients pick available times and book directly on your calendar.

## Before You Start
- [ ] Docker and Docker Compose installed
- [ ] Domain or subdomain ready
- [ ] Google/Outlook calendar access

## Your Context
- Business name? → {{BUSINESS_NAME}}
- Scheduling page URL? → {{SCHEDULING_URL}}
- Default meeting length? → {{MEETING_LENGTH}}

## The Prompt

---
Deploy Cal.com as a self-hosted scheduling tool for {{BUSINESS_NAME}}.

Use Docker Compose. Configure:
- App name: {{BUSINESS_NAME}} Scheduling
- URL: {{SCHEDULING_URL}}
- Default meeting: {{MEETING_LENGTH}} minutes

Set up an initial booking type for "Discovery Call" and configure working hours for Monday-Friday 9am-5pm.
---
```

## Quality Checklist

Before publishing a reverse-seeded prompt:

- [ ] Deployment instructions are complete
- [ ] All required env vars documented
- [ ] Placeholders match context questions
- [ ] Tested with Claude Code successfully
- [ ] Expected result is accurate
- [ ] No hardcoded secrets or URLs
