# Scheduling Seed: Client Booking

> Build and deploy a branded scheduling app from scratch (no repo cloning) by answering 5 questions.

## Agent Contract

You are generating a fresh project from this seed. Follow these rules exactly:

1. Ask exactly the 5 questions in this seed, then wait for answers.
2. During generation, do not use network scaffolding tools (`npx create-next-app`, cloning repos, or fetching templates).
3. Write files directly from this seed's DNA and file contract.
4. Keep generated code minimal, readable, and production-sane.
5. After generation, ask for deployment target: `local-docker`, `railway`, `flyio`, or `other`.

## Ask These 5 Questions

1. What is the company name? (`COMPANY_NAME`)
2. What brand color should be used? (hex, `BRAND_COLOR`)
3. What is the default timezone? (`DEFAULT_TIMEZONE`, example `America/New_York`)
4. What are default working hours? (`WORKING_HOURS`, example `Mon-Fri 09:00-17:00`)
5. What is the default event length in minutes? (`DEFAULT_EVENT_MINUTES`)

## Reverse-Seeded DNA (from scheduling patterns)

### Architecture Patterns
- Next.js 14 App Router with server route handlers under `app/api/*`.
- PostgreSQL + Prisma for data model and relations.
- Public booking UI + simple admin UI for event types and availability rules.
- Availability engine that subtracts existing bookings from configured availability windows.

### Data Model Patterns
- `User` owns `EventType` and `AvailabilityRule`.
- `Booking` references `EventType` and stores attendee details + status.
- `CalendarConnection` stores provider metadata for integration adapters.

### API Patterns
- `GET /api/event-types`: list active event types.
- `GET /api/availability?eventTypeSlug=&date=`: return open slots.
- `POST /api/bookings`: atomic booking with conflict check.
- `GET/POST /api/availability/rules`: admin availability config.

### Availability Algorithm Pattern
1. Resolve weekday rules for selected date.
2. Expand rules into candidate slots (`duration` step).
3. Remove slots overlapping existing bookings.
4. Return ISO timestamps plus display labels.

### Calendar Integration Pattern
- Keep provider logic behind adapters.
- Always generate an ICS payload for fallback.
- Return integration metadata in booking response.

### Deployment Pattern
- `Dockerfile` + `docker-compose.yml` for local runtime.
- `railway.json` for Railway.
- `fly.toml` for Fly.io.
- One app container + managed Postgres on hosted targets.

## Generated Project Contract

Create this structure exactly:

```text
client-booking-app/
  app/
    api/
      availability/
        route.ts
      availability/rules/
        route.ts
      bookings/
        route.ts
      event-types/
        route.ts
    admin/page.tsx
    globals.css
    layout.tsx
    page.tsx
  lib/
    availability.ts
    calendar.ts
    db.ts
    env.ts
  prisma/
    schema.prisma
    seed.ts
  .dockerignore
  .env.example
  Dockerfile
  docker-compose.yml
  fly.toml
  next.config.mjs
  package.json
  railway.json
  README.md
  tsconfig.json
```

## File Generation Details

Generate each file with working code, using these constraints.

### `package.json`
- Scripts:
  - `dev`: `next dev`
  - `build`: `next build`
  - `start`: `next start`
  - `db:generate`: `prisma generate`
  - `db:push`: `prisma db push`
  - `db:seed`: `tsx prisma/seed.ts`
- Dependencies: `next`, `react`, `react-dom`, `@prisma/client`, `zod`.
- Dev dependencies: `prisma`, `typescript`, `tsx`, `@types/node`, `@types/react`, `@types/react-dom`.

### `prisma/schema.prisma`
Use PostgreSQL datasource from `DATABASE_URL`. Include:

```prisma
generator client { provider = "prisma-client-js" }

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

enum BookingStatus {
  confirmed
  canceled
}

model User {
  id                String             @id @default(cuid())
  email             String             @unique
  name              String
  timezone          String             @default("America/New_York")
  eventTypes        EventType[]
  availabilityRules AvailabilityRule[]
  calendarLinks     CalendarConnection[]
  createdAt         DateTime           @default(now())
  updatedAt         DateTime           @updatedAt
}

model EventType {
  id             String    @id @default(cuid())
  userId         String
  user           User      @relation(fields: [userId], references: [id])
  slug           String    @unique
  title          String
  description    String?
  durationMin    Int
  color          String
  active         Boolean   @default(true)
  bookings       Booking[]
  createdAt      DateTime  @default(now())
  updatedAt      DateTime  @updatedAt

  @@index([userId, active])
}

model AvailabilityRule {
  id         String   @id @default(cuid())
  userId     String
  user       User     @relation(fields: [userId], references: [id])
  weekday    Int
  startTime  String
  endTime    String
  createdAt  DateTime @default(now())
  updatedAt  DateTime @updatedAt

  @@index([userId, weekday])
}

model Booking {
  id            String        @id @default(cuid())
  eventTypeId   String
  eventType     EventType     @relation(fields: [eventTypeId], references: [id])
  attendeeName  String
  attendeeEmail String
  attendeeNotes String?
  startAt       DateTime
  endAt         DateTime
  status        BookingStatus @default(confirmed)
  createdAt     DateTime      @default(now())
  updatedAt     DateTime      @updatedAt

  @@index([eventTypeId, startAt, endAt])
}

model CalendarConnection {
  id           String   @id @default(cuid())
  userId       String
  user         User     @relation(fields: [userId], references: [id])
  provider     String
  externalId   String?
  accessToken  String?
  refreshToken String?
  createdAt    DateTime @default(now())
  updatedAt    DateTime @updatedAt

  @@index([userId, provider])
}
```

