# PaidHR: Kenya statutory filings and PaidHR Kenya coverage

Raw research, not conclusions. All sources checked 2026-11-14.
"Official" = KRA, SHA, NSSF, Ministry of Health or Kenya Law. "Secondary" = vendor or blog guides; treat as unverified until an official source is found.
"INFERRED" marks interpretation. "Not found" means I looked and found nothing.

## Part 1: What a Kenyan employer must file each month

| Item | Paid to | Deadline | Rate | Late penalty | Source quality |
|---|---|---|---|---|---|
| PAYE (income tax) | KRA, return on iTax (P10) | On or before the 9th of the following month | Individual income tax bands | Late filing: higher of 25% of tax due or KES 10,000 (secondary) | Deadline official; penalty secondary |
| Affordable Housing Levy (AHL) | KRA (declared on sheet "M" of the PAYE return; paid under "agency revenue / Housing Levy") | Not later than the 9th **working** day after month end | 1.5% employee + 1.5% employer, of gross salary | 3% of unpaid amount per month or part of a month | Official |
| SHIF (Social Health Insurance Fund, replaced NHIF) | Social Health Authority (SHA) | By the 9th of each month | 2.75% of gross salary (employee deduction); KSh 300 minimum (secondary). Employer match: not found | 2% of amount due per month unpaid | Rate, deadline, penalty official; minimum secondary |
| NSSF (pension, Tier I and II) | NSSF | 9th of the following month | 6% employee + 6% employer on pensionable pay up to an upper limit; 2026 (Year 4) upper limit KES 108,000, max KES 6,480 per party, from February 2026 | Not found | **Secondary only.** The official Year 4 notice is an image I could not read |
| NITA levy | National Industrial Training Authority | Not found | KES 50 per employee per month (employer) | Not found | Secondary only |

### Quotes and sources

- **PAYE:** employers must "remit the amounts deducted to KRA on or before the 9th day of the following month", and "A PAYE return should also be filed through iTax on or before the 9th day of the following month."
  Source: https://www.kra.go.ke/individual/filing-paying/types-of-taxes/paye
- **AHL:** "payable to the collector, for remittance into the Fund, not later than the ninth working day after the end of the month in which the gross salary was due". Penalty: "three per centum of the unpaid amount ... for each month or part thereof".
  Sources: https://new.kenyalaw.org/akn/ke/act/2024/2/eng@2026-07-01 (Affordable Housing Act 2024), https://www.kra.go.ke/news-center/public-notices/2099-collection-of-the-affordable-housing-levy-by-kenya-revenue-authority-2
- **SHIF:** "2.75% of the gross salary or wage of the household by the ninth day of each month"; "An employer shall deduct the contribution of a salaried contributor and submit the contribution to the Authority on behalf of the employee". Penalty "two percent of the amount due".
  Sources: https://new.kenyalaw.org/akn/ke/act/ln/2024/49/eng@2025-02-28/source.pdf (Social Health Insurance Regulations 2024, reg. 17), https://new.sha.go.ke/wp-content/uploads/2025/07/PUBLIC_NOTICE_ON_EMPLOYER_REMITTENCES.pdf
- **NSSF:** official notice exists but its figures are in an image: https://www.nssf.or.ke/notice-to-employers-year-4-2026-nssf-contribution-rates (posted 2026-02-18). Figures above from secondary guides, e.g. https://afrotools.com/blog/kenya-nssf-contributions-2026/ and https://serrarigroup.com/kenya-statutory-deductions-2026-nssf-shif-paye-guide/
- **Order of calculation (secondary):** NSSF, SHIF and AHL reduce taxable pay, so PAYE is computed after them. Source: https://serrarigroup.com/kenya-statutory-deductions-2026-nssf-shif-paye-guide/
- **INFERRED:** a Kenyan employer pays four bodies (KRA twice: PAYE and AHL; SHA; NSSF) on two slightly different deadlines (9th calendar day vs 9th working day). That is the Kenyan version of the "filings by hand" pain in the Nigerian angles.

### Job-post terms for the S6 regex (workflow spec)
PAYE, P10, iTax, NSSF, SHIF, SHA, NHIF (legacy, still common in JDs), Housing Levy, AHL, NITA. INFERRED: "NHIF" will still appear in many 2026 JDs.

## Part 2: Does PaidHR run payroll and file these in Kenya?

**Short answer: not confirmed. Nothing public says PaidHR files Kenyan PAYE, AHL, SHIF or NSSF.**

What exists:
- Accion (third party, 2025-06-23): PaidHR "has rapidly expanded to reach Pan-African small and medium-sized enterprises (SMEs) and tech startups across Nigeria, Kenya and South Africa."
  Source: https://www.accion.org/news/paidhr-raises-1-8m-seed-round-led-by-accion-venture-lab-to-boost-africas-growing-workforce/ (already in customers.md)
- PaidHR's own words (2025-06-23): "a platform supporting thousands of workers across Nigeria, Kenya, and South Africa". Source: https://x.com/getPaidHR/status/1937108356386132251 (already in company.md)

What is missing (looked, not found):
- paidhr.com homepage: no mention of Kenya, KES, KRA, NSSF, SHIF or Housing Levy. The only named country is Nigeria; remittances listed are PAYE, pension, NHF, NSITF (Nigerian). Source: https://www.paidhr.com (checked 2026-11-14)
- paidhr.com/pricing: no countries or KES. "Statutory remittance" listed with no country. Source: https://www.paidhr.com/pricing
- Global payroll page: "Compliant in 150+ countries" (no detail); the product described is payouts: "convert their payroll into USD and GBP and pay their employees or contractors across borders". Source: https://www.paidhr.com/platform/global-payroll-employers
- Help center (support.padehcm.com): could not load (expired TLS certificate, 2026-11-14).
- No Kenyan customer, case study, Kenya launch announcement or Kenya office found in web search.
- Do not confuse with **FaidiHR**, a separate Nairobi HR company (founded 2017). Source: https://www.cbinsights.com/compare/faidihr-vs-pade-hcm

**INFERRED:** "workers across Kenya" may mean Kenyan staff of Nigerian customers paid through cross-border payouts, not Kenyan employers with local filings. Only PaidHR can say which.

**User confirmation, 2026-11-14:** the user (PaidHR GTM) confirmed PaidHR runs payroll and files statutory remittances, with a receipt after each, in Kenya. Recorded in work-log/2026-W45.md. This is the only source for the Kenya capability claim; questions 1 to 3 below are answered by it, the rest stay open.

## Questions for PaidHR (open, not blocking)

1. Can a Kenya-registered employer run payroll in KES on PaidHR?
2. Does PaidHR compute and file/remit each of: PAYE (iTax P10), Affordable Housing Levy, SHIF, NSSF, NITA? Which are filed by PaidHR vs only calculated?
3. Is a receipt or proof of remittance issued after each Kenyan filing (as in Nigeria)?
4. Are the 2026 NSSF Year 4 limits and SHIF already live in the product?
5. Any Kenyan customer we can name, or a Kenya result (time saved, filings done)?
6. Does EWA work for Kenyan staff (M-Pesa payout)?
7. Kenyan sender, phone number or office, if any.
