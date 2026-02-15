# WO-2026-003 Research: Yohei Nakajima (BabyAGI, Ditto) & Generative Agent Builders

_Date: 2026-02-15_

## Executive Summary
Yohei Nakajima’s core contribution is not a polished production product; it is a sequence of simple, legible agent design patterns shared in public. BabyAGI (2023) helped popularize task-planning agent loops. Ditto (2024) and BabyAGI-2o (2024) showed a compressed pattern: one LLM loop, a tiny toolset, and dynamic tool creation.

For Seeds, the key lesson is his speed and architecture minimalism. The gap is productionization and market framing: Seeds can win where Yohei intentionally does not focus deeply (deployment reliability, profession-specific workflow mapping, and reusable "DNA extraction" from proven OSS projects).

## 1) Ditto Profile

### What Ditto Is
Ditto is presented as "the simplest self-building coding agent" focused on generating Flask apps from natural language in a no-code web interface.

### How It Works
Ditto runs a single LLM loop with a small toolset. Based on Yohei’s demo/interview and repo docs, the loop plans and executes file operations until completion:
- create directories
- create files with generated code
- update files when errors appear
- fetch/review existing code
- call a completion tool to exit

In the Every transcript, Yohei describes this as a single-file script (~500 lines) that uses LiteLLM and iterates until the task is complete.

### What It Generates
Ditto can generate a multi-file Flask project skeleton and app code:
- `routes/`
- `templates/`
- `static/`
- entrypoint/server wiring in `main.py`

In the podcast demo it generated a Snake-like app and a simple contact/call-tracking app with frontend and backend files.

### Limitations
Observed/declared constraints from public sources:
- Prototype quality: Yohei explicitly positions it as simple, not superior to Replit Agent, and does not claim parity with Devin.
- Reliability issues: demo output was sometimes incomplete/buggy (example: Snake app rendered but controls failed in one run).
- One-shot workflow: he notes it is effectively "one-time use" in the shared demo context and often needs reset/restart.
- Maintenance expectations: README says it was a quick exploration, with limited maintainer attention to PRs.
- Security/robustness limits are implicit in the overall experimental framing (inference from repeated "not production" framing across related repos).

### GitHub Stats (as observed on 2026-02-15)
Repository: `yoheinakajima/ditto`
- Stars: 1.1k
- Forks: 162
- Issues: 4
- Pull Requests: 4
- Watchers: 13
- Commits: 11
- Contributors: 3
- License: MIT

### Community Reception
- Strong signal for an experimental repo: ~1k+ stars for a small, explicitly non-production script.
- Framing resonated with builders: "simple loop + tools" narrative spread via X threads and interviews.
- Reception appears curiosity-led rather than enterprise adoption-led (inference), based on public demo coverage and prototype disclaimers.

## 2) BabyAGI Evolution: Task Agent -> Self-Building Coding Agent

## Timeline
| Period | Stage | Key Shift |
|---|---|---|
| Mar-Apr 2023 | Original Task-Driven Agent / BabyAGI | Loop of execution -> task creation -> reprioritization with vector-memory context (Pinecone/Chroma/Weaviate). |
| 2023 iterations | BabyBee/Cat/Deer/Elf/Fox era | Repeated design-pattern experimentation in public; agent-loop refinement. |
| Sep 2024 | `babyagi_archive` + new `babyagi` | Split: archive original; reposition new BabyAGI as function framework (`functionz`) with DB-backed functions, dependencies, keys, logs, dashboard. |
| Sep 2024 | "3 levels of self-building agents" threads | Conceptual model moves from fixed tool libraries to dynamic tool creation. |
| Oct 2024 | Ditto | Minimal coding-agent variant for multi-file Flask app generation. |
| Oct 2024 | BabyAGI-2o | Further compression: ~174-line self-building general agent with 3 starter tools and dynamic tool creation/installation. |

## Key Design Decisions Across the Evolution
- **Simplicity-first architecture**: keep loop design minimal so others can understand/modify quickly.
- **Function-centric abstraction**: treat tools/skills/API calls as functions.
- **Composable reuse**: smaller functions calling each other for reliability and modularity.
- **Graph + metadata**: store dependencies/imports/keys/logs around functions, not just raw code text.
- **Self-building direction**: move from static toolsets toward runtime creation of missing capabilities.
- **Public experimentation**: release rough versions quickly, absorb feedback, iterate visibly.

## 3) Yohei’s Public Thinking on AI Building Software

### Theme A: "Simple patterns unlock ecosystems"
In interviews, Yohei argues BabyAGI became influential because the core pattern was small and understandable, so many people could imagine improvements.

### Theme B: "Build the simplest thing that can build itself"
This phrase appears directly in BabyAGI materials and threads. The emphasis is bootstrapping: start with minimal primitives, let the agent extend capabilities.

