# Workflow spec: Payroll or HR role posted (Nigeria, Kenya, Ghana)

**Status:** STRUCTURE-APPROVED 2026-11-14 · amended 2026-11-14 (100-day cooldown; Nigeria + Kenya + Ghana; HR leads who joined from another company only; S6 never empty) · COPY-APPROVED 2026-11-14 (Nigeria only; E1 CEO + HR lead, E2, E3; 4 review fixes applied 2026-11-14) · Kenya and Ghana unblocked 2026-11-14 (PaidHR filing in KE and GH confirmed by user; KE/GH copy still to write) · launch blocked on sender identity (PaidHR sign-off not required, user decision 2026-11-14)

Built with `/build-workflow-spec` from idea **C1** in [campaign-strategy.md](../campaign-strategy.md). Methodology: [workflow-anatomy.md](../../../knowledge-base/playbooks/workflow-anatomy.md), [signal-matrix-framework.md](../../../knowledge-base/playbooks/signal-matrix-framework.md). Signal matrix row: **U1** in [signal-matrix.md](../../../context/icp/signal-matrix.md). Every name, number and claim comes from [facts.md](../../../context/messaging/facts.md) or `context/`. Anything unverified is a `{{placeholder}}` or marked TBD/INFERRED.

---

## 1. Mother intent (trigger) [ENGINE]

**An employer in Nigeria, Kenya or Ghana with 20 to 200 staff posted a payroll, compensation and benefits, or HR role in the last 30 days.**

- Catalog match: ⭐ **Hiring specific roles**.
- Why: the company is choosing right now between a person and a system for the work PaidHR does. The link from that choice to a software purchase is INFERRED ([signal-matrix.md](../../../context/icp/signal-matrix.md) §3), so the first send is the test.

## 2. Inclusion / exclusion [ICP]

### Include (all of)

| Box | Rule | Source |
|---|---|---|
| Geo | Company HQ in Nigeria, Kenya or Ghana, and the job located in the same country. Nigeria (Lagos first) is the proven market. Kenya is a listed PaidHR market. Ghana is not publicly listed, but the user confirmed on 2026-11-14 that PaidHR runs payroll and files remittances in both. No Kenyan or Ghanaian customer yet | [icp.md](../../../context/icp/icp.md), [company.md](../../../context/docs/research/company.md), [kenya.md](../../../context/docs/research/kenya.md), [ghana.md](../../../context/docs/research/ghana.md) |
| Size | 20 to 200 employees from company enrichment. Blank or outside 20 to 200 = excluded (no hold view) | [icp.md](../../../context/icp/icp.md) |
| Industry | Any of S1 logistics, S2 manufacturing, S3 retail, S4 tech. Not a filter; context-clause only (section 4) | [signal-matrix.md](../../../context/icp/signal-matrix.md) |
| Trigger | Job title matches Payroll Officer, Payroll Specialist, Payroll and Benefits, Compensation & Benefits, HR Officer, HR Generalist, HR Manager, HR Executive. Posted in the last 30 days | [signal-matrix.md](../../../context/icp/signal-matrix.md) U1 |
| Recipient 1 | **Founder or CEO** (economic buyer). Always contacted | [personas.md](../../../context/icp/personas.md) |
| Recipient 2 | **Current HR lead** (champion): HR Manager, Head of HR, People Lead or HR Lead already in seat, with a LinkedIn start date before the post date, **who joined from another company** (the role before this one was at a different employer). Internal promotions are not contacted. Contacted only if found. Never the person being hired | [personas.md](../../../context/icp/personas.md) |

### Exclude

| Who | Why |
|---|---|
| Current PaidHR customers: FAMASI, Heroshe, Flutterwave, Mono, Risevest, GetEquity, Kredete, GO54, Mira, AEC, NOI Polls, Sygnite, ReelFruit | Already customers ([facts.md](../../../context/messaging/facts.md)) |
| Competitors: SeamlessHR, Workpay, SoftSUITE, Sage, PaySpace, Cadana, Bento | Not buyers ([competitors.md](../../../context/docs/research/competitors.md)) |
| Posts by recruitment agencies, HR outsourcing firms or "Confidential" employers | The poster isn't the employer |
| Companies over 200, under 20, or with no headcount | Outside the ICP / unverifiable |
| Public sector and government agencies | Fit unknown ([icp.md](../../../context/icp/icp.md) open question) |
| Jobs located outside Nigeria, Kenya and Ghana, or in a different country from the company HQ | Covered by C13 (hiring abroad) |
| HR leads promoted internally | Recipient 2 must have joined from another company (user decision 2026-11-14). The CEO is still emailed |
| Accounts contacted in the last 100 days or in active pipeline | Dedupe against CRM / sequencer. Blocklist location TBD |

