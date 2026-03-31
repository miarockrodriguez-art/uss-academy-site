# MFS Empire — Daily Status
**Date:** 2026-03-31
**Reported by:** POLY, Chief of Staff

---

## USS Academy (`uss-academy-site`)

### Commits Today (5)
| Time (UTC) | Summary |
|------------|---------|
| 04:02 | Add SMS/Text Messaging Program section to Terms of Service |
| 04:01 | Add TCPA-compliant SMS consent checkboxes to all 6 forms |
| 00:00 | Update Virtual/Online class description with detailed course content |
| 23:53 (3/30) | Add range fee notice to What to Bring section |
| 23:49 (3/30) | Enhance CALL NOW button, fix BOOK NOW casing, add 3 Tier 1 photos |

**Theme:** TCPA/SMS compliance push — consent checkboxes on all 6 forms + full Section 12 in ToS. Also cosmetic/content tweaks to class descriptions and CTA buttons.

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 0

### index.html
- Status: **VALID** (2,992 lines, DOCTYPE present, `</html>` closes correctly)
- All local page links resolve: `host-a-class.html` · `privacy-policy.html` · `refund-policy.html` · `ember-iron.html` · `gallery.html` · `privacy.html` · `service-areas.html` · `terms.html` — all ✓

### Images Referenced in index.html — All Present (23/23)
`ar15-on-bench-golden.jpg` · `ballistics-expert-witness-firearms-training-orlando.jpg` · `central-florida-range-training-0665.jpg` · `classroom-students-diverse.jpg` · `florida-firearms-range-training-1449.jpg` · `florida-firearms-range-training-1576.jpg` · `group-class-photo-outdoor.jpg` · `nightvision-closeup-nvg.jpg` · `nightvision-operators-dusk.jpg` · `nightvision-suppressed-ar.jpg` · `orlando-outdoor-range-shooting-1014.jpg` · `pcc-permit-to-carry-concealed-firearms-instructor-florida.jpg` · `tactical-field-training-exercise-2621.jpg` · `tactical-field-training-exercise-2956.jpg` · `tactical-firearms-training-sunset-4245-v2.jpg` · `team-ridge-silhouette.jpg` · `thermal-vehicle-cropped.jpg` · `uss-academy-class-session-8887.jpg` · `uss-academy-class-session-8964.jpg` · `uss-academy-class-session-9070.jpg` · `uss-academy-night-vision-training-ca46fc45.jpg` · `uss-academy-student-training-6707.jpg` · `women-group-range-selfie.jpg`

### Carried Action Items
- [ ] **`submit-photo.html` GHL webhook is a placeholder** — replace with real endpoint before promoting the page

---

## CityOne Transportation (`cityone-transportation-site`)

### Last Commit
- **2026-03-28** — "Add Powered by Phoenix Blueprint footer credit" *(no new commits today)*

### Issues / PRs
- **Issues open:** 0
- **PRs open:** 1 — **STILL NEEDS DECISION**

> **PR #1** — *"Add Cloudflare Workers configuration"* (Cloudflare bot, opened 2026-03-26)
> Adds `wrangler.jsonc` for static Workers deployment. Merge to enable Cloudflare versioned deploys; close to keep current setup.

### index.html
- Status: **VALID** (1,607 lines, DOCTYPE present, `</html>` closes correctly)
- Single-page tab app — all 8 pages render in-page, hero image base64-embedded, no broken local refs

### Carried Action Items
- [ ] **Decide on Cloudflare Workers PR #1** — merge or close

---

## Summary
- USS Academy had a TCPA compliance day. All forms updated, ToS Section 12 added. Site is clean — no broken links, all images present.
- CityOne is stable and unchanged since 3/28. Bot PR #1 still pending a decision.
- No open issues on either repo.
