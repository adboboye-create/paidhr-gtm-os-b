# PaidHR outbound campaign strategy

**Status:** draft for review, 2026-11-14. Built with `/campaign-strategy` from `CLAUDE.md`, everything in `context/`, and the Mother Intent Catalog in `knowledge-base/playbooks/workflow-anatomy.md`. No paid data calls were made.

**Next step:** pick one idea and run `/build-workflow-spec` on it. Recommendation at the end.

---

## Read this first: how to read the numbers

- **Volume per month is TBD for every idea.** No list has been pulled yet, and the project rule is never to invent numbers. Each idea gets a volume **band** (High / Medium / Low) that ranks the ideas against each other. The bands are INFERRED from the signal matrix and research, not counted. The first Clay or treg pull for an idea replaces its band with a real count.
- **Signal strength (1 to 5):** how strongly the trigger shows a reason to buy payroll and remittance software now. 5 = a customer named this exact trigger; 1 = no trigger, just fit.
- **Data ease (1 to 5):** how reliably the list can be pulled programmatically in Nigeria today. 5 = public, structured, cheap; 1 = no known source.
- **Rank** = signal strength + data ease, highest first. Ties go to the higher Tier, then to build order (for example C2 ranks above C3 because it runs inside the C1 table).
- **Difficulty:** Easy (one source, few enrichments), Medium (scrape plus AI column or two sources), Hard (stacked signals, untested sources or a partner motion).
- **Evidence labels** follow the signal matrix: **Customer** (a PaidHR customer said it), **Third party**, **PaidHR claim**, **INFERRED**.

**Base list for every idea unless stated:** company HQ in Nigeria (Lagos first), 20 to 200 staff ([context/icp/icp.md](../../context/icp/icp.md)). Headcount data for Nigeria is unreliable (treg returned 1 employee for PaidHR itself, [company.md](../../context/docs/research/company.md)), so every list needs a headcount check.

**Timing for every idea:** the first annual PAYE return under the new tax bands is due 31 January 2027 (INFERRED from the 31 January deadline, [market.md](../../context/docs/research/market.md)), and PenCom started automated pension penalties in October 2026. Launch before January 2027 so the deadline is still ahead of the prospect. Use both as context in copy, never as an accusation.

---

## Customer discovery analysis

| Company | Industry | Size | Key metric | Problem solved | Source |
|---|---|---|---|---|---|
| Heroshe | Cross-border shipping (US, UK to Nigeria, Ghana) | Not found | Remittance took "two weeks or more" before; "in less than a click" after; receipt per remittance | Slow statutory remittance, tax office calls, staff payslip requests | [social-proof-sources.md](../../context/docs/research/social-proof-sources.md) |
| FAMASI | Pharmacy software and APIs | Not found | About one hour saved per payroll run | Manual remittance and pay confirmation as the team grew | [social-proof-sources.md](../../context/docs/research/social-proof-sources.md) |
| Flutterwave, Mono, Risevest, GetEquity, Kredete, GO54 | Fintech and tech | Not found | None | None stated (logo only) | [customers.md](../../context/docs/research/customers.md) |
| ReelFruit | Food manufacturing | Not found | None | None stated (logo only) | [customers.md](../../context/docs/research/customers.md) |
| AEC, Sygnite, NOI Polls, Mira | Engineering, research, restaurant tech | Not found | None | None stated (logo only) | [customers.md](../../context/docs/research/customers.md) |

**Patterns**
- **Who mostly buys:** "logistics, retail, and manufacturing businesses with under 200 employees" (Accion, June 2025, **Third party**). The logos PaidHR shows are mostly fintech, which is not the majority of its users ([icp.md](../../context/icp/icp.md)).
- **Who spoke:** a founder and CEO (FAMASI) and an HR professional (Heroshe). No finance lead on record.
- **Problems named by customers:** manual remittance, slow remittance with tax office calls, founder time on payroll, staff payslip requests. Both are pillar 1 and 2 problems. No customer proof yet for EWA, USSD, attendance or cross-border.

**Challenging the targeting**
- The proof sits in tech (FAMASI, fintech logos) but the volume sits in logistics, retail and manufacturing. Ideas below lead with logistics where Heroshe gives us a matching story, and use tech for funding signals where data is best.
- Retail has volume but no named customer. Retail ideas are held at Tier 3 until PaidHR names a retail customer.
- PaidHR also sells white label and a Payroll API to "Payroll Agencies & Consultants" ([company.md](../../context/docs/research/company.md)). That is an audience outside the employer ICP, used for the Creative (non-ICP) ideas.

