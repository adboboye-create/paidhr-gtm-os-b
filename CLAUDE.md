# PaidHR GTM Context OS

## Company
PaidHR (paidhr.com): Lagos-based HR, payroll and statutory remittance platform with earned wage access, for businesses in Nigeria, Kenya and South Africa (source: context/docs/research/company.md).

## How this folder works
- `.claude/skills/`: reusable Claude skills for repeat GTM tasks. Read when a task matches a skill.
- `context/icp/`: `icp.md` (five-layer ICP, non-fits), `personas.md` (champion, buyer, influencer). Read before any targeting, list building or copy.
- `context/positioning/`: `positioning.md`, `value-proposition.md`, `competitors.md`. Read before writing anything that compares or pitches.
- `context/messaging/`: `messaging.md` (core message, pillars), `facts.md` (the only allowed names, numbers and claims). Read before writing any copy.
- `context/brand-kit/`: `brand.md` (tone, key phrases). Read before producing any customer-facing asset.
- `context/docs/`: `case-studies.md` (every customer story with source). Read before using a customer as proof.
- `context/docs/research/`: raw research notes with sources. Read when you need to verify or cite a company fact.
- `knowledge-base/playbooks/`: step-by-step repeatable GTM processes. Read before running a workflow.
- `knowledge-base/learnings/`: what worked, what failed and why. Read before planning a new campaign or test.
- `meetings/`: meeting notes and decisions. Read when a task references a past conversation.
- `output/campaigns/`: finished campaign assets and copy. Write here; read when iterating on past work.
- `output/outbound/`: outbound sequences, emails and call scripts. Write here; read when iterating on outbound.
- `output/social/`: social posts and content. Write here; read when iterating on social.
- `output/data/`: generated lists, enrichment and analysis outputs. Write here; read when a task needs past data.
- `inspiration/`: ads and examples to learn from. Read when drafting copy or creative for patterns to borrow.
- `tools/`: notes and specs for GTM tools and integrations. Read before using or wiring up a tool.
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
- **Miro** (MCP): diagrams, such as GTM system maps and workflow flows.
- **Notion** (MCP): where we publish finished docs. GitHub stays the source of truth; edit here first, then publish.

## Skills (`.claude/skills/`, from gtm-starter-kit)
- Strategy and copy: `signal-matrix` (ICP and signal matrix), `campaign-strategy` (outbound ideas), `build-workflow-spec` (one play into a spec), `campaign-copy` (emails and DMs from an approved spec), `prompt-builder` (per-row AI prompts).
- Clay build: `campaign-contract`, `clay-build-plan`, `design-clay-table-json`, `import-clay-table`, `build-clay`, `save-clay-schema`, `export-tables`.
- QA and cost: `campaign-qa`, `calculate-costs`, `workspace-cost-audit`, `inbox-placement-test`.
- Research and visuals: `crawl4ai` (free site crawl), `agent-browser` (browser automation), `miro-gtm-flowchart` (GTM system on Miro).
- Voice notes (from OpenWhispr): `openwhispr-cli` (notes and transcriptions from the terminal), `openwhispr-api` (REST API and MCP server reference).
