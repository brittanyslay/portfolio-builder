# Design systems - three locked starting points

Pick ONE, copy its tokens into `DESIGN.md`, and obey it everywhere. These are not moodboards. They are complete, opinionated systems with defined roles, so every page is consistent and re-runnable. Start from one, tune the accent if the person's brand calls for it, and lock it before you build.

All three share the same discipline: one accent used consistently, one radius scale, one shadow rule, one type scale, generous whitespace, real hierarchy. The difference is register.

---

## System A - Field Manual / Editorial
Flat, structural, confident. Reads like a well-set operator's document: paper stock, mono labels, no decoration. Nothing glows, nothing floats.

**Palette (roles)**
| Token | Value | Role |
|---|---|---|
| `--paper` | `#F6F4EF` | Page background |
| `--paper-2` | `#EFEBE2` | Raised surface, table zebra, callout |
| `--ink` | `#15221B` | Primary text, headings |
| `--ink-2` | `#5A655E` | Secondary text, captions, meta |
| `--accent` | `#E4564C` | One accent: rules, active state, key numbers |
| `--accent-2` | `#C0392E` | Accent pressed / hover |
| `--line` | `rgba(21,34,27,.14)` | Hairline borders, dividers |

**Type**: `Archivo` 900 for display and headings (tight, uppercase-friendly). `IBM Plex Mono` for labels, eyebrows, meta, and small caps. Body can run in Archivo 400.

**Spacing / radius / shadow**
- Radius: `2px` on everything. Sharp, not rounded.
- Shadow: none. Depth comes from `--line` borders and `--paper-2` fills, never from a drop shadow.
- Labels: mono, uppercase, `letter-spacing:.12em`, `--ink-2`.
- Section dividers: a single `--line` hairline or a `2px` `--accent` rule for emphasis.

**When to use**: senior operators, editorial or writing-forward brands, consultants, people whose credibility is "I run tight systems." It signals substance over polish.

**Never do**: drop shadows, rounded cards, gradients, more than one accent, a second display font. The moment it looks soft it stops reading as a field manual.

---

## System B - Modern Professional / Serif-Grotesque
The default professional bar. Warm, restrained, quietly premium. This is what `references/examples/professional-sample.html` uses. Serif display carries the authority, a grotesque body keeps it modern, one deep accent does all the color work.

**Palette (roles)**
| Token | Value | Role |
|---|---|---|
| `--paper` | `#FBFAF7` | Page background (warm off-white) |
| `--paper-2` | `#F1EEE7` | Sample bar, subtle fill |
| `--ink` | `#1A1512` | Primary text, headings |
| `--ink-2` | `#5F574F` | Secondary text, leads, meta |
| `--accent` | `#146B5E` | Deep teal: eyebrows, links, key metrics |
| `--accent-2` | `#0D4B41` | Accent pressed, emphasized numbers |
| `--line` | `#E7E1D6` | Hairline rules between sections and rows |

**Type**: `Newsreader` (serif) 400/500 for display, headings, and stat numbers, italic for emphasis words. `Archivo` 400-700 for body, nav, buttons, eyebrows. Set a fixed `--measure` (about `60ch`) for all body copy.

**Spacing / radius / shadow**
- Radius: `6px` on buttons and any rare card. Everything else is hairline-ruled, not boxed.
- Shadow: none by default. Structure comes from `--line` rules and whitespace.
- Stat rows and work lists sit between hairline rules, no boxes.
- One accent only. Italics in the serif carry emphasis, not color.

**When to use**: product, growth, and executive profiles; anyone who needs to be respected by a hiring VP, buyer, or peer. This is the safe, senior default when in doubt.

**Never do**: a second accent color, heavy shadows, boxed-in cards everywhere, a trendy display font that dates. Keep it hairlines and one confident accent.

---

## System C - Clean SaaS / Minimal
Bright, precise, product-grade. White surfaces, near-navy ink, one saturated accent, soft depth. Reads like a well-built product marketing page.

**Palette (roles)**
| Token | Value | Role |
|---|---|---|
| `--surface` | `#FFFFFF` | Cards, page background |
| `--surface-2` | `#F9FAFB` | App background behind cards |
| `--ink` | `#101828` | Primary text, headings |
| `--ink-2` | `#667085` | Secondary text, captions |
| `--accent` | `#F5541F` (or `#2563EB`) | One saturated accent: CTA, active, key stat. Pick warm (orange) or cool (blue), not both |
| `--accent-2` | derived `~12%` darker | Accent hover / pressed |
| `--line` | `#E4E7EC` | Card borders, dividers |

**Type**: a clean grotesque. `Archivo` or `Hanken Grotesk` for both display and body, weight carrying the hierarchy. Do NOT reach for Inter as the default (see the AI-tell note below).

**Spacing / radius / shadow**
- Radius: `8-10px` on cards, buttons, inputs. Consistent scale.
- Shadow: soft and single-layer, e.g. `0 1px 2px rgba(16,24,40,.06), 0 1px 3px rgba(16,24,40,.10)`. One elevation, used consistently. No stacked, colored, or heavy shadows.
- Generous padding inside cards (`24-32px`). Roomy line-height.
- One accent, applied to the primary action and one or two key numbers only.

**When to use**: SaaS founders, technical operators, product and platform people, anyone whose audience lives in modern software UIs and reads "clean and current" as competence.

**Never do**: rainbow accents, glassmorphism, neon gradients, more than one shadow elevation, Inter-by-default. Precision is the whole point; clutter kills it.

---

## Celebrated font pairings
Vetted pairings that read as designed, not defaulted. "Free on Google?" tells you whether you can `@font-face` it without a license.

| Pairing | Vibe | Free on Google? | Notes |
|---|---|---|---|
| Newsreader + Archivo | Warm, senior, editorial-modern | Yes | System B's pairing. Safe, premium-feeling default. |
| GT Sectra + Söhne | High-end editorial, gallery-grade | No (licensed) | Premium. Buy the licenses or don't use it; no free swap is identical. |
| Reckless Neue + PP Neue Montreal | Contemporary, design-studio | No (licensed) | Premium. Strong for creative operators who can license. |
| Fraunces + a grotesque | Soft, characterful serif | Yes | OVERUSED. A common AI-tell now. Use sparingly, and only with a reason. |
| Libre Franklin + Lora | Trustworthy, journalistic | Yes | Reliable, unflashy, ages well. Good for writing-forward sites. |
| Space Grotesk + Newsreader | Techy display over readable serif | Yes | Distinctive without being loud. Good for technical-but-human. |
| Hanken Grotesk (solo) | Clean, single-family SaaS | Yes | One family, weight carries hierarchy. Pairs cleanly with System C. |

**Hard rule (per the `design-taste-frontend` skill): do NOT default to Inter, Fraunces, or Instrument Serif.** They are the fonts every generated site reaches for, so they read as AI tells. Inter is fine as a system-UI fallback in the stack, never as the deliberate brand choice. If you want one of the three, justify it against the person's brand in one sentence; if you can't, pick something with more intent.
