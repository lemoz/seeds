# {{SEED_NAME}}

> {{OUTCOME_STATEMENT}}

## What You'll Get

{{DESCRIPTION_OF_END_RESULT}}

## Before We Start

I need some information to customize this for you:

1. **Company name?** (used for branding)
2. **Primary brand color?** (hex code like #3B82F6)
3. **{{DOMAIN_SPECIFIC_QUESTION_1}}**
4. **{{DOMAIN_SPECIFIC_QUESTION_2}}**

## Let's Build

### Step 1: Project Structure

I'll create the following structure:

```
{{PROJECT_NAME}}/
├── src/
│   ├── app/              # Next.js pages
│   ├── components/       # UI components
│   ├── lib/              # Utilities
│   └── api/              # API routes
├── prisma/
│   └── schema.prisma     # Database schema
├── docker-compose.yml    # Local deployment
├── Dockerfile            # Container build
├── railway.json          # Railway deployment
├── fly.toml              # Fly.io deployment
└── package.json
```

### Step 2: Database Schema

```prisma
{{PRISMA_SCHEMA}}
```

### Step 3: Core Components

{{DESCRIPTION_OF_KEY_COMPONENTS}}

### Step 4: API Endpoints

{{API_ENDPOINT_DESCRIPTIONS}}

---

## Deployment

Where would you like to deploy?

### Option 1: Local Docker
```bash
docker-compose up -d
# Access at http://localhost:3000
```

### Option 2: Railway
```bash
railway login
railway init
railway up
# Returns: https://{{project}}.up.railway.app
```

### Option 3: Fly.io
```bash
fly auth login
fly launch
fly deploy
# Returns: https://{{project}}.fly.dev
```

### Option 4: Other
Tell me your preferred platform and I'll generate the appropriate config.

---

## After Deployment

Once deployed, you can:
- {{POST_DEPLOYMENT_ACTION_1}}
- {{POST_DEPLOYMENT_ACTION_2}}
- {{POST_DEPLOYMENT_ACTION_3}}

## Customization Ideas

Want to extend this further? Common additions:
- {{EXTENSION_IDEA_1}}
- {{EXTENSION_IDEA_2}}
- {{EXTENSION_IDEA_3}}

---

*This seed generates fresh code based on proven patterns. No external repos required.*
