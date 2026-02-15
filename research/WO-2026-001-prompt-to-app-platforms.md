# WO-2026-001 Research: Prompt-to-App Platforms

Date: February 15, 2026  
Scope: Publicly available product pages, docs, support articles, and pricing pages only (no account creation).

## Executive Summary
The prompt-to-app category has converged on a common core: natural-language app generation plus managed hosting. The major difference between vendors is not "can they generate UI/backend," but where they lock value: model credits, hosting, deployment path, and template ecosystems. Hostinger Horizons is the closest visible competitor to Seeds at the distribution layer because it emphasizes remixable templates and one-click launch, but it still keeps the creation loop inside a hosted product and supports only one-way export. Seeds is fundamentally different as a portable, self-contained generation artifact that is not tied to one hosted runtime.

## Platform Deep Profiles

### 1) Bolt.new (StackBlitz)
How it works:
- AI app builder for full-stack web/mobile experiences from prompts, with one-click imports from Figma, GitHub, and ZIP. [1]
- Conversation-driven build loop with token metering and usage controls. [2][3]

Pricing (public):
- Free tier with monthly token allocation; paid plans provide larger monthly/annual token bundles.
- Public support docs show examples such as Pro 10M ($25/mo) and Pro 26M ($50/mo), plus annual bundles and optional usage-based billing. [2][3]

What you own:
- Public docs emphasize GitHub integration for version control, backups, and collaboration, which improves portability of generated code. [4]
- Public support pages reviewed do not clearly state a concise IP ownership clause; legal ownership language should be verified in StackBlitz/Bolt terms before procurement.

Deployment options:
- Built-in publishing to web/mobile targets; custom domains available on paid plans. [3][5]

Template/marketplace model:
- Strong import model (Figma/GitHub/ZIP).
- Public template marketplace depth is less explicit than some competitors; the product emphasizes generation/edit loops over a large public remix economy. [1]

Observed limitations:
- Heavy reliance on token economics and hosted workflow.
- IP clause clarity requires legal review outside support docs.

### 2) Lovable.dev
How it works:
- Prompt-first full-stack generation with visual editing and code-level control.
- Native integrations for backend/data (notably Supabase), custom domains, and publishing from the platform. [6][7][8]

Pricing (public):
- Documented plans include Free (5 daily messages), Starter ($20/month, 100 monthly credits), Launch ($50/month, 250 credits), Scale ($100/month, 500 credits), and Teams. [9]

What you own:
- Lovable states users own their code and can sync with GitHub (no lock-in positioning). [10]
- Self-hosting is documented for generated projects. [11]

Deployment options:
- One-click publish, custom domain support, and self-host path via exported/generated code. [8][11]

Template/marketplace model:
- Built-in template library plus "Remix" for cloning/forking public projects and iterating from them. [12][13]

Observed limitations:
- Credit/message model can constrain high-iteration workflows.
- Ongoing highest-leverage experience remains platform-native even with export/self-host options.

### 3) Softgen.ai
How it works:
- Prompt-based app generation with integrated building blocks (auth, payments, DB, admin patterns) and visual editing.
- Supports app "cloning" and workflow acceleration from existing app setups. [14]

Pricing (public):
- Public pricing advertises tiered monthly plans (examples shown: Starter $25, Pro $50, Growth $125, Agency $325). [15]

What you own:
- FAQ states the project is "yours forever" and that paid users can access GitHub repositories for projects. [16]

Deployment options:
- Deployment documentation includes external deployment workflows such as Vercel and custom domains. [17][18]

Template/marketplace model:
- Product emphasizes reusable app patterns and cloning.
- A broad public remix marketplace (with transparent public artifact liquidity like template economics/rankings) is less visible than in Horizons/Lovable from public docs.

Observed limitations:
- GitHub access being tied to paid tiers increases portability friction for free-tier evaluation. [16]

### 4) v0.dev (Vercel)
How it works:
- Prompt-driven generation for UI/components and increasingly full app flows, with import from Figma, screenshots, and text prompts.
- Strong connection to existing codebases and Git workflows. [19][20]

Pricing (public):
- Free: 5 daily credits plus 200 one-time credits.
- Premium: $20/mo with 5,000 credits.
- Team: $30/user/mo with 5,000 credits per user. [21]

What you own:
- Public docs focus on code portability: edit/download generated code, bi-directional Git sync, and codebase integration.
- Explicit legal ownership wording is not prominent in the docs set reviewed; contract/terms review is still needed for enterprise procurement. [20]

Deployment options:
- One-click deploy path is optimized for Vercel. [22]

Template/marketplace model:
- Community templates/projects and starter flows exist, but distribution gravity is still tightly linked to Vercel ecosystem primitives.

Observed limitations:
- Credits + Vercel-first deployment make this a powerful but ecosystem-centered workflow.

### 5) Replit Agent
How it works:
- Autonomous coding agent inside Replit workspace (plan, implement, debug) with iterative chat-driven refinement. [23][24]

