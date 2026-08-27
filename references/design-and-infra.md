# Design & infra playbook

Concrete artifacts to produce in Phases 4-5. Design work runs through the **design-taste-frontend** skill; this file is the checklist of what a finished, findable, shippable personal site includes.

## Design system (lock it, document it)
- Pick ONE system and write it to `DESIGN.md`: palette (with roles), type (display + body + mono), spacing scale, corner-radius rule, shadow rule, and a short "never do" list. Everything on the site obeys it.
- One accent color, used consistently. One corner-radius scale. Distinctive but appropriate to the audience.
- Bundle fonts locally (`@font-face`) rather than hot-linking Google Fonts if privacy or offline matters.
- Re-runnable: any generated page (e.g. new articles) inherits the same system.

## Pages (typical)
- Home/hero (positioning line + primary CTA), Experience, 2-4 case studies, Playbooks/Writing hub + articles, About, Contact. Résumé PDF.

## SEO / GEO artifacts
- Per page: unique `<title>`, meta description, canonical, OG + Twitter tags, theme-color, favicon.
- **JSON-LD**: `ProfilePage` + `Person` (name, jobTitle, worksFor, alumniOf, knowsAbout, sameAs) on the main pages; `BlogPosting` on articles; `ItemList` on hubs.
- `sitemap.xml` (exclude `noindex` pages), `robots` meta correct, `llms.txt` describing the person + key pages for AI answer engines.
- Consistent facts everywhere (site, résumé, LinkedIn) - models and recruiters reward consistency, punish contradiction.

## Résumé  → `references/templates/resume-template.html`
- Default to the locked résumé template. Fill the `{{PLACEHOLDER}}` tokens; ship a **branded** version matching the site plus an **ATS-safe** variant. 2 pages. Real, defensible numbers only. The seven type rules are in the template header and in `design-guidance.md`.
- **ATS-safe variant - a derivation, not a second file to maintain.** The branded template is already ATS-conscious (one column, real selectable text, standard section names, DOM order = title then date, the bullet dot is a decorative CSS box so the `<li>` text is intact for parsers). To make a maximally-safe variant from it, change only: drop the accent color to ink (never rely on color to carry meaning), keep every section header a standard word ("Experience", "Education", "Skills"), and confirm there are **no** multi-column blocks, tables, text boxes, page headers/footers, images-of-text, or icon glyphs. Do not "simplify" by turning bullets into a wall of text - real `<li>`s parse best. Verify by extracting text from the generated PDF (`pdftotext -layout`) and reading it back: if a bullet, a date, or a title is missing or scrambled in the plain text, an ATS will drop it too.
- **Locale check before you typeset.** This template is a **US résumé**: US Letter, no photo, no date of birth / marital status / nationality, 1-2 pages. Much of Europe, Latin America, Asia, and academia worldwide expect a **CV** instead - often A4, with a photo and personal details, and running longer. Confirm the person's target market; if it's a photo-CV or academic-CV convention, adjust size, sections, and length rather than shipping a US résumé into it.

### Render + QA the PDF (headless print, then verify)
The résumé must be checked for page count and widows/orphans in a real engine before it ships - these are invisible until measured. Serve the folder (`python3 -m http.server`) and render with Playwright/Chromium:
```js
// print to a real 2-page-max PDF
const page = await browser.newPage();
await page.goto(url, { waitUntil: 'networkidle' });
await page.evaluate(() => document.fonts.ready);
await page.pdf({ path: 'resume.pdf', preferCSSPageSize: true, printBackground: true });
```
Then verify, at the true print width (7.4in ≈ 710px for US-Letter with the template's 0.55in side margins):
- **Page count:** open the PDF bytes and count `/Type /Page` minus `/Type /Pages` - must be ≤ 2. If it's 3, nudge all five type-scale tokens down together (never add a size) or trim copy; re-render.
- **Widows:** for each `<li>`, `.summary`, `.emeta`, `.comp`, `.edu`, use `Range.getClientRects()` to find the last visual line and check it holds more than one word. A single-word last line is a widow - reword or add a `&nbsp;` between the last two words. Do not judge this from a screenshot; measure it.
- **Orphans:** confirm no section header sits alone at the foot of a page and no role title is separated from its bullets (the `.job{break-inside:avoid}` + `h2{break-after:avoid}` rules handle this, but a content change can still push a block - re-verify after every copy edit).
- Link the PDF from the site; add a GA event on download if analytics is used.

## LinkedIn rewrite
- A standard deliverable, not optional - use `references/templates/linkedin-rewrite-template.md`. Same facts, same honesty rules, reformatted for LinkedIn's Headline/About/Experience/Skills structure and character limits.
- Flag it for a careful read before the person pastes it, especially if this is a discreet search - LinkedIn is frequently more visible to a current employer than the site link itself.

## Logo sourcing
- Try automated sourcing before asking the person for logo files: `https://logo.clearbit.com/{domain}` (bare domain, no auth) for each employer with a known domain; fall back to checking the company's own homepage for a header logo `<img>` or `apple-touch-icon`/`og:image`. Whatever comes back still needs cropping to its content bounding box and, if it lacks real alpha transparency, color-keying - the same prep as a person-supplied file (see the logo-prep recipe inline in `references/templates/default-template.html`).

## Deploy
- git → host auto-build (Cloudflare Pages / Vercel / Netlify). Document a **one-command deploy** and the site ID/URL in the repo's `CLAUDE.md` or a `deploy.sh`.
- Add `_redirects` (or host equivalent) for any removed/renamed URLs so nothing 404s.
- Verify the live site after deploy (not just local): reload, check a couple of pages, confirm structured data and the résumé link. Check the response headers too, not just the rendered page - a deployment can silently sit behind a login wall (e.g. Vercel's per-deployment SSO protection on non-production URLs) that a quick visual check won't reveal but `curl -sI` will.
- **If a review link needs to stay stable while the site keeps changing** (e.g. it's already in the actual person's hands and re-sharing a new URL isn't acceptable): confirm the host actually supports redeploying the SAME project before promising a stable link. On at least one real build, every Vercel deployment after a project's first one came back blocked at the platform's own account/team-configuration level (confirmed via their deployments API, `readyState:"BLOCKED"`) - reliably, repeatably, across multiple fresh projects, unrelated to auth (a valid token still hit the same block). The workaround: deploy each update to a throwaway project (a brand-new project's first deploy reliably succeeds), then use `vercel alias set <new-deployment-url> <the-stable-project>.vercel.app` to repoint the person's existing link at the new deployment. Delete the previous throwaway project once the alias has moved on. This is a real, repeatable pattern - don't spend time re-diagnosing the block itself; go straight to the alias workaround if a second deploy to the same project stalls in "Building..." for more than ~60-90 seconds.
- Don't chase a deploy issue with more competing parallel deploy attempts - if one CLI deploy is backgrounded and still running, kill it before starting another; multiple simultaneous deploys to the same account can leave stale processes that make later diagnosis (and the actual API status) harder to read.

## Ongoing content (optional)
- A scheduled agent publishing ONE truthful article/week, following an `AUTHORING.md`: verified sources only, no fabricated stats, the person's voice, wired into the hub + `sitemap.xml` + `llms.txt`, even cadence (≈2/month, no clustering).

## Mobile-first
- Build and verify at **375px first**; most personal-site traffic is mobile. Then scale up.
