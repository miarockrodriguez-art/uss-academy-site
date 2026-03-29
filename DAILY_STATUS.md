# MFS Empire — Daily Status
**Date:** 2026-03-29  
**Compiled by:** POLY, Chief of Staff

---

## USS Academy Site

**Status: ACTIVE — Polish & labeling day**

### Recent Commits (today, 5 total)
| Time (UTC) | Summary |
|------------|---------|
| 11:11 | Remove tactical gear image between Classes 24–25 |
| 11:09 | Footer: Student Check-In link — remove emoji, match link styles |
| 09:51 | Layout fixes: Classes 25, 27, 29 — images span all available slots |
| 09:48 | Fix social bar: remove internal note, add "Follow USS Academy" both sides |
| 09:44 | Heading → "Student Information & Check-In", nav + chatbot updated |

### Structure Check
- `index.html` — ✅ Present, valid (`<!DOCTYPE html>` + `</html>`, 2,881 lines / ~272KB)
- All linked pages — ✅ `compete.html`, `host-a-class.html`, `waivers.html`, `gallery.html`, `service-areas.html`, `ember-iron.html` all exist
- Images directory — ✅ 233 images present; all 13 refs in index.html verified ✓
- `netlify.toml` + `_redirects` — ✅ Present

### Flags
- `ember-iron.html` is still a **placeholder** (2KB). Build out when Ember & Iron event is confirmed.
- Videos section remains **placeholder** — real YouTube links pending upload.
- Commit note: `IMG_1125 not found` — Class 27 layout used `class-session-8964` as substitute. Monitor if original photo surfaces.

### Issues / PRs
- Issues: None open
- PRs: None open

---

## CityOne Transportation Site

**Status: STABLE — No commits today**

### Recent Commits (last 24h)
| Date | Summary |
|------|---------|
| 2026-03-28 21:16 | Add "Powered by Phoenix Blueprint" footer credit (subtle, 10px) |

### Structure Check
- `index.html` — ✅ Present, valid (`<!DOCTYPE html>` + `</html>`, 1,607 lines / ~301KB)
- Single-file site — logo and assets are inline base64; no local file dependencies, no broken image risk

### Flags
- **Open PR #1** (open since 2026-03-26, updated 2026-03-28) — Cloudflare Workers autoconfig bot
  - Adds `wrangler.jsonc` for Workers deployment
  - **Action needed:** Merge if moving to Workers; close if staying on Cloudflare Pages static.

### Issues
- Issues: None open

---

## Action Items
1. [ ] **CityOne PR #1** — Decide: merge or close Cloudflare Workers autoconfig PR
2. [ ] **USS Academy** — Upload YouTube videos; replace placeholder video cards
3. [ ] **USS Academy** — Build out `ember-iron.html` once Ember & Iron details are confirmed
4. [ ] **USS Academy** — Locate `IMG_1125` if it exists; optionally replace Class 27 substitute image