Pricing (public):
- Replit pricing publishes Free/Starter, Core ($20/month), Teams ($35/user/month), and Enterprise, with credits included by paid plans (examples: Core includes $25 credits; Teams includes $40/user). [25]

What you own:
- Replit terms indicate users retain rights to content while granting service license rights; public apps are generally MIT by default. [26]

Deployment options:
- Built-in deployment modes (Static, Autoscale, Reserved VM) and custom domain support from within Replit. [27]

Template/marketplace model:
- Mature template gallery and import paths (including GitHub and framework starters). [28]

Observed limitations:
- Production experience is tightly coupled to Replit runtime economics and deployment primitives.

### 6) Hostinger Horizons
How it works:
- Prompt-to-app builder with integrated hosting and domain setup designed for quick launch by non-developers. [29][30]

Pricing (public):
- Public pages and support materials show tiered plans ranging roughly from entry-level to high-message enterprise-like tiers (examples shown: ~$19.99 to ~$199.99/month, message caps by tier). [31]

What you own:
- Supports code export for Node.js/React/Vite apps as ZIP.
- Export is one-way: changes made outside Horizons cannot be imported back into Horizons prompt workflow. [30][32]

Deployment options:
- Native one-click deployment to Hostinger infrastructure with managed hosting/domain tooling.
- Exported apps can be self-hosted on external infrastructure. [30][32]

Template/marketplace model:
- Horizons has a dedicated template gallery and remix workflow where users clone templates, edit via prompts, and publish. [33][34]
- Creator-side incentive mechanisms (template sharing/referrals) are publicly promoted. [35]

Observed limitations:
- Hosted loop is central; external code edits break round-trip prompting continuity.
- Public docs also note technical constraints relative to traditional code-first stacks (for example around broader package/plugin flexibility). [36]

#### Detailed Analysis: Horizons Remixable Templates (Closest Seeds Analog)
What Horizons gets right:
- Distribution unit is increasingly "template + prompt remix," not just one-off generated app.
- Fast path from discovery -> clone -> customize -> launch is strong for non-technical buyers.
- Integrated hosting reduces post-generation friction.

Why it still differs from Seeds:
- Template artifact remains platform-bound; the core value is in Horizons runtime + hosted editing loop.
- One-way export means the portable artifact is derivative code, not a reusable generation DNA object that remains platform-agnostic.
- Remix economics are tied to Hostinger account graph rather than a standalone, tool-agnostic prompt artifact.

### 7) Firebase Studio (Google)
How it works:
- Cloud development environment for AI-assisted app prototyping and coding.
- Supports starting from prompt, template, or existing repo; includes full coding workspaces and app prototyping workflows. [37][38]

Pricing (public):
- During preview, Firebase Studio documents no-cost workspace limits (for example up to 3 workspaces; higher limits for eligible Google Developer Program tiers).
- Gemini usage quotas are explicitly documented (for example request-per-minute/day constraints) and Firebase usage billing still applies where relevant. [39][40]

What you own:
- Import existing repos, create/share custom templates, and work with standard code workspace paradigms, which improves portability. [37][41]
- IP ownership language is governed by Google terms; product docs focus more on quotas/workflows than a concise ownership statement.

Deployment options:
- Direct deployment integration with Firebase App Hosting and adjacent Firebase services. [42]

Template/marketplace model:
- Supports built-in templates and custom template creation/sharing.
- App prototyping agent support is currently narrower (explicitly Next.js web app focus), which affects template breadth in the prototyping path. [38]

Observed limitations:
- Still preview-stage and quota-constrained for many users.
- Strongly aligned to Google/Firebase runtime and service ecosystem.

## Comparison Matrix

| Platform | Closed vs Open | Owned vs Hosted (practical default) | Agent-Locked vs Agent-Agnostic | Deployment posture | Template/Marketplace posture |
|---|---|---|---|---|---|
| Bolt.new | Closed SaaS product | Hosted-first, portable via GitHub integration | Medium-high lock-in (token/workflow centered) | Native publish + custom domains; platform-first | Import-heavy; less explicit public remix economy |
| Lovable | Closed SaaS product | Hosted-first, with export/self-host path | Medium lock-in (platform best path, but export/self-host available) | One-click publish + custom domains + self-host | Strong templates + remix of public projects |
| Softgen | Closed SaaS product | Hosted-first, portability stronger on paid tiers | Medium lock-in (paid tier unlocks stronger portability) | External deployment docs (e.g., Vercel) plus domain setup | Reusable patterns/cloning; marketplace less visible |
| v0 | Closed SaaS product (Vercel ecosystem) | Hosted/design loop with strong code portability | Medium lock-in (Vercel-first but codebase integration strong) | Vercel-optimized one-click deploy | Community templates/projects, ecosystem-centered |
| Replit Agent | Closed SaaS product | Hosted-first with established code export/import norms | Medium lock-in (runtime/credits matter) | Multiple managed deployment modes in-platform | Mature template gallery |
| Hostinger Horizons | Closed SaaS product | Hosted-first, one-way code export | High lock-in in ongoing prompt loop (no round-trip import after external edits) | One-click Hostinger launch; optional self-host after export | High focus on remix templates + creator incentives |
| Firebase Studio | Closed managed platform using open tooling components | Hosted workspace + repo/template portability | Medium lock-in (Firebase/Google service gravity) | Native Firebase App Hosting path | Built-in templates + custom template creation |
| Seeds (target model) | Open artifact model (portable seed prompt) | User-owned generated project + user-chosen infra by design | Low lock-in (agent-agnostic and deploy-target-agnostic) | Multi-target deployment first-class | Seed files are reusable DNA artifacts, not hosted project handles |

