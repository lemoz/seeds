# PRESS RELEASE — Seeds

_Working-backwards document. This is the north star, not a real press release (yet)._

---

**FOR IMMEDIATE RELEASE**

## Seeds: The Open-Source Library That Turns a Prompt Into Deployed Software

**Newark, NJ** — Seeds, an open-source project from Dandelion Industries, today surpassed 1,000 published seeds — self-contained generative prompts that produce fully deployed, customized software when run with any coding agent. Covering 50+ professions and hundreds of common business workflows, Seeds has become the largest open catalog of AI-deployable software patterns in the world.

### The Problem

AI can write code. That's not the hard part anymore.

The hard part is knowing *what* to build. A marketing agency owner who needs a client approval portal doesn't know what database schema to use, what framework fits, or how to deploy it. They just know they're drowning in email threads and need a better way.

Today's options: hire a developer ($10K-$100K), learn to code (months), or use a SaaS tool that's 80% features you don't need at $50-$500/month forever. Coding agents like Claude Code, Codex, and OpenClaw changed the game — but they still need good instructions. "Build me a client portal" produces wildly different results depending on how you ask.

### What Seeds Solves

A **Seed** is a prompt that contains the DNA of a working application. It encodes the architecture, schemas, patterns, and deployment logic that a coding agent needs to generate production-quality software — not a demo, not a toy, a real tool you can hand to clients on day one.

```
Browse catalog → Pick your workflow → Run the seed → Answer 5 questions → Get a URL
```

That's it. No coding. No repo to clone. No infrastructure to understand. The seed IS the source code — compressed into a prompt that any coding agent can unpack.

### How It Works

**Step 1: Find your workflow.**
Seeds are organized by profession and outcome, not technology. A restaurant owner browses "Restaurant" and finds seeds for reservation systems, menu management, kitchen display boards, and customer feedback. A law firm finds client intake, document management, billing, and case tracking.

**Step 2: Run the seed.**
Open your coding agent — Claude Code, Codex, OpenClaw, or any agent that can generate files and execute commands. Paste the seed. It starts asking questions:

> Company name? Brand color? Default timezone? Where do you want to deploy?

**Step 3: Get your software.**
The agent generates every file, configures deployment, and pushes to your chosen platform. Five to thirty minutes later, you have a URL to working software, customized for your business, that you fully own.

### Agent-Agnostic by Design

Seeds don't lock you into one AI tool. They're plain text prompts — structured, yes, but fundamentally just well-crafted instructions. Any coding agent capable of generating files and running shell commands can plant a seed:

- **Claude Code** — Anthropic's coding agent
- **Codex** — OpenAI's coding agent  
- **OpenClaw** — Open-source AI assistant
- **Any future agent** — Seeds are prompts, not plugins

This is intentional. The value isn't in the tool — it's in the pattern. Seeds capture what *good software for this workflow* looks like, and any competent agent can execute on that.

### Where Seeds Come From

Every seed is created through a **reverse-seed process**: analyzing proven open-source projects and extracting their essential DNA.

Take scheduling software. Instead of cloning Cal.com and fighting with its specific stack, dependencies, and assumptions, we study *what makes Cal.com work* — the booking model, the availability logic, the calendar integration patterns — and encode that DNA into a seed. When an agent runs the seed, it generates fresh software inspired by those patterns, with current dependencies, your branding, and your deployment target.

The result is genuinely new software. Not a fork. Not a clone. Software that captures the *essence* of battle-tested tools without their baggage.

### The Catalog

Seeds ships with a browsable catalog website — the front door to the library.

**Browse by profession:**
> Accountant · Marketing Agency · Restaurant · Law Firm · Real Estate · Fitness Studio · Nonprofit · Freelancer · Healthcare Practice · Construction · ...

**Each profession maps to workflows:**
> Marketing Agency → Client Feedback & Approvals · Project Tracking · Client Dashboard · Knowledge Base · Performance Reporting

**Each workflow has one or more seeds:**
> Client Feedback & Approvals → Seed: approval-portal (from Focalboard patterns) · Seed: feedback-hub (from AppSmith patterns)

Mix and match. Run three seeds for three workflows and you have a custom software suite for your business, deployed in an afternoon.

### Open Source, Community-Driven

Seeds is fully open source under MIT license. The entire library — every seed, every profession mapping, every scoring rubric — lives on GitHub.

**Anyone can contribute:**
- Map a new profession and its workflows
- Create a seed for an unmapped workflow  
- Reverse-seed a new OSS project
- Improve an existing seed's success rate
- Add a new deployment target

The scoring rubrics are public. Every seed has a quality score. The community self-regulates what's good enough to publish. Bad seeds get improved or pruned. Good seeds get better with every contribution.

### Why This Matters

Software is too expensive. Not because code is hard to write — AI solved that — but because **knowing what to build** is hard. Seeds democratize that knowledge.

A solo accountant in rural Ohio should have access to the same quality practice management software as a Big Four firm. A food truck owner shouldn't need a $200/month SaaS subscription for something an AI can generate in 20 minutes from a well-written prompt.

Seeds makes the prompt the product. And prompts cost nothing to distribute.

### What Success Looks Like

- **1,000+ published seeds** covering every common business workflow
- **50+ professions** mapped with scored workflows
- **500+ OSS repos** reverse-seeded into the library
- **< 30 minutes** from seed to running URL, consistently
- **> 90% success rate** — seeds that work on first run
- **Active community** contributing new professions, seeds, and improvements
- **The default answer** to "I need software for X" becomes "check Seeds first"

### Quote

"We've been thinking about AI and software wrong. Everyone's building AI tools to help developers write code faster. But most people who need software aren't developers. They're dentists, restaurant owners, coaches, and freelancers. Seeds meets them where they are — describe what you need, get working software. The AI revolution in software isn't about writing code faster. It's about making code unnecessary."

— **Christopher Dossman, Founder, Dandelion Industries**

### About Seeds

Seeds is an open-source project by Dandelion Industries. It is a library of self-contained generative prompts that produce fully deployed, customized software when run with any coding agent. The project is community-driven, MIT-licensed, and free forever.

**GitHub:** github.com/lemoz/seeds  
**Catalog:** seeds.dandelion.industries _(coming soon)_  
**Parent:** Dandelion Industries

---

_This is a working-backwards document. The press release describes the future we're building toward. Every seed planted brings us closer._
