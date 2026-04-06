# POLY Daily Status — 2026-04-06

## USS Academy (uss-academy-site)

- **Latest commit:** `cd16d8a` — Change sticky Call Now text to white bold on gold background (Mia Rodriguez, 2026-04-06)
- **Commits today:** 5 (burst session, ~30min window)
  - `cd16d8a` — Sticky Call Now: white bold text on gold background
  - `7acfd14` — Enlarge sticky Call Now button + pulse glow animation
  - `e0c65df` — Style Blog nav link as plain text to match other nav items
  - `b8b6da7` — Change nav Call Now button to Blog link
  - `ca95921` — Move sticky Call Now button below header and info bar
- **index.html:** Present — `USS Academy v9.1`, ~304KB, all CSS/JS inline, valid structure
- **Local assets referenced:** 18 `images/*.jpg` inline `<img>` tags + 4 CSS background images — no broken paths detected (confirm `/images/` dir is fully deployed)
- **External dependencies:** Google Fonts, Google Analytics (GA4: G-H3Q129SS5F) — both CDN OK
- **Open Issues:** None
- **Open PRs:** None
- **Notes:** Active UI polish session today — sticky CTA redesign and Blog nav swap. Verify on live site that sticky button and Blog link render correctly.

## CityOne Transportation (cityone-transportation-site)

- **Latest commit:** `d43081a` — Add Powered by Phoenix Blueprint footer credit (Mia Rodriguez, 2026-03-28)
- **Commits today:** 0 — last activity 9 days ago
- **index.html:** Present — title: "Cityone Transportation — Orlando Airport Transfers & Theme Park Shuttles", ~300KB (base64 inline image accounts for most of file size)
- **External dependencies:** Google Fonts, EmailJS CDN (`cdn.jsdelivr.net`) — EmailJS powers reservation form; if CDN goes down, form breaks
- **Open Issues:** None
- **Open PRs:** **PR #1** — Cloudflare Workers bot autoconfig (open since 2026-03-26, **11 days unreviewed**)
- **Notes:** Repo is idle. No development activity expected or no commits pushed.

## Action Items

- [ ] **cityone PR #1** — Merge or close the Cloudflare Workers bot PR (open 11 days) — merge to enable CF Workers deployment, close if not using Workers
- [ ] **uss-academy — verify live site** — Confirm sticky CTA button and Blog nav link look correct after today's 5-commit push
- [ ] **cityone index.html** — Base64 inline PNG bloating page to ~300KB; consider externalizing to `/images/`
- [ ] **cityone EmailJS** — Single CDN dependency for reservation form; consider monitoring or fallback

## Overall Status: HEALTHY — USS Academy active today, CityOne idle with 1 pending PR decision
