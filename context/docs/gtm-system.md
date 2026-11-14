# PaidHR Outbound GTM System

Work in progress. Last updated 2026-11-14.

Miro board: [PaidHR GTM System](https://miro.com/app/board/uXjVENnRs9c=/) (flowchart spec: [diagrams/paidhr-gtm-system.json](../../diagrams/paidhr-gtm-system.json); box ids on the board, such as 1D or 2F, match the step letters there)

**What this is.** The end-to-end outbound system for PaidHR, from the Context OS to the weekly review that updates it. It runs on the segments and signals in [signal-matrix.md](../icp/signal-matrix.md), the ICP in [icp.md](../icp/icp.md) and the personas in [personas.md](../icp/personas.md).

**How to read it.** Company facts cite a source. Everything else is a design choice for PaidHR's system, not a fact about PaidHR. Thresholds marked **(proposed)** are starting values to confirm in the first weekly reviews, not benchmarks. Anything the research does not support is marked INFERRED.

**Tools.** Claude Code (reasoning, copy, review), Clay (signals, enrichment, people, email), HubSpot (CRM and suppression), n8n (scheduling, glue, reply routing), PlusVibe (email sending), GitHub (source of truth for the Context OS and results). LinkedIn sending has no tool in this stack; it is done by hand by the sender (tool TBD).

---

## Overview

| # | Step | Main tool | Output |
|---|---|---|---|
| 1 | Context OS | Claude Code, GitHub | Approved ICP, signals, facts, workflow spec |
| 2 | Buying signals | n8n, Clay | Raw signal events, dated |
| 3 | Find companies | Clay | One row per company with its signal |
| 4 | Enrichment | Clay | Headcount, industry, HQ, job posts, domain |
| 5 | ICP fit check | Clay | Pass, park or drop |
| 6 | Routing by segment | Clay | Segment (S1 to S4), size band, lead module, angle |
| 7 | Finding people | Clay | 1 to 2 contacts per company by persona |
| 8 | Find and verify emails | Clay | Verified email, or LinkedIn-only |
| 9 | Sequence (email + LinkedIn) | PlusVibe, sender by hand | Sends |
| 10 | Reply handling | PlusVibe, n8n, Claude | Classified replies and next actions |
| 11 | CRM | HubSpot | Deals with signal, segment and angle attached |
| 12 | Weekly feedback loop | n8n, Claude Code, GitHub | Updated Context OS |

---

## 1. Context OS

**What happens.** Every workflow starts from files in this repo: ICP, personas, signal matrix, positioning, facts and brand. `/build-workflow-spec` turns one signal from the matrix into a workflow spec in `output/campaigns/<workflow-slug>/workflow-spec.md`. `/campaign-copy` writes copy only from a STRUCTURE-APPROVED spec and only from `facts.md`.

**Tools.** Claude Code (skills), GitHub (version history, the source of truth; Notion only gets finished docs, per CLAUDE.md).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Is `facts.md` approved? | No (true today: "facts.md claims not yet approved", work log 2026-11-14 15:51) | Copy is blocked. Approve facts first |
| | Yes | Copy can be written |
| Is the workflow spec STRUCTURE-APPROVED? | No | Back to `/build-workflow-spec` |
| | Yes | Build the Clay table (step 2) |
| Is the segment proof enough to cite? | No (S3 retail: no named customer [icp.md]) | Run without a customer story, or hold until PaidHR names one |
| | Yes | Use the matching story (S1 Heroshe, S4 FAMASI) [case-studies.md] |

---

## 2. Buying signals

**What happens.** Always-on jobs collect the signals ranked in the matrix. Each signal event is stored with its date and source URL so copy can reference it and dedupe can work.

| Signal (matrix id) | Collector | Cadence (from workflow-anatomy.md periodicity) |
|---|---|---|
| U1 Hiring payroll, C&B or HR roles | Clay "Find Jobs"; n8n scrape of Jobberman and MyJobMag into a Clay webhook | Weekly |
| U2 Frontline hiring velocity (3+ roles, proposed) | Same job table as U1, counted by company | Weekly |
| U4 Funding in last 90 days (S4 and funded S1 only) | n8n RSS on TechCabal, Techpoint, Nairametrics; Crunchbase via Clay | Bi-weekly |
| U3 Headcount growth | Clay "Enrich Company" snapshots | Monthly, as a ranking layer only |
| U5 New HR or finance leader | Clay "Find People" with start date | Monthly |

Signals killed in the matrix (PenCom named defaulters, ex-Bento clients) are not collected. Market-wide timing (new PAYE bands since 1 Jan 2026, first annual return 31 Jan 2027 INFERRED, Lagos pension enforcement) goes into copy, not into list selection. [market.md]

**Tools.** n8n (schedules and scrapes), Clay (job and funding actions). Check prices with `treg catalog get <id>` before any treg call (CLAUDE.md).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Did the signal fire inside its window (30 days for jobs, 90 for funding, proposed)? | No | Discard the event |
| | Yes | Step 3 |
| Have we seen this company for this signal before? | Yes, contacted in the last 90 days (proposed) | Suppress; keep the event as history |
| | Yes, but a new signal type | Re-enter with the new signal as the reason |
| | No | Step 3 |

---

## 3. Find companies

**What happens.** Each signal event becomes one company row in the Clay Companies table, keyed on domain. The job post or article URL is kept as the signal source. U7 lookalikes (seeds: Heroshe, ReelFruit, fintech logos [customers.md]) form a base list that the weekly signal jobs match against.

**Tool.** Clay.

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Domain found? | No | Clay company lookup by name; still none: drop (cannot dedupe or enrich) |
| | Yes | HubSpot check |
| In HubSpot? | Customer, open deal, or contacted in the last 90 days | Exclude. Customers go to the account owner, not outbound |
| | Closed-lost over 6 months ago (proposed) | Allow, flag "re-engage" for routing |
| | Not in HubSpot | Step 4 |

---

## 4. Enrichment

**What happens.** Clay adds headcount, LinkedIn industry, HQ country and city, open roles (titles and locations) and funding stage. Job descriptions are kept for the routing layer (U8: mentions of a competitor or a manual process).

**Tool.** Clay (waterfall of providers).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Headcount found and plausible? | Missing, or under 5 while the company posts many jobs | Second source (another Clay provider). Nigerian headcount data is unreliable: treg returned 1 employee for PaidHR [company.md] |
| | Still missing after two sources | Manual check queue (small batch, weekly) |
| | Found | Step 5 |
| Industry found? | No | Claygent reads the website and classifies into S1 to S4 or "other" |
| | Yes | Step 5 |

---

## 5. ICP fit check

**What happens.** Hard filters from [icp.md]. A company must pass all of them.

**Tool.** Clay (formula columns, no AI cost).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| HQ country? | Nigeria | Continue |
| | Kenya or South Africa | Park: no regulation or signal research yet [signal-matrix.md] |
| | Other | Drop |
| Headcount? | Under 20 | Drop: below the Standard tier floor [company.md] |
| | 20 to 200 | Continue [icp.md] |
| | Over 200 | Park: upper limit where PaidHR stops winning is unknown [icp.md] |
| Industry? | Logistics, manufacturing, retail, tech or fintech | Continue to routing |
| | Engineering, research, restaurant tech | Drop: "Don't target as a segment" [icp.md] |
| | Other | Drop |
| Needs EOR (hiring abroad with no local entity)? | Yes | Drop: no EOR on PaidHR's site [competitors.md] |
| | No or unknown | Continue |

---

## 6. Routing by segment

**What happens.** Each passing company gets a segment, a size band, a lead module and an angle. The angle per segment and persona comes from Matrix 1 in [signal-matrix.md].

**Tool.** Clay (formula routing; one AI column for the U8 job-text check).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Segment? | S1 Logistics | Lead: statutory remittance + payroll; Heroshe proof |
| | S2 Manufacturing | Lead: remittance + attendance (shifts, overtime) |
| | S3 Retail | Lead: payroll + attendance across outlets; no customer proof |
| | S4 Funded tech | Lead: payroll + remittance; FAMASI proof |
| Size band? | 20 to 100 | Standard tier framing [company.md] |
| | 100 to 200 | Enterprise tier framing, "Dedicated support" [company.md] |
| Which signal fired? | U1 payroll or HR hire | Angle: system alongside or instead of the hire (INFERRED) |
| | U2 frontline velocity | Angle: attendance, EWA, USSD for field staff |
| | U4 funding | Angle: team about to grow, payroll still manual |
| | U5 new leader | Angle: first-90-days review of tools (INFERRED) |
| Job text names a competitor or manual process (U8)? | Competitor named | Add a comparison line from [competitors.md] |
| | "Excel" or manual remittance | Add the manual-remittance line (Heroshe, FAMASI) |
| | Neither | Base angle only |

---

## 7. Finding people

**What happens.** Clay finds 1 to 2 people per company, picked by persona and size. Persona order is a proposal; who signs at 100+ staff is unknown [personas.md].

**Tool.** Clay (Find People).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Company size? | 20 to 50 (proposed) | Founder or CEO first (FAMASI pattern [customer-videos.md]), then HR if one exists |
| | 50 to 200 | HR manager first (champion), finance lead second |
| HR person found? | Yes | Use as primary contact |
| | No | Founder or CEO; if signal is U1, mention the open HR role |
| Anyone found? | No | Hold the company; recheck at the next monthly people pull |
| Person already in HubSpot or contacted in the last 90 days? | Yes | Skip this person, try the next persona |

---

## 8. Find and verify emails

**What happens.** Clay runs an email waterfall across providers, then a verifier. Email coverage for Nigerian SMEs is unknown (INFERRED weak; measure it in the first run).

**Tool.** Clay.

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Email found? | No | LinkedIn-only track |
| Verifier result? | Valid | Email + LinkedIn track |
| | Catch-all | Send only from a separate low-volume pool (proposed), plus LinkedIn |
| | Invalid | LinkedIn-only track |
| Free webmail (gmail.com etc.) on a 20+ staff company? | Yes | Do not send; LinkedIn-only (INFERRED: likely personal address) |

---

## 9. The sequence (email and LinkedIn)

**What happens.** Copy comes from `/campaign-copy` on the approved spec, one variant per segment and angle. `/campaign-qa` checks the Clay table and the PlusVibe campaign before launch. PlusVibe sends; the sender handles LinkedIn by hand from HubSpot tasks.

Proposed cadence (confirm in the spec):
| Day | Channel | Step |
|---|---|---|
| 1 | Email | Signal-led opener, one question |
| 2 | LinkedIn | Connection request, no pitch |
| 4 | Email | Proof: Heroshe (S1) or FAMASI (S4); S2 and S3 use the deadline angle instead |
| 8 | LinkedIn | DM if connected |
| 11 | Email | Timing: first annual PAYE return under new bands, 31 Jan 2027 (INFERRED) |
| 15 | Email | Short close-out |

**Tools.** PlusVibe (email), HubSpot tasks (LinkedIn by hand), Claude Code (copy and QA skills).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Campaign QA pass? | No | Fix in Clay or PlusVibe, rerun QA |
| | Yes | Launch |
| Track? | Email + LinkedIn | Full cadence |
| | LinkedIn-only | Day 2 and day 8 steps only |
| Copy check: no em dashes, every claim in `facts.md`? | No | Back to `/campaign-copy` |
| | Yes | Load into PlusVibe |

---

## 10. Reply handling

**What happens.** PlusVibe sends each reply to an n8n webhook. Claude classifies it. n8n acts on the class and stops the sequence for that person.

**Tools.** PlusVibe (webhook), n8n (routing), Claude (classification), HubSpot (records).

**Decisions.**
| Reply class | Leads to |
|---|---|
| Interested or asks for a demo | HubSpot deal at "Meeting requested", alert the sender in under 1 business hour (proposed), send booking link |
| Wrong person, names someone | Add the named person, back to step 7 with the referral as the opener |
| Not now, gives a date | HubSpot task for that date; back into the sequence then |
| Already has a tool (SeamlessHR, Sage etc.) | Log competitor in HubSpot; nurture; re-enter on the next new signal |
| Objection (trust after Bento, price, ease of use) | Sender replies with the matching answer from [personas.md]; price is unpublished, so route to a call [company.md] |
| Unsubscribe or "stop" | Suppress in PlusVibe and HubSpot, everywhere, for good |
| Out of office | Pause, resume after the return date |
| Bounce | Mark email invalid in Clay; switch to LinkedIn-only |
| No reply after the last step | Close the person; company waits for a new signal (back to step 2) |

---

## 11. CRM

**What happens.** HubSpot holds every contacted company and person, with the workflow id, signal, segment, size band, angle and sequence step. Deal stages (proposed, PaidHR's real stages TBD):

Meeting requested, Meeting held, Proposal sent, Payroll set up (first run through PaidHR), Won, Lost (with reason).

"Payroll set up" is a stage because the Loan Marketplace needs payroll to run through the PaidHR wallet [company.md].

**Tool.** HubSpot (n8n writes to it from PlusVibe and Clay).

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Meeting held? | No-show | Re-book once, then back to nurture |
| | Held | Proposal stage |
| Deal outcome? | Won | Customer; excluded from outbound; candidate for a case study (only Heroshe has one [customers.md]) |
| | Lost | Lost reason logged; closed-lost re-engage rule in step 3 |

---

## 12. Weekly feedback loop

**What happens.** Every Monday (proposed) n8n pulls PlusVibe and HubSpot numbers into `output/data/weekly-YYYY-Www.md` in GitHub. Claude Code reads it, compares by signal, segment, size band, angle and persona, and proposes edits to the Context OS. Every change is logged in `work-log/`.

**Tools.** n8n (export), GitHub (storage), Claude Code (analysis and edits).

**What it measures.** Reply rate, positive reply rate, meetings, deals and wins per signal, segment, angle and persona; bounce rate; Clay cost per contact (`/calculate-costs`); email coverage for Nigerian companies.

**Decisions.**
| Decision | Answer | Leads to |
|---|---|---|
| Enough sends to judge (200 delivered per variant, proposed)? | No | Keep running |
| | Yes | Compare |
| Variant below the others on positive replies? | Yes, first time | Iterate copy (new angle), log in the spec changelog |
| | Yes, after two iterations | Kill the variant; write why in `knowledge-base/learnings/` |
| | No | Keep; scale volume |
| Signal produced deals? | Yes | Raise its score in the signal matrix; replace volume TBD with real numbers |
| | No after two iterations | Kill the signal in the matrix and record why |
| Bounce above 3% (proposed)? | Yes | Pause sending; fix verification in step 8 |
| New fact from a call (pain quote, objection, customer story)? | Yes | Add to research with source, then to `personas.md`, `facts.md` or `case-studies.md` |

---

## Check against the four pillars

| Pillar | Where the system meets it | Gaps |
|---|---|---|
| **Clean data** | Domain key and HubSpot check before any spend (step 3); two-source headcount and manual queue (step 4); hard ICP filters with no AI (step 5); email verification and webmail block (step 8); bounces written back (step 10); suppression synced across PlusVibe and HubSpot | Nigerian headcount and email coverage are unknown until the first run. Real HubSpot fields and stages are TBD. NDPA (Nigeria Data Protection Act) rules for cold email are not researched [market.md]: check before launch |
| **Always-on signals** | n8n schedules job scrapes weekly, funding bi-weekly, people monthly (step 2); dated events with dedupe and re-entry rules; "no reply" returns companies to wait for a new signal | Jobberman and MyJobMag scrapes need building and could break with site changes. U5 and U3 are monthly, so slow |
| **Composable workflows** | One job-post table feeds U1, U2, U6 and U8 with keyword swaps; ICP check, routing, people and email steps are shared across every workflow; segment changes only the angle and proof | Retail (S3) needs its own Google Maps build (N1). LinkedIn steps are manual, so they do not scale with email |
| **Tight feedback loops** | Weekly review by signal, segment, angle and persona; kill and iterate rules; results written to the signal matrix, learnings and facts in GitHub; every change in the work log | Thresholds are proposed, not proven. Deal cycle length is unknown, so win data will lag reply data by weeks (INFERRED) |

## Open questions

- Who sends: which PaidHR sender and domain, and how many inboxes. Not in research.
- PaidHR's real HubSpot pipeline and fields. Not in research.
- LinkedIn sending tool: none in the stack.
- NDPA rules for B2B cold email in Nigeria. Not researched.
- Sales cycle length and who signs at 100+ staff. Not in research [personas.md].
