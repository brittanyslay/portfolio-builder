# Changelog

## v1.1.0 - 2026-08-20

**Behavior change:** Phase 4 (Design) now defaults to a locked, reusable template instead of picking one of three bespoke design systems and composing from scratch. If you pulled this skill before this version and it composed a custom design system per person, that is no longer the default path - see `references/design-systems.md`, now framed as the escape hatch for when the template genuinely doesn't fit.

Added:
- `references/templates/default-template.html` - a complete, real, brutally-critiqued single-page site (hero, single-color mask-based logo wall, about, stats, numbered career list, pull-quote, two-column about, footer contact card), with inline comments explaining every previously-shipped bug and why its fix looks the way it does.
- `references/templates/palettes.md` and `references/templates/fonts.md` - curated color/font pickers, including deriving a palette directly from the person's own headshot photo.
- `references/templates/linkedin-rewrite-template.md` - a copy-paste-ready LinkedIn rewrite, now a standard Phase 3/5 output.
- Automated logo sourcing guidance (Clearbit domain lookup, then homepage scraping) before falling back to asking the person for files.
- Employer-background-research as a standard intake step.
- A documented workaround for a real Vercel platform issue where redeploys to the same project get blocked (throwaway project + `vercel alias`).
- Stricter privacy rules: no raw email on the public site (résumé is a separate exposure surface and correctly keeps it), private git repo by default for confidential/discreet searches.

Replaced the README/docs preview image, which was a hand-drawn mockup using rounded pill badges and a generic gradient bar - exactly the AI-slop look this skill is supposed to help people avoid - with a real screenshot of the actual default template.

## v1.0.0 - 2026-07-24

Initial release: honesty-gated intake -> positioning -> content -> design -> infra -> honesty-gate process, three bespoke design systems to choose from, example outputs, claims-ledger and reconciliation-pass discipline.
