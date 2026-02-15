# WO-2026-004 Research: OSS App Scaffolding Tools

Date: 2026-02-15

## Scope and Method
This memo analyzes pre-AI scaffolding ecosystems relevant to Seeds: Yeoman, Cookiecutter, create-react-app (CRA), create-t3-app, Projen, and Hygen.

I limited scope to project scaffold generators (not package managers/build tools), and used primary sources (official docs, official GitHub repos, and official project posts) for current state.

All GitHub star counts and latest-release facts below are a single snapshot as of 2026-02-15.

## Executive Summary
- The winning pattern was a low-friction default path plus strong trust distribution (official ownership, predictable output, and discoverable templates).
- The losing pattern was ungoverned template sprawl: quality variance, stale templates, weak discovery, and no durable incentive model for maintainers.
- CRA succeeded early because it optimized time-to-first-app. CRA later declined because front-end architecture moved from SPA bootstrap toward framework-led full-stack patterns; React formally deprecated CRA on February 14, 2025.
- Yeoman pioneered extensible scaffolding and still ships releases, but the broad generator marketplace model fragmented and lost mindshare versus framework-specific CLIs.
- Projen and create-t3-app show a different durable model: fewer templates, stronger central control, and opinionated defaults.

## Tool Profiles (History + Current State)

### 1) Yeoman
- How it works: CLI (`yo`) runs generators (npm packages) in a composable workflow.
- Template format: generator code plus template files; Yeoman docs emphasize EJS-style templating and destination transforms.
- Community size: `yo` has ~3.9k GitHub stars (as of 2026-02-15); Yeoman site claims 5,600+ available generators.
- Current status: Active but niche/declined mindshare. Latest GitHub release is `v6.0.0` (November 12, 2025, as of 2026-02-15); Yeoman published “Yeoman’s Next Chapter Maintenance Reboot” on January 9, 2025, acknowledging lost relevance and restarting maintenance.

### 2) Cookiecutter
- How it works: Render a project from a template repo + prompts.
- Template format: folder containing `cookiecutter.json` (variables), Jinja2 placeholders, and optional pre/post generation hooks.
- Community size: ~24.7k GitHub stars (as of 2026-02-15).
- Current status: Active, mature, lower-churn cadence. Latest GitHub release is `2.6.0` (February 21, 2024, as of 2026-02-15).

### 3) create-react-app (CRA)
- How it works: `npx create-react-app my-app` creates a React app with a preconfigured toolchain.
- Template format: npm templates named `cra-template-*` (default and custom templates).
- Community size: ~104k GitHub stars (as of 2026-02-15).
- Current status: Deprecated. CRA site states deprecation; React announced deprecation on February 14, 2025. Latest GitHub release is `v5.0.1` (April 12, 2022, as of 2026-02-15).

### 4) create-t3-app
- How it works: Interactive CLI chooses stack modules and generates a typed full-stack app.
- Template format: internal repository templates (including `.template` files with interpolation placeholders) synthesized from CLI choices.
- Community size: ~28.5k GitHub stars (as of 2026-02-15).
- Current status: Active. Latest GitHub release is `create-t3-app@7.40.0` (November 5, 2025, as of 2026-02-15).

### 5) Projen
- How it works: Define project configuration in code (`.projenrc.*`), then synthesize files. Treated as “project-as-code” scaffolding + lifecycle management.
- Template format: project types/classes and synthesis rules; extensible via core project types and external jsii modules.
- Community size: ~2.9k GitHub stars (as of 2026-02-15).
- Current status: Active. Latest GitHub release is `v0.99.12` (February 12, 2026, as of 2026-02-15), with very high release cadence.

### 6) Hygen
- How it works: File-system-local code generator for repetitive scaffolding tasks.
- Template format: `_templates` directory with EJS templates and optional frontmatter controls (`to`, `inject`, shell commands).
- Community size: ~6k GitHub stars (as of 2026-02-15).
- Current status: Low-churn and likely maintenance-mode/quasi-dormant (not formally abandoned). Latest GitHub release is `v6.2.11` (September 7, 2022, as of 2026-02-15).

## Comparison Table

| Tool | Primary Unit | Contribution Model | Discovery Model | Maintenance Burden Pattern |
|---|---|---|---|---|
| Yeoman | Generator package (`generator-*`) | Publish npm generator with `yeoman-generator` keyword | Yeoman generator index + npm/GitHub search | Distributed; long-tail generator rot risk |
| Cookiecutter | Template repo | Any Git repo can be a template | Mostly GitHub/distributed lists | Distributed; quality and freshness uneven |
| CRA | npm template (`cra-template-*`) + core CLI | Template packages + core changes | CRA docs + npm naming convention | Core inertia became bottleneck |
| create-t3-app | Centralized option matrix + internal templates | Mostly core repo PRs | Official docs/CLI choices | Centralized quality, lower variance |
| Projen | Project type/module | Core PRs or external modules (`--from`) | CLI discovers project types, including external modules | Strongly opinionated; high automation, tighter governance |
| Hygen | Local template tree (`_templates`) | In-repo templates; optional bootstrap from remote repo | No dominant central registry | Team-local maintenance; low global discoverability |

## Why CRA Succeeded and Yeoman Faded (Relative)

### CRA’s early success factors
- One-command onboarding and immediate time-to-value.
- Official React ecosystem trust and documentation gravity.
- Opinionated defaults reduced decision fatigue.

