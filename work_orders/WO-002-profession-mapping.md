---
id: WO-002
title: Profession Mapping Framework
status: you_review
priority: 1
tags:
  - professions
  - mapping
created_at: 2025-01-15
goal: Map 50 professions with their top workflows. Each profession gets a YAML file listing 5-15 workflows scored against the rubric. This is the catalog backbone — what Seeds covers.
acceptance_criteria:
  - professions/ directory contains 50 YAML files, one per profession
  - Each file follows professions/schema.yml format
  - Each profession has 5-15 workflows identified and scored against rubric/scoring.md
  - "Workflows organized into sectors: Professional Services, Food & Hospitality, Health & Wellness, Education, Creative, Retail, Construction & Trades, Nonprofit, Tech"
  - Total workflow count >= 400 across all professions
  - "Each workflow has: name, description, pain_point, frequency, complexity_score, seedability_score"
  - Top 10 highest-scoring workflows flagged for priority seeding
stop_conditions:
  - If a profession has fewer than 5 identifiable software workflows, skip it and substitute another
  - Focus on workflows where software solves a real pain point, not theoretical needs
estimate_hours: 6
updated_at: 2026-02-15
---
# WO-002: Profession Mapping Framework

## Objective
Create systematic framework for mapping professions and their workflows.

## Tasks

- [ ] Define profession categories (sectors)
- [ ] Create profession YAML template
- [ ] Identify initial 50 professions to map
- [ ] Document workflow discovery methodology
- [ ] Create workflow template with rubric scoring fields

## Acceptance Criteria

- 50 professions identified and categorized
- Each profession has placeholder for workflow count estimate
- Methodology documented for consistent workflow discovery
- Templates ready for workflow mapping

## Professions to Consider

### Professional Services
- Accountant, Lawyer, Consultant, Architect, Financial Advisor

### Healthcare
- Dentist, Therapist, Clinic Admin, Vet, Optometrist, Chiropractor

### Trades
- Contractor, Electrician, Plumber, HVAC, Roofer, Landscaper

### Real Estate
- Agent, Property Manager, Appraiser, Inspector

### Retail/Hospitality
- Restaurant Owner, Salon, Gym, Retailer, Hotel

### Creative
- Photographer, Designer, Video Producer, Marketing Agency

### Education
- Tutor, Course Creator, School Admin, Coach

### Tech
- Startup Founder, Product Manager, DevOps, Freelance Developer
