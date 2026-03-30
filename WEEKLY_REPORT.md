# WEEKLY EMPIRE REPORT
**Prepared by:** POLY — Chief of Staff, MFS Empire  
**Reporting Period:** 2026-03-24 through 2026-03-30  
**Report Date:** 2026-03-30  
**Properties Audited:** `uss-academy-site` · `cityone-transportation-site`

---

## EXECUTIVE SUMMARY

- **Explosive build week:** 60 commits across both empire properties in 7 days — USS Academy alone received 50 commits transforming it from a single-page site into a 28-page SEO ecosystem with full schema markup, 186-photo gallery, 31 classes with Stripe/waitlist, and an image library compressed from 575MB to 31MB.
- **Critical revenue leak identified:** ALL five CRM webhook URLs on USS Academy are still placeholder strings (`PASTE_WEBHOOK_URL_HERE`) — contact forms, waiver signups, waitlist submissions, alumni enrollments, and Ladies Day signups are accepting data from visitors but sending it **nowhere**. No leads are being captured right now.
- **Both sites flying blind:** Neither USS Academy nor CityOne Transportation has Google Analytics installed. Traffic, conversion events, and booking behavior are generating zero data.

---

## CHANGES THIS WEEK

### USS Academy (`uss-academy-site`) — 50 commits

#### Site Architecture
- **28 total HTML pages** now in repo (was ~2 at start of week)
- Gallery separated into standalone `gallery.html` (186 photos, 6-column grid)
- New pages launched: `submit-photo.html`, `service-areas.html`, `ember-iron.html`, `waivers.html`, `waiver-class-registration.html`, `waiver-exam-registration.html`, `waiver-range.html`, `host-a-class.html`, `compete.html`
- Sitemap expanded: 17 → 21 URLs
- Google Search Console verification file added (`google9612a65910aee27d.html`)

#### SEO Push
- Rich results schema deployed: **Organization**, **10 Courses**, **10 FAQs** (`application/ld+json`)
- Event schema intentionally removed (no confirmed class dates yet — correct call)
- SEO keyword Phase 2: all 6 tiers, all 6 regional pages, 18 blog posts updated
- Homepage title + meta description rewritten with primary keywords
- **6 regional landing pages** launched with unique content, LocalBusiness schema, and city-grid coverage:
  - `central-florida-firearms-training.html`
  - `tampa-bay-firearms-training.html`
  - `south-florida-firearms-training.html`
  - `northeast-florida-firearms-training.html`
  - `northwest-florida-firearms-training.html`
  - `space-coast-firearms-training.html`
- **15 new blog posts** (total 18) covering CWP guides, FL statutes, regional keywords, and lifestyle topics

