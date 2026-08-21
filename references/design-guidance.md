# Design guidance - intake, direction, and hard rules

Design is a **guided collaboration**, not order-taking and not a solo guess. Pull the person's taste in, then steer it toward what actually serves them. Never just execute a preference that would hurt them; say so and offer a credible alternative.

## Ask for their taste (then guide it)
Open with something like:
> "Anything you're drawn to design-wise? **Colors** you love or hate, a **font or style**, your **industry's** feel to fit or deliberately break from, and **one or two sites you like** (paste links). Send a **profile photo** too, and tell me: **black-and-white or color?**"

Then **translate and steer**:
- Turn their references into a concrete design read (palette, type, density, motion) - the way `design-taste-frontend` does.
- If a preference undercuts them (e.g. neon/playful for a senior/regulated role, a trendy font that won't age, low contrast), **push back kindly and propose the credible version.** "I hear you on the bright palette - for the VPs screening you I'd dial it to one confident accent so the work leads. Here's both, your call."
- Lock ONE system, document it in `DESIGN.md`, apply it everywhere.

## Default aesthetic
Sober, senior, credible is the default (see `references/examples/professional-sample.html`). Playful/experimental only when the audience is genuinely creative or comedic **and** it serves them - never as novelty. A cute site for a serious person actively hurts them.

## Profile photo (ask for it; feature it with restraint)
- **Ask for one.** If they don't have a good one, note that a clean, well-lit headshot is worth getting.
- **Prioritize subtlety.** Default to a *small, well-cropped* photo (a tasteful circle or tight rectangle in the hero or about), not a giant face filling the screen. Let the **work** lead; the photo is a human anchor, not the hero.
- **Upscale if needed.** If it's low-resolution or soft, upscale it before use so it never looks pixelated on retina.
- **Ask black-and-white or color.**
  - **B&W** reads editorial and timeless and unifies a busy palette - great default for a serious brand.
  - **If they choose B&W, compensate with extra pops of the accent color elsewhere** (a coral rule, a colored eyebrow, one accented word) so the page keeps warmth and contrast and doesn't feel flat or cold.
  - **Color** is fine when the photo is high quality and on-palette.
- Optimize and export at 2× for sharpness; lazy-load below the fold.

## Motion (steer away from it)
- **Default to no animation.** Steer the person away from animations unless they are **incredibly subtle and actually add something** - a soft fade/`prefers-reduced-motion`-safe reveal on the hero, a gentle hover on links/CTAs. That's the ceiling for most personal sites.
- **Banned by default:** scroll-jacking, parallax, autoplaying loops, spinning/bouncing elements, text that animates in word-by-word, anything that delays the reader getting to the content. They read as gimmicky and date fast.
- Every motion must justify itself in one sentence (hierarchy / feedback / a real reveal). If you can't, cut it.
- Always honor `prefers-reduced-motion` and animate only `transform`/`opacity`.

## Consistency (kills the "looks misaligned" feeling)
- One content **measure** for body text across all sections (e.g. `--measure: 62ch`); ragged, inconsistent widths read as misalignment even when left edges match.
- One accent color, one corner-radius scale, one shadow rule, one type scale - applied everywhere. Audit before shipping.
- Verify at **375px first**, then scale up.
