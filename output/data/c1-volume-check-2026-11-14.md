# C1 volume check: payroll or HR roles posted (Nigeria)

**Date:** 2026-11-14. **Method:** `curl` of public category pages (no login, no search URLs, no pagination: both boards disallow `q=`, `page=` and query strings in robots.txt). No paid tools, no crawl4ai install. **For:** `output/campaigns/payroll-hr-role-posted/workflow-spec.md` (volume TBD).

## Sources

| Board | URL | Result |
|---|---|---|
| Jobberman | https://www.jobberman.com/jobs/human-resources | 200 OK. Page says **"Human Resources (117)"** open jobs, Nigeria; Lagos 68, Abuja 14 |
| Jobberman | https://www.jobberman.com/jobs/accounting-auditing-finance | 200 OK. 381 open jobs; **no payroll or compensation titles on page 1** |
| MyJobMag | https://www.myjobmag.com/jobs-by-field | Listing is rendered by JavaScript; no jobs in the static HTML. Needs a browser (crawl4ai or agent-browser). **Not measured** |
| LinkedIn Jobs | n/a | Not checked (Clay "Find Jobs" in the spec) |

## Jobberman HR category, page 1 (16 listings, as shown 2026-11-14)

| Title | Company | Posted | C1 title regex (S1) | Exclusion (S3) |
|---|---|---|---|---|
| Human Resources Manager | Coinbox Limited | Yesterday | Match | |
| HR Team Lead | Kloverharris Limited | 2 days ago | No | HR consulting practice (JD) |
| HR Manager | JV Management Consulting Limited | 3 days ago | Match | Consultancy; S3 regex does **not** catch "consulting" |
| Human Resource Business Partner | MP Infrastructure | 3 days ago | No | |
| HR Assistant | Homelight Properties Limited | 3 days ago | No | |
| Talent Manager | MP Infrastructure | 3 days ago | No | |
| HR Manager | Foshan Jieko Machinery Equipment Co., Ltd. | 3 days ago | Match | |
| HR and Admin Executive | Tecpoint Global Solutions Limited | 3 days ago | **No (regex gap)** | |
| Recruitment Manager | JV Management Consulting Limited | 4 days ago | No | |
| Human Resource Manager | Greenwood Limited | 5 days ago | Match | |
| HR Officer | The MSS Company | 2 weeks ago | Match | |
| Human Resource Business Partner | Anonymous employer | 2 weeks ago | No | Anonymous |
| HR & Operations Manager | Celeb Laser and Aesthetics Clinic | 3 weeks ago | **No (regex gap)** | |
| Head of Human Resources / Executive Assistant | Anonymous employer | 4 weeks ago | No (regex gap) | Anonymous |
| HR Officer | Anonymous employer | 1 month ago | Match | Anonymous |
| Administrative /Human Resources Officer | Anonymous employer | 1 month ago | Match | Anonymous |

Counts from page 1 (deterministic):
- Posted in the last 7 days: **10**. C1 title match and not excluded: **3** (Coinbox, Foshan Jieko, Greenwood).
- Posted in the last 30 days (all 16): C1 title match and not excluded: **4** (adds The MSS Company).
- Anonymous employers: 5 of 16 (31%). Dropped by S3.
- Payroll-specific titles (cells A and B): **0** on HR page 1 and 0 on Finance page 1.

Headcount (20 to 200) not checked for any of these. Company names above are seed rows, not qualified leads.

## Estimate (INFERRED)

Page 1 is all we can read without breaking robots.txt, so the weekly rate is an estimate:
- 117 open HR jobs. If a post stays up about 30 days (INFERRED), that's about **27 new HR posts a week** on Jobberman.
- About 44% of page 1 matches the C1 titles (7 of 16) and 31% is anonymous, so about **8 usable posts a week** before the 20 to 200 headcount and agency filters. The filters will cut that further; real figure TBD until the Clay or LinkedIn pull.
- Payroll-only roles (cells A and B) look rare on Jobberman. Most C1 volume will land in cells C and D (HR roles).

## Findings for the spec owner (S1 / S3 regex)

1. S1 misses common titles seen today: "HR and Admin Executive", "HR & Operations Manager", "Head of Human Resources", "HR Business Partner". Suggest allowing `HR (and|&) \w+ (executive|manager|officer)`, `head of (HR|human resources)` and `HR business partner`.
2. S3 does not drop consultancies posting for clients: add `consult` to the poster regex (JV Management Consulting, Kloverharris HR consulting).
3. MyJobMag needs a browser to read; Jobberman category pages work with plain HTTP.