## Where Seeds Is Fundamentally Different
1. Artifact-first vs workspace-first:
- Competitors primarily sell hosted workspaces that generate apps.
- Seeds is a portable generation artifact (the seed prompt) that can be versioned, forked, and reused independent of one vendor runtime.

2. Deployment-agnostic by contract:
- Most platforms nudge toward their native hosting.
- Seeds requires explicit multi-target deployment choices (local Docker, Railway, Fly.io, Render, cloud), making deployment flexibility part of the product contract.

3. Lower structural lock-in:
- In hosted platforms, the fastest iteration loop usually lives inside the vendor product.
- In Seeds, the durable value is the seed DNA plus generated code under the user’s control.

4. Reverse-seed provenance model:
- Seeds intentionally derives reusable software DNA from OSS patterns and regenerates fresh code.
- This is closer to a portable software recipe system than a hosted app-builder subscription.

5. Economics can shift from "platform credits" to "model + infra choice":
- Competitors commonly monetize message/credit/token bundles.
- Seeds can decouple authoring/generation from long-term hosting platform lock-in.

## Public-Info Gaps / Stop-Condition Notes
- This report intentionally used only public information (no paid access, no account creation).
- For enterprise procurement, legal review is still required for each vendor’s formal terms on IP ownership, indemnity, and data usage/training rights.
- Some vendor pricing/details are dynamic; use cited URLs as of research date and re-verify before decisions.

## Sources
[1] https://support.bolt.new/en/articles/14131842-what-is-bolt-new  
[2] https://support.bolt.new/en/articles/11793142-how-does-bolt-billing-work  
[3] https://support.bolt.new/en/articles/11887607-how-can-i-control-my-token-usage-in-bolt  
[4] https://support.bolt.new/en/articles/12692368-integrate-bolt-with-github  
[5] https://support.bolt.new/en/articles/12888418-how-does-deployment-work-in-bolt  
[6] https://docs.lovable.dev/introduction  
[7] https://docs.lovable.dev/integrations/supabase  
[8] https://docs.lovable.dev/integrations/custom-domains  
[9] https://docs.lovable.dev/billing-and-subscriptions/plans-and-credits  
[10] https://lovable.dev/compare  
[11] https://docs.lovable.dev/advanced-guides/self-hosting  
[12] https://docs.lovable.dev/features/templates  
[13] https://docs.lovable.dev/features/remix-projects  
[14] https://academy.softgen.ai/getting-started/overview  
[15] https://softgen.ai/pricing  
[16] https://academy.softgen.ai/getting-started/faq  
[17] https://academy.softgen.ai/deployment/vercel  
[18] https://academy.softgen.ai/deployment/domain  
[19] https://v0.dev/docs/how-it-works  
[20] https://v0.dev/docs/codebase-integration  
[21] https://v0.dev/pricing  
[22] https://v0.dev/docs/deployments  
[23] https://docs.replit.com/getting-started/intro-replit-agent  
[24] https://docs.replit.com/replitai/agent  
[25] https://replit.com/pricing  
[26] https://replit.com/terms-of-service  
[27] https://docs.replit.com/replit-workspace/workspace-features/deployment  
[28] https://docs.replit.com/replit-workspace/workspace-features/project-importing  
[29] https://www.hostinger.com/horizons  
[30] https://support.hostinger.com/en/articles/11741575-what-is-hostinger-horizons  
[31] https://www.hostinger.com/tutorials/hostinger-horizons  
[32] https://support.hostinger.com/en/articles/11741616-how-to-launch-and-manage-your-hostinger-horizons-project  
[33] https://www.hostinger.com/horizons/templates  
[34] https://support.hostinger.com/en/articles/11741485-how-to-use-remix-templates-in-hostinger-horizons  
[35] https://www.hostinger.com/horizons/template-creator-program  
[36] https://www.hostinger.com/tutorials/hostinger-horizons#h-what-are-the-limitations-of-hostinger-horizons  
[37] https://firebase.google.com/docs/studio/overview  
[38] https://firebase.google.com/docs/studio/get-started  
[39] https://firebase.google.com/docs/studio/quotas-and-pricing  
[40] https://firebase.google.com/pricing  
[41] https://firebase.google.com/docs/studio/customize-workspace  
[42] https://firebase.google.com/docs/studio/deploy-app
