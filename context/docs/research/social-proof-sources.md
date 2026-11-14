# PaidHR: Social proof source register (customer videos)

Raw input for a social proof document. Every quote below is from a customer video embedded on https://www.paidhr.com/customers (checked 2026-11-14). Nothing here is approved copy yet.

## How this was made

- **Videos:** the customers page embeds 3 unique YouTube videos (re-checked 2026-11-14). Two are customer stories (FAMASI, Heroshe). The third (Cross Border) is a product ad with no customer in it, so it is listed at the end as a non-source.
- **Transcripts:** audio transcribed locally with Whisper large-v3 (faster-whisper). Each line was then checked against YouTube's auto-captions. Full transcripts:
  - FAMASI: [raw/video-transcript-famasi-thPhRuim05g-whisper.txt](raw/video-transcript-famasi-thPhRuim05g-whisper.txt)
  - Heroshe: [raw/video-transcript-heroshe-1L3R7CMEmjI-whisper.txt](raw/video-transcript-heroshe-1L3R7CMEmjI-whisper.txt)
  - Cross Border: [raw/video-transcript-cross-border-y52Z7VZffug-whisper.txt](raw/video-transcript-cross-border-y52Z7VZffug-whisper.txt)
  - The older auto-caption transcripts are kept next to them for comparison.
- **Status per quote:**
  - **Both agree:** Whisper and the captions give the same words (captions sometimes mishear a name, such as "paid" for "Pade").
  - **Whisper only:** the captions are garbled at that point, so only Whisper's reading supports the wording. Listen before publishing.
  - Words in [square brackets] are my corrections and are INFERRED.
- **Links:** each quote links to its moment in the video (`?t=` seconds).
- **Human check:** no person has listened to the videos against this file yet. Do that before any quote is published.

## Read before using any of this

1. **Old brand name.** Both customer videos are from 2023 and say "Pade", PaidHR's name before the 2024 rebrand ([customer-videos.md](customer-videos.md)). Either quote them as spoken and add "(now PaidHR)", or paraphrase. Do not silently change "Pade" to "PaidHR" inside quote marks.
2. **Age.** The videos were uploaded 2023-08-25 (Heroshe) and 2023-09-21 (FAMASI). Whether both are still customers in 2026 is TBD. Confirm with PaidHR before naming them.
3. **Permission.** PaidHR published these videos itself, which suggests the customers agreed to their use. That is INFERRED; confirm reuse rights for new formats (ads, outbound).
4. **Speaker titles.**
   - Adeola Ayoola, "CEO and co-founder at FAMASI": stated in the video at 00:17. Name confirmed by the YouTube description.
   - Michelle Adaware, Heroshe: the name comes from the YouTube description. **Her job title is TBD.** Whisper heard "P4O Specialist" and the captions "T4 operations specialist". The video never says "HR" in her title, but she calls herself "an HR professional" (01:22).
5. **No hard metrics.** Neither video gives headcount, money saved, or a before/after figure besides the time figures below. Company sizes are TBD.

---

## FAMASI