## 3. Sources [ENGINE]

| Purpose | Source | Tool and cost |
|---|---|---|
| Trigger: job posts | Nigeria: Jobberman, MyJobMag. Kenya: BrighterMonday, MyJobMag Kenya. Ghana: Jobberman Ghana, MyJobMag Ghana. All: LinkedIn Jobs. Kenya and Ghana board coverage not yet checked; verify on the first scrape | `crawl4ai` (local, free) for the job boards; Clay "Find Jobs" for LinkedIn. Optional: treg `mobiusengine-jobs.jobs.search` (needs its own credential; Nigerian board coverage unknown; run `treg catalog get` first) |
| Full job description text | The job post page | Same scrape |
| Domain, LinkedIn page, industry, headcount | LinkedIn company page | Clay "Enrich Company", or treg `icypeas.companies.enrich` (about $0.0095 per success; confirm with `treg catalog get`) |
| Founder/CEO and current HR lead | LinkedIn people search | Clay "Find People" (title + start date) |
| HR lead work history (S7b) | LinkedIn profile experience list | Clay "Enrich Person" (LinkedIn profile). Cost TBD; runs only on rows where S7 = true |
| Work email | Email waterfall | Clay waterfall. Provider and cost TBD |
| Exclusion lists | Customers, competitors, agencies, CRM | Static lists + sequencer blocklist |

## 4. Signals table [ENGINE]

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| S1 | Qualifying job post | trigger | Regex on title, case-insensitive: `payroll\|compensation\|benefits\|HR (officer\|generalist\|executive\|manager)\|human resources (officer\|manager)` AND `today - posted_date <= 30` | boolean |
| S2 | Headcount in band | trigger (filter) | `employee_count` between 20 and 200; blank = false | boolean |
| S3 | Exclusion match | trigger (filter) | Domain or company name exact match against customer, competitor, agency and CRM lists; poster name regex `confidential\|recruit\|staffing\|outsourc` | boolean (true = drop) |
| S4 | Role cluster | **router** | Title regex `payroll\|compensation\|benefits` → `payroll_role`; all other S1 passes → `hr_role` | enum: `payroll_role` / `hr_role` |
| S5 | JD names statutory remittance | **router** | Job description regex `PAYE\|pension\|PFA\|PenCom\|NHF\|NSITF\|ITF\|NSSF\|SHIF\|NHIF\|housing levy\|SSNIT\|tier 2\|remittance\|statutory deduction` | boolean |
| S6 | Remittances named in JD | context-clause | Regex extraction of which statutory items appear (only when S5 = true). Nigeria: PAYE, pension, NHF, NSITF. Kenya: PAYE (also P10, iTax), NSSF, SHIF (NHIF and SHA map to SHIF), Housing Levy (AHL maps to Housing Levy). Ghana: PAYE (also GRA), SSNIT (Tier 1 maps to SSNIT), Tier 2 pension. NITA and Tier 3 are not extracted (not in facts.md). PFA and PenCom map to "pension". If S5 fired but none of these is named (e.g. only "statutory deductions"), output = "statutory remittances" so the variable is never empty. These are read terms, not copy claims | list, joined ("PAYE and pension") |
| S7 | HR lead in seat | context-clause (feeds the cell D inference only) | Find People: title regex `HR Manager\|Head of HR\|People (Lead\|Manager)\|HR Lead` AND `start_date < posted_date` | boolean |
| S7b | HR lead joined from another company | trigger (recipient 2 only) | S7 = true AND the experience entry before the current role is at a different company (LinkedIn company ID, or normalized name if no ID). No prior experience listed = false | boolean + name |
| S10 | Country | context-clause | HQ country from enrichment; must equal job country | enum: NG / KE / GH. **Never routes** |
| S8 | Segment | context-clause | LinkedIn industry mapped to logistics / manufacturing / retail / tech / other per [signal-matrix.md](../../../context/icp/signal-matrix.md) segment definitions | enum. **Never routes** |
| S9 | Job location city | context-clause | Location field on the post | text |