### `lib/availability.ts`
Implement:
- `getOpenSlots(params)` that receives:
  - date string (`YYYY-MM-DD`)
  - event duration minutes
  - array of rules (`weekday`, `startTime`, `endTime`)
  - array of bookings (`startAt`, `endAt`)
- Return array of `{ startAtIso, endAtIso, label }`.
- Slot conflict logic: `candidateStart < bookingEnd && bookingStart < candidateEnd`.

### `lib/calendar.ts`
Implement adapter pattern:
- `buildIcsEvent({ title, description, startAt, endAt, attendeeName, attendeeEmail })` returns string.
- `buildCalendarPayload({ provider, booking })`:
  - if provider `google` or `outlook`, return provider-specific placeholder payload object.
  - else return ICS payload.

### `app/api/event-types/route.ts`
- `GET`: return active event types with `slug`, `title`, `durationMin`, `color`.

### `app/api/availability/route.ts`
- `GET` query params: `eventTypeSlug`, `date`.
- Load event type, owning user availability rules for weekday, and same-day bookings.
- Use `getOpenSlots` and return `{ slots }`.

### `app/api/bookings/route.ts`
- `POST` body: `eventTypeSlug`, `startAtIso`, `attendeeName`, `attendeeEmail`, `attendeeNotes?`.
- Validate with `zod`.
- Compute `endAt` from event type duration.
- Reject overlaps with existing bookings (`409`).
- Create booking and include calendar payload response:
  - `{ booking, calendar: { type, payload } }`.

### `app/api/availability/rules/route.ts`
- `GET`: return current user's availability rules (single-user bootstrap is acceptable).
- `POST`: upsert a rule by `(weekday, startTime, endTime)`.

### `app/page.tsx`
Build a minimal booking page that:
- Shows brand header using `COMPANY_NAME` and `BRAND_COLOR`.
- Loads event types.
- Lets attendee pick date, slot, name, and email.
- Calls availability endpoint and booking endpoint.
- Shows success message with booked time.

### `app/admin/page.tsx`
Build a minimal admin page that:
- Lists availability rules.
- Form to add a rule (`weekday`, `startTime`, `endTime`).
- Lists event types and durations.

### `prisma/seed.ts`
Seed with one default user and one event type:
- `timezone = DEFAULT_TIMEZONE`
- `durationMin = DEFAULT_EVENT_MINUTES`
- availability derived from `WORKING_HOURS` (Mon-Fri baseline acceptable).

### `lib/env.ts`
- Parse required env vars (`DATABASE_URL`, `NEXT_PUBLIC_COMPANY_NAME`, `NEXT_PUBLIC_BRAND_COLOR`).

### `lib/db.ts`
- Prisma singleton for Next.js runtime.

### `.env.example`
Include:
- `DATABASE_URL=postgresql://postgres:postgres@localhost:5432/scheduling`
- `NEXT_PUBLIC_COMPANY_NAME=COMPANY_NAME`
- `NEXT_PUBLIC_BRAND_COLOR=BRAND_COLOR`
- `DEFAULT_TIMEZONE=DEFAULT_TIMEZONE`

### `Dockerfile`
- Node 20 Alpine image.
- Install dependencies, copy source, run `prisma generate`, build Next.js.
- Start with `npm run start` on port `3000`.

### `docker-compose.yml`
- `db` service: `postgres:16-alpine` with healthcheck.
- `app` service builds current directory, maps `3000:3000`, depends on db.

### `railway.json`
- Dockerfile build.
- Start command: `npm run start`.
- Ensure `DATABASE_URL` is expected from Railway Postgres plugin.

### `fly.toml`
- App name based on slugified `COMPANY_NAME` plus `-booking`.
- Internal port `3000`.
- Health check path `/`.

### `README.md`
Include:
- local setup (`npm install`, `cp .env.example .env`, `npm run db:push`, `npm run db:seed`, `npm run dev`)
- API summary
- deployment steps for Docker, Railway, Fly.io.

## Deployment Branching Logic

After file generation and a basic smoke check (`npm run build` if dependencies are installed), ask:

`Where should I deploy? (local-docker / railway / flyio / other)`

Then execute only one branch:

### Branch: `local-docker`
1. `docker compose up --build -d`
2. Run Prisma setup in container (`db push` and `db seed`).
3. Return URL: `http://localhost:3000`

### Branch: `railway`
1. `railway login`
2. `railway init`
3. Provision Postgres plugin.
4. Set required variables.
5. `railway up`
6. Return generated Railway URL.

### Branch: `flyio`
1. `fly auth login`
2. `fly launch --copy-config --no-deploy`
3. Create Postgres attachment (managed or external).
4. Set secrets.
5. `fly deploy`
6. Return generated Fly URL.

### Branch: `other`
- Ask platform name.
- Generate equivalent config using Dockerfile baseline.

## Quality Gate

Before returning completion, confirm:
- Booking page exists and can create bookings.
- Availability rules can be added/read.
- Prisma schema contains User, EventType, AvailabilityRule, Booking, CalendarConnection.
- Calendar integration pattern exists via adapter + ICS fallback.
- Docker, Railway, and Fly configs exist.

If any target deployment fails, document failure reason and continue with remaining target attempts when requested.
