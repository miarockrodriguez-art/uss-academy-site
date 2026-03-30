# MFS Empire — Daily Status
**Date:** 2026-03-30
**Reported by:** POLY, Chief of Staff

---

## USS Academy (`uss-academy-site`)

### Commits Today (5)
| Time | Summary |
|------|---------|
| 11:10 | Sitemap expanded to 21 URLs + `submit-photo.html` added |
| 10:45 | Google Search Console verification file added |
| 10:43 | Rich results schema — Organization, 10 Courses, 10 FAQs, Event |
| 10:34 | Favicon fixed — clean `.ico` at root + SVG shield |
| 09:59 | Homepage SEO: title, meta description, OG tags updated |

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 0

### index.html
- Status: **VALID** (278KB, DOCTYPE, title, meta description, canonical all present)
- Title: `Firearm Training Classes in Central Florida | USS Academy`
- Canonical: `https://www.ussacademy.org/`

### Nav Links — All Pages Present
| Page | Status |
|------|--------|
| waivers.html | ✓ |
| compete.html | ✓ |
| host-a-class.html | ✓ |
| gallery.html | ✓ |
| service-areas.html | ✓ |
| submit-photo.html | ✓ (NEW today) |

### Images Referenced in index.html — All Present
`group-class-photo-outdoor.jpg` · `uss-academy-night-vision-training-ca46fc45.jpg` · `team-ridge-silhouette.jpg` · `central-florida-range-training-0665.jpg` · `orlando-outdoor-range-shooting-1014.jpg` · `uss-academy-class-session-8964.jpg` · `nightvision-operators-dusk.jpg` · `nightvision-closeup-nvg.jpg` · `nightvision-suppressed-ar.jpg`

### Action Items
- [ ] **`submit-photo.html` GHL webhook is a placeholder** — replace with real endpoint before promoting the page

---

## CityOne Transportation (`cityone-transportation-site`)

### Last Commits (2026-03-28, 5 commits)
- Slogan rollout across all 8 pages, hero styling, HTML corruption fix, Phoenix Blueprint footer credit

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 1 — **NEEDS DECISION**

> **PR #1** — *"Add Cloudflare Workers configuration"* (opened by Cloudflare bot 2026-03-26)
> Adds `wrangler.jsonc` for static Workers deployment. Merge to enable Cloudflare versioned deploys; close to keep current setup.

### index.html
- Status: **VALID** (single-page tab app, hero image base64-embedded, no broken local links)
- No separate HTML files referenced — all tabs render in-page

### Action Items
- [ ] **Decide on Cloudflare Workers PR #1** — merge or close

---

## Summary
- USS Academy had a heavy SEO + content day. All files intact, no broken links.
- CityOne is stable. One bot PR pending decision.
- No open issues on either repo.
