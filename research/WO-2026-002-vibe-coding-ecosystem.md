# WO-2026-002 Research: Vibe Coding Prompt Libraries and Cursor Rules Ecosystem

Date: 2026-02-15

## Scope and Method

This research focuses on coding-oriented prompt libraries and rule ecosystems (not general prompt marketplaces). For paid products, only publicly visible listings, demos, and reviews were used.

## 1) VibeCodex.io Profile

### What it offers
- VibeCodex positions itself as a coding prompt library for developers (marketed as a large curated collection), with topic areas such as app development, debugging, and API work.
- The `.io` site currently presents a waitlist/"coming soon" experience rather than a fully browsable production library.

### How prompts are structured
Public copy emphasizes structured prompts that include:
- difficulty level
- estimated completion time
- required tech stack
- clear implementation steps

### Community size (publicly visible)
- VibeCodex landing copy claims "Trusted by 1000+ developers worldwide" (captured 2026-02-15).
- The public site does not expose a transparent live member counter, ratings feed, or a canonical OSS metrics panel (captured 2026-02-15).

### Takeaway
- VibeCodex appears to be in an early commercialization phase: strong positioning and packaging, limited public proof of mature library scale today.

## 2) cursor.directory and awesome-cursorrules

## 2a) cursor.directory Profile

### How rules are organized
- `cursor.directory/rules` is organized via language/framework/tool tags (examples visible on listing: TypeScript, React, Python, Node.js, Next.js, etc.).
- The project also markets a downloadable rules template with "300+" rules and "170+" MCP servers.

### How contributions work
- The current canonical GitHub project is `leerob/directories` (with `pontusab/directories` redirecting there).
- Contribution flow in `CONTRIBUTING.md` is PR-based:
  1. edit a rule file in `apps/web/src/data/rules/`
  2. run `pnpm run check-rules` to validate structure
  3. submit PR for review
- Repository activity shows a broad contributor base: 146 contributors (captured 2026-02-15).

### How users consume it
- Users browse the web directory and copy rule text into Cursor rules (project docs and templates show `.cursor/rules` and related Cursor rule usage flow).

### Community size (publicly visible)
- Site claims: 72.1K+ members, 300+ rules, and 170+ MCP servers (captured 2026-02-15).
- GitHub repo (`leerob/directories`) shows 3.9k stars, 639 forks, 0 open issues, and 28 watchers (captured 2026-02-15; GitHub UI rounded stars).

## 2b) awesome-cursorrules Profile

### How rules are organized
- Repository is explicitly organized by category in `rules/` and in README sections:
  - language-specific rules
  - framework-specific rules
  - AI assistant behavior rules
  - workflow/automation rules
  - tooling/integration rules

### How contributions work
- Contribution path is straightforward PR-based curation:
  1. add/update `.mdc` files under `rules/`
  2. update README with file link and description
  3. open PR with rationale and examples

### How users consume it
- Users copy curated `.mdc` rule files into their own Cursor projects.
- Consumption is mostly copy/adapt, not packaged distribution.

### Community size (publicly visible)
- GitHub repo (`PatrickJS/awesome-cursorrules`) shows 37.9k stars, 3.2k forks, 44 open issues, 306 watchers, and 68 contributors (captured 2026-02-15; GitHub UI rounded stars/forks).

### Takeaway across both
- `cursor.directory` is a productized discovery surface with a backing OSS pipeline.
- `awesome-cursorrules` is a community-first, GitHub-native canonical list.

## 3) Notion-Based Vibe Coding Prompt Kits (Paid and Free)

## Paid examples
- **Gumroad: "The Vibe Coding Prompt Kit"**: listed at $18, includes Notion template access, and shows 5 stars from 17 reviews (captured 2026-02-15).
- **Packaging pattern**: most paid kits bundle prompts + a Notion workspace + optional community access, then distribute via creator storefronts (captured 2026-02-15).

## Free examples
- **Notion Template: "Vibe Coding Prompts by Stotion"**: free, with 13.6K views and 4.95/5 from 80 ratings (captured 2026-02-15).
- **Notion Template: "Vibe Coding Hub"**: free, with 17K views and 4.95/5 from 59 ratings (captured 2026-02-15).
- **Gumroad: "Vibe Coding Starter Kit"**: listed at $0+ with Notion template access and 5 stars from 2 reviews (captured 2026-02-15).

## How this segment works
- Distribution is creator-led (Notion Template Gallery + Gumroad pages).
- Consumption is copy/paste from Notion databases/checklists into AI coding tools.
- Curation quality signal is mostly social proof (ratings/views), not benchmarked implementation outcomes.

