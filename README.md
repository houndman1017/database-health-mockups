# Database Health Mockups

V1 UI mockups for the CRM Database Health PRD: overview (agent), team lead view, unreachable-contacts fix flow, suggested details review, priority-contacts-with-no-plan fix flow, and loading/empty/confirmation states. Use the floating "Screen" switcher at the bottom of the page to move between them.

**Status:** Deploys to Cloudflare Workers (static assets) from the `main` branch via Workers Builds.

- Worker name: `database-health-mockups-r8m3t5`
- URL: https://database-health-mockups-r8m3t5.houndman1017.workers.dev/ (once connected)

All numbers, names and contact details in the mockups are illustrative sample data. `[TBD]` marks values the PRD hasn't settled.

## Files

- `site/` — **the published site.** Edit `site/index.html` to change what's live.
  - `index.html` — all six screens in one page, with a `noindex` robots meta tag. Hash routes: `#overview`, `#team`, `#unreachable`, `#unreachable/bounced`, `#suggestions`, `#noplan`, `#states`.
  - `_headers` — sends `X-Robots-Tag: noindex, nofollow, noarchive, nosnippet, noimageindex` and `Referrer-Policy: no-referrer` on every response.
  - `robots.txt` — `Disallow: /` for all crawlers.
- `wrangler.jsonc` — Worker config: name and `assets.directory = ./site`.

## Not discoverable

Search engines are blocked three ways (meta tag, `X-Robots-Tag` header, `robots.txt`). Anyone with the link can still open it. For real access control, enable Cloudflare Access on the `workers.dev` route (Worker → Settings → Domains & Routes), and consider disabling Preview URLs.

## Updating

1. Edit `site/index.html`.
2. Commit and push to `main` — Cloudflare rebuilds and redeploys.

## Cloudflare build settings

| Setting | Value |
|---|---|
| Build command | *(blank)* |
| Deploy command | `npx wrangler deploy` |
| Non-production branch deploy command | `npx wrangler versions upload` |
| Root directory | `/` |
