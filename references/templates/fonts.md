# Font pairing options for the default template

The template takes two font roles: `--sans` (nav, body, headings, buttons - does almost everything) and `--serif` (italic only, used for exactly one emphasis word in the hero headline and the pull-quote). Both load via a single Google Fonts `<link>`.

> **The résumé is different: one font only.** `references/templates/resume-template.html` uses a single `--sans` family and no serif role at all - a résumé needs no display face, and weight carries the whole hierarchy. Pick the résumé's font from the `--sans` column below; do **not** carry the site's serif-italic emphasis treatment onto the résumé.

## Default - Libre Franklin + Lora

```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Franklin:wght@400;500;600;700;800;900&family=Lora:ital@1&display=swap" rel="stylesheet" />
```
```css
--sans:"Libre Franklin",system-ui,-apple-system,sans-serif;
--serif:"Lora",Georgia,serif;
```
Trustworthy, journalistic, ages well. Safe default for a Director+ level audience.

## Alternates

| Pairing | Google Fonts `family=` params | Vibe |
|---|---|---|
| Newsreader + Archivo | `Newsreader:ital,wght@0,400;0,500;1,500\|Archivo:wght@400;600;700;800;900` (swap the sans/serif roles: Newsreader is the serif here) | Warm, senior, editorial-modern |
| Space Grotesk + Newsreader | `Space+Grotesk:wght@500;600;700\|Newsreader:ital@1` | Techy display over a readable serif italic accent |
| Hanken Grotesk (solo, no second family) | `Hanken+Grotesk:wght@400;500;600;700;800;900` | Single-family, weight carries all hierarchy - drop the `<em>` italic treatment entirely if using this, there's no serif role to fill it |

## Hard rule (do not default to these - they are the current AI-generated-site tells)
**Inter, Fraunces, Instrument Serif.** Inter is fine buried in a fallback stack, never as the deliberate brand choice. Fraunces/Instrument Serif specifically are the two most common LLM-default display serifs right now - if a serif is genuinely warranted, pick from the alternates above or something else with real reasoning, not either of these.

## Verify before shipping
- Load the actual Google Fonts URL and confirm the weights/italics you reference in CSS are the ones actually requested in the `<link>` - a missing weight silently falls back to a nearby one the browser has, which reads as slightly-wrong rather than obviously broken (easy to miss).
- **Italic descender clearance**: if the `<em>` word contains a descender (g, j, p, q, y), a tight `line-height` on the parent can clip it. This template's hero `line-height:1.15` was tuned to clear this - if you change the hero's line-height, re-check descenders don't clip.
