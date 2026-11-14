# Workflow spec: New HR or People leader (NG)

**Status:** COPY-APPROVED 2026-11-14 · structure amended 2026-11-14 with Clay build fixes (no angle or copy change)

- **Slug:** `new-hr-leader-180-days`
- **Origin:** campaign idea C8 in [campaign-strategy.md](../campaign-strategy.md), signal U5 in [signal-matrix.md](../../../context/icp/signal-matrix.md) (HR and People titles only; finance leaders are C9)
- **Evidence status:** INFERRED. No PaidHR customer has named a new HR leader as their buying trigger (research/signals.md #9). The first send is the test.
- **Built with:** `/build-workflow-spec`, approved section by section on 2026-11-14

---

## 1. Mother Intent (Trigger) [ENGINE]

**A Nigerian company with 20 to 200 staff has a new HR or People leader who started in the role in the last 180 days.**

- Catalog match: ⭐ New leadership (past 90/180 days), [workflow-anatomy.md](../../../knowledge-base/playbooks/workflow-anatomy.md).
- The recipient is the trigger person (champion persona). No second contact is needed.
- Volume: TBD until the first pull. LinkedIn start dates for Nigerian companies with 20 to 200 staff may be sparse.

---

## 2. Inclusion / Exclusion [ICP]

### Include

| Filter | Rule | Source |
|---|---|---|
| Country | Company HQ in Nigeria. Kenya and South Africa out: every remittance fact is Nigerian (PAYE, pension, NHF, NSITF) | context/icp/icp.md, context/messaging/facts.md |
| Headcount | 20 to 200. Enrichment headcount is unreliable for NG; hand-check at list QA | context/icp/icp.md |
| Industry | S1 Logistics, S2 Manufacturing, S3 Retail (tier 1), S4 Tech (tier 2). Industries with no tier are out. Keyword lists in Section 4, signal 3. S4 is "tech", not "funded tech": no funding source is built (amended 2026-11-14) | context/icp/icp.md, context/icp/signal-matrix.md |
| Trigger: title | Current title contains one of: HR Manager, Head of HR, HR Lead, HR Director, HR & Admin Manager, Head of People, People Lead, People & Culture Manager or Lead, People Operations Manager or Lead, Chief People Officer, Chief Human Resources Officer, HR Officer, Senior HR Officer, HR Generalist | context/icp/signal-matrix.md U5, context/icp/personas.md |
| Trigger: start date | Current role started 0 to 180 days before the pull date. Applied as "6 months or less", because Clay gives start dates as year and month only | Section 1 |
| Hire type | External hires AND internal promotions are both included (hire type is a router, see Section 4) | Approved 2026-11-14 |
| Recipient | The new HR or People leader. Champion persona | context/icp/personas.md |
| One contact per company | If several people match: leader title over practitioner title, then most recent start date | Approved 2026-11-14 |

### Exclude

| Who | Why |
|---|---|
| Under 20 or over 200 staff | Below the Standard tier floor; above the size where PaidHR proof holds (facts.md proof caveats) |
| HR Assistant, HR Intern, Recruiter, Talent Acquisition | Not the HR owner of payroll and remittance |
| Missing start date | The trigger can't be proven |
| Previous company is a PaidHR customer | Champion-migration intent; the catalog says not to mix it with others. Park for a separate play. Needs the customer list (TBD). Matched on the previous employer's **domain** against Exclusions (Type = Customer). If Enrich Person returns no previous domain, check the `Ready to send` previous companies against the customer list by eye before each send (free). Paid alternative if by-eye checking doesn't scale: Enrich Company on the previous company's LinkedIn URL, about 1 Action per person |
| Current PaidHR customers | Named logos: FAMASI, Heroshe, Flutterwave, Mono, Risevest, GetEquity, Kredete, GO54, Mira, AEC, NOI Polls, Sygnite, ReelFruit. Full list: TBD (CRM export) |
| Competitors and HR or payroll vendors | SeamlessHR, Workpay, SoftSUITE, Bento Africa, Sage, PaySpace, Cadana, Deel, and any company in HR software (context/positioning/competitors.md) |
| HR outsourcing firms, payroll consultancies, recruitment agencies | Partner or non-ICP play (C15) |
| Government and public-sector bodies | ICP open question |
| Active pipeline or open deals | TBD (CRM export). Loaded into the Exclusions table as Type = Pipeline |
| Company contacted by any PaidHR workflow in the last 100 days (e.g. `payroll-hr-role-posted`) | No double-touching. Matches that spec's 100-day cooldown. Loaded into the Exclusions table as Type = Recently contacted, from a sequencer export refreshed before each monthly run (source S7) |
| Person no longer in the role | Search data can lag. Optional check, signal 11 |

**Known risk:** a new HR Officer at a larger company may report to a Head of HR who has been there for years, so we'd be emailing the doer, not the decider. Checked at list QA, not by an extra lookup.

---

## 3. Sources [ENGINE]

| # | What | Source | Cost | Status |
|---|---|---|---|---|
| S1 | Company checks: HQ country, employee count, industry, once per company | Clay "Enrich Company" on the domain of each company a passing person works at | About 1 Action per company | Standard. Clay's search size buckets are 11-50 and 51-200, so the floor of 20 is enforced here, not in the search |
| S2 | Trigger: people in Nigeria with a matching current title and a role started 6 months ago or less | Clay "Find People" (title include/exclude, person country, company size 11-50 and 51-200, industry exclude, job start date filters) | Free (search and import) | Source verified (signal-matrix U5); volume untested. The search preview count is the free volume check |
| S3 | Person profile: current role, previous role's title, company name, company LinkedIn URL and (if returned) company domain | Clay "Enrich Person" | About 1 Action per person | Standard |
| S4 | Optional re-check of the job change if S2 start dates look unreliable | treg `leadmagic.x.job-change-detector` | $0.075/call per signal matrix; run `treg catalog get` before any call | Untested |
| S5 | Headcount re-check | Clay "Enrich Company"; fallback treg `icypeas.companies.enrich` ($0.0095/success) or `companyenrich.companies.workforce` ($0.049/success); confirm prices first | Low | Hand-check at QA |
| S6 | Email | Clay email waterfall | Clay credits, TBD | Standard |
| S7 | Exclusions: PaidHR customers and open pipeline (CRM export from PaidHR); companies contacted by any PaidHR sequence in the last 100 days (sequencer export, refreshed before each monthly run). All keyed on plain company domain | CRM export + sequencer export, uploaded as one Exclusions CSV | Free | TBD |
| S8 | Not built: company in the C1 job-post table in the last 30 days | C1 job-post table | n/a | Dropped 2026-11-14: the approved copy never uses it |
| S9 | Optional: is the person still in the role (signal 11) | Clay "Use AI" on the Enrich Person result | About 1 Action + a small AI cost per person | Recommended, not required |

No funding source: it would only ever be a context clause here, and it's weak for S2 and S3.

---

## 4. Signals table [ENGINE]

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| 1 | Company HQ in Nigeria | trigger | Boolean: company country = Nigeria | true / false (false = drop) |
| 2 | Headcount 20 to 200 | trigger | Count: Enrich Company employee count between 20 and 200 (the search can only narrow to 11-200); hand-check at QA | true / false |
| 3 | Industry in a target segment | trigger | Keyword match (case-insensitive) on the Enrich Company industry field, first match wins: **Logistics** = logistic, transport, freight, shipping, warehous, courier, delivery. **Manufacturing** = manufactur. **Retail** = retail. **Tech** = software, internet, information technology, IT services, financial services, fintech. Drop if the industry also matches human resources services, staffing, recruit or government | `segment` = Logistics / Manufacturing / Retail / Tech, or drop |
| 4 | HR or People title | trigger | Regex on current title against the Section 2 include list; exclude-list regex wins | true / false |
| 5 | Role started in the last 180 days | trigger | Count: whole months between the current role's start month (YYYY-MM) and the pull month. 6 or less = true; missing = drop | `months_in_role` |
| 6 | Hire type | **router** | Boolean: the company LinkedIn URL of the previous role equals the current company LinkedIn URL, both cleaned (lowercase, no https, no www, no trailing slash). Match on the LinkedIn URL, not name text. Compare the previous **role**, not the previous company entry (LinkedIn groups promotions under one company) | `promoted` / `external`. No previous role = `external`. Previous role exists but has no company LinkedIn URL = `review`: held from sending, checked by hand |
| 7 | Title tier | **router** | Regex on current title: Manager, Head, Lead, Director, Chief = `leader`; Officer, Generalist = `practitioner` | `leader` / `practitioner` |
| 8 | Tenure stage | context-clause | Clusters on signal 5 (month-based, the closest match to 0 to 90 / 91 to 180 days): 3 months or less = `new` (still settling in); 4 to 6 months = `settled` (past the first quarter) | `tenure_stage`. Never routes. Picks the E1 L1 variant |
| 9 | Segment | context-clause | From signal 3 | Not used by the approved copy. Never routes |
| 10 | ~~Company posting payroll, HR or frontline jobs now~~ | dropped | Not built (2026-11-14): the approved copy never uses it | n/a |
| 11 | Still in the role (optional) | trigger | AI classification on the Enrich Person work history, hard enum output | `YES` / `NO` / `REVIEW`. Only `YES` (or the check skipped) passes |

**Why only two routers:** hire type changes the situation (learning someone else's setup vs owning a setup you already know). Title tier changes who decides (the leader owns the system choice; the practitioner runs the filings). Tenure doesn't change the angle, because both stages face the same next event (31 Jan 2027 PAYE return, INFERRED). Segment doesn't change the angle, because facts.md has no attendance proof, so every segment leads with statutory remittance.

---

## 5. Routing matrix with angles [ENGINE]

Hire type: 2 values. Title tier: 2 values. Stacked: 2 × 2 = **4 cells.**

**Timing overlay for every cell (not a router):** the person started after the new tax rules went live on 1 Jan 2026. The first annual PAYE return under them is due 31 Jan 2027 (INFERRED, research/market.md; copy can't call this date confirmed until it's verified). Monthly PAYE is due by the 10th; pension within 7 working days of salary.

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| **A. External leader** | `hire_type = external` AND `title_tier = leader` | An HR leader has just arrived from another company and is now accountable for a payroll and remittance setup someone else chose. In the first months in a role, a new leader reviews what they inherited and decides what stays. The first annual PAYE return under the new rules falls on their watch. | **Choose the remittance system before the first return you answer for.** The decision is open now and won't be later. PaidHR files PAYE, pension, NHF and NSITF with a receipt for each remittance and is updated for the new tax law. Proof: Heroshe, an HR-led company whose remittance went from "two weeks or more" to a confirmation call in about two days, with a receipt per remittance. |
| **B. Promoted leader** | `hire_type = promoted` AND `title_tier = leader` | Someone already inside the company has stepped up to run HR. They know the current payroll and remittance steps from the inside, may have done some of them, and now own the outcome and the authority to change them. | **You know exactly how the filings get done today. Now it's your call to change it.** The promotion is when the person who knows the manual steps gets the say over them. Receipts for every remittance give the new owner proof to show the founder. Proof: Heroshe. |
| **C. External practitioner** | `hire_type = external` AND `title_tier = practitioner` | A new HR Officer or Generalist has joined a company with 20 to 200 staff. At that size they are likely the person who will run the monthly payroll and statutory filings, while still learning how this company does them. They do the work but probably don't sign off on software. | **Let the system carry the filings while you learn the company.** Remittance "in less than a click" with a receipt each time, instead of doing PAYE, pension and NHF by hand. The ask is a look they can take to whoever decides, not a buying decision. Proof: Heroshe (the HR person who did the filings). |
| **D. Promoted practitioner** | `hire_type = promoted` AND `title_tier = practitioner` | Someone moved into an HR Officer or Generalist role from another role in the same company. They have likely taken over payroll and remittance tasks that someone else ran before. | **You've taken over the filings. Here is how they run without the manual steps.** Same remittance-with-receipts mechanism as C. Copy may name their previous role at this company. Same ask as C: a look to take to the decider. Proof: Heroshe. |

### Branch coverage

| Data | A | B | C | D | Rule for copy |
|---|---|---|---|---|---|
| `previous_company` | Sometimes | No (same company) | Sometimes | No | Not used in copy (removed from the contract 2026-11-14). Enriched only for the champion-migration check |
| `previous_title` | Sometimes | Yes | Sometimes | Yes | Used only in B and D |
| `tenure_stage` | Yes | Yes | Yes | Yes | Picks the E1 L1 variant in every cell (not printed as text) |

### Niche-native check
- Every angle names the Nigerian statutory set (PAYE, pension, NHF, NSITF), the new tax law and a specific personnel event (arrived or promoted, deciding or doing). A generic HR tool couldn't send these unchanged.
- No angle says what is wrong with the current setup. Each says what is happening (new owner, decision open, filings changing hands), which stays clear of the facts.md ban on diagnosing the team as failing.

### Proof available (facts.md)
- Heroshe: receipt after each remittance (H2), "two weeks or more" before (H3), "in less than a click" (H5), confirmation call "I think the next two days" (H6).
- Heroshe H8 ("I leave the software to do the operational tasks and I do the strategic tasks") and H9 ("I would recommend Pade to any HR professional…") added to facts.md on 2026-11-14. PaidHR sign-off not required (user decision 2026-11-14); re-check against the video before use.

---

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in branches |
|---|---|---|
| `{{first_name}}` | Clay Enrich Person: first name | A, B, C, D |
| `{{company_name}}` | Clay Find Companies: company name, cleaned (no "Ltd", "Limited", "Nigeria") | A, B, C, D |
| `{{current_title}}` | Clay Enrich Person: current position title | A, B, C, D |
| `{{previous_title}}` | Clay Enrich Person: title of the previous role | B, D always; A, C sometimes. Copy uses it in B and D only |
| `{{email}}` | Clay email waterfall | A, B, C, D (no email = LinkedIn only) |
| `{{linkedin_url}}` | Clay Find People: profile URL | A, B, C, D |
| `{{sender_name}}`, `{{sender_title}}`, `{{signature}}` | facts.md sender identity | All. TBD, blocks sending |

Routing-only fields (never printed in copy): `hire_type`, `title_tier`, `tenure_stage`, `months_in_role`, `segment`.

Removed 2026-11-14 because the approved copy never uses them: `{{segment_noun}}`, `{{previous_company}}` (still enriched, for the champion check only), `{{hiring_now}}`. The copy's dynamic lines reach the sequencer as `{{e1l1}}`, `{{social_proof}}`, `{{e1cta}}`, `{{e2l1}}`, `{{e2l2}}`, `{{e2cta}}`, `{{e3l1}}`, `{{e3cta}}`, each built only from the variables above.

Copy may use only these variables. Nothing about tools they used before, team size, or why they were hired.

---

## 7. Cadence and channel [ENGINE]

- **Periodicity:** monthly, always on. The first pull covers the full 180-day backlog; each later pull adds people who started in the last ~30 days. Each person enters once.
- **Channel:** email + LinkedIn. Email carries the message; a LinkedIn connection request follows email 1. No email found = LinkedIn only. **LinkedIn tool: TBD.** Until one is named, connection requests are sent from the Clay `LinkedIn only` and `Ready to send` views outside Clay.
- **Steps:** 3 emails + 1 LinkedIn connection. Spacing and wording set in `/campaign-copy`.
- **Timing overlay expiry:** remove the 31 Jan 2027 PAYE-return framing from copy once that date passes. Launch before mid-January to use it. The four angles hold without it.
- **Cooldown:** 100 days per company across all PaidHR workflows.

---

## Open items before launch

- Sender identity and CTA ladder (facts.md): TBD, blocks sending.
- PaidHR customer list and open pipeline (CRM export): TBD, needed for exclusions.
- Real volume: TBD until the first Clay pull (free search preview count, see the Clay build guide Part 2.3).
- Sequencer export of companies contacted in the last 100 days: TBD, needed for exclusions.
- LinkedIn tool for the connection request: TBD.
- Clay build guide: [new-hr-leader-180-days-clay-build-guide.md](new-hr-leader-180-days-clay-build-guide.md). Spec amended 2026-11-14 with its 9 fixes (tenure in months, headcount floor after enrichment, segment keyword lists and S4 = tech, hire type on cleaned LinkedIn URLs with a `review` outcome, champion check by domain, unused variables removed, exclusion sources, optional still-in-role check, LinkedIn tool TBD).
- 31 Jan 2027 annual PAYE return date: INFERRED, verify before stating it as fact.

---

## Copy

**Scope:** Nigeria only. Channel: email (3 steps, day 0 / 3 / 10, same thread) + empty LinkedIn connection request after Email 1. Register: signal play.
**Facts status:** every fact used is in [facts.md](../../../context/messaging/facts.md). PaidHR sign-off is not required (user decision 2026-11-14, facts.md sign-off policy). Heroshe quotes (H2, H3, H5, H8) still need a human listen against the video.
**Sender:** `{{sender_signature}}` is TBD in facts.md and blocks sending.
**January expiry:** "January" appears in E1 L2, E1 CTAs A, B and D, E2 leader e2l1 and E3 leader CTA. From 1 Feb 2027 this sequence needs a post-January version (re-approved here), not just a new L2.
**Persona review (2026-11-14):** 3 fixes applied: leader proof in past tense (2023 video), E2 receipt line as a product claim, E1 B-new "yours to decide on".

### Email 1: APPROVED 2026-11-14 (day 0, new thread)

**Subject (static, all cells):** `{new role and payroll|payroll in the new role|hr, payroll and paye}`

**Body shape:** `{{first_name}},` on its own line, then L1, L2, L3, proof, CTA, `{{sender_signature}}`. Routes are exhaustive (cells A to D × tenure stage new/settled), so no fallback.

**L1 (`{{e1l1}}`), dynamic: cell × tenure_stage**
+ A, new: Still new to running HR at {{company_name}}, you're probably deciding which parts of the payroll and remittance setup you took over should stay.
+ A, settled: A few months into running HR at {{company_name}}, my guess is you've had a proper look at how payroll and remittances get done there.
+ B, new: Now that you've moved from {{previous_title}} to running HR at {{company_name}}, the payroll and remittance process you already know is probably yours to decide on.
+ B, settled: A few months after moving from {{previous_title}} to running HR at {{company_name}}, how payroll and remittances get done is likely your decision now.
+ C, new: Still new in HR at {{company_name}}, I'd guess you're learning how payroll and the monthly filings run there while already doing them.
+ C, settled: A few months into HR at {{company_name}}, the monthly payroll and filings are probably a fixed part of your week by now.
+ D, new: Moving from {{previous_title}} into HR at {{company_name}} probably means the monthly payroll and filings have landed with you.
+ D, settled: A few months after moving from {{previous_title}} into HR, I'd guess the monthly payroll and filings are yours to run now.

**L2 (static, spintax).** Expires 31 Jan 2027: replace after that date.
`{The annual PAYE return is due by 31 January, and this one is probably the first under the new tax law.|By 31 January the annual PAYE return is due, probably the first one filed under the new tax law.}`

**L3 (static, spintax)**
`PaidHR runs payroll and files PAYE, pension, NHF and NSITF with a receipt after each remittance, {already updated for the new law|fully updated for the new tax law}.`

**Proof (`{{social_proof}}`), dynamic: title_tier**
+ Leader (A, B): At Heroshe, a shipping company, remittance used to take "two weeks or more". On PaidHR, their HR team remitted "in less than a click" and got a receipt each time.
+ Practitioner (C, D): Heroshe's HR team put it this way: "I leave the software to do the operational tasks and I do the strategic tasks."

**CTA (`{{e1cta}}`), dynamic: cell**
+ A: Worth a look before you settle how the January return gets filed?
+ B: Would a receipt for every filing be useful to show leadership before January?
+ C: Would it help to have something to show whoever signs off on payroll software?
+ D: Would it help to see it before January, with something you could show whoever signs off on payroll software?

**Sample (cell A, new; name and company are fictional):**

> **new role and payroll**
>
> Amaka,
>
> Still new to running HR at Ikeja Freight, you're probably deciding which parts of the payroll and remittance setup you took over should stay.
>
> The annual PAYE return is due by 31 January, and this one is probably the first under the new tax law.
>
> PaidHR runs payroll and files PAYE, pension, NHF and NSITF with a receipt after each remittance, already updated for the new law.
>
> At Heroshe, a shipping company, remittance used to take "two weeks or more". On PaidHR, their HR team remitted "in less than a click" and got a receipt each time.
>
> Worth a look before you settle how the January return gets filed?
>
> {{sender_signature}}

Facts trace: value prop variant B, tax law, annual PAYE return deadline, Heroshe H3/H5/H2 (leader proof), Heroshe H8 (practitioner proof). All in facts.md.

### Email 2: APPROVED 2026-11-14 (day 3, same thread)

**Subject:** `Re:` + Email 1 subject (unchanged)

```
{{first_name}},

{{e2l1}}

{{e2l2}}

{{e2cta}}

{{sender_name}}
```

Routing: title_tier (2 routes, exhaustive). New value vs E1: leaders get PaidHR's 2025 filing volume; practitioners get staff self-service for payslips and leave.

**e2l1**
+ Leader (A, B): One more number ahead of January: PaidHR filed ₦934M in PAYE and processed ₦754M in pension in 2025.
+ Practitioner (C, D): Besides the filings, payslip and leave requests from staff usually end up with HR too.

**e2l2**
+ Leader (A, B): Each remittance comes with a receipt, which is the paper trail you'd want on file for the return.
+ Practitioner (C, D): On PaidHR, staff request payslips and leave themselves, in the app or on WhatsApp and USSD where the company has those switched on.

**e2cta**
+ Leader (A, B): Should I send over a sample month of filings with the receipts attached?
+ Practitioner (C, D): Would that take a few requests off your desk?

**Sample (cell A; fictional name):**

> **Re: new role and payroll**
>
> Amaka,
>
> One more number ahead of January: PaidHR filed ₦934M in PAYE and processed ₦754M in pension in 2025.
>
> Each remittance comes with a receipt, which is the paper trail you'd want on file for the return.
>
> Should I send over a sample month of filings with the receipts attached?
>
> {{sender_name}}

Facts trace: 2025 compliance volume (self-reported), receipt per remittance, employee self-service (WhatsApp/USSD caveat kept).

### Email 3: APPROVED 2026-11-14 (day 10, same thread)

**Subject:** `Re:` + Email 1 subject (unchanged)

```
{{first_name}},

{{e3l1}}

{{e3cta}}

{{sender_name}}
```

Routing: title_tier (2 routes, exhaustive). New value vs E1/E2: leaders get data security as a selection reason; practitioners get the referral to whoever decides.

**e3l1**
+ Leader (A, B): Last note from me on this. If the payroll setup is under review, staff data will be part of that decision, and PaidHR is ISO 27001 certified and NDPA registered.
+ Practitioner (C, D): Last note from me on this. If payroll software is someone else's call at {{company_name}}, I'm happy to send them a short overview with you copied.

**e3cta**
+ Leader (A, B): Worth a conversation before January, or should I leave it here?
+ Practitioner (C, D): Who would be the right person?

**Sample (cell C; fictional name and company):**

> **Re: new role and payroll**
>
> Tolu,
>
> Last note from me on this. If payroll software is someone else's call at Ikeja Freight, I'm happy to send them a short overview with you copied.
>
> Who would be the right person?
>
> {{sender_name}}

Facts trace: Security (ISO 27001, NDPA).

### LinkedIn

Empty connection request (no note), sent after Email 1. No DMs (per spec Section 7).