### CRA’s decline factors
- React ecosystem shifted toward framework-first architectures and integrated routing/data/SSR concerns.
- React now explicitly recommends frameworks and has deprecated CRA (February 14, 2025).
- Long period without core release velocity (latest GitHub release `v5.0.1` on April 12, 2022, as of 2026-02-15) reduced confidence for new adopters.

### Yeoman’s early success factors
- First major generalized scaffolding ecosystem in JavaScript.
- Generator composability and very large catalog (5,600+ generators).

### Yeoman’s fade factors
- Marketplace fragmentation: varying quality, stale dependencies, uneven UX between generators.
- Framework-specific CLIs captured happy paths with tighter guardrails.
- Yeoman itself acknowledges relevance decline while rebooting maintenance (January 9, 2025).

Inference: At ecosystem scale, trust and curation beat raw template count.

## Template Contribution, Discovery, and Maintenance by Ecosystem

### Yeoman
- Contribute: publish `generator-name` packages and tag with `yeoman-generator` keyword.
- Discover: official generator listing plus npm/GitHub search.
- Maintain: each generator owner maintains independently; platform-level quality control is weak.

### Cookiecutter
- Contribute: publish a Git template repo with `cookiecutter.json` and template files.
- Discover: decentralized via GitHub and template collections.
- Maintain: template owners maintain independently; compatibility drift is common at scale.

### CRA
- Contribute: publish `cra-template-*` packages.
- Discover: CRA docs and npm conventions.
- Maintain: depends on both template maintainer and central CLI behavior; once core deprecates, ecosystem value collapses quickly.

### create-t3-app
- Contribute: primarily via upstream PRs to template/options in core repo.
- Discover: controlled through official CLI prompts and docs.
- Maintain: central maintainers enforce quality/consistency; smaller extension surface.

### Projen
- Contribute: core project types by PR, or external project types/modules consumed with `projen new --from`.
- Discover: project type auto-discovery in CLI.
- Maintain: synthesis model reduces drift but increases coupling to projen versioning.

### Hygen
- Contribute: template files live in repo-local `_templates`; can import starter templates from GitHub repos.
- Discover: mostly local/team-internal reuse, little marketplace discoverability.
- Maintain: owned by each team/repo, which keeps relevance high for local use but weak for cross-org sharing.

## What Breaks at 1000+ Templates
1. Discovery entropy: users cannot distinguish high-quality templates quickly.
2. Taxonomy collapse: tags/categories diverge and search precision drops.
3. Template rot: dependency, API, and framework drift outpace maintainer updates.
4. Trust collapse: users encounter broken/outdated scaffolds and stop trusting the catalog.
5. Security exposure: unvetted template code and generation hooks become supply-chain risk.
6. Support overload: issue triage shifts from product bugs to template-specific breakage.
7. Fork explosion: near-duplicate templates fragment usage and maintenance effort.

## Lessons for Seeds

### 1) Template Format
- Use a constrained manifest-first format for 80% of cases (metadata, inputs, outputs, compatibility bounds).
- Allow escape hatches (script hooks) but sandbox and policy-gate them.
- Version template contracts explicitly (e.g., `seed_api_version`) to enable migrations.

### 2) Discovery UX
- Default to curated paths by workflow/outcome, not raw template browsing.
- Rank by verified quality signals: freshness, successful generation rate, deployment pass rate, and security checks.
- Treat search facets (profession, workflow, stack, hosting target) as first-class, enforced taxonomy.

### 3) Quality Control
- Require CI verification on every template revision against declared compatibility matrix.
- Auto-deprecate templates on repeated generation/deploy failures.
- Add provenance + review state badges: `official`, `verified`, `community`.

### 4) Community Model
- Two-tier ecosystem:
  - Tier A: centrally maintained “official” seeds for top workflows.
  - Tier B: community seeds with strict submission checks and periodic re-verification.
- Reward maintainers with visibility and usage analytics; prune inactive templates aggressively.

## Practical Direction for Seeds (Decision Heuristics)
- Optimize for trust density, not catalog size.
- Keep the default path opinionated and short.
- Make template health observable and automatic.
- Prefer composable parameters over unconstrained custom scripts.
- Build deprecation/migration as a first-class lifecycle feature.

## Sources
- GitHub stars/releases in this memo were re-checked on 2026-02-15.
- Yeoman homepage (generator ecosystem size): https://yeoman.io/
- Yeoman authoring docs (generator naming/keyword/discovery): https://yeoman.io/authoring/
- Yeoman `yo` repository (stars/releases): https://github.com/yeoman/yo
- Yeoman maintenance update (relevance + reboot): https://yeoman.io/blog/maintenance-reboot
- Cookiecutter repository (stars/releases): https://github.com/cookiecutter/cookiecutter
- Cookiecutter docs (template internals/hooks): https://cookiecutter.readthedocs.io/en/stable/tutorials/tutorial2.html
- CRA repository (stars/releases/status banner): https://github.com/facebook/create-react-app
- CRA deprecation notice: https://create-react-app.dev
- React blog deprecating CRA (February 14, 2025): https://react.dev/blog/2025/02/14/sunsetting-create-react-app
- CRA custom templates docs (`cra-template-*`): https://create-react-app.dev/docs/custom-templates/
- create-t3-app repository (stars/releases + templates): https://github.com/t3-oss/create-t3-app
- create-t3-app docs (CLI behavior): https://create.t3.gg/en/installation
- Projen repository (stars/releases): https://github.com/projen/projen
- Projen docs (project types/extensions/discovery): https://projen.io/docs/concepts/projects/project-types/
- Hygen repository (stars/releases + template model): https://github.com/jondot/hygen