- **Routers:** S4 (2 values) × S5 (2 values) = **4 cells**.
- **Count clusters:** none. No count routes.
- **Left out of v1:** C6 (Excel or competitor named in JD). Low volume, and naming a tool risks the facts.md ban on diagnosing the prospect. Candidate for iteration 2.

## 5. Routing matrix with angles [ENGINE]

Every cell gets both recipients: the CEO always, the HR lead only where S7b = true.

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| **A** | S4 = `payroll_role` AND S5 = true | They're adding a person whose written job is the filings PaidHR automates: the JD lists {{remittances_named}} by name. Those filings are done today by someone, by hand or alongside other work, and the company has decided they need a dedicated owner. | **Give the payroll hire a system that files for them.** PaidHR files the exact remittances in their JD with a receipt after each one, so the new hire checks receipts rather than doing the filing. Proof: Heroshe, remittance "in less than a click" with a receipt, versus "two weeks or more". CEO lens: decide the system before the hire starts. HR-lead lens: the person you're hiring starts on receipts, not portals. |
| **B** | S4 = `payroll_role` AND S5 = false | They're adding a dedicated payroll person, but the JD is about the payroll run itself (computation, payments, payslips), not filings. Payroll volume has grown enough to need its own owner. | **The payroll run done in the system, with the hire reviewing it.** Salaries computed on the 2026 tax bands, staff paid, payslips self-served, so the new role reviews the run rather than building it. Proof: FAMASI, about one hour saved per payroll run. Remittance only as "also included", never as something they listed. |
| **C** | S4 = `hr_role` AND S5 = true | They're hiring a general HR person, and statutory filings are written into that job next to recruiting, onboarding and staff relations. Remittance sits on the HR desk as one of many tasks. | **Take the filings off the HR desk.** PaidHR files the {{remittances_named}} listed in their JD, with a receipt each time, so the new HR hire spends their time on people work. Proof: Heroshe, an HR-led team where remittance went from "two weeks or more" to "in less than a click". CEO lens: the HR hire's time goes to people, not filings. HR-lead lens: one less thing to hand over and supervise. |
| **D** | S4 = `hr_role` AND S5 = false | They're building or expanding the HR function, and the JD doesn't place payroll or filings with this role, so payroll likely sits with the founder or finance today. If S7 = false and the title is HR Manager, this is probably their first HR leader. | **Set up the new HR function on one system from day one.** Payroll, statutory remittance, leave and payslips in one place before the new HR person builds their own process, on a system "fully updated for Nigeria's new tax law". Proof: FAMASI saved about one hour per payroll run (facts.md wording; still to be verified against the video). CEO lens: get payroll off your desk as HR arrives. HR-lead lens (only if S7b = true): the person joining your team starts on the system you choose. |

**Branch coverage**
- `{{remittances_named}}` exists only in A and C. B and D never reference it.
- `{{hr_lead_name}}` exists only where S7b = true. The CEO email never depends on it.
- `{{job_title}}` and `{{job_board}}` exist in all cells (guaranteed by the trigger).
- `{{segment}}` line is optional colour in every cell; `other` = no line.
- **Country (S10) does not change the cell, but it limits the claims.** Nigeria-only lines ("2026 tax bands" in B, "fully updated for Nigeria's new tax law" in D) exist only where S10 = NG. For KE and GH, A and C use the country filing line from facts.md (Kenya: PAYE, Housing Levy, SHIF and NSSF; Ghana: PAYE, SSNIT and Tier 2 pension), and B and D use the payroll claims without the Nigerian tax-law lines. Heroshe and FAMASI are Nigerian proof; for KE and GH they can be used only as "a Nigerian team", never implied as local.

**Niche-native test:** every angle opens on the specific role they posted, and in A and C on the filings their own JD names.

