# Sequencer export: payroll-hr-role-posted (Nigeria)

Generated 2026-11-14 from the approved copy in [workflow-spec.md](workflow-spec.md). Regenerate whenever the copy changes. Do not launch until facts.md sign-off and sender identity are done.

```
Campaign: C1 payroll or HR role posted (NG), two sub-campaigns: ceo and hr_lead
Tag: c1-payroll-hr-role-ng, plus route_cell (A/B/C/D) and recipient_role for reporting
Recommended settings: plain text ON, open tracking OFF, ignore out-of-office replies ON
Suggested schedule: Mon-Fri, 08:00-17:00 Africa/Lagos (confirm)
Stop rule: a reply from either the CEO or the HR lead at the same company stops both sub-campaigns

Custom variables (one column per variable in the lead upload; the data tool resolves each per lead by route_cell and recipient_role):
- e1l1, e1l2, social_proof, e2l1, e2l2, job_title, route_cell, recipient_role
  (built-ins excluded: first_name, company_name, email, sender signature)

Step 1 | wait: 0 days | new thread
Subject: {your new hire and payroll|payroll and the new hire|before the new hire starts}
Body:
{{first_name}},

{{e1l1}}

{{e1l2}}

{{social_proof}}

{Worth a look before the new hire starts?|Is the payroll system part of the plan before they start?|Worth sorting this before the new hire starts?}

{{sender_signature}}

Step 2 | wait: 3 days | same thread (subject "Re: <same subject>")
Body:
{{first_name}},

{{e2l1}}

{{e2l2}}

{Would it help to see one month of payroll and filings in PaidHR?|Want to see what one month of payroll and filings looks like in PaidHR?}

{{sender_signature}}

Step 3 | wait: 7 days (day 10) | same thread
Body (ceo sub-campaign):
{{first_name}},

{Last note from me on this.|This is my last note on this.}

If payroll and filings sit with someone else at {{company_name}}, {who would be the right person to ask?|who should I speak to instead?}

{{sender_signature}}

Body (hr_lead sub-campaign):
{{first_name}},

{Last note from me on this.|This is my last note on this.}

{Is the payroll system yours to choose, or already decided before the {{job_title}} starts?|Will you pick the payroll system, or is that settled before the {{job_title}} starts?}

{{sender_signature}}
```

Line values for e1l1, e1l2, social_proof, e2l1 and e2l2 per cell and lens are in the spec's `## Copy` section. Convert `{{var}}` and `{a|b}` to your sequencer's syntax at upload.