**Best seeds for lookalikes:** Heroshe (logistics, story), FAMASI (founder-led tech, story), ReelFruit (manufacturing, logo only), the fintech logo set (logo only).

---

## Ranked summary

| Rank | # | Campaign | Mother intent | Segment and persona | Signal | Data | Volume band (INFERRED) | Difficulty | Tier |
|---|---|---|---|---|---|---|---|---|---|
| 1 | C1 | Payroll or HR role posted | Hiring specific roles | All segments; founder or CEO, HR manager | 4 | 4 | Medium | Medium | **Tier 1** |
| 2 | C2 | Golden ICP: logistics firm hiring for payroll and frontline | Hiring specific roles (stacked) | S1 logistics; HR manager | 5 | 3 | Low | Hard | **Tier 1** |
| 3 | C3 | Funded in the last 90 days | Companies fundraising | S4 funded tech, funded logistics; founder or CEO | 3 | 5 | Medium | Easy | **Tier 1** |
| 4 | C4 | PAYE return countdown (no AI) | Regulatory changes | All segments; finance lead, HR manager | 2 | 5 | High | Easy | **Tier 1** |
| 5 | C5 | Frontline hiring wave | Hypergrowth (hiring velocity) | S1, S2, S3; HR manager, founder | 3 | 4 | Medium | Medium | **Tier 1** |
| 6 | C6 | Job post says "Excel payroll" or names a tool | Competitor customers (via job posts) | All; HR manager | 4 | 3 | Low | Medium | Tier 2 |
| 7 | C7 | Heroshe lookalikes | Lookalike of customers | S1 logistics and shipping; HR manager | 2 | 4 | High | Easy | Tier 2 |
| 8 | C8 | New HR leader (first 90 days) | New leadership | All; new HR manager or Head of HR | 3 | 3 | Low | Medium | Tier 2 |
| 9 | C9 | New finance leader (first 90 days) | New leadership | All; new Finance Manager or Head of Finance | 3 | 3 | Low | Medium | Tier 2 |
| 10 | C10 | Tax-law engagers on LinkedIn | LinkedIn content engagement | All; HR manager, finance lead | 3 | 3 | Medium | Medium | Tier 2 |
| 11 | C11 | Lagos pension enforcement | Regulatory changes | Lagos employers, S1 and S2 first; finance lead | 2 | 4 | High | Easy | Tier 2 |
| 12 | C12 | Moonshot founders and speakers | Companies attending an event | S4 and funded S1; founder or CEO | 2 | 4 | Low | Easy | Tier 2 |
| 13 | C13 | Hiring outside Nigeria | Hiring offshore | S4; founder, finance lead | 3 | 3 | Low | Medium | Tier 3 |
| 14 | C14 | Creative Ideas: 3 uses from their website | Niche-specific play | All, S1 to S3 first; founder or CEO | 1 | 4 | High | Medium | Tier 2 |
| 15 | C15 | Accountants and payroll consultants (non-ICP) | Niche-specific play (partner channel, new intent) | Accounting, tax and payroll firms serving SMEs; partner or owner | 2 | 3 | Medium | Hard | Tier 2 |
| 16 | C16 | VC platform and accelerator teams (non-ICP) | Niche-specific play (portfolio channel, new intent) | VC funds and accelerators backing Nigerian startups; platform lead | 2 | 3 | Low | Hard | Tier 3 |
| 17 | C17 | Retailer opens a new outlet | Niche-specific play (physical expansion) | S3 retail; founder, HR manager | 3 | 2 | Low | Hard | Tier 3 |
| 18 | C18 | "Salary advance" listed as a perk in job posts | Website content mentions (job posts) | S1 to S3; HR manager | 3 | 2 | Low | Medium | Tier 3 |
| 19 | C19 | Team just crossed 20 staff | Hypergrowth (headcount) | All; founder or CEO | 4 | 1 | Low | Hard | Tier 3 |
| 20 | C20 | Manufacturer registers new products | Niche-specific play (regulatory registry) | S2 manufacturing; founder, HR manager | 2 | 1 | Low | Hard | Tier 3 (blocked) |

Required types: **New Hire** = C8 (and C9). **Lookalike** = C7. **Creative (non-ICP)** = C15 (and C16). **Creative Ideas** = C14. **No-AI** = C4. **Golden ICP** = C2. **Creative stretch** = C6, C10, C12, C18.

Segments are from [signal-matrix.md](../../context/icp/signal-matrix.md): S1 logistics, S2 manufacturing, S3 retail, S4 funded tech. Personas are from [personas.md](../../context/icp/personas.md).

---

