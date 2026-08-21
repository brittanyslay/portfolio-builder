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

## Résumé (compose with resume-* skills)
- A **branded** version matching the site + an **ATS-safe** plain variant. 2 pages. Real, defensible numbers only.
- Generate the PDF via headless Chrome `--print-to-pdf`. Link it from the site; add a GA event on download if analytics is used.

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
