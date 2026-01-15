# Client Scheduling System

> Clients book meetings directly on your calendar without email back-and-forth.

## What You'll Get

A branded scheduling page where clients can:
- See your available time slots
- Book meetings instantly
- Receive confirmation emails
- Add events to their calendar

Plus an admin dashboard where you can:
- Manage event types (Discovery Call, Project Kickoff, etc.)
- Set your availability windows
- View and manage bookings

## Before We Start

I need some information to customize this for you:

1. **Company name?** (used for branding)
2. **Primary brand color?** (hex code like #3B82F6)
3. **Default meeting length?** (e.g., 30 minutes)
4. **Your timezone?** (e.g., America/New_York)
5. **Working hours?** (e.g., Mon-Fri 9am-5pm)

## Let's Build

### Step 1: Project Structure

I'll create the following structure:

```
scheduling-app/
├── src/
│   ├── app/
│   │   ├── page.tsx              # Public booking page
│   │   ├── admin/
│   │   │   └── page.tsx          # Admin dashboard
│   │   └── api/
│   │       ├── availability/
│   │       │   └── route.ts      # Get available slots
│   │       ├── bookings/
│   │       │   └── route.ts      # Create/manage bookings
│   │       └── event-types/
│   │           └── route.ts      # Manage event types
│   ├── components/
│   │   ├── Calendar.tsx          # Date picker
│   │   ├── TimeSlots.tsx         # Available times
│   │   ├── BookingForm.tsx       # Attendee details
│   │   └── AdminNav.tsx          # Admin navigation
│   └── lib/
│       ├── db.ts                 # Database client
│       ├── availability.ts       # Slot calculation
│       └── email.ts              # Email sending
├── prisma/
│   └── schema.prisma
├── docker-compose.yml
├── Dockerfile
├── railway.json
├── fly.toml
└── package.json
```

### Step 2: Database Schema

```prisma
model User {
  id            String      @id @default(cuid())
  email         String      @unique
  name          String
  timezone      String      @default("America/New_York")
  eventTypes    EventType[]
  bookings      Booking[]
  availability  Availability[]
  createdAt     DateTime    @default(now())
}

model EventType {
  id          String    @id @default(cuid())
  title       String
  slug        String
  duration    Int       // minutes
  description String?
  color       String    @default("#3B82F6")
  userId      String
  user        User      @relation(fields: [userId], references: [id])
  bookings    Booking[]
  active      Boolean   @default(true)
  createdAt   DateTime  @default(now())
}

model Booking {
  id            String    @id @default(cuid())
  eventTypeId   String
  eventType     EventType @relation(fields: [eventTypeId], references: [id])
  userId        String
  user          User      @relation(fields: [userId], references: [id])
  startTime     DateTime
  endTime       DateTime
  attendeeName  String
  attendeeEmail String
  notes         String?
  status        String    @default("confirmed") // confirmed, cancelled
  createdAt     DateTime  @default(now())
}

model Availability {
  id        String   @id @default(cuid())
  userId    String
  user      User     @relation(fields: [userId], references: [id])
  dayOfWeek Int      // 0=Sunday, 1=Monday, etc.
  startTime String   // "09:00"
  endTime   String   // "17:00"
}
```

### Step 3: Core Components

**Availability Calculator** - Finds open slots by:
1. Getting user's availability windows for the day
2. Fetching existing bookings
3. Subtracting booked times from available windows
4. Returning slots in attendee's timezone

**Booking Flow**:
1. Attendee selects date → fetches available slots
2. Attendee picks time → shows booking form
3. Form submitted → creates booking + sends emails
4. Confirmation shown with calendar links

### Step 4: API Endpoints

```
GET  /api/availability?date=2024-01-15&eventType=discovery
     → Returns available time slots for that date

POST /api/bookings
     → Creates new booking, sends confirmation emails
     Body: { eventTypeId, startTime, attendeeName, attendeeEmail, notes }

GET  /api/bookings
     → Lists bookings (admin only)

PATCH /api/bookings/:id
     → Update booking status (cancel, reschedule)

GET  /api/event-types
     → Lists active event types

POST /api/event-types
     → Creates new event type (admin only)
```

---

## Deployment

Where would you like to deploy?

### Option 1: Local Docker
```bash
docker-compose up -d
# Access at http://localhost:3000
# Admin at http://localhost:3000/admin
```

### Option 2: Railway
```bash
railway login
railway init
railway up
# Returns your public URL
```

### Option 3: Fly.io
```bash
fly auth login
fly launch
fly deploy
# Returns your public URL
```

### Option 4: Other
Tell me your preferred platform (Render, DigitalOcean, Vercel+Supabase, etc.) and I'll generate the config.

---

## After Deployment

Once deployed, you can:
- Visit `/admin` to create your first event type
- Set your availability schedule
- Share your booking link: `https://yourapp.com/book/discovery-call`

## Customization Ideas

Want to extend this further? Common additions:
- **Google Calendar sync** - Auto-block booked times
- **Zoom integration** - Auto-create meeting links
- **Payment required** - Collect payment before booking
- **Intake form** - Custom questions before booking
- **Team scheduling** - Round-robin assignment
- **Buffer time** - Gaps between meetings

---

*This seed generates fresh code based on scheduling app patterns. No external repos required.*