## Campaign details

Proof names and numbers below come only from [facts.md](../../context/messaging/facts.md). Quotes are in [social-proof-sources.md](../../context/docs/research/social-proof-sources.md).

### C1. Payroll or HR role posted (Rank 1, Tier 1)

- **Mother intent:** Hiring specific roles. Signal matrix U1.
- **Targeting level:** Focused.
- **Segment and persona:** all four segments. Email the founder or CEO (economic buyer) and, where one exists, the current HR lead. Don't email the hiring candidate.
- **Signal:** a job post in the last 30 days for "Payroll Officer", "Payroll Specialist", "Compensation & Benefits", "HR Officer", "HR Generalist" or "HR Manager", company in Nigeria, then the 20 to 200 check.
- **Data source:** Jobberman, MyJobMag, LinkedIn Jobs. Scrape with `crawl4ai` (local, no cost) or Clay "Find Jobs"; treg `mobiusengine-jobs.jobs.search` is listed at $0.000016 per result but needs its own provider credential, and it is not yet known whether it covers Jobberman or MyJobMag. Run `treg catalog get` first. Live examples seen 2026-11-14: GIG Logistics, Vicadeti Logistics, Obor Logistics ([signal-matrix.md](../../context/icp/signal-matrix.md)).
- **AI strategy:** read the job description and pull which tasks it lists (payroll processing, PAYE, pension, NHF remittance, payslips, attendance). Route the email by the tasks named.
- **Angle (save time, mitigate risk):** they are choosing right now between a person and a system for the work PaidHR does. Angle is "give the new hire the system", not "don't hire": PaidHR files PAYE, pension, NHF and NSITF with a receipt per remittance, so the new person spends their time on people, not filings. Proof: Heroshe ("I leave the software to do the operational tasks and I do the strategic tasks", H8). Timing: the 2027 PAYE return lands in their first months.
- **Overview for the copywriter:** open with the role they posted and one task from the job description. Line two: what that task looks like inside PaidHR (receipt per remittance). Proof: Heroshe. CTA: "Worth a look before the new hire starts?" Differs from C6 (which keys on tools or Excel named in the post) and C5 (which keys on frontline roles).
- **Volume band:** Medium. Real count TBD; run one week of scraping to measure. Periodicity: weekly.
- **Difficulty:** Medium. Scraping two Nigerian job boards plus one AI column.
- **Tier reason:** strong, visible, weekly trigger; one build serves every segment.

### C2. Golden ICP: logistics firm hiring for payroll and frontline (Rank 2, Tier 1)

- **Mother intent:** Hiring specific roles, stacked with hiring velocity and lookalike.
- **Targeting level:** Niche.
- **Segment and persona:** S1 logistics and delivery, 20 to 200 staff. HR manager first, founder second.
- **Signal:** all of: LinkedIn industry in logistics or freight; a payroll or HR job post in the last 30 days (C1); 3+ rider, driver, dispatch or warehouse posts in the last 30 days (C5).
- **Data source:** the same job-board table as C1 and C5, filtered to logistics. Industry from LinkedIn or Clay company enrichment.
- **AI strategy:** what a rep would find in 10 minutes: count of frontline roles open, the cities they are hiring in, whether they deliver across states (website), and the HR or payroll task in the job description.
- **Angle (mitigate risk, save time):** a spread-out team that is growing on two fronts at once. Remittance for that team with a receipt per filing, plus clock-in by location that flows into payroll. Proof: Heroshe, the closest customer match (cross-border shipping, HR-led). Before: "two weeks or more", tax office calls. After: "in less than a click", receipt as evidence.
- **Overview:** open with the two hiring facts ("you're hiring a payroll officer and [N] riders in Lagos this month"). Heroshe proof in one sentence. Mention location-based clock-in as a second line (PaidHR claim, not customer-proven). CTA: "Want to see how Heroshe runs remittance?" This is the most specific email in the set and the one a rep would write by hand.
- **Volume band:** Low. TBD; it is a subset of C1 and C5.
- **Difficulty:** Hard. Three signals stacked; easy once C1 and C5 tables exist.
- **Tier reason:** strongest fit and proof match; low volume, so run it as the logistics route inside C1, not alone.

### C3. Funded in the last 90 days (Rank 3, Tier 1)

