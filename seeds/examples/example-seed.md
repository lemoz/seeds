---
id: calcom-agency-scheduling
name: Cal.com Agency Scheduling
source:
  repo: https://github.com/calcom/cal.com
  version: main
  commit: "replace-with-commit-sha"
workflow: client-scheduling
profession: marketing-agency
outcome: "Clients can book branded discovery calls without back-and-forth."
oss_tool: calcom
deployment: docker
status: draft
---

# Cal.com Agency Scheduling

## The Outcome
A branded scheduling portal where prospects can book discovery calls, with team routing and time-zone handling already configured.

## Before You Start
- [ ] Confirm where you want to deploy (local Docker, VPS, or Railway).
- [ ] Gather your company logo, primary color, and preferred time zone.
- [ ] List the team members who will accept meetings.

## Your Context
Answer these to customize the seed. Use placeholders like {{COMPANY_NAME}}.

- What is your company name? -> {{COMPANY_NAME}}
- What is your primary brand color (hex)? -> {{BRAND_COLOR}}
- What time zone should scheduling default to? -> {{DEFAULT_TIMEZONE}}
- What is the default meeting length (minutes)? -> {{MEETING_LENGTH_MIN}}
- Which team members should be bookable? -> {{TEAM_MEMBERS}}

## The Prompt

---
You are setting up Cal.com for a marketing agency scheduling workflow.

Use the repo at https://github.com/calcom/cal.com and deploy with docker.

Goals:
1) Brand the booking page for {{COMPANY_NAME}} using {{BRAND_COLOR}}.
2) Create a "Discovery Call" event type with duration {{MEETING_LENGTH_MIN}} minutes.
3) Set default time zone to {{DEFAULT_TIMEZONE}}.
4) Add the team members listed in {{TEAM_MEMBERS}} with round-robin routing.

Return:
- Deployment steps
- Required env vars and config changes
- Links or screenshots showing the branded booking page
---

## Expected Result
The booking page loads with the agency's branding, and test bookings can be created for the Discovery Call event.

## Customization Ideas
- Add a qualification form before booking.
- Create separate event types for "Audit Review" and "Project Kickoff."
- Route bookings by service line or industry focus.