**Facts gate notes**
- Heroshe H2, H3, H5, H6, the FAMASI hour and "fully updated for Nigeria's new tax law" are in [facts.md](../../../context/messaging/facts.md). All four cells have usable proof today.
- Heroshe H8 ("operational tasks... strategic tasks") is not in facts.md; no angle depends on it.
- The 31 Jan 2027 PAYE return date is INFERRED and not in facts.md. Not used in the angles; may become a `{{placeholder}}` timing line once verified. Nigeria only.
- **Kenya and Ghana are in facts.md as of 2026-11-14**: filing claims approved on the user's confirmation, local deadlines from official sources ([kenya.md](../../../context/docs/research/kenya.md), [ghana.md](../../../context/docs/research/ghana.md)). No local customer proof. Don't write "PaidHR serves Ghana" (not public).

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in branches |
|---|---|---|
| `{{first_name}}` | Find People → recipient first name (CEO or HR lead) | All |
| `{{company_name}}` | Enrich Company → name (cleaned: no "Ltd", "Limited", "Nigeria") | All |
| `{{job_title}}` | Job post → title (as posted) | All |
| `{{job_board}}` | Job post → source (Jobberman / MyJobMag / LinkedIn) | All |
| `{{job_city}}` | Job post → location (S9) | All; blank allowed, copy must read without it |
| `{{remittances_named}}` | S6 regex extraction, joined ("PAYE and pension"); only PAYE, pension, NHF, NSITF; "statutory remittances" when none of the four matched | A, C only |
| `{{segment}}` | S8 enum (logistics / manufacturing / retail / tech / other) | All; copy maps each value to one fixed line, `other` = no line |
| `{{route_cell}}` | S4 × S5 → A / B / C / D | All (routing only, never in copy) |
| `{{recipient_role}}` | `ceo` or `hr_lead` (S7b decides whether `hr_lead` exists) | All (picks the lens, never in copy) |
| `{{hr_lead_name}}` | S7b → name of current HR lead who joined from another company | Only where S7b = true; HR-lead email only |
| `{{country}}` | S10 → Nigeria / Kenya / Ghana | All; gates country-specific claims (section 5 branch coverage) |
| `{{sender_name}}`, `{{sender_title}}`, `{{sender_signature}}` | facts.md sender identity (signature = name + title) | All. **TBD in facts.md; blocks sending** |

Copy can't mention headcount, funding, number of open roles, salary or any JD content beyond the remittance names. None of it is delivered.

## 7. Cadence and channel [ENGINE]

- **Periodicity:** always-on, weekly. Scrape every Monday for posts from the last 7 days (first run looks back 30 days). An account enters a sequence within 7 days of detection.
- **Re-trigger:** at most once per account every 100 days.
- **Channel:** email. Three steps over about 10 days. CEO and HR lead in parallel threads; a reply from either stops both. LinkedIn out for v1.
- **Launch window:** Nigeria before January 2027, so the annual PAYE return is still ahead of the prospect (timing context only until verified). Kenya and Ghana: monthly deadlines only (KE 9th and 9th working day; GH 14th and 15th), so no seasonal window. Context only, not a hook.
- **Measure:** reply rate by `{{route_cell}}`, by `{{recipient_role}}` and by `{{country}}`, to test whether "hiring a payroll person" predicts buying software. Volume per week: TBD until the first scrape.

---

## Definition of done

- [x] Mother intent: one sentence, signal-led, matched to the catalog
- [x] Inclusion: ICP box + trigger + recipient, tagged [ICP]
- [x] Exclusion: who's out and why
- [x] Sources: trigger + every enrichment
- [x] Signals table: all deterministic, every role declared
- [x] Count clusters: none route (declared)
- [x] Routing matrix with an angle in every cell
- [x] Branch coverage checked
- [x] Variables contract mapped
- [x] Engine/ICP markers on every section
- [x] Cadence and channel declared

**Next:** `/campaign-copy` on this file. Open blockers for sending (not for copy): sender identity and CTA ladder in facts.md; weekly volume TBD; Kenya and Ghana copy not yet written (facts are now in facts.md).

---

## Copy

