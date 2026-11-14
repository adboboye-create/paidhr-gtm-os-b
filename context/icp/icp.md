# PaidHR ICP

Sources in [brackets] are files in `context/docs/research/`. INFERRED marks an inference already made in research. Last updated 2026-11-14.

## 1. Firmographic

| Attribute | Fit | Source |
|---|---|---|
| Country | Nigeria first (Lagos HQ); also Kenya, South Africa | [company.md] |
| Headcount | 20 to 200. Floor: Standard tier starts at 20. Ceiling: "The majority of PaidHR's users are ... businesses with under 200 employees" | [company.md] pricing, [customers.md] |

### Industries, ranked by evidence

| Tier | Industries | Evidence | Use |
|---|---|---|---|
| 1. Primary | Logistics, retail, manufacturing | "The majority of PaidHR's users are logistics, retail, and manufacturing businesses" (Accion, June 2025, exact quote). Matching customers: Heroshe (shipping), ReelFruit (food manufacturing) | Build lists here first |
| 2. Secondary | Tech startups, mainly fintech | Accion names "tech startups"; 6 of 12 named logos (Flutterwave, Mono, Risevest, GetEquity, Kredete, GO54); FAMASI video | Strongest logo proof, but not the majority of users |
| No tier | Engineering (AEC, Sygnite), research (NOI Polls), restaurant tech (Mira) | One logo each, no story | Don't target as a segment |

Watch-out: the logos PaidHR shows (tier 2) are not the customers it mostly has (tier 1). Copy aimed at tier 1 has only Heroshe and ReelFruit as matching proof, and ReelFruit is logo-only. [customers.md], [case-studies.md]

Open questions: which retail and manufacturing customers exist (none named); whether the June 2025 mix still holds in 2026; win rates by industry.

## 2. Technographic

| Attribute | Fit | Source |
|---|---|---|
| Current payroll | Manual: remittances made and confirmed by hand, staff texted to confirm pay | [customer-videos.md] FAMASI |
| Current HR tools | Tools that cannot process statutory deductions, or are not "simple to use" | [customer-videos.md] Heroshe, FAMASI |
| Payroll system on old tax bands | Systems on old bands produce incorrect deductions | [market.md] |
| Workforce devices | Staff without smartphones or data (USSD works with no internet) | [company.md], [signals.md] |
| Integration need | Payroll API available | [company.md] |

Open question: which named payroll or HR tools prospects use today. Not in research.

## 3. Intent signals

### Market-wide "why now" (true for every Nigerian employer: use for timing and copy, not for picking accounts)
- Nigeria Tax Act payroll rules live since 1 Jan 2026; first annual PAYE return under them due 31 Jan 2027 (INFERRED). [market.md]
- PenCom and NLC pension enforcement in Lagos from June 2026; automated penalties. [market.md]

### Account-level signals

Evidence key: **Customer** = a PaidHR customer named it as their trigger. **PaidHR claim** = only PaidHR's marketing supports it. **Inferred** = no direct evidence.

| Signal | How to spot it in one account | Evidence it predicts a purchase | Source |
|---|---|---|---|
| Team growing past 20 staff | Headcount from LinkedIn or enrichment. Caveat: treg enrichment returned 1 employee for PaidHR itself, so check headcount by hand | **Customer**: FAMASI CEO, "as a team [grew] we realized there was a need for a more sustainable HR solution" | [customer-videos.md], [company.md] |
| Statutory remittance pain (slow filings, tax office calls) | Hard to see from outside. Proxy: Lagos employer in a sector PenCom has already targeted (electricity) | **Customer**: Heroshe, "two weeks or more", "calls from the tax office" | [customer-videos.md], [market.md] |
| Recent funding round | Funding announcements in Nigerian tech press (Nairametrics, TechCabal, Techpoint) | **Inferred**: named logos skew funded startups; no customer said funding triggered the buy | [customers.md], [market.md] |
| Shift, hourly or field workforce | Job postings for field or shift roles (treg `apollo.companies.jobs`, about $0.026 per call, untested) | **PaidHR claim**: attendance, EWA and USSD features | [signals.md], raw/treg-jobs-paidhr-2026-11-14.json |
| Staff paid in USD, GBP or outside Nigeria | Job posts in other countries; remote roles | **PaidHR claim**: $2M+ cross-border since Oct 2024 | [company.md] |
| Former outsourced-payroll customer (e.g. Bento) | No list of affected companies in research | **Inferred** and 21 months old; most have likely moved | [competitors.md], [signals.md] #3 |

Use for list building now: team growth and recent funding (both observable). Use remittance pain as the message, not the filter: it is the best-evidenced pain but cannot be seen from outside.

Not observable from outside: staff turnover and manual salary advances. Untested: new HR or finance leader, hiring for payroll roles. [signals.md] #7, #9, #10

## 4. Persona

See `personas.md`. Champion: HR manager or HR operations. Economic buyer: founder or CEO. Influencer: finance lead.

## 5. Engagement readiness

| Ready now if | Source |
|---|---|
| Runs payroll in Nigeria with 20+ staff | [company.md] |
| Has a named HR or finance owner of payroll and remittance | [customer-videos.md] |
| Faces a near deadline: monthly PAYE by the 10th; pension within 7 working days of salary; annual PAYE return by 31 Jan (2027 is the first under the new law, INFERRED) | [market.md] |
| Team is growing ("as a team [grew] we realized there was a need for a more sustainable HR solution") | [customer-videos.md] |
| Willing to run payroll through the PaidHR wallet (required for Loan Marketplace) | [company.md] |

## Not a fit

| Who | Why | Source |
|---|---|---|
| Under 20 employees | Below the Standard tier floor (INFERRED) | [company.md] |
| Companies that need EOR to hire without a local entity | No EOR claim on PaidHR's site; Workpay leads with EOR | [competitors.md] |

## Open questions

- Upper size limit where PaidHR stops winning. Not in research.
- Public sector fit (SoftSUITE sells there). Not in research.
- Win rates by industry. Not in research.
