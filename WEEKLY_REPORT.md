# WEEKLY EMPIRE REPORT
**Prepared by:** POLY — Chief of Staff, MFS Empire  
**Reporting Period:** 2026-03-30 through 2026-04-06  
**Report Date:** 2026-04-06  
**Properties Audited:** `uss-academy-site` · `cityone-transportation-site`

---

## EXECUTIVE SUMMARY

- **USS Academy had its biggest content and infrastructure week yet:** 49 commits shipped GA4 tracking to all 28 pages, wired 11 forms to live GHL webhooks, launched 8 new SEO blog articles, added 6 new landing pages (3 languages + 3 keyword pillars), deployed a slide-in lead capture form, and added OG images site-wide — the academy is now a fully instrumented, lead-capturing machine.
- **CityOne Transportation has a silent critical failure:** The reservation form at the core of the site uses EmailJS with unconfigured placeholder credentials (`YOUR_EMAILJS_PUBLIC_KEY`, `YOUR_SERVICE_ID`, `YOUR_TEMPLATE_ID`). Every customer reservation since launch has triggered a success confirmation to the user but delivered zero notification to the operator. Additionally, the site has no analytics, no SEO meta tags, no sitemap, and no robots.txt.
- **Empire-wide infrastructure matured significantly this week:** BreadcrumbList and FAQPage schema deployed across 21+ USS Academy pages, robots.txt and sitemap verified, image compression saved hundreds of KBs, and a Cloudflare redirect loop was resolved — the academy is now technically sound and search-engine-ready.

---

## CHANGES THIS WEEK

### USS Academy (`uss-academy-site`) — ~49 commits

#### Lead Capture & CRM (RESOLVED from last week's critical C-1)
- **All 11 forms wired to live GHL webhook** — contact, waiver, class registration, alumni, Ladies Day, lead capture, and slide-in forms all now POSTing to GoHighLevel in production. Last week's critical revenue leak is sealed.
- **Slide-in lead capture form deployed to all 28 pages** — triggers at 50% scroll depth, collects name/email/phone, submits to GHL webhook.
- **Exit-intent popup deployed** — fires on cursor moving to browser chrome, captures leads before bounce.
- **`share.html`** (UGC page): student photo/video upload form with GHL webhook + QR code on homepage.

#### Analytics (RESOLVED from last week's critical C-2)
- **GA4 installed on all 28 pages** — measurement ID `G-H3Q129SS5F`. Empire is no longer flying blind on USS Academy.

#### Content — Blog Launch
- **8 new blog articles published** under `/blog/` subdirectory (2026-04-05):
  - `florida-concealed-carry-permit.html`
  - `armed-vs-unarmed-firearms-course.html`
  - `first-firearms-training-class.html`
  - `florida-firearms-safety-course.html`
  - `choose-firearms-instructor-central-florida.html`
  - `women-firearms-ccw-florida.html`
  - `florida-stand-your-ground-law.html`
  - `beginner-to-confident-firearms-journey.html`
- **`blog.html` updated** to index all 8 articles.
- All blog articles have: full SEO head, BreadcrumbList schema, BlogPosting schema, GA4, slide-in form, sticky Call Now button, Twitter card.

#### New Pages (6 total)
- **Language landing pages:** `espanol.html`, `portugues.html`, `kreyol.html` — serving Spanish, Portuguese, and Haitian Creole-speaking students.
- **SEO keyword pillars:** `ccw-near-me.html`, `best-gun-class-orlando.html`, `first-time-buyer.html`.

#### SEO & Schema
- **OG image deployed to 21+ pages** — `og-image.jpg` (1200x630 branded) added.
- **BreadcrumbList schema** added to 21+ pages.
- **FAQPage schema** confirmed on 10 pages.
- **Google Search Console meta tag** added and GSC verification confirmed (`google9612a65910aee27d.html`).
- **Canonical URLs** verified site-wide using `https://www.ussacademy.org/` prefix.
- **Cloudflare redirect loop resolved** — `www` redirect rule removed from `_redirects` (was causing infinite loop).
- **Robots.txt and sitemap.xml** confirmed present and valid.
- **Image compression** — ballistics image: 727KB → 90KB; PCC permit image: 2.1MB → 100KB.

#### UX / Conversion
- **Sticky "Call Now | 1-800-508-8772" button** deployed across all pages (fixed top-right, gold on navy).
- Blog nav link styling polished (2026-04-06).

---

