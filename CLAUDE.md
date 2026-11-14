# PaidHR GTM Context OS

## Company
PaidHR (paidhr.com): Lagos-based HR, payroll and statutory remittance platform with earned wage access, for businesses in Nigeria, Kenya and South Africa (source: context/docs/research/company.md).

## How this folder works
- Root: `README.md` (what this repo is, not affiliated with PaidHR), `THIRD-PARTY.md` (licenses for adapted code and skills), `.gitignore`, `.env` (empty, gitignored).
- `.claude/`: `settings.json` (enables the Miro plugin, tracked), `settings.local.json` (sets `TREG_CONFIG`, gitignored), `skills/` (reusable Claude skills, see Skills below). Read a skill when a task matches it.
- `context/icp/`: `icp.md` (five-layer ICP, non-fits), `personas.md` (champion, buyer, influencer), `signal-matrix.md` (segments x personas, 12 scored buying signals, workflow tracker). Read before any targeting, list building or copy.
- `context/positioning/`: `positioning.md`, `value-proposition.md`, `competitors.md`. Read before writing anything that compares or pitches.
- `context/messaging/`: `messaging.md` (core message, pillars), `facts.md` (the only allowed names, numbers and claims, incl. Kenya and Ghana). Read before writing any copy.
- `context/brand-kit/`: `brand.md` (tone, key phrases). Read before producing any customer-facing asset.
- `context/docs/`: `case-studies.md` (every customer story with source), `gtm-system.md` (12-step outbound system, tools and decisions). Read before using a customer as proof or changing the system.
- `context/docs/research/`: raw research with sources: `company.md`, `customers.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md`, `customer-videos.md`, `social-proof-sources.md` (quote bank H1-H9, F1-F10), `kenya.md`, `ghana.md`, `treg-enrich-paidhr-2026-11-14.json`; `raw/` holds treg JSON pulls and video transcripts. Read when you need to verify or cite a company fact.
- `diagrams/`: `paidhr-gtm-system.json` (flowchart spec) and `.svg`. The Miro board is newer than the SVG (logos removed).
- `knowledge-base/playbooks/`: `workflow-anatomy.md` (mother intent catalog, spec anatomy), `signal-matrix-framework.md`, `copy-frameworks.md`, `copy-iron-laws.md`, `copy-bans.yaml`, `linkedin-dm-frameworks.md`, `clay/` (`expert.md`, `iron-laws.md`, `formulas.md`, `prompts.md`, `actions-data-credits.md`), `templates/facts-template.md`. Read before running a workflow.
- `knowledge-base/learnings/`: what worked, what failed and why. Empty until the first sends. Read before planning a new campaign or test.
- `meetings/`: meeting notes and decisions. Empty so far. Read when a task references a past conversation.
- `output/campaigns/`: `campaign-strategy.md` (20 ideas C1-C20, C1 recommended); `payroll-hr-role-posted/` (C1: `workflow-spec.md`, `sequencer-export.md`); `new-hr-leader-180-days/` (C8: `workflow-spec.md`, Clay build guide, clay-flow `.json`/`.html`/`.png`); `social-proof/social-proof-pack.md` (DRAFT). Write here; read when iterating on past work.
- `output/outbound/`: outbound sequences, emails and call scripts. Empty so far. Write here; read when iterating on outbound.
- `output/social/`: social posts and content. Empty so far. Write here; read when iterating on social.
- `output/data/`: `c1-volume-check-2026-11-14.md` (Jobberman count for C1). Write here; read when a task needs past data.
- `inspiration/`: `clay-archie-jessica-jin-linkedin.mp4` (Clay brand video post). Read when drafting copy or creative for patterns to borrow.
- `tools/`: `rex/` (Clay via your browser session, plus the ClayLens extension and table registry), `crawl4ai/` and `agent-browser/` (install notes). Read before using or wiring up a tool.
- `weekly-priorities/`: one file per ISO week with the week's priorities. Read at the start of every session.
- `work-log/`: one file per ISO week logging every change. Read at session start; append after every change.

## Rules
- Cite a source (URL or file path) for every company fact.
- Never invent numbers. If a figure is unknown, say so and mark it TBD.
- No em dashes in any copy.
- Ask before sending or publishing anything.
- Log every change in this week's work log (`work-log/YYYY-Www.md`) with a timestamp.

## Tools
- **treg** (CLI): paid data lookups (enrichment, company and people data). Check the price with `treg catalog get <id>` before every call. Login lives in `.treg/` via `TREG_CONFIG`.
- **GitHub** (`git`, `gh` CLI): source of truth, https://github.com/adboboye-create/paidhr-gtm-os-b (public). Many sessions share this checkout: stay on `main`, stage only your own files.
- **Miro** (MCP, plugin in `.claude/settings.json`): diagrams, such as GTM system maps and workflow flows. Board: [PaidHR GTM System](https://miro.com/app/board/uXjVENnRs9c=/).
- **Notion** (MCP, via the marketing plugin): where we publish finished docs. GitHub stays the source of truth; edit here first, then publish. Published Context OS: [PaidHR GTM OS](https://app.notion.com/p/4181b751cd3481d4a174e0147d8eeb70) (private draft; mirrors `context/` and `output/`, raw research excluded; republish after edits).
- **Clay**: enrichment and campaign tables. Driven through Rex (`tools/rex/`, your browser session, no API key) and the Clay skills below.
- **crawl4ai** (local, free): site crawls into Markdown. Install notes in `tools/crawl4ai/README.md`.
- **agent-browser** (CLI): pages that need a real browser (e.g. MyJobMag). Install notes in `tools/agent-browser/README.md`.
- **yt-dlp** and **Whisper large-v3** (local, free): customer video captions and transcripts in `context/docs/research/raw/`.
- **curl**: free checks of public pages; respect robots.txt (see `output/data/c1-volume-check-2026-11-14.md`).
- Planned in `context/docs/gtm-system.md`, not connected yet: HubSpot (CRM), n8n (scheduling, reply routing), PlusVibe (sending). LinkedIn sending tool: TBD.

## Skills (`.claude/skills/`, from gtm-starter-kit)
- Strategy and copy: `signal-matrix` (ICP and signal matrix), `campaign-strategy` (outbound ideas), `build-workflow-spec` (one play into a spec), `campaign-copy` (emails and DMs from an approved spec), `prompt-builder` (per-row AI prompts).
- Clay build: `campaign-contract`, `clay-build-plan`, `design-clay-table-json`, `import-clay-table`, `build-clay`, `save-clay-schema`, `export-tables`.
- QA and cost: `campaign-qa`, `calculate-costs`, `workspace-cost-audit`, `inbox-placement-test`.
- Research and visuals: `crawl4ai` (free site crawl), `agent-browser` (browser automation), `miro-gtm-flowchart` (GTM system on Miro).
- Voice notes (from OpenWhispr): `openwhispr-cli` (notes and transcriptions from the terminal), `openwhispr-api` (REST API and MCP server reference).
