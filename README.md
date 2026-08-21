# portfolio-builder

A Claude Code skill that builds a truthful, well-designed personal portfolio site from a real person's real history, for job seekers, freelancers, advisors, founders, and operators.

![An example portfolio the skill builds: a clean editorial hero for a product designer, with a serif headline, a short intro, two CTAs, and a row of client logos.](docs/portfolio-builder.jpg)

## What it does

- **Refuses to fabricate.** Every metric, title, date, employer, and story is tagged by source and reconciled across documents. A claim the person can't defend is cut or reframed. It never ships. A pre-launch claims ledger flags anything unconfirmed and blocks the publish.
- **Starts from a real, reusable template, not a from-scratch design exercise.** The default template already survived a full brutal critique (design, copy/positioning, technical consistency) plus multiple rounds of live user feedback; color and font are the only open choices (including deriving a palette straight from the person's own headshot photo). It still gets critiqued and iterated per person - mobile-first, verified at 375px - because content-specific issues don't come free just because the layout is proven.
- **Positions before it designs.** A six-phase process - intake, positioning, content, design, infra, honesty gate - that reads target job descriptions and reconciles sources before writing a single line of HTML.
- **Ships the whole package.** SEO and structured data, a branded plus ATS-safe résumé, a copy-paste-ready LinkedIn rewrite, one-command deploy, and an accessibility and performance pass.
- **Sources company logos automatically where it can.** Tries a free logo lookup by domain before asking the person to hunt down and send files.
- **Protects the person.** Discreet by default for a quiet job search, careful current-employer framing, and no exposed private contact info or secrets.

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

## Example prompts

- `build my portfolio site from my resume`
- `make me a personal site from my LinkedIn`
- `I need a portfolio for a job search`
- `turn my career history into a website`
- `build a personal brand site for a founder`
- `design a developer portfolio`
- `overhaul my personal site so it looks senior, not templated`
- `make a one-page site that doesn't look AI-generated`
- `turn my résumé and case studies into a freelance site`
- `redesign my advisory site and keep it discreet for a quiet job search`

## What's inside

| File | What it covers |
| --- | --- |
| `SKILL.md` | The full six-phase process, operating principles, and refusal rules. |
| `references/intake.md` | Ingest-and-reconcile pass: source-tagged dossier, contradiction diff, unsupported-claim detection. |
| `references/honesty-gate.md` | The hard pre-publish checklist and claims-ledger rules. |
| `references/templates/default-template.html` | The default, locked, brutally-critiqued page template - copy it, fill in the placeholders. |
| `references/templates/palettes.md` | Curated color palette options, including deriving one from the person's own photo. |
| `references/templates/fonts.md` | Curated font-pairing options. |
| `references/templates/linkedin-rewrite-template.md` | A copy-paste-ready LinkedIn Headline/About/Experience/Skills rewrite - a standard output, not optional. |
| `references/design-guidance.md` | Taste checklist and the render → critique → iterate loop. |
| `references/design-systems.md` | Escape hatch: locked, re-runnable bespoke design systems, for when the default template genuinely doesn't fit. |
| `references/design-and-infra.md` | SEO/GEO, structured data, résumé variants, and one-command deploy. |
| `references/example-run.md` | A full worked run on a subject with nothing verifiable, where the skill refuses and pivots to the truth. |
| `references/examples/` | Escape-hatch design-system examples (not the default template): a professional bespoke build (`professional-sample.html`) and a playful edge case (`edge-case-patrick.html`). |

**Composes with** `design-taste-frontend` for the design system and anti-slop frontend work, and the `resume-*` skills for the branded and ATS-safe résumé variants.

## License

Free for noncommercial use (PolyForm Noncommercial 1.0.0), with attribution. See [LICENSE.md](LICENSE.md).

---

Built by [Brittany Slay](https://brittanyslay.com), a B2B marketing leader who builds AI-native tools. More free Claude skills at [brittanyslay.com/skills](https://brittanyslay.com/skills). Want an AI-native build or a GTM function built for real? [Get in touch](https://brittanyslay.com/#contact).
