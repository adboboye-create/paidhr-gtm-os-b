# PaidHR Signal Matrix

Work in progress, not a final deliverable. Validate with sales and leadership before building. Last updated 2026-11-14.
Built with `knowledge-base/playbooks/signal-matrix-framework.md` and the Mother Intent Catalog in `knowledge-base/playbooks/workflow-anatomy.md`.

**Sources.** File names in [brackets] are in `context/docs/research/`, except [icp.md] and [personas.md], which are in `context/icp/`. Web sources found while building this matrix are linked inline (checked 2026-11-14).

**Evidence labels.** **Customer**: a PaidHR customer said it. **Third party**: an outside source (Accion, press) said it. **PaidHR claim**: only PaidHR's own marketing supports it. **INFERRED**: the research does not support it; it is my reasoning and needs testing.

---

## 0. What we are matching against

| Item | Summary | Source |
|---|---|---|
| Product | HR, payroll and statutory remittance (PAYE, pension, NHF, NSITF) in one platform, plus attendance, earned wage access (EWA), loan marketplace, cross-border payroll, WhatsApp and USSD access for staff | [company.md] |
| Core pain | Manual payroll and remittance: "two weeks or more" to remit, "calls from the tax office", founder spending "one hour" per run | [customer-videos.md] |
| Who buys today | "logistics, retail, and manufacturing businesses with under 200 employees" (Accion, June 2025); logos skew to funded Lagos fintechs | [customers.md] |
| Size band | 20 to 200 staff (Standard tier floor 20; Accion ceiling 200) | [icp.md], [company.md] |
| Market | Nigeria first. Kenya and South Africa are served, but research has no regulation or customer data for them | [company.md], [market.md] |
| Competitors | SeamlessHR, Workpay, SoftSUITE, Sage, PaySpace, Cadana; Bento (paused) | [competitors.md] |
| Product shape | Multi-module. Lead module and upsell module change by segment, so Matrix 1 carries them | [company.md] |

**Market-wide "why now" (applies to every row, use for timing and copy, not to pick accounts):**
- Nigeria Tax Act payroll rules live since 1 Jan 2026; systems on old bands produce wrong deductions. [market.md]
- First annual PAYE return under the new law due 31 Jan 2027 (INFERRED from the 31 Jan annual deadline). [market.md]
- PenCom and NLC pension enforcement in Lagos from June 2026; automated penalty calculation announced Oct 2026. [market.md]

Implication: every workflow below should launch before January 2027 so the PAYE return deadline is still ahead of the prospect (INFERRED).

---

## 1. Matrix 1: Segments x Personas

### Axis choice

- **Rows: industry segment, Nigeria, 20 to 200 staff.** Industry is observable (LinkedIn industry, job post category), mutually exclusive, and changes the angle: tier 1 industries have frontline workforces (attendance, EWA, USSD); tech startups have salaried, smartphone staff and investor scrutiny. [icp.md]
- **Columns: the three personas** from [personas.md]: Champion (HR manager or HR operations), Economic buyer (founder or CEO), Influencer (finance lead).
- **Left out as rows:** Kenya and South Africa (no regulation, customer or signal research yet); cross-border employers (overlaps the tech row, so it is a signal in Matrix 2, not a row); payroll agencies for white label (one product page, no customers named, INFERRED small volume); engineering, research and restaurant tech (one logo each, "Don't target as a segment"). [icp.md], [company.md]

### Segment definitions