- **Mother intent:** Companies fundraising (post-announcement; Nigeria has no Form D equivalent).
- **Targeting level:** Focused.
- **Segment and persona:** S4 funded tech and funded logistics startups (for example Fez Delivery, seen 2026-11-14). Founder or CEO.
- **Signal:** a seed to Series B round announced in the last 90 days, Nigeria HQ, then the 20 to 200 check.
- **Data source:** TechCabal, Techpoint, Nairametrics (RSS via Clay HTTP or `crawl4ai`, no cost); Crunchbase via Clay; treg `aviato.companies.funding_rounds` ($0.01 per success) or `predictleads.companies.financing_events` ($0.04 per call), prices from the signal matrix, confirm with `treg catalog get`.
- **AI strategy:** pull the round size, lead investor and what the money is for (the press release usually names hiring plans). Count open roles on their careers page.
- **Angle (save time):** the team is about to grow and payroll grows with it. FAMASI's CEO: "As the team grew, we realized there was a need for a more sustainable HR solution", and about one hour saved per payroll run. Logos (Flutterwave, Mono, Risevest) as a single line of logo proof.
- **Overview:** congratulate in five words, not a paragraph. Line two: their hiring plan from the release. Line three: FAMASI proof. CTA: "Worth setting up before the next hires start?" Do not imply investors require it (INFERRED, not evidenced).
- **Volume band:** Medium. Nigeria raised about $635M from January to September 2026 ([market.md](../../context/docs/research/market.md)); round count per month TBD. Periodicity: bi-weekly.
- **Difficulty:** Easy. Structured, public, cheap.
- **Tier reason:** best data in Nigeria and PaidHR's strongest proof sits in this segment; signal link to purchase is INFERRED.

### C4. PAYE return countdown (Rank 4, Tier 1, no AI)

- **Mother intent:** Regulatory changes.
- **Targeting level:** Broad.
- **Segment and persona:** the whole base list, finance lead and HR manager. Lead with S1 and S2 (most users).
- **Signal:** none at account level. Market-wide: the 2027 annual PAYE return is the first under the new bands (INFERRED date 31 January 2027). Penalty for missing the annual return: ₦100,000 then ₦50,000 a month (search-result summaries, [market.md](../../context/docs/research/market.md); verify before quoting).
- **Data source:** base list only (Clay or Apollo by industry, size, Nigeria).
- **AI strategy:** none. See the No-AI section.
- **Angle (mitigate risk):** the deadline is fixed, the bands changed, and DLA Piper reports systems on old bands produce wrong deductions (Third party). PaidHR is "Fully updated for Nigeria's new tax law, effective 1 January 2026" (PaidHR claim).
- **Volume band:** High. Time-boxed: send November 2026 to mid-January 2027.
- **Difficulty:** Easy.
- **Tier reason:** fast, cheap, time-limited window; weakest signal, so expect lower reply rates per email.

### C5. Frontline hiring wave (Rank 5, Tier 1)

- **Mother intent:** Hypergrowth (hiring velocity). Signal matrix U2.
- **Targeting level:** Focused.
- **Segment and persona:** S1 (riders, drivers, dispatch, warehouse), S2 (machine operators, production), S3 (sales attendants, cashiers). HR manager; founder for companies with no HR title.
- **Signal:** 3+ frontline posts at one company in the last 30 days (threshold INFERRED; tune after the first pull).
- **Data source:** same job-board table as C1, aggregated by company.
- **AI strategy:** count roles by type and city; classify the workforce (field, shift, outlet). Route the module: field = location clock-in; shift = overtime into payroll; low-wage = EWA and USSD.
- **Angle (save time, retention):** more frontline staff means more clock-ins, more payslip questions and more salary-advance requests. Hours flow from clock-in to payroll; staff reach payslips and earned wages on WhatsApp or USSD with no data. Proof: Heroshe on payslips ("that burden just goes off my neck", H7). EWA at no cost to the employer ("automatically included in your PaidHR plan", PaidHR claim).
- **Overview:** open with the count ("[N] dispatch riders in Lagos and Ibadan this month"). One module line chosen by route. Proof line. CTA: "Want to see how clock-in feeds payroll?"
- **Volume band:** Medium. TBD. Periodicity: weekly.
- **Difficulty:** Medium. Same scrape as C1, plus counting and routing.
- **Tier reason:** points straight at the tier 1 industries; near-zero extra build on top of C1.

### C6. Job post says "Excel payroll" or names a tool (Rank 6, Tier 2, creative stretch)

