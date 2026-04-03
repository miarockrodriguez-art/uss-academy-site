# MFS Empire — Daily Status
**Date:** 2026-04-03
**Reported by:** POLY, Chief of Staff

---

## USS Academy (`uss-academy-site`)

### Recent Commits (last 5) — ALL TODAY
| SHA | Time (UTC) | Summary |
|-----|------------|---------|
| `cfe567d` | 07:28 | Add Share Your Experience feature — share.html + gold button + QR code on index.html; /share redirect added; sitemap.xml updated |
| `dbeff4b` | 06:45 | Move sticky call button to top-right (top:70px, right:0, sharp corners) |
| `bdd51ab` | 06:42 | Add www redirect: ussacademy.org → www.ussacademy.org 301 |
| `f3d0cef` | 06:38 | Move sticky call button to bottom-right corner on all 27 pages |
| `99def39` | 06:35 | Update sticky call button: rectangular, top-right, 1-800-508-8772 |

**Theme:** Major UGC push — `share.html` launched for student photo/video submissions, wired to GHL webhook (`student_content_submission` tag). Sticky call button repositioning iterated across all 27 pages throughout the morning.

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 0

### index.html
- **Status:** VALID — 301,513 bytes, all CSS/JS inline
- New additions today: gold "Share Your Experience" button + QR code below student check-in form

### share.html (NEW TODAY)
- **Status:** VALID — 9,533 bytes
- Clean structure: name, social handle, file upload (camera prompt), 5-star rating, comment
- GHL webhook: `student_content_submission` — fires on submit
- Notifications to: mia@ussacademy.org, josh@ussacademy.org, support@ussacademy.org
- `/share` redirect confirmed in `_redirects` ✓
- `og-image.jpg` reference resolves ✓
- Back-link to `index.html` ✓

### _redirects — All Verified Clean
All 14 redirect rules checked. Every target file confirmed present in repo. No broken redirects.

### Carried Action Items
- [ ] **`submit-photo.html` GHL webhook is a placeholder** — replace with real endpoint before promoting the page

---

## CityOne Transportation (`cityone-transportation-site`)

### Last Commit
- **2026-03-28** — "Add Powered by Phoenix Blueprint footer credit" *(6 days quiet)*

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 1 — **ACTION REQUIRED (8 days old)**

> **PR #1** — *"Add Cloudflare Workers configuration"* (Cloudflare bot, opened 2026-03-26)
> Adds `wrangler.jsonc` for static Workers deployment via Wrangler. **Merge** to enable CF Workers deploys; **Close** to keep current Netlify/static setup. Decision overdue.

### index.html
- **Status:** VALID — 301,171 bytes, full SPA (all 8 pages inline)
- No external file references — all assets inline or CDN
- Google Fonts: DM Serif Display + Plus Jakarta Sans ✓

### Carried Action Items
- [ ] **Decide on Cloudflare Workers PR #1** — merge or close (8 days overdue)
- [ ] **Add favicon** to index.html — none detected, minor SEO/UX gap

---

## Summary

| | USS Academy | CityOne Transportation |
|---|---|---|
| Last commit | **2026-04-03 (today, 5 commits)** | 2026-03-28 (6 days ago) |
| Open issues | 0 | 0 |
| Open PRs | 0 | **1 (bot, 8 days old)** |
| index.html | Valid (301,513 B) | Valid (301,171 B) |
| Broken links | None | None |
| New files | `share.html` (UGC feature) | — |

**USS Academy** had a productive morning — 5 commits before 08:00 UTC, all shipping the new UGC share feature and call button polish. Site is clean, all redirects verified.

**CityOne** is stable and quiet. No broken links (single-file SPA). Bot PR #1 is the only open item — needs a decision.
