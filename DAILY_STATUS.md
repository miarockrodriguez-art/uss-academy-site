# POLY Daily Status — 2026-04-07

## USS Academy (uss-academy-site)

- **Latest commit:** GA4 form_submission + stripe_click event tracking across all 32 pages and 4 Stripe links (Mia Rodriguez, 07:36 UTC)
- **Commits today:** 3
  - Add GA4 form_submission and stripe_click event tracking — 16 form types, 32 pages, 4 Stripe links
  - Add GA4 phone_call_click event tracking to all 28 pages — every tel: link fires GA4 event
  - Fix 15 redirect loops — remove redundant rewrite rules, let Cloudflare handle .html stripping natively
- **index.html:** Present — `USS Academy v9.1`, ~307KB, valid structure
- **Local src= assets:** 22 `images/*.jpg` — all 22 follow consistent naming convention, no broken paths detected
- **Local href= pages:** 17 linked pages — all confirmed present in repo root
- **Pages in repo not linked from index.html:** `compete.html`, `terms.html`, `waiver-class-registration.html`, `waiver-exam-registration.html`, `waiver-range.html`, regional training pages (central, northeast, northwest, south, space-coast, tampa-bay) — expected, likely linked from inner nav/footer
- **Open Issues:** None
- **Open PRs:** None

## CityOne Transportation (cityone-transportation-site)

- **Latest commit:** Fix Port Canaveral sub-tab bug — duplicate IDs caused Destinations to show Rideshare content (Mia Rodriguez, 04:38 UTC)
- **Commits today:** 5 (active bug-fix session)
  - Fix Port Canaveral sub-tab bug — duplicate IDs, gave Destinations unique IDs and updated JS
  - v-refresh-003 — force Pages redeploy
  - v-refresh-002 — force Worker redeploy
  - Add TABLE-A through TABLE-L identifier comments to all 12 rate table sections
  - v-refresh-001 — force Worker redeploy
- **index.html:** Present — `v-refresh-003`, ~310KB, single-file site, valid structure
- **Local src= assets:** None — all images are base64 inline data URIs, zero local file dependencies
- **Local href= links:** None — all external (Square checkout, social links, mailto, tel)
- **Open Issues:** None
- **Open PRs:** **PR #1** — Cloudflare Workers bot autoconfig (open since 2026-03-26, **12 days unreviewed**)

## Action Items

- [ ] **cityone PR #1** — Merge or close Cloudflare Workers bot PR (open 12 days) — merge to enable CF Workers versioned deployments, close if not needed
- [ ] **uss-academy — verify GA4 events** — Confirm form_submission, stripe_click, and phone_call_click events firing correctly in GA4 DebugView after today's tracking push
- [ ] **uss-academy — verify redirect fix** — Confirm the 15 redirect loops are resolved on live site after today's `_redirects` cleanup

## Overall Status: HEALTHY — Both repos active today. USS Academy: GA4 tracking + redirect fixes. CityOne: Port Canaveral bug patched.
