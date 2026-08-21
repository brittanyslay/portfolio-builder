# Honesty / QA gate

The hard gate before anything goes live. Run **every** item. If a single box can't be honestly checked, it doesn't publish. End with the person's explicit sign-off.

## Mandatory artifact - the claims ledger
Before publish, produce `claims-ledger.md`: one row for **every claim on the site** - each metric, title, date, employer, testimonial, and named achievement. Columns:

| Claim (as it appears on the site) | Where (page/section) | Source tag (📁/🗣️/⛔) | Confirming source / quote | Confirmed (y/n) |

**Rule: nothing publishes until every row is Confirmed = y, or the claim is cut.** A row you can't confirm is not a small copy problem to smooth over - it is the exact thing this skill exists to stop. Build the ledger by walking the finished site, not the dossier, so nothing that slipped in during drafting escapes the check.

## Truthfulness (the core)
- [ ] **Every metric** on the site traces to 📁 (a record) or a claim the person explicitly confirmed. Search the built site for numbers; each one has a source.
- [ ] No **placeholder / representative / illustrative** figures left presented as real. (Grep the source for "placeholder", "TODO", "data-ph", "example", round-suspicious numbers.)
- [ ] No inflated or altered **titles, dates, or employers**. Titles match what the person actually held.
- [ ] No **fabricated testimonials, client logos, awards, or endorsements.** Every quote is real, attributed, and permitted.
- [ ] **Weak spots reframed honestly**, not hidden behind invented numbers. Gaps are addressed with truthful framing.
- [ ] Structured data (JSON-LD) and meta descriptions **match reality** - no keyword-stuffed false claims for GEO/SEO.

## Reputation & discretion
- [ ] **De-risk applied**: figures/claims that create legal or reputational exposure (contentious former employer, NDA'd data) are softened or removed per the person's instruction - even if true.
- [ ] **Job-search safe**: no unrequested "open to work" signals; current-employer framing won't tip anyone off.
- [ ] Nothing that could embarrass them if the person on the other end (recruiter, former boss, current employer) read it.

## Voice & craft
- [ ] Reads in **their voice**, matched to samples. No AI tells (em-dash if banned, no "leverage/robust/seamless/delve", no forced rule-of-three, no identical paragraph rhythm).
- [ ] Copy self-audit: every visible string re-read; nothing grammatically broken or hallucinated.
- [ ] **Copy-sensitivity scan**: read every string for unintended alarming or ambiguous connotations - e.g. "shooting" next to "3D printing" reading as firearms, violent idioms, or dog-whistles - and reword to remove the ambiguity. A true, innocent phrase that *reads* wrong to a stranger still costs the person.
- [ ] Design passed the **critique loop** (not round one). Distinctive and level-appropriate. Verified at 375px.

## Privacy & security
- [ ] **No raw email address on the public site** (visible mailto link, footer text, or in the JSON-LD `email` field) unless the person explicitly asked for it to be public. Route the site's contact CTA to LinkedIn or a form instead. This is a different surface than the résumé PDF, which correctly *does* include the email - a résumé is meant to be handed directly to an employer; the public site (even `noindex`) is reachable by anyone with the link. Don't apply the résumé's rule to the site or vice versa.
- [ ] No other personal contact info exposed beyond what the person chose to share.
- [ ] **Confidential/discreet search: the git repo is private by default.** Don't rely on `noindex` alone to keep a job search quiet - a public repo makes the dossier, positioning notes, and full history readable to anyone who finds it, employer included.
- [ ] No secrets, tokens, API keys, or private data in a public repo or shipped bundle.
- [ ] Cookie/consent and analytics handled privately (consent-gated, minimal).

## Technical
- [ ] Every internal link resolves; no dead links; redirects for any removed pages.
- [ ] `noindex` pages are excluded from `sitemap.xml`; canonicals correct.
- [ ] Accessibility (contrast, alt text, keyboard) and Core Web Vitals pass.
- [ ] Résumé: branded + ATS-safe variant, 2 pages, links resolve.

## Sign-off
- [ ] The person has **reviewed and confirmed every 🗣️ and ⛔ item** that made it into a claim.
- [ ] The person has explicitly approved publishing.

> If publishing repeatedly for many people: this gate is non-negotiable per person. The moment you let it slide "because the copy sounds impressive," you are mass-producing plausible lies on real people's professional profiles. That is the failure this whole skill exists to prevent.
