# WO-005 Reverse-Seed Test Report

## Scope

- Work Order: `WO-005`
- Seed under test: `seeds/scheduling/client-booking.md`
- Test date: `2026-02-15`
- Runner: Codex Builder agent in this workspace

## Test Setup

### Seed Inputs Used (5 questions)

1. `COMPANY_NAME`: `Acme Scheduling`
2. `BRAND_COLOR`: `#0F766E`
3. `DEFAULT_TIMEZONE`: `America/New_York`
4. `WORKING_HOURS`: `Mon-Fri 09:00-17:00`
5. `DEFAULT_EVENT_MINUTES`: `30`

### Method

1. Performed a smoke generation in `/tmp/wo005-scheduling-smoke-timed` using the seed's file contract.
2. Captured generation wall-clock timing with `/usr/bin/time -p`.
3. Counted generated files with `find ... -type f | wc -l`.
4. Attempted deployment command paths for local Docker, Railway, and Fly.io.

## Results

| Check | Result |
|---|---|
| Seed line count stop condition (`<500`) | Pass (`340` lines) |
| Generation time | `0.26s` (`real`) |
| Generated file count | `24` files |
| Core structure present | Pass (`app`, `app/api`, `lib`, `prisma`, deployment config files) |
| Local Docker deployment attempt | Failed: Docker daemon socket blocked by sandbox permissions |
| Railway deployment attempt | Failed: `railway` CLI not installed |
| Fly.io deployment attempt | Failed: `flyctl`/`fly` CLI not installed |

## Deployment Attempt Logs (Summary)

### Local Docker

Command:

```bash
cd /tmp/wo005-scheduling-smoke && docker compose up --build -d
```

Observed failure:

- Could not access Docker daemon socket (`operation not permitted`).

### Railway

Command:

```bash
railway --version
```

Observed failure:

- `command not found: railway`

### Fly.io

Commands:

```bash
flyctl version
fly version
```

Observed failures:

- `command not found: flyctl`
- `command not found: fly`

## Conclusions

- Generation portion is validated as working for project structure output and required file families.
- Deployment paths are defined in the seed, but could not be executed in this runtime due tool/sandbox constraints.
- Failures are documented per WO stop conditions and do not block seed publication.
