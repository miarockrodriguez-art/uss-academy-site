# MFS Empire — Daily Status
**Date:** 2026-04-02
**Reported by:** POLY, Chief of Staff

---

## USS Academy (`uss-academy-site`)

### Recent Commits (last 5)
| Date (UTC) | Summary |
|------------|---------|
| 2026-04-01 23:26 | Make phone numbers prominent in modal popups — gold, bold, larger |
| 2026-04-01 04:54 | Wire all 8 website forms to GHL API — live contact creation |
| 2026-03-31 19:47 | Fix font sizing on SEO content to match site standard (15px → 14px) |
| 2026-03-31 19:28 | Fix all 9 SEO audit issues across 19 files |
| 2026-03-31 13:21 | POLY daily check — 2026-03-31 |

**Theme:** Major CRM milestone — all 8 forms are now live-wired to GoHighLevel (GHL sub-account `GOBk9IDY9xnt7JJeDYsI`). CRM status: **LIVE**. Phone numbers in Pay modal, Waiver success, and Range partner success modals are now gold (#C9A84C), bold, 15–16px, and wrapped as `tel:` links.

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 0

### index.html
- Status: **VALID** — large single-file app, all CSS/JS inline
- **Google Fonts:** Cinzel + Barlow + Barlow Condensed (fonts.googleapis.com CDN)
- **External JS:** None — all JavaScript inline
- **Local images:** 24 unique files in `images/` directory — all referenced via `<img>` or CSS `background-image`

### Image Asset List (24 files)
`ar15-on-bench-golden.jpg` · `ballistics-expert-witness-firearms-training-orlando.jpg` · `central-florida-range-training-0665.jpg` · `classroom-students-diverse.jpg` · `female-shooter-rifle-bw.jpg` · `florida-firearms-range-training-1449.jpg` · `florida-firearms-range-training-1576.jpg` · `nightvision-closeup-nvg.jpg` · `nightvision-operators-dusk.jpg` · `nightvision-suppressed-ar.jpg` · `orlando-outdoor-range-shooting-1014.jpg` · `orlando-outdoor-range-shooting-1120.jpg` · `pcc-permit-to-carry-concealed-firearms-instructor-florida.jpg` · `tactical-field-training-exercise-2621.jpg` · `tactical-field-training-exercise-2956.jpg` · `tactical-firearms-training-sunset-4245-v2.jpg` · `team-ridge-silhouette.jpg` · `thermal-vehicle-cropped.jpg` · `uss-academy-class-session-8887.jpg` · `uss-academy-class-session-8964.jpg` · `uss-academy-class-session-9070.jpg` · `uss-academy-night-vision-training-ca46fc45.jpg` · `uss-academy-student-training-6707.jpg` · `women-group-range-selfie.jpg`

### Carried Action Items
- [ ] **`submit-photo.html` GHL webhook is a placeholder** — replace with real endpoint before promoting the page

---

## CityOne Transportation (`cityone-transportation-site`)

### Last Commit
- **2026-03-28** — "Add Powered by Phoenix Blueprint footer credit" *(4 days quiet)*

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 1 — **ACTION REQUIRED**

> **PR #1** — *"Add Cloudflare Workers configuration"* (Cloudflare bot, opened 2026-03-26 — now **7 days old**)
> Adds `wrangler.jsonc` for static Workers deployment. **Merge** to enable CF Workers versioned deploys; **Close** to keep current setup. Decision overdue.

### index.html
- Status: **VALID** — large single-file app
- **Google Fonts:** DM Serif Display + Plus Jakarta Sans
- **External JS:** EmailJS via jsdelivr CDN (`@emailjs/browser@4`, deferred)
- **Local images:** None — hero image is base64-encoded inline (zero external image file dependencies)
- **Favicon:** ⚠️ None detected — minor SEO/UX gap

### Action Items
- [ ] **Decide on Cloudflare Workers PR #1** — merge or close (7 days overdue)
- [ ] **Add favicon** to index.html

---

## Summary

| | USS Academy | CityOne Transportation |
|---|---|---|
| Last commit | 2026-04-01 | 2026-03-28 |
| Open issues | 0 | 0 |
| Open PRs | 0 | **1 (bot, 7 days old)** |
| index.html | Valid | Valid |
| CRM integration | **GHL LIVE (all 8 forms)** | None |

**USS Academy** hit a major milestone: GHL CRM is now live across all 8 forms. Site is clean, no broken links, actively developed.

**CityOne** is stable but quiet — 4 days since last commit. Bot PR #1 is the only open item and needs a decision. Favicon missing.

No open issues on either repo.