### Theme C: "Deterministic at interfaces, flexible inside"
In interview discussion, he distinguishes internal flexible architectures from deterministic external interaction (APIs/tools) for reliability.

### Theme D: "Modularity over monoliths"
He repeatedly emphasizes modular workflows/tools that can be recomposed by agents later, both as a product principle and an investment lens.

### Theme E: "Build-in-public as R&D strategy"
His process is to publish prototypes, gather community feedback, and iterate quickly; this also creates market and founder discovery loops for him.

### Theme F: "Experimental, not production"
He consistently warns that these projects are experiments for inspiration/discussion, not hardened production systems.

## 4) Other Notable Generative Agent Builders (Emerging/Adjacent)

| Builder | Why It Matters | Public Signal |
|---|---|---|
| OpenHands (`OpenHands/OpenHands`) | Open-source software-development agent platform; broad community and active ecosystem. | 67.8k stars, 8.4k forks (GitHub). |
| SWE-agent (`SWE-agent/SWE-agent`) | Research-driven coding agent focused on solving real GitHub issues; benchmark-centric development. | 18.5k stars, 2k forks; active SWE-bench claims/news in README. |
| GPT-Engineer (`AntonOsika/gpt-engineer`) | Early influential codegen CLI/community project; helped normalize NL->multi-file project generation workflows. | 55.2k stars, 7.3k forks (GitHub). |
| Cognition / Devin | Commercial "AI software engineer" category-shaper; strong mindshare and ongoing product/model releases. | Official product positioning and active release cadence on cognition.ai. |

## 5) What Yohei Got Right (Seeds Should Learn)
- Publish minimal but complete loops that people can run and modify quickly.
- Keep architecture legible: fewer abstractions, explicit tools, clear loop boundaries.
- Use function-level composition and logging as the unit of agent learning/reuse.
- Treat model progress as leverage: architecture should improve when model/tool-calling quality improves.
- Use public iteration as a distribution channel and feedback engine.

## 6) Gaps Yohei Leaves Open That Seeds Can Fill

### 1. Deployment
Yohei’s projects are mostly exploratory repos and demos. Seeds can differentiate with consistent path-to-running software and deployment outcomes.

### 2. Profession Mapping
Yohei optimizes for general experimentation. Seeds already has profession/workflow schemas and can map output to real operator jobs and repeatable workflows.

### 3. DNA Extraction From Proven OSS
Yohei’s emphasis is self-building loops and function tooling. Seeds’ reverse-seed process (repo scoring + extraction) is a stronger path to reproducible, domain-grounded app generation.

### 4. Reliability and Operability
He explicitly labels projects as non-production. Seeds can own deterministic packaging, quality gates, and operational guardrails.

### 5. Portfolio-Level Standardization
Yohei’s work is highly creative and fast, but heterogeneous. Seeds can standardize templates, scoring, and output contracts across many seeds.

## 7) Practical Direction for Seeds
1. Preserve a "minimal loop" seed template inspired by Ditto/BabyAGI-2o for rapid prototyping.
2. Layer Seeds-specific deployment and workflow contracts on top of that minimal loop.
3. Encode profession-specific function packs and schema constraints rather than fully open-ended self-building by default.
4. Add reuse memory at function/workflow level, but gate with quality checks before promoting generated code into reusable seed DNA.
5. Keep a public build log cadence: frequent small releases beat infrequent large launches in this segment.

## Sources
- BabyAGI repo: https://github.com/yoheinakajima/babyagi
- BabyAGI archive: https://github.com/yoheinakajima/babyagi_archive
- Ditto repo: https://github.com/yoheinakajima/ditto
- BabyAGI-2o repo: https://github.com/yoheinakajima/babyagi-2o
- Yohei blog, "Birth of BabyAGI": https://yoheinakajima.com/birth-of-babyagi/
- Yohei blog, "The Future of Autonomous Agents": https://yoheinakajima.com/the-future-of-autonomous-agents/
- Thread archive (Ditto thread): https://threadreaderapp.com/thread/1846289276151255187.html
- Thread archive (Yohei thread index): https://threadreaderapp.com/user/yoheinakajima
- Rattibha archive (BabyAGI 2 thread): https://en.rattibha.com/thread/1840678823681282228
- Every transcript, "Building AI That Builds Itself": https://every.to/podcast/transcript-of-building-ai-that-builds-itself
- OpenHands repo: https://github.com/OpenHands/OpenHands
- SWE-agent repo: https://github.com/SWE-agent/SWE-agent
- GPT-Engineer repo: https://github.com/AntonOsika/gpt-engineer
- Cognition: https://cognition.ai/
