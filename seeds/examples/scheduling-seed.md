---
id: scheduling-client-booking
name: Client Booking Scheduler
version: 1.0.0
source_dna: cal.com-patterns-generalized
owner: seeds-project
---

# Client Booking Scheduler Seed

Build a deployable scheduling app from scratch in an empty directory.

## Outcome

Generate a Next.js 14 scheduling app with:
- Public booking page
- Admin availability configuration
- Prisma + PostgreSQL schema
- Booking and availability APIs
- Calendar integration patterns (adapter-based)
- Deployment configs for local Docker, Railway, and Fly.io

## Hard Constraints

1. Generation must be self-contained.
2. Do not clone or fetch external repositories.
3. Do not copy Cal.com code verbatim.
4. Use generalized patterns only.
5. Keep generated code simple and readable.

## Ask These 5 Questions First

1. Company name
2. Primary brand color (hex)
3. Default timezone (IANA, e.g. `America/New_York`)
4. Working hours (e.g. `Mon-Fri 09:00-17:00`)
5. Preferred deployment target (`docker`, `railway`, `fly`)

## Customization Hooks

Use the answers to set:
- `APP_NAME`
- `BRAND_COLOR`
- `DEFAULT_TIMEZONE`
- `DEFAULT_WORKING_HOURS`
- `DEPLOY_TARGET`

## Project DNA (Generalized from Cal.com)

Extracted patterns to preserve:
- `User -> EventType -> Booking` relational model
- Availability windows by weekday and timezone
- Slot computation by subtracting existing bookings from windows
- Public booking flow + admin management surface
- Calendar sync abstraction via provider adapters

Patterns intentionally left out:
- Vendor-specific enterprise logic
- Complex team routing and billing layers
- Exact upstream naming and implementation details

## Generate This Structure

```text
scheduling-app/
  package.json
  next.config.mjs
  tsconfig.json
  .env.example
  .gitignore
  Dockerfile
  docker-compose.yml
  railway.json
  fly.toml
  prisma/
    schema.prisma
    seed.ts
  src/
    app/
      layout.tsx
      globals.css
      page.tsx
      admin/page.tsx
      api/
        event-types/route.ts
        availability/route.ts
        bookings/route.ts
    components/
      BookingForm.tsx
      AvailabilityForm.tsx
      EventTypeList.tsx
    lib/
      db.ts
      availability.ts
      calendar.ts
      validation.ts
```

## File Requirements

### `package.json`

Use Next.js 14 and Prisma stack:

```json
{
  "name": "scheduling-app",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "db:push": "prisma db push",
    "db:seed": "tsx prisma/seed.ts"
  },
  "dependencies": {
    "@prisma/client": "^5.22.0",
    "next": "14.2.30",
    "react": "18.3.1",
    "react-dom": "18.3.1",
    "zod": "^3.24.1"
  },
  "devDependencies": {
    "prisma": "^5.22.0",
    "tsx": "^4.19.2",
    "typescript": "^5.6.3",
    "@types/node": "^22.10.1",
    "@types/react": "^18.3.12"
  }
}
```

### `.env.example`

```bash
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/scheduling"
APP_NAME="{{APP_NAME}}"
BRAND_COLOR="{{BRAND_COLOR}}"
DEFAULT_TIMEZONE="{{DEFAULT_TIMEZONE}}"
```

### `prisma/schema.prisma`

Create this schema (field names may vary slightly, relations must match):

```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id                String               @id @default(cuid())
  email             String               @unique
  name              String
  timezone          String               @default("America/New_York")
  eventTypes        EventType[]
  availabilityRules AvailabilityWindow[]
  bookings          Booking[]            @relation("HostBookings")
  createdAt         DateTime             @default(now())
}

model EventType {
  id          String    @id @default(cuid())
  userId      String
  user        User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  title       String
  slug        String    @unique
  durationMin Int
  description String?
  isActive    Boolean   @default(true)
  bookings    Booking[]
  createdAt   DateTime  @default(now())

  @@index([userId, isActive])
}

model AvailabilityWindow {
  id        String   @id @default(cuid())
  userId    String
  user      User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  weekday   Int
  startTime String
  endTime   String
  createdAt DateTime @default(now())

  @@index([userId, weekday])
}

model Booking {
  id             String    @id @default(cuid())
  eventTypeId    String
  eventType      EventType @relation(fields: [eventTypeId], references: [id], onDelete: Restrict)
  hostUserId     String
  hostUser       User      @relation("HostBookings", fields: [hostUserId], references: [id], onDelete: Restrict)
  attendeeName   String
  attendeeEmail  String
  attendeeNotes  String?
  startAt        DateTime
  endAt          DateTime
  timezone       String
  status         String    @default("confirmed")
  externalRef    String?
  createdAt      DateTime  @default(now())

  @@index([eventTypeId, startAt])
  @@index([hostUserId, startAt])
}

model CalendarConnection {
  id           String   @id @default(cuid())
  userId       String
  provider     String
  accountEmail String
  accessToken  String?
  refreshToken String?
  createdAt    DateTime @default(now())

  @@index([userId, provider])
}
```