- **Video:** "Growth Story feat FAMASI", https://youtu.be/thPhRuim05g (2:08, uploaded 2023-09-21)
- **Speaker:** Adeola Ayoola, CEO and co-founder
- **Company:** "We're building the OS for pharmacies in emerging markets by building software and APIs that allow businesses and individuals connect to pharmacies." ([00:17](https://youtu.be/thPhRuim05g?t=17))
- **Persona fit:** founder or CEO running payroll themselves (the buyer persona in [../../icp/personas.md](../../icp/personas.md))

| ID | Quote (as spoken) | Link | Theme | Pillar | Status |
|---|---|---|---|---|---|
| F1 | "Prior to using Pade, everything was manual, like you have to make remittances manually, have to manually confirm that remittances have been done, also have to individually text people to confirm that they have received their payments. It was stressful." | [00:00](https://youtu.be/thPhRuim05g?t=0) | Before: manual pain | 2 | Both agree |
| F2 | "With paying salaries, I had to individually text everyone on the team to confirm that they have received their payments." | [00:35](https://youtu.be/thPhRuim05g?t=35) | Before: manual pain | 2 | Both agree |
| F3 | "I had to earmark about one hour of the day whenever I [sat down] to run payroll just to manually make payments." | [00:40](https://youtu.be/thPhRuim05g?t=40) | Before: time cost (number) | 2 | Both agree, except "[sat down]": both transcripts say "signed", so the correction is INFERRED. Safe cut: "I had to earmark about one hour of the day ... just to manually make payments." |
| F4 | "As the team grew, we realized there was a need for a more sustainable HR solution." | [00:44](https://youtu.be/thPhRuim05g?t=44) | Trigger: team growth | 2 | Whisper only (captions: "as a team girl") |
| F5 | "I checked out a couple of them, but it just didn't seem very simple to use. And then I stumbled on Pade and it looked very simple, so I decided to give it a try." | [00:48](https://youtu.be/thPhRuim05g?t=48) | Why chosen over alternatives | 2 | Both agree |
| F6 | "With Pade, I have that one hour saved and I mean, in entrepreneurship, time is very important. So I have that one hour saved to be able to focus on other things while being rest assured that Pade has my people paid." | [00:57](https://youtu.be/thPhRuim05g?t=57) | After: time saved (number) | 2 | Whisper only for "saved" (captions: "received"). The rest agrees. |
| F7 | "It has made my life simpler. I get a notification before it's payroll day to say, do you want to run your payroll? It's easy for me to see the reports. It's easy for me to make the remittances. It's just a very simple interface to use, really." | [01:15](https://youtu.be/thPhRuim05g?t=75) | After: ease of use, features | 2, 1 | Both agree |
| F8 | "I would definitely recommend Pade to other people. I have been recommending already." | [01:10](https://youtu.be/thPhRuim05g?t=70) | Recommendation | All | Both agree |
| F9 | "And I think that everyone should get on it." | [01:29](https://youtu.be/thPhRuim05g?t=89) | Recommendation | All | Both agree |
| F10 | "I'm particularly excited for the solutions that make it easier for my team to enjoy the work that they do and access other services." | [01:34](https://youtu.be/thPhRuim05g?t=94) | Employee benefits (forward-looking) | 3 | Whisper only for "work" (captions: "one"). Weak: it is about features that did not exist yet in 2023. INFERRED link to EWA. |

**Numbers from this video:** about one hour per payroll run, before (F3). That hour saved, after (F6). No other figures.

---

## Heroshe

- **Video:** "Growth Story feat Heroshe", https://youtu.be/1L3R7CMEmjI (2:12, uploaded 2023-08-25)
- **Speaker:** Michelle Adaware (title TBD, see note 4 above)
- **Company:** "We are a service-oriented business that deals with cross-border shipping. In other words, you can get quality and affordable products from the US and UK down to Nigeria and Ghana." ([00:21](https://youtu.be/1L3R7CMEmjI?t=21))
- **Persona fit:** HR operations lead (the champion persona in [../../icp/personas.md](../../icp/personas.md)); logistics is a primary ICP industry ([../../icp/icp.md](../../icp/icp.md))

| ID | Quote (as spoken) | Link | Theme | Pillar | Status |
|---|---|---|---|---|---|
| H1 | "What I've noticed about most HR software is the fact that they are unable to help most HR professionals process statutory deductions, which has been a pain to most of us." | [00:00](https://youtu.be/1L3R7CMEmjI?t=0) | Category pain: other HR tools | 1 | Both agree |
| H2 | "But with Pade, you're able to get your statutory deductions remitted and you also get a receipt once you're able to remit your payment, which just gives you an assurance that you've not just made payment, but you've gotten an evidence for the payment you've made." | [00:08](https://youtu.be/1L3R7CMEmjI?t=8) | After: proof of remittance | 1 | Both agree. Strongest quote for pillar 1. |
| H3 | "The major HR problem or challenge I've faced in a couple of years would be remitting statutory deductions. It's always a pain in the head because you have to wait for two weeks or more to get that processed." | [00:41](https://youtu.be/1L3R7CMEmjI?t=41) | Before: time cost (number) | 1 | Both agree |
| H4 | "And sometimes you keep getting calls from the tax office and honestly, it could be really overwhelming." | [00:54](https://youtu.be/1L3R7CMEmjI?t=54) | Before: tax office pressure | 1 | Both agree |
| H5 | "I remember the first time when I used Pade to remit my statutory deductions. It was so fast because in less than a click, I noticed that the payment had gone. I was even able to see like a summary of all the payments we need to make." | [01:00](https://youtu.be/1L3R7CMEmjI?t=60) | After: speed | 1 | Both agree |
| H6 | "And I got a call in, I think the next two days, telling me that my payments had been processed and remitted." | [01:13](https://youtu.be/1L3R7CMEmjI?t=73) | After: time to confirmation (number) | 1 | Whisper only after "next two days" (captions garbled). She hedges with "I think". This is a confirmation **call**, not a receipt (see Corrections below). |
| H7 | "I would say Pade has helped to simplify my job as an HR professional because every single time when I need employees to get their payslip, they always reach out to me and I have to do the manual process. But with Pade, once they get their payment, they see their payslip and that burden just goes off my neck." | [01:22](https://youtu.be/1L3R7CMEmjI?t=82) | After: staff self-service | 2 | Whisper only (captions garbled: "paid as you have to simplify my job as a nature professional") |
| H8 | "I also get notifications for their anniversaries. I think they are more or less HR operational tasks, which is not what I'm focused on. So I leave the software to do the operational tasks and I do the strategic tasks." | [01:37](https://youtu.be/1L3R7CMEmjI?t=97) | After: time for strategic work | 2 | Both agree |
| H9 | "I would recommend Pade to any HR professional. If you're a young HR professional or even if you're mid-level. I think Pade will help you to do a great job." | [01:48](https://youtu.be/1L3R7CMEmjI?t=108) | Recommendation | All | Both agree |

**Excluded:** [01:18] Unclear in both transcripts (Whisper: "I think Pade is so hard with statutory deductions"; captions: "it's superb good for self training terms"). Do not quote.

**Numbers from this video:** "two weeks or more" to process remittance, before (H3). "in less than a click", after (H5). Confirmation call "I think the next two days" (H6). No other figures.

---

## Not a source: Cross Border product video

https://youtu.be/y52Z7VZffug ("Meet Cross Border by PaidHR", 1:30, uploaded 2024-10-22) is a voiced-over product ad. No customer appears, so it is not social proof. Its one figure, "150 countries and 49 currencies" ([00:43](https://youtu.be/y52Z7VZffug?t=43)), is a PaidHR claim and conflicts with the website ("49 currencies across 120 countries", "45+ currencies"; see [company.md](company.md)). Treat it as TBD.

---

## Quotes grouped by proof theme

For building the social proof document. IDs refer to the tables above.

| Theme | Best quote | Backup | Pillar |
|---|---|---|---|
| Remittance with evidence | H2 | H5, H6 | 1 |
| Tax office pressure removed | H4 (before) + H2 (after) | | 1 |
| Time saved on payroll | F3 (before) + F6 (after) | H8 | 2 |
| Manual work gone | F1 (before) + F7 (after) | F2, H7 | 2 |
| Staff stop asking HR for payslips | H7 | | 2 |
| Simpler than alternatives | F5 | H1 | 2, 1 |
| Peer recommendation | H9 (to HR), F8 + F9 (to founders) | | All |

Gaps: nothing on EWA or employee wellbeing (pillar 3) beyond F10, nothing on the 2026 Nigeria tax law (pillar 4), no Kenya or South Africa customer, no customer from after the rebrand.

## Corrections to earlier notes

- **"Receipts within about two days" is wrong.** [customer-videos.md](customer-videos.md), [../case-studies.md](../case-studies.md) and [../../messaging/messaging.md](../../messaging/messaging.md) all state this. The video says she gets a receipt after remitting (H2) and, separately, a call "I think the next two days" confirming the payments were processed and remitted (H6). Those docs are corrected to match.
- **Michelle's title** was earlier read as possibly "HR operations specialist". Still TBD; neither transcript supports "HR" in the title.