**Scope:** Nigeria only (S10 = NG). Channel: email only. Sequence: 3 emails, day 0, 3, 10; CEO and HR lead in parallel threads; a reply from either stops both. Kenya and Ghana copy not yet written; facts.md lines approved 2026-11-14, so run `/campaign-copy` for KE and GH when ready.
**Facts status:** every fact used is in [facts.md](../../../context/messaging/facts.md). PaidHR sign-off is not required (user decision 2026-11-14, facts.md sign-off policy). Still re-check the FAMASI and Heroshe video wording before launch.

### Email 1 (day 0, new thread)

**Subject (static, same for every cell and both lenses):** `{your new hire and payroll|payroll and the new hire|before the new hire starts}`

**Body shape:** `{{first_name}},` on its own line, then L1, L2, proof, CTA, `{{sender_signature}}`. Routes are exhaustive (A to D cover every lead), so no fallback.

#### CEO lens (approved 2026-11-14)

**L1 (`{{e1l1}}`)**
+ A (S4 = payroll_role AND S5 = true): From the {{job_title}} post on {{job_board}}, filing {{remittances_named}} is part of the job, so my guess is those filings have outgrown being a side task.
+ B (S4 = payroll_role AND S5 = false): Hiring a {{job_title}} tells me the monthly payroll run at {{company_name}} probably needs its own owner now.
+ C (S4 = hr_role AND S5 = true): The {{job_title}} post on {{job_board}} includes filing {{remittances_named}}, so I'd guess those filings will sit on the HR desk next to everything else.
+ D (S4 = hr_role AND S5 = false): Hiring for the {{job_title}} role suggests {{company_name}} is building out HR, and payroll probably still sits with you or finance for now.

**L2 (`{{e1l2}}`)**
+ A: PaidHR files {{remittances_named}} and sends a receipt after each remittance, so whoever you hire checks receipts instead of doing the filing.
+ B: PaidHR runs payroll and files PAYE, pension, NHF and NSITF along with it, so the person you hire reviews each run rather than building it.
+ C: PaidHR files {{remittances_named}} with a receipt after each remittance, so your new HR hire spends their time on people, not filings.
+ D: PaidHR keeps payroll and PAYE, pension, NHF and NSITF remittance in one place, so the new HR hire starts on one system instead of building their own process.

**Proof (`{{social_proof}}`)**
+ A: Heroshe, a shipping company, used to wait "two weeks or more" for remittance. With PaidHR it happens "in less than a click".
+ B: FAMASI, a pharmacy software company, saved about one hour per payroll run with PaidHR.
+ C: Heroshe's HR team used to wait "two weeks or more" for remittance. Now it happens "in less than a click", and a receipt follows.
+ D: Once FAMASI moved payroll to PaidHR, it saved about one hour per payroll run.

**CTA (static):** `{Worth a look before the new hire starts?|Is the payroll system part of the plan before they start?}`

**Sample (cell A, CEO):**

> **your new hire and payroll**
>
> Tunde,
>
> From the Payroll Officer post on Jobberman, filing PAYE and pension is part of the job, so my guess is those filings have outgrown being a side task.
>
> PaidHR files PAYE and pension and sends a receipt after each remittance, so whoever you hire checks receipts instead of doing the filing.
>
> Heroshe, a shipping company, used to wait "two weeks or more" for remittance. With PaidHR it happens "in less than a click".
>
> Worth a look before the new hire starts?
>
> {{sender_signature}}

#### HR-lead lens (approved 2026-11-14; sent only where S7b = true, in its own thread)

Same subject, CTA and body shape as the CEO lens. Proof lines are the CEO-lens proof for the same cell.

**L1 (`{{e1l1}}`)**
+ A: The {{job_title}} role your team has open on {{job_board}} includes filing {{remittances_named}}, so I imagine you'll be handing those filings to the new hire soon.
+ B: Adding a {{job_title}} to your team probably means the monthly payroll run at {{company_name}} is getting its own owner.
+ C: The {{job_title}} post on {{job_board}} lists filing {{remittances_named}}, which I'd guess is one more task you'd hand over and then keep checking.
+ D: With a new {{job_title}} joining HR at {{company_name}}, my guess is you're deciding how payroll and remittance will run as the team grows.