### Takeaway
- Notion kits are effectively "prompt ops in a document": fast to ship and easy to monetize, but usually lightweight on reproducibility and deployment guarantees.

## 4) Vibe Coding Framework (docs.vibe-coding-framework.com)

### What it is
- The Vibe Coding Framework describes a structured methodology for converting ideas into production-ready apps with an explicit multi-layer prompt architecture.
- Current docs define five core modules: **S.C.A.F.F**, **V.E.R.I.F.Y**, **S.H.I.E.L.D**, **R.A.F.T**, and **C.O.R.E** (captured 2026-02-15).

### How it differs from simple prompt lists
- It behaves more like a process framework (playbook + architecture) than a flat prompt catalog.
- It provides a repeatable thinking model, not just standalone one-off prompts.

### Community size (publicly visible)
- Public docs pages do not publish a transparent member count or canonical repository metrics panel (captured 2026-02-15).
- The docs do show active maintenance signals (for example, "Last updated 10 months ago" on core pages, captured 2026-02-15).

### Takeaway
- VCF sits between a prompt library and a full generator: stronger methodology than marketplace prompt packs, but still primarily guidance-oriented rather than an end-to-end deployment system.

## 5) Analysis: Prompt Libraries vs App Generators

The practical line is **runtime responsibility**:

- **Prompt library / rule directory**: gives instructions/context so the human + AI can code faster.
- **Framework**: provides a repeatable approach for planning and generating code quality.
- **App generator**: owns the path from spec to running software (including deployable output).

By this lens:
- VibeCodex, cursor.directory, awesome-cursorrules, and most Notion kits are primarily **coding assistance libraries**.
- Vibe Coding Framework is a **methodology framework**.
- Seeds is in the **app generator** category (see section 7).

## 6) What Popular Prompts/Rules Have in Common

Across the highest-traction examples, common traits are:
- **Narrow scope + strong specificity**: prompts target concrete tasks/stacks (not generic "build me X").
- **Explicit constraints**: coding standards, architecture boundaries, and output format expectations are spelled out.
- **Reusable structure**: checklists, sections, and template fields make prompts composable.
- **Tool-aware packaging**: `.mdc` files and Cursor rule conventions reduce friction.
- **Workflow leverage**: popular entries reduce repeated setup decisions (architecture defaults, testing expectations, file structure conventions).

## 7) How Seeds Differs (End-to-End Deployment vs Coding Assistance)

Seeds' docs define a stronger contract than prompt libraries: from one seed prompt to generated code **and deployment target selection** that ends with a working URL.

### Core difference
- Most ecosystem offerings help users write code faster.
- Seeds is designed to deliver an operational outcome: generated software + deployment path.

### Comparison snapshot

| Dimension | Prompt Libraries / Cursor Rules | Seeds |
|---|---|---|
| Primary value | Better coding guidance | Full generation + deployment flow |
| Output guarantee | Better prompts/rules | Running application URL target |
| Deployment responsibility | User-driven | Built into seed flow |
| Packaging | Prompt snippets, `.mdc`, Notion docs | Self-contained generative seed DNA |
| Consistency model | Community curation | Reverse-seed extraction + workflow contract |

## 8) Implications for Seeds Positioning

- Position against prompt libraries as a **delivery system**, not a better prompt catalog.
- Borrow ecosystem strengths (clarity, reusable structure, task-specific rules), but keep differentiation centered on **end-to-end deployability**.
- If Seeds adds prompt/rule surfaces later, they should funnel into seed execution and deployment outcomes, not become a standalone snippet marketplace.

## Sources

- https://vibecodex.io/
- https://vibecodex.dev/
- https://vibecodex.dev/blog/prompt-library-for-vibe-coding
- https://cursor.directory/
- https://cursor.directory/rules
- https://cursor.directory/template
- https://github.com/leerob/directories
- https://github.com/pontusab/directories
- https://github.com/PatrickJS/awesome-cursorrules
- https://www.notion.com/templates/vibe-coding-prompts-by-stotion
- https://www.notion.com/templates/vibe-coding-hub
- https://gofundltd.gumroad.com/l/vibe-coding-prompt-kit
- https://gofundltd.gumroad.com/l/vibe-coding-starter-kit
- https://docs.vibe-coding-framework.com/
- https://docs.vibe-coding-framework.com/fundamentals/scaff
- https://docs.vibe-coding-framework.com/vibe-coding-framework/overview
- docs/concept.md
- README.md
