# Handoff guide (generate at the end, every build)

Every site this skill builds gets deployed *somewhere*. If that somewhere is an account the client doesn't control (your own Vercel/Netlify/GitHub, used to move fast during the build), the client needs a way to take full ownership later without you in the loop. Generate this guide as a standard Phase 5 deliverable, after the site itself is live and verified — not just when a client happens to ask for it.

## When to generate it

Always, at the end of the build, once:
- The site is deployed and working at its current URL.
- You know which domain registrar the client used (ask if unclear — don't guess).

Skip it only if the client explicitly says they'll manage hosting themselves from day one (e.g. they already have their own Vercel account and you deployed directly into it) — there's nothing to hand off.

## Default host: recommend Netlify Drop

For a non-technical client, Netlify's drag-and-drop deploy (`app.netlify.com/drop`) is the simplest real option that exists today:
- No GitHub account, no git, no CLI, no terminal.
- Drag the zip file straight into a browser window → live URL in seconds.
- Free plan includes custom domains with SSL (verified live against netlify.com/pricing — confirm this is still true before relying on it, pricing pages change).

Only deviate from this default if the client specifically wants git-based deploys (e.g. they already collaborate via GitHub, or want deploy-on-push). If you do, adapt Part 1 of the template to that host's real flow — verify every button label and URL against that host's *current* live docs the same way described below, don't write it from memory or from this file's example values.

## Filling in the template

`references/templates/handoff-guide-template.html` is the black-and-white, IKEA-manual-style guide (numbered circular steps, icon-labeled callouts, arrow-prefixed micro-instructions, framed screenshot, chapter dividers). Fill in these placeholders:

| Placeholder | Example | Notes |
|---|---|---|
| `{{DOMAIN}}` | `hiredani.com` | bare domain, no protocol |
| `{{ZIP_NAME}}` | `hiredani-com-site.zip` | the handoff zip's filename |
| `{{CLIENT_EMAIL}}` | `jane@gmail.com` | whatever email they'll sign up with |
| `{{HOST_NAME}}` | `Netlify` | capitalized product name |
| `{{HOST_SIGNUP_URL}}` / `{{HOST_LOGIN_URL}}` / `{{HOST_DROP_URL}}` | `app.netlify.com/signup` etc. | verify live, see below |
| `{{SIGNUP_BUTTON_LABEL}}` | `Sign up with Google` | match the host's real button text exactly |
| `{{HOST_APP_DOMAIN}}` | `netlify.app` | the free subdomain suffix the host issues |
| `{{DNS_A_VALUE}}` | `75.2.60.5` | the host's documented apex-domain IP (Netlify's is stable; re-verify for other hosts) |
| `{{HOST_DOMAIN_DOCS_URL}}` | live docs URL for connecting a custom domain | |
| `{{REGISTRAR_NAME}}` / `{{REGISTRAR_URL}}` / `{{REGISTRAR_DNS_DOCS_URL}}` | `Namecheap`, `namecheap.com`, KB article URL | whichever registrar the client actually uses — GoDaddy, Google Domains, etc. all differ, re-verify their real flow |
| `{{NETLIFY_DROP_IMG}}` | data URI | see screenshot step below — name kept literal even for non-Netlify hosts, just repoint it at whatever the equivalent upload screen is |

## Verify against live docs, not memory

This is the same discipline the rest of the skill uses for factual claims — apply it to UI copy too. Before writing a single button label or URL into the filled-in guide:
1. Navigate to the host's actual current signup/drop/domain pages and the registrar's actual DNS settings docs.
2. Confirm exact button text, page URLs, and flow order match what you're about to write.
3. Capture one real screenshot of the drag-and-drop (or equivalent) screen via headless Chrome (`--headless --disable-gpu --window-size=1280,900 --screenshot=...`) and embed it as a base64 data URI **by writing a script that reads the PNG and injects it directly into the HTML file on disk** — never route the base64 through your own output/context, it's extremely token-expensive per character for anything beyond a small image.
4. Link the host's and registrar's own official docs pages as a fallback reference at each step, in case their UI changes after this guide is written.

Don't hardcode a remembered IP, CNAME target, or exact screen layout as guaranteed-current — if a docs page only shows illustrative values, tell the client to copy whatever their own dashboard shows them, and say so explicitly in the copy.

## Verifying the guide itself before delivery

- **Test at real mobile width using device emulation, not a headless-Chrome `--window-size` flag.** `--window-size=375,...` does not reliably honor `<meta name="viewport" content="width=device-width">` — it can silently render at a ~980px virtual viewport and produce a screenshot that looks broken even when the page is fine, or vice versa. Use an interactive browser tool's real mobile-device emulation (e.g. resize to a 375×812 preset) and confirm with a DOM script: `document.documentElement.clientWidth` should equal the emulated width, and scan `document.querySelectorAll('body *')` bounding rects for any `right > clientWidth` — that's the authoritative check, more reliable than eyeballing a screenshot.
- **Always include `<meta name="viewport" content="width=device-width, initial-scale=1">`** in the guide's `<head>` — this file is not always wrapped by an Artifact skeleton (it may be opened as a raw file, emailed, or placed in Drive), so it needs its own viewport tag.
- **No widows, no runt lines.** `text-wrap: balance` on short wrapped fragments (step titles, micro-list items, callout text) keeps a two-line wrap even instead of leaving one long line and a two-word orphan. `text-wrap: pretty` on `body` (inherited by default, since `text-wrap` is an inherited CSS property) handles longer paragraphs. Give inline `<code>` chips `white-space: nowrap` so a value like `CNAME Record` doesn't break its pill mid-phrase across two lines.
- Re-check for horizontal overflow after *every* copy edit, not just once at the end — trimming or lengthening text can reflow a flex row that was fine before.

## Delivery

- Publish as a Claude Artifact (private by default) and share the link, or hand the client a plain HTML file directly (`SendUserFile`) if there's no Artifact tool available.
- If the client wants a copy in a shared Drive folder: a giant embedded screenshot makes the raw HTML file too large to create via a Drive API call inline (the base64 has to be generated as literal output tokens — cost scales directly with file size and made a ~900KB zip cost roughly 190K tokens for one 22KB slice in one measurement). Two working alternatives instead of fighting that wall:
  1. **Real browser automation** (e.g. a connected Chrome extension) to drag-and-drop the actual file into Drive's uploader — bypasses your context entirely, but only works if Drive exposes a discoverable file input; in practice its upload widget often doesn't expose one cleanly, so this can dead-end.
  2. **A companion Google Doc**, created directly via the Drive file-creation tool's plain-text/HTML content field (no giant image, just the steps as real formatted text) with a prominent link at the top to the full illustrated Artifact version. This is small, fast, and doesn't fight the token wall at all — it's the reliable default when a Drive copy is requested.
