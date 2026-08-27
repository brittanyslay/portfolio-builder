# Intake interview

Goal: a **source-tagged dossier** rich enough to build from without inventing anything. Ingest documents first (résumé, LinkedIn export, current site, bios, writing), then interview to fill gaps and capture what documents can't: voice, constraints, and the story behind the numbers.

Tag every answer: 📁 verified from a record · 🗣️ their account (unverified) · ⛔ to confirm.

## 1. Identity & goal
- Name, location, current title/employer, pronouns (ask; never infer).
- What is this site *for*? (job search / freelance / advisory / speaking / credibility). Target roles or clients.
- **Which deliverables do you actually want?** Portfolio site · branded résumé PDF · ATS-safe résumé · LinkedIn rewrite - all four or a subset? (Confirming this up front stops you from building the wrong set or missing one they expected.)
- **Target level, in their words** (IC / senior IC / manager / director / VP / C-level). This sets the register and the résumé density; it's the single fastest way to avoid the "this doesn't feel like something a [VP] would use" reset later.
- Audience who must be impressed (recruiters, VPs/CMOs, buyers, peers).
- Timeline and any hard constraints.

## 2. Career facts - per role (this is where fabrication risk lives)
For each role, capture and tag:
- Exact title, employer, dates, employment type. (Flag any title inflation to fix.)
- Scope: team size, budget owned, what they actually owned vs. contributed to.
- **The metrics - and for each, "how would you defend this number if a skeptical interviewer pushed?"** A number they can't defend does not ship. Capture the source (dashboard, board deck, their memory).
- **For every metric, also capture the baseline and the timeframe** ("+32% *from what, over what period*"; "$10M influenced *in FY24*"). Without this, every bullet triggers a "percent or absolute? over what?" round later; with it, each bullet is self-contained on the first pass.
- The real story: what was broken, what they built, what changed. (This is the case-study spine.)
- Recognition (awards, promotions) - who gave it, when.

## 3. Voice
- Paste 2-3 samples of their real writing (emails, posts, docs).
- Words/phrases they'd **never** use. House style rules (e.g. no em-dash, reading level, formality).
- First person? How much personality?

## 4. Constraints & discretion (the context documents miss)
- Any **sensitive employers or relationships** where a true fact must be softened or omitted? (contentious exits, litigation, NDAs).
- Is this a **quiet** job search? (→ no "open to work" signals, safe current-employer framing).
- Anything explicitly **off-limits** to publish.
- Risk tolerance: bold claims vs. conservative.

## 4b. Employer background research (adds credible color, not filler)
For each employer on the site, research and verify their real public background: founding year, notable facts (an acquisition, a patent, a signature product), rough size/scale, and where relevant a real, citable source URL. This does two things: it lets the site contextualize an unfamiliar employer for a reader who's never heard of it ("Dallas-based luxury hotel chain, 51 properties" tells a reader something a bare name doesn't), and it demonstrates the site wasn't assembled from the résumé alone. Keep the citation URL in `dossier.md` next to the fact - treat this the same as any other 📁-tagged claim, sourced independently of the person.

## 5. Assets
- Headshot(s), logo/monogram, brand colors/fonts if any, existing domain + host, analytics, past site to preserve or overhaul.
- Testimonials/references they can actually use (with permission).

## 6. Proof inventory
- The 3-5 things they most want to be known for - and the evidence for each. Anything with no evidence becomes a ⛔ to resolve or drop.

## 7. Résumé specifics (decide up front - these are the usual sources of rework)
Ask these before typesetting the résumé; each one, left unasked, is a predictable extra round.
- **One page or two?** Governs how hard to compress. If they don't know: default to one page under ~10 years of experience, two beyond.
- **Contact line: which surfaces, and how much?** Email, phone (yes/no), site, LinkedIn, GitHub, location. Metro only ("Denver, CO") vs full address (default to metro). State **remote / relocation** stance explicitly so it isn't guessed.
- **Credentials / post-nominals:** which to show (MBA, PMP, PE, PhD…) and where - after the name, in a line under it, or not at all.
- **Dates format + the awkward bits:** months-and-years or years-only; and decide up front how to handle any **employment gaps or short stints** - the honest options are grouping, year-only dates, or a brief framing line. Surfacing this early avoids an uncomfortable late reveal and a scramble.
- **What must lead, and what they're tired of leading with.** The one role/achievement that has to be first, and anything they've overused. Prevents a reorder cycle after the first draft.
- **ATS keyword lock:** from the target JDs, confirm the 5-10 exact phrases/skills that must appear verbatim. Agreeing the keyword set now makes it a one-pass match instead of a tuning loop.
- **Where the filled file lives:** the résumé carries private data (full name, employers, metrics, contact). Confirm it stays local / private and is delivered as a PDF - never committed to a shared or public repo.

## Verification & reconciliation
Once every source is ingested (résumé, LinkedIn, current site, bios, target JDs), **diff them against each other** and write `reconciliation.md`. Do not skip this because the sources "seem to agree." Fabrication hides in the gap between what someone says and what their records show; this step is where you catch it.

List, with source tags:
- **Contradictions between sources** - a metric, scope, or claim stated one way on the résumé and another way on LinkedIn or the current site.
- **Unsupported claims** - anything that appears in *none* of the provided documents. Treat these as ⛔: they must be confirmed against a real source or cut. A claim that lives only in conversation is 🗣️ until proven.
- **Title / date / employer mismatches** - job titles, employment dates, or employer names that don't line up across sources. Resolve each to the true value before it reaches the site.

`reconciliation.md` is a working document: every row stays open until it's resolved (confirmed to a source, corrected, or dropped). Its open rows feed the ⛔ to-do and the pre-publish honesty gate.

## Output
`dossier.md`: every fact tagged 📁/🗣️/⛔, a per-role table with defensible metrics, voice notes, a constraints list, and an asset inventory. `reconciliation.md`: contradictions, unsupported claims, and title/date/employer mismatches across sources. Together their open rows are the pre-publish to-do.
