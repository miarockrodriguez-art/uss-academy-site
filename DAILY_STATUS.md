# POLY Daily Status — 2026-04-05

## USS Academy (uss-academy-site)

- **Latest commit:** `9d24324` — Add Google Analytics GA4 (G-H3Q129SS5F) to all 28 pages (Mia Rodriguez, 2026-04-05)
- **Commits today:** 3
  - `9d24324` — GA4 (G-H3Q129SS5F) added to all 28 pages, GA placeholder removed
  - `e5014f2` — CRO slide-in lead form on 28 pages, stronger contact CTA
  - `23b06b5` — Fix mobile horizontal scroll: overflow-x:hidden + img max-width:100% on 24 pages
- **index.html:** Present — title: "Firearm Training Classes in Central Florida | USS Academy", 305KB, valid structure
- **Local links:** All referenced .html files confirmed present in root
- **Open Issues:** None
- **Open PRs:** None
- **Notes:** High-activity day. GA4 tracking live. CRO lead form deployed site-wide. Mobile scroll bug patched.

## CityOne Transportation (cityone-transportation-site)

- **Latest commit:** `d43081a` — Add Powered by Phoenix Blueprint footer credit (Mia Rodriguez, 2026-03-28)
- **Commits today:** 0 — last activity 8 days ago
- **index.html:** Present — title: "Cityone Transportation — The Blend", 301KB (large due to base64 inline image)
- **Open Issues:** None
- **Open PRs:** **PR #1** — Cloudflare Workers autoconfig bot PR (open since 2026-03-26, **12 days unreviewed**)
- **Notes:** No active development. Base64 inline image bloating index.html by ~300KB — recommend externalizing.

## Action Items

- [ ] **cityone PR #1** — Merge or close the Cloudflare Workers bot PR (open 12 days)
- [ ] **cityone index.html** — Move base64 inline PNG to `/images/` to reduce page weight (~300KB savings)
- [ ] **cityone** — No commits in 8 days; confirm if active work is expected or site is in maintenance mode

## Overall Status: HEALTHY — USS Academy active, CityOne idle with pending PR