### CityOne Transportation (`cityone-transportation-site`) — 6 commits (all 2026-03-27 to 2026-03-28)

**Note:** Zero commits from 2026-03-29 through 2026-04-06. All activity was concentrated at the tail end of last week's reporting window.

- Slogan deployed to all 8 page tabs (9 total instances) as 28px Georgia serif italic in hero sections.
- "Powered by Phoenix Blueprint" footer credit added.
- Broken HTML restored from clean commit after prior corruption.
- Rates disclaimer added to Port Canaveral section.
- Service type, rates, email, and slogan placement updated.

---

## ISSUES FOUND

### CRITICAL — Production Failures

| # | Property | Issue | Impact |
|---|----------|-------|--------|
| C-1 | CityOne | **EmailJS NOT CONFIGURED.** Credentials `YOUR_EMAILJS_PUBLIC_KEY`, `YOUR_SERVICE_ID`, `YOUR_TEMPLATE_ID` are literal placeholder strings in production code. The reservation form shows a success card to customers but the operator receives zero notification. Every reservation since launch has been silently lost. | All reservation requests are lost. Revenue impact unknown but active. |
| C-2 | CityOne | **No Google Analytics or any tracking.** Zero data collected on traffic, reservations, form conversions, or bounce rate. | No performance visibility whatsoever. |

### HIGH — SEO / Visibility

| # | Property | Issue |
|---|----------|-------|
| H-1 | CityOne | **No `<meta name="description">`** — site is invisible/incomplete to search engines. |
| H-2 | CityOne | **No OG tags** — `og:title`, `og:description`, `og:image` all missing. Social shares show blank previews. |
| H-3 | CityOne | **No canonical tag** — search engines have no authoritative URL signal. |
| H-4 | CityOne | **No sitemap.xml** — pages cannot be efficiently crawled or indexed. |
| H-5 | CityOne | **No robots.txt** — no crawl instructions for search engines. |
| H-6 | CityOne | **Page `<title>` is a dev-facing name:** "Cityone Transportation — The Blend" — "The Blend" is the internal design concept. This exact string would appear in Google search results. |

### MEDIUM — Content / Polish

| # | Property | Issue |
|---|----------|-------|
| M-1 | USS Academy | **TBD event date** — "Ladies Day — Annual Event" calendar entry shows "TBD" to live visitors (`<div class="cal-month">TBD</div>`). Displayed publicly until a date is set. |
| M-2 | USS Academy | **Missing `twitter:card`** on `share.html`, `submit-photo.html`, and `privacy.html` — all other pages have it. Minor SEO hygiene gap. |
| M-3 | CityOne | **Social media links unverified** — Facebook, Instagram, Twitter/X, YouTube links exist in footer but account validity unconfirmed. |

### LOW — Architecture Notes

| # | Property | Issue |
|---|----------|-------|
| L-1 | CityOne | **Single-file SPA architecture** — all 7 "pages" share one URL via JS tab switching. Each service type (rideshare, fleet, destinations, etc.) cannot be individually indexed by search engines or deep-linked. |
| L-2 | USS Academy | **Blog articles use `href="/blog.html"`** for "Back to Blog" but canonical is `https://www.ussacademy.org/blog`. Functional if `_redirects` handles it, but worth confirming no 404 edge case. |

---

## HTML STRUCTURE AUDIT

### USS Academy

| Page | DOCTYPE | Meta Desc | og:title | og:image | Viewport | Canonical | GA4 | Twitter Card | TODO/Placeholder |
|------|---------|-----------|----------|----------|----------|-----------|-----|-------------|------------------|
| `index.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ 2x TBD (event date) |
| `blog.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | None |
| All 8 blog articles | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | None |
| `share.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ Missing | None |
| `submit-photo.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ Missing | None |
| `privacy.html` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ Missing | None |
| `privacy-policy.html` | ✅ | N/A | N/A | N/A | N/A | N/A | N/A | N/A | Redirect shell — by design |

**Broken internal links: NONE detected.** All 17+ internal page references verified against the repo file tree.

### CityOne Transportation

| Page | DOCTYPE | Meta Desc | og:title | og:image | Viewport | Canonical | GA4 | Twitter Card | TODO/Placeholder |
|------|---------|-----------|----------|----------|----------|-----------|-----|-------------|------------------|
| `index.html` | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | **CRITICAL: EmailJS credentials are placeholders** |

**Internal links:** Site uses JS tab navigation only (`showPage()` calls) — no traditional `href` internal links. Square payment link appears valid. Social links unverified.