### `src/lib/availability.ts`

Implement slot generation algorithm:

1. Parse requested date and event duration.
2. Find weekday availability windows for host.
3. Build candidate slots at 15-minute increments.
4. Remove candidates that overlap existing confirmed bookings.
5. Return ISO timestamps and display labels in requested timezone.

Use this overlap rule:

```ts
const overlaps = (aStart: Date, aEnd: Date, bStart: Date, bEnd: Date) =>
  aStart < bEnd && bStart < aEnd;
```

### `src/lib/calendar.ts`

Provide adapter interface and no-op default implementation:

```ts
export type CalendarProvider = "none" | "google" | "outlook";

export interface CalendarAdapter {
  createEvent(input: {
    title: string;
    description?: string;
    startAt: string;
    endAt: string;
    attendeeEmail: string;
  }): Promise<{ externalRef?: string }>;
}
```

Then implement:
- `NoopAdapter` that returns `{}`
- `getCalendarAdapter(provider)` factory with TODO placeholders for Google/Outlook

### API Routes

Implement minimal but working handlers:

1. `GET /api/event-types`
- Return active event types for default host.

2. `GET /api/availability?date=YYYY-MM-DD&eventTypeSlug=...`
- Validate query with Zod.
- Resolve event type and host.
- Return computed slots.

3. `POST /api/bookings`
- Validate body.
- Ensure slot is still available.
- Create booking transactionally.
- Call calendar adapter and persist `externalRef` when provided.
- Return `201` with booking object.

### UI Requirements

1. `src/app/page.tsx`
- Show app name and brand color accent.
- Let user choose event type, date, and available slot.
- Render `BookingForm` for attendee details and submit booking.

2. `src/app/admin/page.tsx`
- List event types.
- Allow basic weekday availability edits.
- Show latest bookings table (read-only is fine).

3. Components can be simple server/client React components with plain CSS.

## Deployment Config Requirements

### `Dockerfile`

- Multi-stage or single-stage is acceptable.
- Must run `next build` and `next start` on port 3000.

### `docker-compose.yml`

Include app + postgres services. App depends on db and passes `DATABASE_URL`.

### `railway.json`

```json
{
  "$schema": "https://railway.com/railway.schema.json",
  "build": { "builder": "DOCKERFILE" },
  "deploy": {
    "startCommand": "npm run start",
    "restartPolicyType": "ON_FAILURE",
    "restartPolicyMaxRetries": 5
  }
}
```

### `fly.toml`

Use app port `3000` and include basic HTTP service checks.

## Generation Procedure

1. Create all files.
2. Substitute customization hook values.
3. Run formatting only if tooling is already present.
4. Do not require network during generation.
5. Print summary: files created + next commands.

## Verification Checklist (During Generation)

- Booking page renders and calls availability API.
- Availability API returns slot list based on rules.
- Booking API creates DB row and returns `201`.
- Prisma schema includes User/EventType/Booking/AvailabilityWindow.
- Deployment files exist for Docker, Railway, Fly.io.

## Deployment Logic

After generation, branch on `DEPLOY_TARGET`:

### If `docker`

```bash
cp .env.example .env
docker compose up --build -d
```

Return URL: `http://localhost:3000`

### If `railway`

```bash
railway login
railway init --name scheduling-app
railway up
```

Return Railway URL from CLI output.

### If `fly`

```bash
fly auth login
fly launch --no-deploy
fly deploy
```

Return Fly URL from CLI output.

If deployment fails for one target, document failure and continue with available targets.

## Output Contract

At completion, print:

1. Resolved customization values
2. File count
3. Verification results
4. Deployment target attempted
5. Final URL (or failure reason with logs summary)

## Notes on Limits

- Keep generated MVP intentionally small and extensible.
- Calendar providers beyond no-op are scaffold patterns, not full OAuth implementations.
- Advanced routing (team round-robin, pooled availability) is out of scope for this first extraction.