| # | Segment | Target definition (filterable) | Lead module / upsell (hypothesis) | Priority | Proof we can cite |
|---|---|---|---|---|---|
| S1 | Logistics and delivery | Nigeria HQ (Lagos first), 20 to 200 staff, LinkedIn industry "Transportation, Logistics, Supply Chain and Storage" or "Truck Transportation" or "Freight and Package Transportation"; riders, drivers, dispatch or warehouse roles in job posts | Statutory remittance + payroll / Time and attendance, EWA, USSD | **High**: tier 1 industry and the only tier 1 customer with a story (Heroshe) | Heroshe video and case study [customer-videos.md], [customers.md] |
| S2 | Manufacturing (food, FMCG, light industry) | Nigeria HQ, 20 to 200 staff, LinkedIn industry "Food and Beverage Manufacturing" or "Manufacturing"; factory operator, production or machine roles in job posts | Statutory remittance + payroll / Attendance (shifts, overtime), EWA | **High**: tier 1 industry; proof is thin (ReelFruit logo only) | ReelFruit logo only [customers.md] |
| S3 | Retail (multi-outlet) | Nigeria HQ, 20 to 200 staff, LinkedIn industry "Retail" or "Retail Groceries" or "Retail Apparel and Fashion"; 3+ physical outlets on Google Maps (INFERRED threshold) | Payroll + attendance (geo-referenced clock-in) / EWA, USSD | **Medium**: tier 1 industry but no named retail customer, so no proof | None named [icp.md] |
| S4 | Funded tech startups (mainly fintech) | Nigeria HQ, 20 to 200 staff, LinkedIn industry "Financial Services", "Software Development", "IT Services"; disclosed VC round | Payroll + statutory remittance / Cross-border payroll, performance (OKRs) | **High** for reachability, **Medium** for volume: strongest logos and best data footprint, but "not the majority of users" | 6 of 12 logos, FAMASI video [customers.md], [customer-videos.md] |

### Company examples (seed lists, not qualified)

Never fabricated. Headcount was not verified for any prospect below; check 20 to 200 in Clay before use. Current customers are listed as lookalike seeds only, not as targets.