#### Functionality
- 31 classes renumbered continuously (Tier 1–6 + Standalone: #01–#31)
- Stripe payment links live on: Tier 4 (2 classes), Tier 5 Night Vision, Tier 6 (3 options)
- **Waitlist system** deployed: 28+ buttons + modal form (Name, Email, Phone, Class Name)
- All 31 class disclaimers standardized: per-person pricing + session types + contact info
- CWP/BOOK NOW buttons replaced all "Inquire" and "Register & Pay" CTAs
- FL Statute 790 + FL Statute 776 hyperlinked on Self-Defense Seminar section
- Student Check-In form: selfie upload removed, instructor/location dropdowns added, form header updated
- Submit Your Photo page: consent form with photo upload, GHL tags scaffolded
- Serving Those Who Serve section: Military, Veterans, LE, First Responders, UCF, Rollins
- Partners section: USSA Group first, USCCA second, NRA badge → clickable link

#### Performance & Accessibility
- **Image compression: 575MB → 31MB** (543MB saved, 197 images under 200KB each)
- Hero image preloaded; GPU carousel acceleration (`will-change: opacity`)
- **186 images renamed** with SEO keyword filenames
- Accessibility overhaul: 84 fixes — ARIA labels, skip links, focus-visible, `prefers-reduced-motion`, color contrast improvements
- **URGENT FIX shipped:** Cloudflare email-decode script removed — was causing random Google.com redirects
- Favicon fixed: USS Academy shield SVG + clean `.ico` at root
- Hero upgraded to 3-image auto-carousel (5s crossfade)

#### CRM Infrastructure (scaffolded but not live)
- CRM webhook config block deployed in `index.html`
- Supports: GoHighLevel, Zapier, Make, WordPress, or any endpoint
- 5 webhook slots: WAIVER, CONTACT, REGISTER, ALUMNI, LADIES
- `CRM.LIVE = false` — banner suppressed until webhooks are connected

---

### CityOne Transportation (`cityone-transportation-site`) — 10 commits

- **v5 → v6 → v7** iterations shipped
- Phone numbers finalized: Main `(407) 509-0880` · Line 2 `(407) 963-8278` — all old numbers removed
- Email updated: `Bookmyride@cityonetransportation.com`
- Slogan **"Relax and Enjoy the Ride"** added to all 8 page tabs (9 total instances)
- Slogan promoted: tiny 8px header → prominent 28px Georgia serif italic in every hero
- Rate corrections: SeaWorld/Convention `$85→$75` / `$110→$100`
- Port Canaveral rates confirmed: MCO `$165/$185`, SFB `$235/$250`, Amtrak `$195/$220`
- Holiday rate disclaimer added to all pricing tables
- Rideshare renamed: "Private Transfer" → "Orlando/Kissimmee Transfers" · "KSC Transfer" → "Kennedy Space Center Transfers"
- Airline dropdown: 40+ MCO airlines added to reservation form
- Duplicate rate panel IDs fixed (tabs now function independently)
- "Powered by Phoenix Blueprint" footer credit added (subtle, 10px low-opacity)
- Broken HTML repaired (restored from clean commit after `sed` corruption)

---

## ISSUES FOUND

### CRITICAL — Revenue/Data at Risk

| # | Property | Issue | Impact |
|---|----------|-------|--------|
| C-1 | USS Academy | **ALL 5 CRM webhooks are placeholder strings.** `PASTE_WAIVER_WEBHOOK_URL_HERE`, `PASTE_CONTACT_FORM_WEBHOOK_URL_HERE`, `PASTE_REGISTRATION_WEBHOOK_URL_HERE`, `PASTE_ALUMNI_SIGNUP_WEBHOOK_URL_HERE`, `PASTE_LADIES_DAY_SIGNUP_WEBHOOK_URL_HERE` — all forms show success UX but data is lost. | Every lead, waiver, registration, alumni, and Ladies Day signup is being dropped. |
| C-2 | USS Academy | **No Google Analytics installed.** No `gtag.js`, no GA4 measurement ID. Commit note from 3/29 flagged `GA_MEASUREMENT_ID` as pending. | Zero traffic data, zero conversion tracking, zero funnel visibility. |
| C-3 | CityOne | **No Google Analytics installed.** No tracking of any kind on the site. | Cannot measure bookings, traffic sources, or form submissions. |
| C-4 | CityOne | **Zero SEO meta tags** — no `<meta name="description">`, no OG tags, no canonical, no schema markup. Title is generic: "Cityone Transportation — The Blend". | Site is effectively invisible to search engines and shows blank/generic previews on social sharing. |

### HIGH — SEO/Visibility Gaps

| # | Property | Issue |
|---|----------|-------|
| H-1 | USS Academy | **`og:image` missing on homepage.** OG title and description are present, but no `og:image` tag. Facebook, LinkedIn, iMessage shares will show no preview image. |
| H-2 | USS Academy | **`ember-iron.html` has no meta description, no OG tags, no canonical.** Placeholder page with no SEO scaffolding. |
| H-3 | USS Academy | **Regional pages missing OG tags** (checked `central-florida-firearms-training.html` — has title/description/canonical/schema but no `og:title`, `og:description`, or `og:image`). |
| H-4 | USS Academy | **Event schema removed** — intentionally deferred until Josh provides class schedule dates. No Event rich results in GSC until restored. |

### MEDIUM — Content Placeholders

| # | Property | Issue |
|---|----------|-------|
| M-1 | USS Academy | Google My Business review feed: connector pending setup — shows placeholder message to visitors |
| M-2 | USS Academy | Team logo in Partners section: "Coming Soon" badge visible on live site |
| M-3 | USS Academy | 32 videos catalogued in gallery but **none are hosted** — 2.7GB total, needs YouTube/CDN upload |
| M-4 | USS Academy | `submit-photo.html`: GHL webhook is `console.log` only — photo submission data not reaching any CRM |
| M-5 | USS Academy | `IMG_4151` still missing — noted in commit history as "Mia to provide file" — image slot may be empty |
| M-6 | CityOne | Multiple "coming soon" and "placeholder" instances visible in site content |

### LOW — Polish Items

| # | Property | Issue |
|---|----------|-------|
| L-1 | USS Academy | `CRM.LIVE = false` flag in place — once webhooks go live, flip to `true` to show CRM-connected banner |
| L-2 | USS Academy | Social handle links use `facebook.com/ussacademy`, `instagram.com/ussacademy`, etc. — confirm these handles are claimed and active |
| L-3 | CityOne | All-in-one single-file architecture with JS tabs is convenient but limits SEO — each "page" shares one URL, preventing individual indexing of service types |

---

## HTML STRUCTURE AUDIT

| Page | DOCTYPE | `lang="en"` | `<title>` | `<meta desc>` | Canonical | Schema | OG Tags | Status |
|------|---------|-------------|-----------|---------------|-----------|--------|---------|--------|
| `index.html` (USS) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | Partial (no image) | ⚠️ |
| `central-florida-*.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ⚠️ |
| `ember-iron.html` | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| `submit-photo.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ⚠️ |
| `blog.html` | ✅ | ✅ | ✅ | (assumed) | (assumed) | N/A | N/A | ⚠️ |
| `index.html` (CityOne) | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |

**Internal links audited:** All regional pages link back to `https://ussacademy.org` with full absolute URLs. No broken internal links detected in sampled pages. CityOne uses JS tab navigation (no `<a href>` internal links to break).

---

## RECOMMENDATIONS FOR NEXT WEEK

### Priority 1 — Fix the Revenue Leak (Do This First)
1. **Paste CRM webhook URLs into `index.html`** — open the `CRM` config block, replace all 5 `PASTE_*_HERE` strings with live GoHighLevel (or Zapier) webhook URLs. Set `CRM.LIVE = true`. Every form on the site — contact, waiver, registration, alumni, Ladies Day — will immediately start capturing leads.
2. **Fix `submit-photo.html` GHL webhook** — replace `console.log` with actual `fetch()` POST to a GHL webhook so photo submissions reach the CRM.

### Priority 2 — Install Analytics
3. **Add GA4 to USS Academy** — create a GA4 property, get the `G-XXXXXXXXXX` measurement ID, add `gtag.js` to the `<head>` of `index.html` (and ideally all other pages via a shared script tag or Netlify inject).
4. **Add GA4 to CityOne** — same process. At minimum add a `<meta name="description">` and basic OG tags immediately so the site isn't invisible on social.

### Priority 3 — SEO Quick Wins
5. **Add `og:image` to USS Academy homepage** — pick the best hero photo (e.g. `uss-academy-ranch.jpg`), host it at a permanent URL, add `<meta property="og:image" content="...">`. Also add OG tags to all 6 regional pages.
6. **Add meta description and OG tags to `ember-iron.html`** — minimal effort, high impact for when Ember & Iron launches.
7. **Add full SEO head to `cityone-transportation-site/index.html`** — meta description, OG title/desc/image, canonical, and a basic LocalBusiness schema block. This alone will unlock social sharing previews and search engine indexing.

### Priority 4 — Content Completions
8. **Upload 32 videos to YouTube** — create a USS Academy YouTube channel, upload all 32 training videos, update `gallery.html` video card placeholders with real `<iframe>` embeds.
9. **Get Josh's class schedule** — once confirmed, restore Event schema to `index.html` with real `startDate`/`endDate` values to unlock Event rich results in Google Search Console.
10. **Provide `IMG_4151`** — confirm whether this image exists and upload to the `images/` folder.
11. **Claim social handles** — verify `@ussacademy` is active on Facebook, Instagram, TikTok, and Twitter before the social links in the footer go live in front of 29,000+ students.

### Priority 5 — CityOne Architecture (Future Sprint)
12. Consider splitting CityOne's tab-based single-page design into separate HTML files per service (rideshare, fleet, destinations, etc.) to allow individual URL indexing by Google.

---

## COMMIT METRICS

| Property | Commits This Week | Est. Files Touched | Key File Sizes |
|----------|------------------|--------------------|----------------|
| `uss-academy-site` | 50 | 30+ HTML + 186 images | `index.html` 277KB · `blog.html` 101KB |
| `cityone-transportation-site` | 10 | 1 HTML | `index.html` 301KB |
| **EMPIRE TOTAL** | **60** | **31+ files** | — |

---

## EMPIRE HEALTH SCORECARD

| Category | USS Academy | CityOne |
|----------|-------------|----------|
| HTML Structure | ✅ Valid | ✅ Valid |
| Meta Description | ✅ (main pages) | ❌ Missing |
| OG / Social Tags | ⚠️ Partial | ❌ Missing |
| Schema Markup | ✅ Deployed | ❌ Missing |
| Sitemap | ✅ 21 URLs | ❌ None |
| Google Analytics | ❌ Not installed | ❌ Not installed |
| CRM / Lead Capture | ❌ Placeholders only | ❌ Not connected |
| Internal Links | ✅ Clean | ✅ (JS tabs) |
| Page Speed (images) | ✅ Compressed | ⚠️ Unknown |
| Accessibility | ✅ 84 fixes applied | ⚠️ Not audited |

---

*POLY — Chief of Staff, MFS Empire*  
*Automated report generated 2026-03-30*  
*Next report: 2026-04-06*
