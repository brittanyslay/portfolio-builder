---
name: portfolio-builder
description: Build or overhaul a truthful, well-designed personal portfolio / personal-brand website for a real person, from their real history. Runs a rigorous intake → positioning → content → design → infra → honesty-gate process, enforces "verify or don't claim," and iterates design through a critique loop. Use when someone wants a portfolio site, personal site, résumé site, or personal-brand overhaul built from their résumé / LinkedIn / career. Composes with the design-taste-frontend and resume-* skills.
---

# Portfolio Builder

Turn a **real person's verified material** into a well-positioned, tasteful, honest personal site. This is **not a template generator** — it is a process that refuses to fabricate, enforces taste through a critique loop, and protects the person's reputation and privacy. The generation is a commodity; the **honesty gate and the taste loop are the product.**

## When to use
"Build me a portfolio / personal site," "overhaul my personal brand site," "turn my résumé into a site," "make me a site for my job search / freelance / advisory." Also for redesigns of an existing personal site.

## Operating principles (hold these the whole way through)
1. **Truth is the product.** Only claim what the person's real material supports. Every metric, title, date, employer, and story traces to a source they gave or confirmed. Unsure → ask. Never invent to impress.
2. **Source-tag as you gather:** 📁 verified from a record they provided · 🗣️ their account, unverified · ⛔ not yet confirmed. Nothing 🗣️ or ⛔ ships as a hard claim without their explicit sign-off.
3. **Taste is a loop, not a guess.** Apply a real design system, render, critique, and iterate *with the person*. Never ship round one.
4. **Push back.** If something is overstated, off-brand, legally or reputationally risky, or would embarrass them, say so plainly and offer a truthful alternative. Friction is where the value is.
5. **Discretion by default.** Assume a quiet job search: no unrequested "open to work" signals, careful current-employer framing, guard their privacy and contact info.
6. **Their voice, not yours.** Write as them, from real samples. No marketing-slop verbs, no AI tells if that's their standard.

## The process — 6 phases, in order (+ optional ongoing)
Do not design before positioning. Do not publish before the honesty gate.

### Phase 1 — Intake (ask, ingest, verify)  → `references/intake.md`
**First move: ask the person for their raw material. Do not proceed without it.**
> "To build this well and truthfully, share what you have: your **résumé** (attach or paste), your **LinkedIn** (URL or export), your **current site** if any, and **paste any target job descriptions, role postings, or client/company links** you're aiming at so I position you *for them*. Plus any writing samples, a headshot, and logos."

Then:
- **Ingest & reconcile every source.** Build a source-tagged dossier, then run the **reconciliation pass** (references/intake.md): diff the sources and list contradictions + any claim that appears in *none* of the provided documents. Fabrication hides in that gap.
- **Read the target JDs** to extract the language, must-haves, and proof the audience is screening for; positioning aims at those.
- Run the interview for what documents can't give: voice, constraints (sensitive employers, discretion), and the **goal + single primary action** (hard checkpoint — you cannot build a site with no purpose and no CTA).
- For **every metric**, capture how they'd defend it. Undefendable → doesn't ship.
- Outputs: `dossier.md` (source-tagged) · `reconciliation.md` (contradictions + unsupported claims) · asset inventory.

*(See `references/example-run.md` for a full worked example — a subject with nothing verifiable, where the skill refuses to fabricate and pivots to the truth.)*

### Phase 2 — Positioning
- Derive ONE sharp positioning line + 3–5 proof pillars, drawn only from the dossier.
- Surface real range/segmentation (e.g. SMB→enterprise) if the material supports it.
- **Confirm positioning with the person before building on it.**

### Phase 3 — Content (their voice, truthful)  → honesty rules in `references/honesty-gate.md`
- Draft: hero/home, experience, 2–4 case studies, playbooks/articles, about, résumé copy.
- **Case-study rule:** every number is 📁 or gets confirmed. A metric they can't defend is cut or reframed qualitatively — reframe weak spots honestly, don't paper over them with invented figures.
- **De-risk on request:** strip figures that create legal or reputational exposure (e.g. a contentious former employer) even when true.
- Match their voice from samples.

### Phase 4 — Design (compose with `design-taste-frontend`)  → `references/design-guidance.md`, `references/design-systems.md`, `references/examples/`
- **Default to a credible, professional aesthetic matched to their level.** Sober and senior is the default; a personal site's job is to be *respected* by a hiring VP / buyer / peer. Go **playful or experimental only when the audience is genuinely creative/comedic AND it serves them — never as novelty.** A cute site for a serious person actively hurts them. When in doubt: restrained, editorial, one accent. (See `references/examples/professional-sample.html` for the default bar; `references/examples/edge-case-patrick.html` for when playful is actually correct.)
- Start from a **locked design system** in `references/design-systems.md`; pick ONE, document it in a `DESIGN.md` so the whole site is consistent and re-runnable.
- **Critique loop:** render → self-critique against the taste checklist → get the person's reaction → iterate. Verify in-browser at **375px first** (most traffic is mobile). Never ship the first pass.
- Distinctive **and** appropriate to their level. If they say "this doesn't feel like something a [VP/senior/etc.] would use," believe them and reset — don't defend it.

### Phase 5 — Infra (findable + shippable)  → `references/design-and-infra.md`
- **SEO/GEO:** per-page title/meta, JSON-LD (`ProfilePage`/`Person`, `BlogPosting`, `ItemList`), `sitemap.xml`, `llms.txt`, canonicals, correct `noindex` (and exclude noindexed pages from the sitemap).
- **Résumé:** compose with the `resume-*` skills — a branded version + an **ATS-safe** variant, 2 pages, PDF via headless print.
- **Deploy:** git → host auto-build (Cloudflare/Vercel/Netlify); document a one-command deploy.
- Accessibility + Core Web Vitals pass.

### Phase 6 — Honesty / QA gate (HARD gate — never skip)  → `references/honesty-gate.md`
Run the full checklist. **Nothing publishes until every 🗣️/⛔ claim is confirmed or cut, and the person signs off.** This is the heart of the skill and the thing everyone else skips.

### Ongoing (optional)
A scheduled **weekly-content agent** that publishes ONE truthful article, wired into the hub/sitemap/llms.txt, following an `AUTHORING.md` (no fabricated stats, verified sources only, their voice).

## Refuse / escalate
- Never fabricate metrics, titles, dates, employers, testimonials, logos, or endorsements to make someone look better. If asked to, explain why and offer a truthful alternative.
- Don't build people-scraping, credential-harvesting, or anything that impersonates a real org or person.
- Don't publish data you can't verify onto a live professional profile.
- Don't expose their personal contact info or any secret/credential in a public repo.

## Failure modes to watch
- **Fabrication-at-scale** — the #1 risk when the person's history isn't independently verifiable. The honesty gate exists precisely for this.
- **Slop** — from skipping the critique loop.
- **Generic voice** — from not collecting real writing samples.
- **The "contentious employer" trap** — a thin intake misses the context that changes how a true fact must be framed.
- **Job-search leakage** — publishing signals that tip off a current employer.
