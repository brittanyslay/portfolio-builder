# Changelog

## v1.3.0 - 2026-08-29

Design-intake and palette upgrades aimed at the real goal: a distinct-looking portfolio
that needs very minimal edits, built fast from a LinkedIn profile + a résumé - not a
from-scratch interrogation, and not a template that makes everyone's site look the same.

- **Ask for direction, not colors.** The taste question no longer asks "what colors do you
  want?" (a top rework loop - people name a hex, it reads wrong, you start over). It now asks
  for **mood, feel, and vibe** (warm/cool, calm/bold, editorial/techy/expressive, the
  three-second impression, brands whose feel they admire) and the skill **derives the actual
  palette itself**.
- **Portrait-derived palette is now the default, not an option.** Phase 4 and `palettes.md`
  default to building the palette from the person's own profile photo - either their literal
  sampled colors, or a **calibrated harmonized variation** (analogous or restrained
  complementary, tuned to pass WCAG AA) when the photo is neutral/low-contrast. This is both
  the anti-slop move and the anti-sameness move: two people never get the same palette.
- **"Do not let every build look the same."** New Phase 4 rule: keep the proven skeleton but
  vary the three levers that make each build distinct - portrait-derived palette, a font
  pairing chosen to the person's vibe, and a varied hero/accent treatment.
- **Fast path (LinkedIn + résumé → near-final draft).** New SKILL.md section: ingest both,
  auto-build the dossier, derive everything derivable (palette, font, positioning, logos), ask
  only the handful of things you genuinely can't derive, then one critique + honesty pass. The
  honesty gate is unchanged.

## v1.2.0 - 2026-08-27

Added a locked **résumé** template to sit alongside the site template. Phase 5 previously
delegated the résumé vaguely to "the resume-* skills" with no actual artifact in the repo;
now `references/templates/resume-template.html` is a complete, tokenized, print/PDF US-Letter
résumé with its own locked type system, learned from a full typographic critique pass
(resume-writer / designer / hiring-manager / HR / ATS lenses):

- **One font family** (two max) on **one five-size type scale** - replaces the nine
  near-identical sizes that make most résumés read as a single gray mass.
- **Ruthless widow/orphan control:** `text-wrap:pretty` + `hyphens:none`, `nowrap` on
  hyphenated compounds, and block-level group integrity (`.job` welds a role title to its
  bullets, rows and bullets never split, a section header never ends a page). Verify with
  `Range.getClientRects()` line-grouping, not by eye.
- **Clear section breaks**, **disciplined bold** (metrics and marquee names only), **2 pages,
  ATS-safe**, and truth-only (downstream of the honesty gate).

The seven rules are documented in the template header and in `references/design-guidance.md`
(new "Résumé typography" section); SKILL.md Phase 5 now points at the template. Privacy rule
reinforced: the template stays tokenized - a real person's filled-in résumé is never committed
to a shared or public repo; fill it locally and deliver the PDF.

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
