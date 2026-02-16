# WO-005 Test Report: Reverse-Seed Process

Date: 2026-02-15
Work Order: `WO-005`
Seed under test: `seeds/scheduling/client-booking.md`

## Test Scope

- Validate seed completeness and required sections
- Validate seed line-count stop condition (< 500 lines)
- Run a generation smoke test to confirm project structure can be created
- Attempt deployment commands for Docker, Railway, and Fly.io

## Commands and Results

### 1) Seed structure checks

Command:

```bash
wc -l seeds/scheduling/client-booking.md
rg -n "Project DNA|Customization Hooks|Deployment Config Requirements|docker-compose.yml|railway.json|fly.toml|CalendarConnection|Output Contract" seeds/scheduling/client-booking.md
```

Result:
- Line count: `394`
- Required sections/config markers: present

Status: PASS

### 2) Generation smoke test (structure-only)

Method:
- Created empty temp directory
- Followed the seed contract to generate a scheduling app structure with required core files
- Measured elapsed time and counted generated files

Command artifact output:

```text
tmpdir=/tmp/wo005-smoke-gQZ9
generation_ms=102
file_count=25
```

Status: PASS (working project structure generated)

### 3) Deployment attempts

Environment findings:

```text
docker_cli=/usr/local/bin/docker
railway_cli=missing
fly_cli=missing
```

#### Local Docker

Command:

```bash
docker compose up --build -d
```

Exit code: `1`

Failure:

```text
permission denied while trying to connect to the Docker daemon socket ... connect: operation not permitted
```

Status: FAIL (sandbox daemon permission)

#### Railway

Command:

```bash
railway login
```

Exit code: `127`

Failure:

```text
command not found: railway
```

Status: FAIL (CLI unavailable)

#### Fly.io

Command:

```bash
fly auth login
```

Exit code: `127`

Failure:

```text
command not found: fly
```

Status: FAIL (CLI unavailable)

## Summary

- Seed generation requirements are satisfied and self-contained for build-time output.
- Project structure generation smoke test passed (`25` files in `102 ms`).
- Deployment commands are correctly specified in seed, but execution failed in this environment due to runtime/tooling constraints.

## Follow-up Needed Outside This Sandbox

1. Run `docker compose up --build -d` on a host with Docker daemon access.
2. Install/authenticate Railway CLI and run `railway up`.
3. Install/authenticate Fly CLI and run `fly deploy`.
