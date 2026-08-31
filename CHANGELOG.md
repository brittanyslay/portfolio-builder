# Changelog

## v1.2.0 - 2026-08-30

Added a standard Phase 5 deliverable: a "move to your own accounts" handoff guide, generated at the end of every build where the site is live on an account the client doesn't personally control - not just when asked. `references/templates/handoff-guide-template.html` is a black-and-white, IKEA-manual-style guide (numbered circular steps, icon-labeled callouts, arrow-prefixed micro-instructions, framed screenshot, chapter dividers), placeholder-driven so it adapts to whatever host/registrar the client actually uses. `references/handoff-guide.md` documents the placeholder list, why Netlify Drop is the default recommendation for non-technical clients (no GitHub, no CLI, free custom domains), the same live-docs verification discipline the rest of the skill already applies to factual claims, and two QA rules learned the hard way while building the reference guide:
- Test mobile layout with real device emulation, not a headless-Chrome `--window-size` flag - the flag doesn't reliably honor `width=device-width` and can make a fine page look broken (or a broken page look fine).
- Use `text-wrap: balance` on short wrapped fragments and `white-space: nowrap` on inline `<code>` chips to avoid widowed words and mid-phrase line breaks.

Also documents a fallback for "put a copy in Drive" requests when the guide embeds a screenshot: a giant embedded image makes the raw HTML too expensive to create via an inline-content API call (cost scales with file size, since the content has to be generated as literal output). A companion Google Doc with the steps as plain formatted text plus a link to the full illustrated version sidesteps this cleanly.

## v1.1.4 - 2026-08-21

Corrected the logo-wall guidance added in v1.1.3: it recommended `repeat(N, 132px)` (fixed-pixel grid columns) for a known logo count, which turned out to be a real bug when actually shipped - 3 columns at 132px each only spans about half of a ~1160px-wide panel, leaving the rest as dead empty space. Corrected to `repeat(N, 1fr)` (fluid columns), which fills the real container width while keeping each logo's own box a fixed height.

## v1.1.3 - 2026-08-21

Normalized logo-wall sizing in the default template: every `.logo` now gets the same fixed box (previously fixed height + natural width, which let a compact icon-mark render at roughly a sixth the width of a wide wordmark at the same height - a real, user-flagged problem). `mask-size:contain` fits each logo's real shape into that shared box, the standard "logo wall" pattern. The `--ar` custom property is no longer used for sizing; removed from the markup and the logo-prep recipe.


Pulled the README preview image for now while it gets reconsidered further. `docs/portfolio-preview.png` is still in the repo, just not currently linked from the README.

## v1.1.1 - 2026-08-20

Fixed the new preview image: the placeholder headshot was a flat solid-color box with the demo persona's initials, which read as its own crude design element rather than an obvious "photo goes here" placeholder. Replaced with a generic person-silhouette icon. Also removed an unnecessary gendered pronoun ("his") that had crept into the demo copy for a fictional, unspecified persona - inconsistent with this skill's own intake rule to ask pronouns rather than infer them.

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