| Segment | Lookalike seeds (current customers) | Prospect examples found 2026-11-14 | Status |
|---|---|---|---|
| S1 | Heroshe | GIG Logistics (hiring a Compensation and Benefits Officer, [MyJobMag](https://www.myjobmag.com/job/compensation-benefits-officer-gig-logistics-1); size likely above 200, check); Vicadeti Logistics (hiring a Payroll and Benefits Manager, [Jobberman](https://www.jobberman.com/listings/payroll-and-benefits-manager-vdgjqv)); Obor Logistics Nigeria (hiring an HR Manager, [Jobberman](https://www.jobberman.com/listings/hr-manager-j6q7g6)); Kwik Delivery, Dellyman ([TechEconomy](https://techeconomy.ng/dellyman-inks-last-mile-deliveries-with-temu/)); Fez Delivery ($1M seed, [Condia](https://thecondia.com/wp-content/fez-delivery-secures-seed-1-million/)); Chowdeck ([Seedtable](https://seedtable.com/best-logistics-startups-in-lagos)) | Partial. More via Clay filters in the definition |
| S2 | ReelFruit | Ayoola Foods (listed 51 to 200 staff, [allbusiness.africa](https://allbusiness.africa/business/ayoola-foods-limited)); L&L Foods, Fastizers ([How We Made It In Africa](https://www.howwemadeitinafrica.com/p/how-this-cookie-company-cracked-the-nigerian-market)); D&B lists food manufacturers in Lagos as a list source ([D&B](https://www.dnb.com/business-directory/company-information.food_manufacturing.ng.lagos.html)) | Partial. Requires Clay research: Nigeria, 20 to 200, food or FMCG manufacturing |
| S3 | None | None verified | Requires Clay research: Nigeria, 20 to 200, retail industries, then Google Maps outlet count |
| S4 | Flutterwave, Mono, Risevest, GetEquity, Kredete, GO54, FAMASI | None verified as non-customers in this pass | Requires Clay research: Nigeria, 20 to 200, funding announced in last 12 months |

### Matrix 1: the angle per cell

Angles describe the prospect's situation, not a diagnosis. Quotes come from [customer-videos.md] and [personas.md] and are auto-captions; check against the video before using in copy.

| Segment | Champion: HR manager / HR ops | Economic buyer: founder / CEO | Influencer: finance lead |
|---|---|---|---|
| **S1 Logistics** | Remittance for a spread-out team without the two-week wait and the tax office calls; receipts after each filing as proof. Direct match to Heroshe ("distributed workforce", "calls from the tax office"). **Customer** | Riders and drivers paid on time and clocked in by location, without the founder confirming each payment by hand. Payroll part is **Customer** (FAMASI); field-staff attendance is a **PaidHR claim** | Pension remitted within 7 working days of salary while PenCom runs automated penalties in Lagos; one ledger for PAYE, pension, NHF, NSITF. **Third party** (market.md) + **PaidHR claim**. No finance quote exists |
| **S2 Manufacturing** | Shifts and overtime flow from clock-in into payroll, and statutory deductions on new 2026 bands. **PaidHR claim**; band change is **Third party** (DLA Piper) | Factory staff can draw earned wages before payday at no cost to the company ("Support your team without spending a naira"). **PaidHR claim**. Retention link is INFERRED | First PAYE annual return under new bands due 31 Jan 2027; old-band systems produce wrong deductions. **Third party**; the 2027 date is INFERRED |
| **S3 Retail** | Clock-ins across outlets feed payroll; staff get payslips and leave on WhatsApp or USSD, so fewer pay queries reach HR. Payslip relief is **Customer** (Heroshe "that [burden] just goes off my neck"); multi-outlet is INFERRED | Staff without smartphones or data still reach pay, payslips and wage access via USSD. **PaidHR claim** (USSD launched 2026-10-26) | Pay and attendance in one system across outlets ("Disconnected tools cost more than money"). **PaidHR claim**; no finance quote |
| **S4 Funded tech** | Remittances done and evidenced, payslips self-served, time back for strategic work ("I leave the software to do the operational [tasks]"). **Customer** (Heroshe) | Team just grew; payroll still takes founder time ("one hour of the day" per run, texting staff to confirm). **Customer** (FAMASI: "as a team [grew] we realized there was a need") | Statutory compliance as investors and NRS look closer; cross-border pay for staff abroad in 45+ currencies. Compliance pressure is **Third party**; investor angle is INFERRED; cross-border is **PaidHR claim** |

### Phase 2 scoring (High / Med / Low)

| Segment | Signal density | Product fit | Penetrability (Nigeria data) | Overall |
|---|---|---|---|---|
| S1 Logistics | High: posts frontline and payroll roles on Jobberman and MyJobMag (seen above) | High: Accion mix + Heroshe | Med: many on LinkedIn; headcount data for Nigeria is unreliable (treg returned 1 employee for PaidHR) | **1st** |
| S4 Funded tech | High: funding press, LinkedIn, job boards | Med: logos fit, but not the majority of users | High: best digital footprint | **2nd** |
| S2 Manufacturing | Med: job posts; few VC events | High: Accion mix | Low to Med: weaker LinkedIn footprint (INFERRED) | **3rd** |
| S3 Retail | Med: Google Maps outlets + job posts (INFERRED) | Med: Accion mix, no proof | Low to Med (INFERRED) | **4th** |

All four rows carry into Matrix 2. Penetrability scores are INFERRED; the first Clay pulls will show real coverage.

---

## 2. Matrix 2: Buying signals

### Scoring the four tests

Each test is scored 1 to 5, total out of 20. Scores are judgment calls from the research; any score not backed by a source is INFERRED by definition. **Volume is TBD for every signal**: no pull has been run. Measure it on the first Clay or treg run and replace the score.

- **Buying reason**: does it explain why they would buy now?
- **Volume**: enough accounts per month across Nigeria 20 to 200?
- **Data**: can a Clay operator or treg pull it today?
- **Story**: can the first line of an email reference it naturally?

Tool prices are from `treg catalog search` on 2026-11-14. Run `treg catalog get <id>` to confirm the price before every call (CLAUDE.md rule).

### Signal list with Iron Law details

| # | Type | Signal (observable event) | Mother intent | Evidence | Data source | Tool to detect | Key filters | Buy | Vol | Data | Story | Total | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U1 | Universal | Posts a job for a payroll, compensation and benefits, or HR generalist role | Hiring specific roles | INFERRED ([signals.md] #10). Live examples exist (GIG Logistics, Vicadeti) | Jobberman, MyJobMag, LinkedIn Jobs | Clay "Find Jobs"; treg `mobiusengine-jobs.jobs.search` ($0.000016/result, needs its own provider credential, not yet run [company.md]); treg `akta.x.jobs` ($0.02/result) | Titles: "Payroll Officer", "Payroll Specialist", "Compensation & Benefits", "HR Generalist", "HR Officer", "HR Manager"; country Nigeria; posted last 30 days; then ICP filter 20 to 200 | 4 | 3 | 3 | 5 | 15 | VERIFIED (source); volume TBD |
| U2 | Universal | Frontline hiring velocity: 3+ open frontline roles at once | Hypergrowth (hiring velocity) | **PaidHR claim** (attendance, EWA, USSD) [signals.md] #6; link to purchase INFERRED | Jobberman, MyJobMag, LinkedIn Jobs | Same as U1, aggregated by company | S1: rider, driver, dispatch, warehouse. S2: machine operator, production, factory. S3: sales attendant, cashier, store. Last 30 days, count 3+ (threshold INFERRED) | 3 | 4 | 3 | 4 | 14 | VERIFIED (source); threshold and volume TBD |
| U3 | Universal | Headcount grew 20%+ in 6 months, or just crossed 20 | Hypergrowth (headcount) | **Customer** (FAMASI: team grew, needed "a more sustainable HR solution") | LinkedIn company headcount history | Clay "Enrich Company"; treg `companyenrich.companies.workforce` ($0.049/success), `icypeas.companies.enrich` ($0.0095/success), `fiber-ai.linkedin.company.profile` ($0.04/call) | Nigeria, 20 to 200 now; growth 20%+ over 6 months or under 20 six months ago | 4 | 3 | 2 | 4 | 13 | VERIFIED (COMPOUND): Nigerian headcount data is unreliable (treg returned 1 for PaidHR). Pair with U1 or U2 |
| U4 | Universal (S4 strongest) | Announced a funding round in the last 90 days | Fundraising | INFERRED ([icp.md]: logos skew funded; no customer named funding as the trigger). Market: ~$635M raised Jan to Sep 2026 [market.md] | TechCabal, Techpoint, Nairametrics; Crunchbase | Clay "Find Organization" (Crunchbase); treg `predictleads.companies.financing_events` ($0.04/call), `aviato.companies.funding_rounds` ($0.01/success); RSS of the three outlets via Clay HTTP | Nigeria HQ; seed to Series B; announced last 90 days; then 20 to 200 | 3 | 3 | 4 | 4 | 14 | VERIFIED for S4 and funded S1 (e.g. Fez Delivery). KILLED for S2 and S3: little VC in SME manufacturing and retail (INFERRED, per framework guidance on non-VC markets) |
| U5 | Universal | New HR or finance leader started in last 90 days | New leadership | INFERRED ([signals.md] #9: "Not found") | LinkedIn profiles | Clay "Find People" with start date; treg `leadmagic.x.job-change-detector` ($0.075/call) | Titles: HR Manager, Head of HR, People Lead, Finance Manager, Head of Finance; start date last 90 days; Nigeria; 20 to 200 | 3 | 2 | 3 | 4 | 12 | VERIFIED (source); untested |
| U6 | Universal | Nigerian company hiring staff outside Nigeria (Kenya, South Africa, UK, remote) | Hiring offshore | **PaidHR claim** ($2M+ cross-border since Oct 2024) [company.md] | LinkedIn Jobs, company careers pages | Clay "Find Jobs" by location; treg job search (as U1) | HQ Nigeria; job location not Nigeria or "remote"; last 60 days | 3 | 2 | 3 | 4 | 12 | VERIFIED (source). Mostly S4. Watch: Workpay and Deel lead here, and PaidHR has no EOR [competitors.md] |
| U7 | Universal | Lookalike of current customers | Lookalike of customers | **Third party** (Accion customer mix) | Seeds: Heroshe, ReelFruit, plus fintech logos | Clay lookalike / company search by industry and size | Seeds per segment (S1 Heroshe; S2 ReelFruit; S4 fintech logos); Nigeria; 20 to 200 | 2 | 5 | 4 | 2 | 13 | VERIFIED. Static, no timing: use as the base list that U1 to U3 run against, not as a standalone workflow |
| U8 | Universal (compound) | HR job post names a competitor or a manual process (e.g. "SeamlessHR", "Sage", "Excel payroll", "remittance") | Competitor customers via job posts | INFERRED | Job description text from U1 pulls | AI column (Clay "Use AI") on job description | Keyword list above | 3 | 1 | 3 | 4 | 11 | VERIFIED (COMPOUND): routing layer on U1, not its own workflow |
| N1 | Niche (S3) | Retailer adds a new outlet (Google Maps location count rises) | Niche-specific (physical expansion) | INFERRED | Google Maps | treg `crawl4ai.google.serp.maps` ($0.00023/success); Clay HTTP to Google Places | Brand name search in Lagos, Abuja, Port Harcourt; outlet count 3+; monthly snapshot delta | 3 | 2 | 3 | 4 | 12 | VERIFIED (source); delta logic untested |
| N2 | Niche (S2) | Manufacturer registers new products (new SKUs = growth) | Niche-specific (regulatory registry) | INFERRED | NAFDAC registered products database (source not verified in this pass) | Clay HTTP scrape, if accessible | Company name match; new registrations last 90 days | 2 | 2 | 1 | 3 | 8 | NEEDS VERIFICATION: confirm the registry is public and scrapable before building |
| N3 | Niche (all, Lagos) | Employer named in PenCom or tax enforcement news | Regulatory changes | **Third party** that enforcement exists [market.md]; no names published in 2026 (search 2026-11-14 found only aggregates) | PenCom press, Nairametrics, BusinessDay | RSS via Clay HTTP | Company names in enforcement stories | 5 | 1 | 1 | 2 | 9 | KILLED as a list source: names are not published. Keep enforcement as copy context only. Naming a prospect's default in copy would also break "guess their situation, not their problems" |
| N4 | Niche | Former Bento Africa client | Competitor customers (displaced) | INFERRED, 21 months old [signals.md] #3 | No list exists | None | n/a | 4 | 1 | 1 | 3 | 9 | KILLED: no programmatic source; most have likely moved |

### Universal vs niche-specific

- **Universal (one build, keyword swaps per segment): 8** (U1 to U8). U1 and U2 are the same Clay build with different title keywords. U7 is the base list; U8 is a routing layer.
- **Niche-specific: 4** (N1 to N4). Two killed (N3, N4), one needs verification (N2), one live (N1, retail only).
- **Compounding insight:** a single Nigerian job-post table (U1 + U2 + U6 + U8) covers all four segments by swapping title and location keywords. That one build carries most of the matrix.

### Matrix 2 by segment (Play + lead module)

| Signal | S1 Logistics | S2 Manufacturing | S3 Retail | S4 Funded tech |
|---|---|---|---|---|
| U1 Payroll or HR hire | Play: payroll or C&B role at a logistics firm. Lead: statutory remittance | Play: payroll or HR officer at a manufacturer. Lead: statutory remittance | Play: HR officer at a retailer. Lead: payroll + attendance | Play: first HR or People hire. Lead: payroll + remittance |
| U2 Frontline velocity | Play: riders, drivers, dispatch. Lead: attendance + EWA | Play: operators, production. Lead: attendance + EWA | Play: sales attendants, cashiers. Lead: attendance + USSD | n/a |
| U3 Headcount growth | Pair with U2. Lead: payroll | Pair with U2. Lead: payroll | Pair with N1. Lead: payroll | Pair with U4. Lead: payroll |
| U4 Funding | Only funded logistics startups. Lead: payroll + remittance | KILLED | KILLED | Play: round announced, team scaling. Lead: payroll + remittance |
| U5 New HR or finance leader | Lead: statutory remittance | Lead: statutory remittance | Lead: payroll + attendance | Lead: payroll + remittance |
| U6 Hiring abroad | Rare (Heroshe serves Ghana, INFERRED) | n/a | n/a | Play: hiring in Kenya, SA, UK. Lead: cross-border payroll |
| U8 Competitor or manual in job post | Routing layer | Routing layer | Routing layer | Routing layer |
| N1 New outlet | n/a | n/a | Play: new branch opened. Lead: attendance + payroll | n/a |
| N2 New product registrations | n/a | Needs verification | n/a | n/a |

---

## 3. Build first: top signals

| Rank | Signal | Segments | Why first |
|---|---|---|---|
| 1 | **U1 Hiring a payroll, C&B or HR role** | All four | Highest story score: the company is choosing right now between a person and a system for exactly what PaidHR does. Live examples exist on Jobberman and MyJobMag today. One build serves every segment. Weakness: link to purchase is INFERRED, so treat the first campaign as the test |
| 2 | **U2 Frontline hiring velocity** | S1, S2, S3 | Points straight at the tier 1 industries Accion names as most of PaidHR's users, and routes to the modules competitors pitch less in SME copy (attendance, EWA, USSD; SeamlessHR does pitch shift teams upmarket). Same table as U1, so near-zero extra build |
| 3 | **U4 Funding in the last 90 days** | S4 (+ funded S1) | Best data access in Nigeria (press + Crunchbase), clear narrative, and PaidHR's strongest proof (fintech logos, FAMASI) sits here. Kept to tech because SME manufacturers and retailers rarely raise VC |
| 4 | **U3 Headcount growth, as a compound filter** | All, paired with U1, U2 or U4 | The only signal a customer named as their trigger (FAMASI). Not a standalone workflow because Nigerian headcount data is unreliable; use it to rank accounts that already fired U1, U2 or U4 |
| 5 | **U5 New HR or finance leader** | All | Natural opener and a known 90-day evaluation window, but untested and likely low volume in Nigeria 20 to 200. Build after 1 to 4 show results |

Not built first: N1 (retail has no proof to cite yet), N2 (source unverified), U6 (competitors lead on EOR and multi-country), N3 and N4 (killed).

**Timing overlay for all five:** launch before January 2027 and reference the first PAYE annual return under the new bands (31 Jan 2027, INFERRED) and Lagos pension enforcement as context, not as an accusation. [market.md]

---

## 4. Matrix 3: Workflow tracker

| W # | Status | Workflow name | Mother intent | Campaigns | Campaign status | Launch date | Campaign name | Persona | Industry | Company size | Enrichment 1 to 5 | Channel | # Iteration | Changelog | Clay URL | Copy URL | Total leads | Steps | Total emails | Progress | Bounce |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W1 | Planned | Hiring payroll or HR roles (NG) | Hiring specific roles | | | | | | | | | | | | | | | | | | |
| W2 | Planned | Frontline hiring velocity (NG) | Hypergrowth (hiring velocity) | | | | | | | | | | | | | | | | | | |
| W3 | Planned | Recently funded NG startups | Fundraising | | | | | | | | | | | | | | | | | | |
| W4 | Planned | Headcount growth into 20 to 200 | Hypergrowth (headcount) | | | | | | | | | | | | | | | | | | |
| W5 | Planned | New HR or finance leader | New leadership | | | | | | | | | | | | | | | | | | |
| W6 | Planned | NG companies hiring abroad | Hiring offshore | | | | | | | | | | | | | | | | | | |
| W7 | Planned | Retail new outlet (Google Maps) | Niche-specific | | | | | | | | | | | | | | | | | | |
| W8 | Planned (blocked) | Manufacturer new product registrations | Niche-specific | | | | | | | | | | | | | | | | | | |

U7 (lookalike) and U8 (competitor or manual mention) are layers inside W1 to W5, not workflows of their own.

---

## Open questions

- Real volume for every signal: TBD until the first pull.
- Does the treg job search (`mobiusengine-jobs`) cover Jobberman and MyJobMag, or only LinkedIn and Indeed? Check with `treg catalog get` before relying on it.
- Kenya and South Africa: no regulation or signal research yet, so no rows.
- Retail customers: none named. Ask PaidHR for one before running S3 copy.
- Win rates by industry and the upper size limit: not in research. [icp.md]