- **Mother intent:** Competitor customers (via job posts). Signal matrix U8.
- **Targeting level:** Niche.
- **Segment and persona:** all; HR manager.
- **Signal:** the job description text from C1 mentions "Excel", "spreadsheet", "manual payroll", "remittance", or a named tool (SeamlessHR, Sage, Workpay, SoftSUITE).
- **Data source:** the C1 table plus one AI column on the description.
- **AI strategy:** extract the exact phrase and tool. For spreadsheet mentions, route to the "manual" angle; for a named tool, route to the "receipts" angle.
- **Angle:** spreadsheet route: the FAMASI before and after ("everything was manual", one hour saved). Tool route: remittance with a receipt per filing, tax-law updated. Never criticise the named tool (insult test, [facts.md](../../context/messaging/facts.md)).
- **Overview:** quote their own job post line back in a neutral way ("your Payroll Officer post mentions monthly Excel reconciliations"). One proof line. CTA: soft question.
- **Volume band:** Low. A routing layer inside C1, not its own list.
- **Difficulty:** Medium.
- **Tier reason:** strongest story but low volume; build as a route inside C1.

### C7. Heroshe lookalikes (Rank 7, Tier 2, required Lookalike)

- **Mother intent:** Lookalike of customers. Signal matrix U7.
- **Targeting level:** Focused.
- **Segment and persona:** S1 logistics, shipping, freight and delivery, 20 to 200. HR manager or HR operations (the Heroshe speaker's role).
- **Signal:** none (fit only). Seed: Heroshe.
- **Data source:** Clay lookalike or company search by LinkedIn industry and size; Seedtable and press lists of Lagos logistics startups ([signal-matrix.md](../../context/icp/signal-matrix.md)).
- **AI strategy:** from the website, pull what they ship, where (states, countries) and whether they run riders or agents. Use it in line one.
- **Angle (mitigate risk):** "a shipping company like yours" plus Heroshe's before and after on remittance, with the receipt quote (H2).
- **Overview:** open with one fact about their routes. Heroshe line. Link to the Heroshe video. CTA: "Want the two-minute version from Heroshe's HR team?"
- **Volume band:** High (static list, used once per account). TBD.
- **Difficulty:** Easy.
- **Tier reason:** large and easy, but no timing; best as the base list C1 and C5 run against, or as a filler send.

### C8. New HR leader in the first 90 days (Rank 8, Tier 2, required New Hire)

- **Mother intent:** New leadership (past 90 days). Signal matrix U5.
- **Targeting level:** Focused.
- **Segment and persona:** all; new HR Manager, Head of HR or People Lead.
- **Signal:** started the role in the last 90 days, company Nigeria 20 to 200.
- **Data source:** Clay "Find People" with start date; treg `leadmagic.x.job-change-detector` ($0.075 per call, price from signal matrix; confirm first).
- **AI strategy:** pull start date, previous company and whether that company was a PaidHR logo or competitor customer (for context only, don't name the competitor).
- **Angle (save time):** a new HR lead inherits payroll and remittance, and the 2027 PAYE return falls in their first months. Quick win: remittance with a receipt per filing. Proof: Heroshe, "I would recommend Pade to any HR professional" (H9).
- **Overview:** welcome in one line; reference their previous company. Line two: what they are inheriting this January. Proof. CTA: "Is payroll on your first-90-days list?"
- **Volume band:** Low. TBD. Periodicity: monthly.
- **Difficulty:** Medium. Start dates in Nigeria may be thin on LinkedIn.
- **Tier reason:** classic opener, but untested and likely low volume in Nigeria 20 to 200.

### C9. New finance leader in the first 90 days (Rank 9, Tier 2)

- **Mother intent:** New leadership (past 90 days).
- **Targeting level:** Focused.
- **Segment and persona:** all; new Finance Manager, Head of Finance, CFO (influencer).
- **Signal and data:** as C8 with finance titles.
- **AI strategy:** as C8.
- **Angle (mitigate risk):** penalties are now automated (PenCom, October 2026, Third party), so filings should be too. "₦934M in PAYE filed and ₦754M in pension processed in 2025" (PaidHR claim, quote exactly). No finance-buyer customer quote exists; say so internally and don't invent one.
- **Overview:** one line on their new role, one on the January PAYE return and pension timing (within 7 working days of salary), one proof line. CTA: "Want a look at what one month of filings looks like?"
- **Volume band:** Low. TBD.
- **Difficulty:** Medium.
- **Tier reason:** same as C8; weaker proof for this persona.

### C10. Tax-law engagers on LinkedIn (Rank 10, Tier 2, creative stretch)

- **Mother intent:** LinkedIn content engagement.
- **Targeting level:** Focused.
- **Segment and persona:** HR managers and finance leads at Nigerian companies, 20 to 200.
- **Signal:** liked or commented in the last 30 days on posts about the Nigeria Tax Act, new PAYE bands or PenCom enforcement (posts by PaidHR, law firms such as DLA Piper Africa, payroll vendors, Nairametrics).
- **Data source:** LinkedIn post engager scrape (Clay or a treg LinkedIn posts endpoint; check price first). The treg pull of PaidHR's own LinkedIn posts already exists in `context/docs/research/raw/`.
- **AI strategy:** pull the post they engaged with and, if they commented, the gist of the comment.
- **Angle (mitigate risk):** they already care about the change; offer the practical step (front-end offer 1 below).
- **Overview:** reference the post topic, not the act of engaging ("saw you're following the new PAYE bands"). Offer the readiness check. CTA: "Want it for your team?"
- **Volume band:** Medium. TBD.
- **Difficulty:** Medium.
- **Tier reason:** warm and topical; engagement is a weaker buying signal than a job post.

### C11. Lagos pension enforcement (Rank 11, Tier 2)

- **Mother intent:** Regulatory changes.
- **Targeting level:** Focused.
- **Segment and persona:** Lagos-based employers, S1 and S2 first; finance lead.
- **Signal:** location only. PenCom and NLC enforcement in Lagos from June 2026; automated penalties from October 2026 (Third party). Employer names in enforcement news are not published, so no account-level trigger (signal matrix N3, killed as a list source).
- **Data source:** base list filtered to Lagos.
- **AI strategy:** light: count of staff (pension liability scales with it) and industry.
- **Angle (mitigate risk):** pension due within 7 working days of salary, now checked automatically; PaidHR remits pension with a receipt per remittance. Guess their situation, never accuse them of default.
- **Overview:** one line on the Lagos enforcement news, one on receipts, Heroshe proof. CTA: "Want to see a pension receipt from PaidHR?"
- **Volume band:** High. TBD.
- **Difficulty:** Easy.
- **Tier reason:** easy and timely, but no account-level signal; overlaps C4, so run one or the other per account.

### C12. Moonshot founders and speakers (Rank 12, Tier 2, creative stretch)

- **Mother intent:** Companies attending an event.
- **Targeting level:** Niche.
- **Segment and persona:** founders and business operators at Moonshot 2026 (Lagos, October 2026). PaidHR's team attended ("connecting with founders, HR leaders, and business operators", [signals.md](../../context/docs/research/signals.md)).
- **Signal:** listed as a speaker or exhibitor on the public event pages, company Nigeria 20 to 200.
- **Data source:** Moonshot speaker and partner pages via `crawl4ai`; LinkedIn posts tagged #Moonshot2026.
- **AI strategy:** pull the talk title or panel topic.
- **Angle (save time):** "we were there too" plus a line tied to their talk topic; FAMASI proof for founders.
- **Overview:** open with their session. Bridge to team growth. FAMASI line. CTA: "Did we miss each other at Moonshot?"
- **Volume band:** Low (one event). TBD. Repeat for each major Lagos event.
- **Difficulty:** Easy.
- **Tier reason:** warm, cheap and quick; one-off volume.

### C13. Hiring outside Nigeria (Rank 13, Tier 3)

- **Mother intent:** Hiring offshore. Signal matrix U6.
- **Targeting level:** Focused.
- **Segment and persona:** S4 tech; founder and finance lead.
- **Signal:** Nigerian HQ company posting roles in Kenya, South Africa, the UK or "remote" in the last 60 days.
- **Data source:** LinkedIn Jobs and careers pages by location.
- **AI strategy:** pull the countries and role count.
- **Angle (save time):** pay a team abroad from the same dashboard as local payroll. Only quote "$2M+ in cross-border payments processed since October 2024" (PaidHR claim). Keep currency and country counts fuzzy ([facts.md](../../context/messaging/facts.md)). Never claim EOR.
- **Volume band:** Low. TBD.
- **Difficulty:** Medium.
- **Tier reason:** Workpay and Deel lead here and PaidHR has no EOR; no customer proof for cross-border.

### C14. Creative Ideas: 3 uses from their website (Rank 14, Tier 2, required Creative Ideas)

- **Mother intent:** Niche-specific play.
- **Targeting level:** Broad.
- **Segment and persona:** whole base list, S1 to S3 first; founder or CEO.
- **Signal:** none.
- **Data source:** base list plus a website scrape (`crawl4ai`, free).
- **AI strategy:** read their website and classify the workforce (riders, outlets, factory, office). Generate three PaidHR uses tied to what they do. Example for a delivery company: (1) riders clock in by location and hours flow into payroll, (2) riders check payslips and draw earned wages by USSD with no data, (3) PAYE and pension filed with a receipt each month. Only modules from [company.md](../../context/docs/research/company.md); no invented outcomes.
- **Angle:** shows research, gives immediate ideas, lets them pick.
- **Overview:** "I had an idea for {{company_name}}" plus three bullets. One proof line matched to the first bullet. CTA: "Would any of these be useful?"
- **Volume band:** High. TBD.
- **Difficulty:** Medium (prompt quality decides it; build with `/prompt-builder`).
- **Tier reason:** no timing signal; good as the always-on base campaign once Tier 1 runs.

### C15. Accountants and payroll consultants (Rank 15, Tier 2, required Creative non-ICP)

- **Mother intent:** Niche-specific play (partner channel). New intent, flagged: not in the catalog.
- **Targeting level:** Focused.
- **Segment and persona:** accounting, tax advisory and outsourced payroll firms in Lagos and Abuja that serve SMEs. Partner, owner or head of payroll services.
- **Signal:** their website lists payroll, PAYE or pension remittance as a service.
- **Data source:** Google Maps ("accounting firm", "tax consultant", "payroll services" in Lagos) via treg `crawl4ai.google.serp.maps` ($0.00023 per success per the signal matrix; confirm first), then a website scrape. Professional body directories (for example ICAN or CITN) may list members; not verified, check before use.
- **AI strategy:** read their service page; pull the services they list and the industries of clients they name.
- **Angle (make money, save time):** PaidHR offers white label and a Payroll API so firms can "launch your own payroll business without building one" ([company.md](../../context/docs/research/company.md)), or refer clients. Their clients face the same 2027 PAYE return.
- **Overview:** open with the payroll service on their site. Offer white label or referral as two options. CTA: "Open to a 20-minute look at how other firms would run it?" Copy must not claim existing partner firms: none are named in research.
- **Volume band:** Medium. TBD.
- **Difficulty:** Hard. A partner motion needs a partner offer PaidHR has not published (terms TBD).
- **Tier reason:** one deal brings many employers, and few vendors email these firms; partner terms are unknown, so confirm with PaidHR first.

### C16. VC platform and accelerator teams (Rank 16, Tier 3, Creative non-ICP)

- **Mother intent:** Niche-specific play (portfolio channel). New intent, flagged.
- **Targeting level:** Niche.
- **Segment and persona:** platform or portfolio-support leads at VC funds and accelerators backing Nigerian startups.
- **Signal:** led or joined a Nigerian round in the last 12 months (from the C3 table).
- **Data source:** investor names from the C3 funding table; people via LinkedIn.
- **AI strategy:** count their Nigerian portfolio companies in the 20 to 200 band.
- **Angle (save time for the portfolio):** a portfolio perk for payroll and remittance. PaidHR's own seed came from Accion Venture Lab ([company.md](../../context/docs/research/company.md)), which shows investor familiarity but is not an endorsement; don't imply one.
- **Volume band:** Low. TBD.
- **Difficulty:** Hard. Needs a perk offer PaidHR has not defined.
- **Tier reason:** speculative; no perk exists yet.

### C17. Retailer opens a new outlet (Rank 17, Tier 3)

- **Mother intent:** Niche-specific play (physical expansion). Signal matrix N1.
- **Targeting level:** Niche.
- **Segment and persona:** S3 multi-outlet retail; founder, HR manager.
- **Signal:** outlet count on Google Maps rises month on month (3+ outlets).
- **Data source:** Google Maps snapshots via treg `crawl4ai.google.serp.maps`; delta logic untested.
- **AI strategy:** name the new location.
- **Angle:** clock-ins across outlets feed payroll; staff reach payslips and leave by WhatsApp or USSD.
- **Volume band:** Low. TBD.
- **Difficulty:** Hard (monthly snapshots and diffing).
- **Tier reason:** no retail customer to cite; hold until PaidHR names one.

### C18. "Salary advance" listed as a perk in job posts (Rank 18, Tier 3, creative stretch)

- **Mother intent:** Website content mentions (in job posts).
- **Targeting level:** Niche.
- **Segment and persona:** S1 to S3; HR manager.
- **Signal:** job posts that offer "salary advance" or "staff loans" as a benefit (signal 7 in [signals.md](../../context/docs/research/signals.md)).
- **Data source:** C1 and C5 job text, keyword match.
- **AI strategy:** quote the benefit line.
- **Angle (save money, retention):** they already fund advances; EWA gives staff earned pay before payday with "PaidHR fronts the capital" (PaidHR claim). Never call EWA a loan.
- **Volume band:** Low. TBD.
- **Difficulty:** Medium.
- **Tier reason:** sharp angle but rare in posts, and EWA has no customer proof.

### C19. Team just crossed 20 staff (Rank 19, Tier 3)

- **Mother intent:** Hypergrowth (headcount). Signal matrix U3.
- **Targeting level:** Focused.
- **Segment and persona:** all; founder or CEO.
- **Signal:** headcount under 20 six months ago, 20+ now, or 20%+ growth in 6 months.
- **Data source:** LinkedIn headcount history via Clay or treg (`companyenrich.companies.workforce`, $0.049 per success). Nigerian headcount data is unreliable.
- **Angle:** FAMASI's exact trigger: "As the team grew, we realized there was a need for a more sustainable HR solution."
- **Volume band:** Low. TBD.
- **Difficulty:** Hard.
- **Tier reason:** the only trigger a customer named, but the data can't be trusted alone; use it to rank C1, C3 and C5 accounts instead.

### C20. Manufacturer registers new products (Rank 20, Tier 3, blocked)

- **Mother intent:** Niche-specific play (regulatory registry). Signal matrix N2.
- **Segment and persona:** S2 manufacturing; founder, HR manager.
- **Signal and data:** new NAFDAC product registrations in the last 90 days. The registry has not been verified as public or scrapable.
- **Angle:** new lines mean new shifts and overtime; attendance into payroll.
- **Volume band, difficulty:** Low; Hard.
- **Tier reason:** blocked until the source is verified.

---

## No-AI campaigns

**C4. PAYE return countdown**
- **Why it works without AI:** every Nigerian employer faces the same fixed date and the same new bands, so the deadline is the personalisation. It costs only the base list.
- **Core message:** (1) the January return is the first under the 2026 bands; (2) systems still on the old bands produce wrong deductions (DLA Piper); (3) PaidHR is updated for the new law and files PAYE, pension, NHF and NSITF with a receipt per remittance; (4) CTA: "Want a quick check of last month's payroll against the new bands?" Three short lines, one link.

**C11 can also run without AI** if needed: Lagos enforcement news plus receipts.

---

## Front-end offer suggestions

1. **2026 bands payroll check.** We run one month of their payroll figures through the new 2026 PAYE bands and show any differences in deductions. Low effort for the prospect, directly tied to the January deadline, and it puts their data into PaidHR. Needs PaidHR to confirm it can offer this and who runs it (TBD).
2. **PaidRight salary benchmark.** PaidHR already publishes a salary benchmark from "25,000+ workers and 400+ employers" ([company.md](../../context/docs/research/company.md)). Offer the report for their industry and city as a no-pitch first touch, especially for C5, C8 and C14. Check the report is shareable.
3. **One-month remittance trial with receipts.** Run one month of PAYE and pension through PaidHR and keep the receipts. This is the Heroshe moment ("in less than a click", then a receipt) inside 30 days. Trial terms are not published (TBD).

---

## Recommendation: build C1 first

**Build C1, "Payroll or HR role posted", with C2 (logistics) and C6 (Excel or tool mentions) as routes inside it.**

1. **Strongest signal we can see from outside.** A company posting for a payroll or HR officer is deciding right now how payroll and remittance get done. No other visible signal is this close to the purchase.
2. **Data is reachable today at little or no cost.** Jobberman, MyJobMag and LinkedIn Jobs are public; live examples were found on 2026-11-14. `crawl4ai` scrapes them locally.
3. **One build, many campaigns.** The same job-post table feeds C2, C5, C6 and C18 by changing keywords ([signal-matrix.md](../../context/icp/signal-matrix.md) reached the same conclusion).
4. **Proof matches.** The HR-led Heroshe story fits the HR route and the logistics route; FAMASI fits the founder route.
5. **Timing.** Launching in November leaves the January PAYE return ahead of every prospect.

**Risk:** the link from "hiring a payroll officer" to "buying software" is INFERRED. Treat the first send as the test, and track reply rate by route.

**Quick parallel win:** C4 (PAYE countdown, no AI) can go out within days on the base list while C1 is built, but only until mid-January 2027.

**Before building:**
- Confirm sending inboxes are warmed and a sender identity exists ([facts.md](../../context/messaging/facts.md) lists sender name, title and CTA as open questions).
- Run one week of job-board scraping to replace the C1 volume band with a real count.
- Run `/build-workflow-spec` on C1.

## Open questions

- Real monthly volume for every idea: TBD until the first pull.
- Partner terms for C15 and perk terms for C16: not published.
- Whether PaidHR can offer the payroll check (front-end offer 1) and a trial (offer 3).
- A named retail customer, needed before C17.
- The CTA ladder and sender identity in [facts.md](../../context/messaging/facts.md).
