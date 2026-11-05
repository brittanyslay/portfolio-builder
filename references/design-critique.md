# Design & copy self-critique (run it on your own build, before the honesty gate)

The honesty gate (`references/honesty-gate.md`) proves the site is *true*. This file proves it
is *good*: that the design and the copy clear a real bar, in the person's register, before you
hand anything back. It is the "self-iterate" half of the skill. Most people will never run a
second round on their own work, so the skill runs it for them. You do not ship round one, and
you do not ask the person to find the problems you could have found yourself.

Run this after the build is assembled and before Phase 6. Produce `design-critique.md`: a scored
pass against the rubric below, with a one-line verdict per row and a note on what you changed.
It is a working artifact, same as `claims-ledger.md` - open rows stay open until they are fixed
or consciously accepted with a reason. **A build that has not passed this does not reach the
honesty gate.**

## How to run it (render, look, score, fix, repeat)
1. **Render the real thing, not a guess.** Serve the site and open it in a real browser (headless
   Chromium is fine for capture, but confirm layout with real device emulation, not a
   `--window-size` flag, which does not reliably honor `width=device-width`). Look at
   **375px first**, then a desktop width. A mobile-only check has missed a real desktop-only bug
   before; a desktop-only check misses the width most traffic actually uses.
2. **Score every row** below as pass / fix. "Fix" is not a note for later; it blocks the handoff.
3. **Fix, then re-render and re-score the rows you touched.** Copy edits reflow layout, so a row
   that passed can regress. Re-check overflow and line-wrapping after every copy change.
4. **Loop until every row passes.** If a row cannot pass (a constraint you cannot change), write
   why you are accepting it, in one line, so the decision is visible rather than silent.

## Design rubric
- [ ] **Level-appropriate register.** The design matches who is screening this person (a hiring
      VP, a buyer, a peer). Sober and senior is the default; playful is earned, never chosen for
      novelty. If the person says "this doesn't feel like something a [senior title] would use,"
      that is a failed row, not a difference of opinion.
- [ ] **Not an AI tell.** No defaulted Inter / Fraunces / Instrument Serif as the brand choice,
      no rounded-pill-plus-gradient-bar look, no glassmorphism, no rainbow of accents. One accent
      hue family carries the page; any extra hue has a real reason.
- [ ] **Contrast is computed, not eyeballed.** Every token used as text-on-background clears WCAG
      AA (4.5:1 for normal text; 3:1 for large). Check the mid-cycle state of any animated
      gradient too, not just its endpoints. Record the measured ratio for each pairing.
- [ ] **One of everything, applied everywhere.** One type scale, one radius scale, one shadow
      rule, one body measure (e.g. `--measure`). Ragged, inconsistent widths read as misalignment
      even when the left edges line up. Audit for drift before you score this a pass.
- [ ] **Equal-size cards.** Any set of cards or tiles in a grid is equal width and equal height
      (stretch the row, do not let one card run full-width or taller). Extra height falls to the
      bottom as padding, never a mid-card hole and never a `margin-top:auto` gap above the buttons.
- [ ] **Mobile is a real presence at 375px.** The portrait is not a shrunken off-center thumbnail;
      stats and lists reflow cleanly; nothing overflows horizontally. Confirm with a DOM check
      (`clientWidth` equals the emulated width; no element's `right` exceeds it), not by eye.
- [ ] **No orphaned or widowed words** in headlines, section headers, stat labels, or short
      wrapped fragments. Verify a hero headline wraps to clean lines with no single word stranded,
      using line-grouping in a live browser rather than a screenshot.
- [ ] **Motion justifies itself or it is cut.** Default to almost none. Every animation earns its
      place in one sentence (hierarchy, feedback, or a real reveal) and honors
      `prefers-reduced-motion`. No scroll-jacking, parallax, autoplay loops, or word-by-word text.
- [ ] **Images are clean.** Headshot is sharp at 2x (upscaled if soft), baseline-encoded (no
      progressive-JPEG blur flash), lazy-loaded below the fold. Logos share one box, one color via
      mask, cropped to their content bounds with real alpha.
- [ ] **Favicon is legible at 16-32px**, not just at its viewBox size. Render it at real tab size
      and look.

## Copy & voice rubric
- [ ] **Reads in their voice**, matched to real samples, not a generic professional default.
- [ ] **No AI slop.** No "leverage / seamless / robust / cutting-edge / delve / unlock synergies,"
      no forced rule-of-three, no "no X, no Y, just Z" ad-copy cadence, no identical paragraph
      rhythm section after section. Say the thing directly.
- [ ] **No templated repetition.** The about paragraph is not the hero subline reworded; stat
      labels are not the same phrase four times. Reusing a sentence verbatim across sections reads
      as lazy and is a failed row.
- [ ] **Parallel construction** holds across items that sit together: nav items, section headers,
      stat labels, and list rows share grammatical form and rhythm. Fix drift when you see it.
- [ ] **Stat labels are honest about what they measure.** A peak from years ago is labeled as a
      peak, never as an implied current number.
- [ ] **Copy-sensitivity scan.** Read every visible string for a connotation a stranger could
      misread (a violent idiom, a phrase that reads wrong next to the one beside it). A true,
      innocent phrase that *reads* wrong to a recruiter still costs the person. Reword it.
- [ ] **Every visible string re-read** for anything grammatically broken, truncated, or left as a
      live `{{PLACEHOLDER}}`.

## Verdict
End with one line: **ready for the honesty gate** (every row passes or is accepted with a reason),
or **not yet** with the open rows named. Do not carry a "fix" row silently into Phase 6. The
honesty gate checks truth; this checklist is why the truthful thing is also worth looking at.