---

## EMPIRE COMMIT METRICS

| Property | Commits This Week | New HTML Files | Key Changes |
|----------|------------------|----------------|-------------|
| `uss-academy-site` | ~49 | 15+ (6 pages + 8 blog + share) | GA4, GHL webhooks, blog, SEO, OG images |
| `cityone-transportation-site` | 6 | 0 | Slogan, footer credit, HTML repair |
| **EMPIRE TOTAL** | **~55** | **15+** | — |

**USS Academy file count:** 37 HTML files total (29 root + 8 blog articles)  
**CityOne file count:** 1 HTML file (301KB monolithic SPA)

---

## EMPIRE HEALTH SCORECARD

| Category | USS Academy | CityOne | vs. Last Week |
|----------|-------------|---------|---------------|
| HTML Structure | ✅ Valid | ✅ Valid | — |
| Meta Description | ✅ All pages | ❌ Missing | USS: improved |
| OG / Social Tags | ✅ All pages | ❌ Missing | USS: improved |
| Twitter Card | ⚠️ 3 pages missing | ❌ Missing | — |
| Schema Markup | ✅ Full | ❌ None | — |
| Sitemap | ✅ Present | ❌ None | — |
| Robots.txt | ✅ Present | ❌ None | — |
| Google Analytics | ✅ GA4 Live (all 28 pages) | ❌ None | USS: **FIXED** ✅ |
| CRM / Lead Capture | ✅ All 11 forms live | ❌ Broken (EmailJS) | USS: **FIXED** ✅ |
| Broken Internal Links | ✅ None | ✅ None (JS nav) | — |
| TODO / Placeholder Content | ⚠️ 1 (TBD event date) | ❌ Placeholder credentials in prod | — |
| Page Speed | ✅ Images compressed | ⚠️ Unknown | — |
| Accessibility | ✅ Audited | ⚠️ Not audited | — |

---

## RECOMMENDATIONS FOR NEXT WEEK

### Priority 1 — Fix CityOne Reservation System (URGENT)
1. **Configure EmailJS credentials** — replace `YOUR_EMAILJS_PUBLIC_KEY`, `YOUR_SERVICE_ID`, and `YOUR_TEMPLATE_ID` in `index.html` with real values from the EmailJS dashboard. Test a live form submission end-to-end. Alternatively, migrate reservation form to a GHL webhook (same pattern as USS Academy) for consistency across the empire.
2. **Fix `<title>`** — change from `"Cityone Transportation — The Blend"` to `"Cityone Transportation | Orlando Private Car & Airport Transfer Service"` or similar customer-facing copy.

### Priority 2 — CityOne SEO Minimum Viable Setup
3. **Add `<meta name="description">`** — single line, 150 chars, targeting Orlando airport transfer keywords.
4. **Add OG tags** — `og:title`, `og:description`, `og:image` (create a 1200x630 branded image). Unlocks social sharing previews immediately.
5. **Add canonical tag** — `<link rel="canonical" href="https://www.cityonetransportation.com/">` (or whatever the live domain is).
6. **Add GA4** — create a property, drop the measurement ID in. Zero visibility without this.
7. **Create `sitemap.xml` and `robots.txt`** — basic crawl infrastructure.

### Priority 3 — USS Academy Polish
8. **Set the Ladies Day date** — replace `TBD` in the `index.html` calendar with the actual date, or hide the entry until it is confirmed. Visitors are currently seeing "TBD" for an event.
9. **Add `twitter:card`** to `share.html`, `submit-photo.html`, and `privacy.html` — three-line fix on each.
10. **Confirm `/blog` clean URL redirect** in `_redirects` — blog articles link to `/blog.html` but canonical is `/blog`. Ensure no 404 edge case for the blog index.

### Priority 4 — Empire Growth
11. **Verify CityOne social handles** — confirm the Facebook, Instagram, Twitter/X, and YouTube accounts linked in the footer are active and claimed before driving traffic.
12. **USS Academy: upload videos to YouTube** — 32 training videos are in the repo at 2.7GB+ and are not yet embedded. Create a USS Academy YouTube channel, upload, and update `gallery.html` with real `<iframe>` embeds.
13. **USS Academy: set class schedule dates** — once Josh provides dates, restore Event schema to `index.html` to unlock Event rich results in Google Search Console.

---

*POLY — Chief of Staff, MFS Empire*  
*Report generated: 2026-04-06*  
*Next report: 2026-04-13*
