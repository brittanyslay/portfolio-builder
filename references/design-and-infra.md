# Design & infra playbook

Concrete artifacts to produce in Phases 4–5. Design work runs through the **design-taste-frontend** skill; this file is the checklist of what a finished, findable, shippable personal site includes.

## Design system (lock it, document it)
- Pick ONE system and write it to `DESIGN.md`: palette (with roles), type (display + body + mono), spacing scale, corner-radius rule, shadow rule, and a short "never do" list. Everything on the site obeys it.
- One accent color, used consistently. One corner-radius scale. Distinctive but appropriate to the audience.
- Bundle fonts locally (`@font-face`) rather than hot-linking Google Fonts if privacy or offline matters.
- Re-runnable: any generated page (e.g. new articles) inherits the same system.

## Pages (typical)
- Home/hero (positioning line + primary CTA), Experience, 2–4 case studies, Playbooks/Writing hub + articles, About, Contact. Résumé PDF.

## SEO / GEO artifacts
- Per page: unique `<title>`, meta description, canonical, OG + Twitter tags, theme-color, favicon.
- **JSON-LD**: `ProfilePage` + `Person` (name, jobTitle, worksFor, alumniOf, knowsAbout, sameAs) on the main pages; `BlogPosting` on articles; `ItemList` on hubs.
- `sitemap.xml` (exclude `noindex` pages), `robots` meta correct, `llms.txt` describing the person + key pages for AI answer engines.
- Consistent facts everywhere (site, résumé, LinkedIn) — models and recruiters reward consistency, punish contradiction.

## Résumé (compose with resume-* skills)
- A **branded** version matching the site + an **ATS-safe** plain variant. 2 pages. Real, defensible numbers only.
- Generate the PDF via headless Chrome `--print-to-pdf`. Link it from the site; add a GA event on download if analytics is used.

## Deploy
- git → host auto-build (Cloudflare Pages / Vercel / Netlify). Document a **one-command deploy** and the site ID/URL in the repo's `CLAUDE.md` or a `deploy.sh`.
- Add `_redirects` (or host equivalent) for any removed/renamed URLs so nothing 404s.
- Verify the live site after deploy (not just local): reload, check a couple of pages, confirm structured data and the résumé link.

## Ongoing content (optional)
- A scheduled agent publishing ONE truthful article/week, following an `AUTHORING.md`: verified sources only, no fabricated stats, the person's voice, wired into the hub + `sitemap.xml` + `llms.txt`, even cadence (≈2/month, no clustering).

## Mobile-first
- Build and verify at **375px first**; most personal-site traffic is mobile. Then scale up.
