# MFS Empire — Daily Status
**Date:** 2026-03-28  
**Compiled by:** POLY, Chief of Staff

---

## USS Academy Site

**Status: ACTIVE — Heavy build day**

### Recent Commits (today, 5 total)
| Time | Summary |
|------|---------|
| 09:27 | Batch update — Ask Your Instructor, Ember & Iron, videos removed, sticky bar |
| 09:20 | Hero carousel (3 rotating images, 5s crossfade) |
| 06:55 | Fix 3 photo placements — NV truck, Q&A resize, Cert photo |
| 06:33 | 18-point correction — hero, phones, photos, gallery rebuild |
| 05:47 | Complete gallery rebuild — 188 photos, 32 videos |

### Structure Check
- `index.html` — ✅ Present, valid (`<!DOCTYPE html>` + `</html>`, ~308KB)
- All linked pages — ✅ `compete.html`, `host-a-class.html`, `waivers.html`, `ember-iron.html` all exist
- `images/` directory — ✅ Present
- `netlify.toml` + `_redirects` — ✅ Present

### Flags
- `ember-iron.html` is a **placeholder** (2KB). Needs real content when Ember & Iron event is confirmed.
- Videos section is **placeholder** — real YouTube links pending upload.
- index.html is 308KB — large but single-page; monitor if load times become an issue.

### Issues / PRs
- Issues: None
- PRs: None

---

## CityOne Transportation Site

**Status: ACTIVE — Pricing & disclaimer update**

### Recent Commits (today, 1 today + 1 overnight)
| Time | Summary |
|------|---------|
| 09:27 | Add ALL RATES SUBJECT TO CHANGE disclaimer to Port Canaveral section |
| 00:15 | Update service type, rates, email (Bookmyride@), slogan placement |

### Structure Check
- `index.html` — ✅ Present, valid (`<!DOCTYPE html>` + `</html>`, ~300KB)
- Single-file site — no local asset dependencies; logo is inline base64 (no broken image risk)

### Flags
- **Open PR #1** — Cloudflare Workers autoconfig bot PR (opened 2026-03-26, updated today)
  - Adds `wrangler.jsonc` for Cloudflare Workers deployment
  - **Action needed:** Decide to merge or close. If site stays on Cloudflare Pages (static), this may be unnecessary.

### Issues
- Issues: None

---

## Action Items
1. [ ] **CityOne PR #1** — Review and merge or close Cloudflare Workers autoconfig PR
2. [ ] **USS Academy** — Upload YouTube videos and replace placeholder video cards
3. [ ] **USS Academy** — Build out `ember-iron.html` once Ember & Iron event details are confirmed
