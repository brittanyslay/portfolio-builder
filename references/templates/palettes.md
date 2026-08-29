# Palette options for the default template

The default template (`default-template.html`) takes exactly these color tokens: `--page`, `--paper`, `--paper-2`, `--ink`, `--ink-2`, `--line`, `--accent`, `--accent-2`, `--pink` (third accent), `--eye` (fourth accent, used only on the hero eyebrow label). Swapping a palette means swapping these nine values - never restructure the CSS to accommodate a palette.

**You derive the palette; the person reacts to it - do not ask them to choose colors** (that is the #1 rework loop). Build the portrait-derived palette (below), apply it to the actual hero, and show *that* - plus maybe one alternate direction - because swatches alone don't tell a person how a palette reads in context. They say yes or nudge it; you don't hand them a menu of presets to pick from. Ten minutes of seeing the real thing saves multiple full-rebuild cycles. A portrait-derived palette is also why two people never get the same site.

## Default - Portrait-derived

Sample the person's own headshot for real colors instead of guessing:
1. Load the photo, sample several points from hair/clothing/eyes at full saturation.
2. Average each region's RGB - that becomes `--accent` (usually hair) and `--eye` (their actual eye color, if used at all - see the one-hue-family note below).
3. Sample the darkest shadow tone in the hair (not the flattest midtone) for `--ink` - a bright accent hue works as a small highlight but reads muddy as body-text-sized ink; the darkest shadow value is reliably close to a usable near-black.
4. Sample the brightest clean point in their clothing (not skin, which will skew warm/pink) for `--paper`.
5. `--pink`/third accent is NOT portrait-derived by default - it's a deliberate design choice layered on top. Keep it muted/desaturated (rose, not magenta) rather than saturated, and sanity-check the full combination doesn't accidentally read as a flag or political color association (see the Rasta-check note below) before locking it in.

This technique produces a palette that's genuinely theirs, not a generic "professional" pick, and is a strong answer if a person asks "why these colors."

### Two ways to use the photo (both are "portrait-derived")
1. **Literal** - the sampled colors above, when the photo has genuinely usable, distinct color (a real accent in hair, eyes, or clothing) and the result passes contrast without reading muddy.
2. **Harmonized variation** - when the photo is mostly neutral, low-contrast, or monotone (very common, and a muddy literal palette is worse than none), do NOT force the literal sample. Instead pull the photo's *dominant* hue and overall temperature (warm/cool), then build the accent as a *calibrated* color in a harmony with it: **analogous** (a neighbouring hue) for a calm, cohesive feel, or a restrained **complementary** for more contrast - at a saturation and lightness tuned to pass WCAG AA on the page. Keep the neutrals (`--ink`, `--paper`, `--page`) sampled from the photo's real dark and light values, so the palette still belongs to the person even though the accent is a deliberate harmony rather than a literal pixel.

Pick per photo, and say which you used and why ("your jacket's slate blue, dialed to one confident accent"). Either way the answer to "why these colors" is "they're yours" - which is the whole point, and the reason two people never land the same palette.

## Curated alternates (use when a portrait isn't available, or the person wants something else)

| Name | `--page` | `--paper` | `--ink` | `--accent` | `--accent-2` | Vibe |
|---|---|---|---|---|---|---|
| Espresso & Rose *(session default, shown live)* | `#E4DDD1` | `#F7F6F1` | `#56361B` | `#D3AA8C` | `#7F5F35` | Warm, senior, a little editorial |
| Field Manual | `#EAE7DE` | `#F6F4EF` | `#15221B` | `#E4564C` | `#C0392E` | Flat, structural, operator-confident |
| Deep Teal | `#EFEDE6` | `#FBFAF7` | `#1A1512` | `#146B5E` | `#0D4B41` | Restrained, quietly premium |
| Cobalt & Bone | `#F0F1F3` | `#FFFFFF` | `#101828` | `#2563EB` | `#1D4ED8` | Precise, modern, product-grade |
| Forest & Amber | `#EDEFE9` | `#F8F9F5` | `#1C2A1F` | `#B8863B` | `#8C6427` | Grounded, outdoorsy without being rustic-cliché |

For every alternate, still derive `--pink`/third accent and `--eye`/fourth accent as muted, deliberate choices in the same family logic as the default - don't leave them as an untouched leftover from a different palette iteration (a real bug: an early saturated magenta stayed in the codebase after the rest of the palette moved to a muted rose, and it silently reappeared in the favicon months later since the favicon was never re-derived from the current tokens).

## Hard rules regardless of which palette

- **One accent hue family carries the page.** A third/fourth accent is fine (this template uses two extras deliberately) but each needs a real reason, not "it looked nice" - every additional hue is a chance to look uncalibrated rather than intentional.
- **Verify contrast, every token, every time.** Compute WCAG contrast (4.5:1 for normal-size text) for every token used as text-on-background - don't eyeball it. A previously-shipped build had THREE tokens fail this (a teal at 3.56:1, a gold at 4.14:1, a pink at ~4.2:1 during a gradient animation's mid-cycle) before a critique pass caught them.
- **Avoid the "AI premium palette" tell.** Warm cream background + brass/clay/oxblood accent + espresso-brown text is the single most overused "considered professional" palette generated by default. If your palette lands exactly there, either lean harder into a real source (the portrait technique above) or deliberately pick a different family (cold, saturated, or monochrome-plus-one-pop) so it doesn't read as a template.
- **Sanity-check unintended associations.** A green+gold combination plus a red-leaning accent can read as a national flag or political color set even when that's the furthest thing from the intent - if a color combination gives anyone pause, it's worth changing even if you can't immediately articulate why (this was flagged by the actual client mid-build and was worth taking seriously, not dismissing).
- **A large solid-color fill (a footer band, a full-bleed section) needs more than the flat `--ink` value.** A color that reads fine as body text can look muddy/flat at that scale - use a subtle gradient (the ink token to a near-black variant, or the ink token with a soft radial highlight in the accent) instead of a flat single-hex fill for any large surface.