**L2 (`{{e1l2}}`)**
+ A: PaidHR files {{remittances_named}} and sends a receipt after each remittance, so the person joining your team starts by checking receipts, not filing.
+ B: PaidHR runs payroll and files PAYE, pension, NHF and NSITF along with it, so your new hire reviews each run rather than building it.
+ C: PaidHR files {{remittances_named}} with a receipt after each remittance, so there is one less task to hand over and check.
+ D: PaidHR keeps payroll and PAYE, pension, NHF and NSITF remittance in one place, so the person joining starts on the system you choose.

**Sample (cell C, HR lead):**

> **payroll and the new hire**
>
> Amaka,
>
> The HR Officer post on MyJobMag lists filing PAYE, pension and NHF, which I'd guess is one more task you'd hand over and then keep checking.
>
> PaidHR files PAYE, pension and NHF with a receipt after each remittance, so there is one less task to hand over and check.
>
> Heroshe's HR team used to wait "two weeks or more" for remittance. Now it happens "in less than a click", and a receipt follows.
>
> Is the payroll system part of the plan before they start?
>
> {{sender_signature}}

### Email 2 (day 3, same thread, both lenses)

**Subject:** `Re:` + the Email 1 subject (unchanged).

**Body shape:** `{{first_name}},` then L1, L2, CTA, `{{sender_signature}}`. Routes exhaustive by cell group, no fallback. New value versus Email 1: the tax-law update plus PaidHR's own volume figures.

**L1 (`{{e2l1}}`)**
+ A, C: Whoever takes on {{remittances_named}} at {{company_name}} will be filing under Nigeria's new tax law, which took effect on 1 January 2026, and PaidHR is fully updated for it.
+ B, D: Whoever takes the {{job_title}} role will likely be working with payroll under Nigeria's new tax law, which took effect on 1 January 2026, and PaidHR is fully updated for it.

**L2 (`{{e2l2}}`)**
+ A, C: In 2025, PaidHR filed ₦934M in PAYE and processed ₦754M in pension.
+ B, D: So far in 2026, PaidHR has processed ₦119.2bn in payroll.

**CTA (static):** `{Would it help to see one month of payroll and filings in PaidHR?|Want to see what one month of payroll and filings looks like in PaidHR?}`

**Sample (cell B, CEO):**

> **Re: your new hire and payroll**
>
> Tunde,
>
> Whoever takes the Payroll Specialist role will likely be working with payroll under Nigeria's new tax law, which took effect on 1 January 2026, and PaidHR is fully updated for it.
>
> So far in 2026, PaidHR has processed ₦119.2bn in payroll.
>
> Would it help to see one month of payroll and filings in PaidHR?
>
> {{sender_signature}}

### Email 3 (day 10, same thread)

**Subject:** `Re:` + the Email 1 subject (unchanged). Static by lens, spintax, every cell.

**CEO lens:**

```
{{first_name}},

{Last note from me on this.|This is my last note on this.}

If payroll and filings sit with someone else at {{company_name}}, {who would be the right person to ask?|who should I speak to instead?}

{{sender_signature}}
```

**HR-lead lens:**

```
{{first_name}},

{Last note from me on this.|This is my last note on this.}

{Is the payroll system yours to choose, or already decided before the {{job_title}} starts?|Will you pick the payroll system, or is that settled before the {{job_title}} starts?}

{{sender_signature}}
```

### Copy QA and facts trace

`QA: passed. insult ok, nexus ok, facts-traced ok, spintax static-only ok, no-cliche ok, no repeated lines across emails, subject unchanged in thread [word counts: E1 62 to 85, E2 38 to 44, E3 28 to 34]`

- Heroshe "two weeks or more", "in less than a click", receipt after each remittance: facts.md Heroshe result (H2, H3, H5, H6).
- FAMASI about one hour per payroll run: facts.md FAMASI result (verify wording against video).
- PAYE, pension, NHF and NSITF filing: facts.md value prop variant A.
- "Fully updated for Nigeria's new tax law, effective 1 January 2026": facts.md Tax law.
- ₦934M PAYE, ₦754M pension (2025); ₦119.2bn payroll 2026 YTD: facts.md approved claims (PaidHR's own figures, self-reported).
- Not used: payslips, leave, EWA, on-time claim, logo names.

**Blocks launch:** `{{sender_signature}}` (sender name and title) is TBD in facts.md; weekly volume TBD.
