# portfolio-builder

A Claude Code skill that builds a truthful, well-designed personal portfolio site from a real person's real history.

## The core idea

The generation is a commodity. Any model can emit a portfolio page. The hard parts are not writing HTML: they are refusing to fabricate, and iterating design until it actually looks good. So that is what this skill invests in. **The honesty gate and the taste loop are the product.**

## Who it is for

Anyone building or overhauling a personal site from a résumé, LinkedIn, or career history: job seekers, freelancers, advisors, founders, operators. Works for a quiet job search or a public personal brand.

## What it does

Six phases, run in order. It does not design before positioning, and it does not publish before the honesty gate.

1. **Intake.** Ingest the résumé, LinkedIn, current site, and target job descriptions. Build a source-tagged dossier and reconcile the sources against each other.
2. **Positioning.** One sharp line plus a few proof pillars, drawn only from what the material supports. Confirmed with the person.
3. **Content.** Draft the site in their voice. Every metric is verified or cut.
4. **Design.** Start from a locked design system, render, critique, and iterate. Never ship the first pass.
5. **Infra.** SEO and structured data, a branded plus ATS-safe résumé, one-command deploy, accessibility and performance.
6. **Honesty gate.** A hard checklist. Nothing publishes until every claim is confirmed or cut and the person signs off.

## What makes it different

- **Verify, do not fabricate.** Every claim is tagged by source and reconciled across documents. A number the person cannot defend does not ship. Before publish, the skill produces a claims ledger: every claim on the site, its source, and a confirmed / not-confirmed flag. Unconfirmed rows block the launch.
- **A real design critique loop.** It applies an opinionated design system, renders, critiques its own output against a taste checklist, gets the person's reaction, and iterates. Mobile-first, verified at 375px. It is built to avoid templated, AI-slop output.

## Install

Clone into your skills directory:

```
# User-wide (available in every project)
git clone https://github.com/brittanyslay/portfolio-builder.git ~/.claude/skills/portfolio-builder

# Or per-project
git clone https://github.com/brittanyslay/portfolio-builder.git /path/to/project/.claude/skills/portfolio-builder
```

Already have the folder locally? Copy it in instead:

```
cp -R portfolio-builder ~/.claude/skills/portfolio-builder
```

Claude Code auto-triggers it when you ask for a portfolio or personal site, or you can invoke it directly with `/portfolio-builder`.

## Composes with

- `design-taste-frontend` for the design system and anti-slop frontend work.
- The `resume-*` skills for the branded and ATS-safe résumé variants.

## What it refuses to do

- Never fabricates metrics, titles, dates, employers, testimonials, logos, or endorsements to make someone look better.
- Never builds people-scrapers, credential harvesters, or anything that impersonates a real person or org.
- Never publishes unverifiable claims to a live professional profile, or exposes private contact info or secrets in a public repo.

## License

MIT.
