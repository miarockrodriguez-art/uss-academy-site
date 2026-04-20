# WEEKLY EMPIRE REPORT
**POLY — Chief of Staff, MFS Empire**
**Report Period:** April 13 – April 20, 2026
**Generated:** 2026-04-20
**Repos Covered:** `uss-academy-site` · `cityone-transportation-site`

---

## EXECUTIVE SUMMARY

- **USS Academy had its single most productive week on record** — 67 commits transformed the site with a full calendar booking system, 30-page Twitter Card rollout, 11 pages expanded to 1,200+ words each, 12 images renamed for SEO, and every orphan page eliminated. The site is now audit-clean and conversion-ready.
- **CityOne Transportation went live with full email automation** — all 3 forms (quote, contact, reservation) now fire to `bookmyride@cityonetransportation.com` via EmailJS, an admin control panel was built, and mobile navigation was added; however the site is **missing all SEO meta tags** (description, canonical, OG, Twitter Card, analytics) — this is the empire's #1 open issue.
- **Combined: 82 commits, ~42 files changed, 8,000+ lines added across both properties** — the empire's digital infrastructure made a generational leap this week.

---

## CHANGES THIS WEEK

### USS ACADEMY — `uss-academy-site`
**Total commits: 67** | **Period: Apr 13–20**

#### Calendar & Booking System
- Built `calendar.html` from scratch — full monthly grid with 91 class dates across Apr–Dec 2026, color-coded by tier (CWP, Beginner, Advanced, Tactical, Special), animated shield watermark, today highlighting
- Wired 28+ Book Now buttons to GoHighLevel booking widgets (`api.leadconnectorhq.com`)
- Added dynamic next-class-date logic to schedule cards — auto-advances as dates pass
- Pinned "Book a Call" + "Ladies Day" cards at top; all others sort chronologically
- Replaced show/hide toggle with scrollable 640px container with gold scrollbar
- Added `calendar.html` to `sitemap.xml`

#### Sitewide SEO Push
- **Twitter Card meta tags** added to all 30 HTML pages
- **FAQPage JSON-LD schema** added to 4 pages: service-areas (4 Q&A), waivers (8 Q&A), gallery (4 Q&A), refund-policy (4 Q&A)
- **12 images renamed** from generic/unnamed to keyword-rich filenames (e.g., `USS+ACADEMY-CCW` → `uss-academy-ccw-class-orlando-group`)
- Fixed 7 audit items: H1 added to gallery, canonical/OG/Twitter on calendar, canonicals on 3 waiver pages, og:image on share.html, calendar added to sitemap, duplicate privacy-policy.html deleted
- GA4 (`G-H3Q129SS5F`) added to `calendar.html`
- Phone deduplication in schema: removed duplicate telephone from service-areas JSON-LD

#### Content Expansion (11 Thin Pages → 1,200+ Words)
| Page | Before | After |
|------|--------|-------|
| compete.html | 729 words | 2,014 words |
| host-a-class.html | 768 words | 1,953 words |
| waivers.html | 864 words | 1,527 words |
| service-areas.html | 1,143 words | 1,297 words |
| terms.html | 1,165 words | 1,295 words |
| 6 regional pages | 796–946 words | 2,059–2,241 words |

#### Navigation & Internal Linking
- **Zero orphan pages** — fixed `compete.html` and `host-a-class.html` nav links across all 29 content pages
- Added waiver form links from `waivers.html` → 3 waiver sub-pages
- Blog and Share pages: full 14-link nav matching `index.html` exactly
- Gallery and Service Areas: full nav + brand fonts/colors

#### Sitewide Phone Number Correction
- Replaced `800-508-8772` with `407-305-8335` — **429 replacements across 37 files**
- Removed `(USSA)` label from phone number — **55 instances across 15 files**
- Cleaned up duplicate phone in hero and announcement banner

#### UI & Brand Refinements
- Gold particle network animation on hero section (tactical targeting grid)
- Count-up animation on stat numbers (29,000 / 27 / 4.9 / 5.0)
- Card hover effects: gold glow + 4px lift on course cards
- 2px gold top border on section headings
- Hero gradient overlay + warm gold radial tint on instructor section
- Sticky call button: clipped corners, top-right fully filled
- All gold CTA buttons: clipped-corner `clip-path` styling
- Calendar card hover: gold left border, dark drop shadow, −4px lift
- Consolidated 2 testimonial sections into 1 with 6 reviews + Submit button
- Swapped nav order: Schedule first, Courses second

#### New Pages & Files
- `404.html` — branded navy/gold 404 with shield logo, clipped-corner buttons, schedule CTA
- `_headers` — security headers file (CSP, X-Frame-Options, etc.)
- Exit intent popup restyled to match USS Academy brand (shield logo, navy/gold, clipped button)
- Live Google Reviews feed: 4+ star reviews, clipped corner cards, auto-fetch from Places API

#### Mobile Fix
- `overflow-x: hidden` + `max-width: 100%` applied to all 37 HTML files — eliminates horizontal scroll on mobile

---

### CITYONE TRANSPORTATION — `cityone-transportation-site`
**Total commits: 15** | **Period: Apr 14 + Apr 20**

#### Email Automation — All 3 Forms Live
- Wired **quote form**, **contact form**, and **reservation form** to EmailJS
- Service: `service_hexohos` (Microsoft 365), Template: `template_k13dd9n`
- All submissions route to `bookmyride@cityonetransportation.com`
- Fixed template variable mapping: `from_name`, `from_email`, `phone`, `pickup_location`, `destination`, `date`, `time`, `passengers`, `message`, `reservation_number`
- Fixed `ReferenceError` — undefined `pickup` variable → corrected to `dest`
- Fixed EmailJS init race condition: removed `defer`, moved to `DOMContentLoaded`
- Added full debug logging (params, success, error status/text on all 3 forms)
- Reservation success heading changed from "Confirmed" → "Submitted" (accurate expectation)

#### Admin Control Panel (`admin.html`)
- Password-protected admin panel created
- Controls: announcement ticker (on/off + text), emergency banner (on/off + text + color)
- Pricing editor for all hotel rate tables
- Wired to main site via localStorage

#### Pricing & Content Updates
- All hotels alphabetized within Disney, Universal, and SeaWorld sections
- Port Canaveral section added to Hotels pricing (10 rate fields)
- Removed `$100 administrative fee` language
- Added service disclaimer

#### Mobile Navigation
- Hamburger menu added for viewport < 768px (animated → X icon)
- Fixed white gap below mobile header (positioning conflict with fixed nav)

---

## ISSUES FOUND

### CRITICAL

#### 1. CityOne — Missing ALL SEO Meta Tags
**File:** `cityone-transportation-site/index.html`
**Status:** 🔴 Critical
The CityOne homepage is entirely missing:
- `<meta name="description">` — Google will auto-generate a snippet (bad)
- `<link rel="canonical">` — duplicate content risk
- All Open Graph tags (`og:title`, `og:description`, `og:image`) — social shares show nothing
- Twitter Card tags — no Twitter preview
- Google Analytics / GA4 — zero conversion tracking

CityOne is essentially invisible to SEO and untracked for conversions.

#### 2. CityOne — Admin Password in Git History
**Commit:** `8d31c40` (2026-04-20T06:55:54Z)
**Status:** 🔴 Security — Cannot be undone
Commit message includes: `Password: #November302013` — this is now permanently readable in the public git history. The password must be rotated immediately. Consider environment-based auth or a proper backend for admin access.

---

### MODERATE

#### 3. USS Academy — Duplicate Phone in Calendar Notice Bar
**File:** `calendar.html` (notice bar)
**Status:** 🟡 Visual Bug
The notice bar reads: `...| 407-305-8335 | 407-305-8335 | support@ussacademy.org` — the phone number appears twice. One instance should be removed.

#### 4. USS Academy — `share.html` Canonical URL Missing `.html`
**File:** `share.html`
**Status:** 🟡 Minor SEO
Canonical is set to `https://www.ussacademy.org/share` (no extension) while all other pages use `.html`. If the server doesn't redirect `/share` → `/share.html`, this creates a canonical mismatch.

#### 5. CityOne — EmailJS Public Key in Git History
**Commit:** `fec57845b` (2026-04-20)
**Status:** 🟡 Security Note
The EmailJS public key (`URLtKQDq3xZsiz7HL`) and service ID are committed to public git history. While EmailJS public keys are designed to be client-side, anyone can use this key to send from your EmailJS account. Consider rate limiting in your EmailJS dashboard.

---

### MINOR

#### 6. USS Academy — Scroll Animation Reverted Twice
Two animation commits were pushed then reverted within hours (scroll fade-in, gold underline on stats) suggesting feature decisions need to be validated locally before commit. Creates noise in git history.

#### 7. USS Academy — `index.html` Size (339KB)
`index.html` is 339KB — very large for a single HTML file. While functional, this may affect Time to First Byte on slower connections. Future consideration: split schedule data into a JSON file loaded async.

#### 8. CityOne — `admin.html` Has No Auth Beyond Password Prompt
The admin panel uses a simple JS `prompt()` password check — this is client-side only and bypassable. Acceptable for a private tool but worth noting if the site ever goes fully public.

---

## SEO META TAG AUDIT

### USS Academy (`uss-academy-site`) — 30 pages

| Tag | Status |
|-----|--------|
| `<title>` | ✅ All pages |
| `<meta name="description">` | ✅ All pages |
| `<link rel="canonical">` | ✅ All pages |
| `og:title` / `og:description` / `og:image` | ✅ All pages |
| `twitter:card` / `twitter:title` / `twitter:image` | ✅ All 30 pages (added this week) |
| FAQPage JSON-LD | ✅ 4 pages |
| BreadcrumbList JSON-LD | ✅ share.html + others |
| LocalBusiness JSON-LD | ✅ index.html |
| GA4 (`G-H3Q129SS5F`) | ✅ All pages |
| Sitemap | ✅ 30 URLs in sitemap.xml |
| robots.txt | ✅ Present |

**USS Academy SEO Grade: A** — Fully equipped. No missing tags.

### CityOne Transportation (`cityone-transportation-site`) — 1 public page

| Tag | Status |
|-----|--------|
| `<title>` | ✅ Present ("Cityone Transportation — The Blend") |
| `<meta name="description">` | ❌ MISSING |
| `<link rel="canonical">` | ❌ MISSING |
| `og:title` / `og:description` / `og:image` | ❌ MISSING |
| `twitter:card` | ❌ MISSING |
| JSON-LD schema | ❌ MISSING |
| GA4 / Analytics | ❌ MISSING |
| Sitemap | ❌ MISSING |
| robots.txt | ❌ MISSING |

**CityOne SEO Grade: D** — Title only. Site is invisible to search engines and untracked.

---

## TODO & PLACEHOLDER CONTENT AUDIT

**USS Academy:** ✅ Zero TODO comments, zero placeholder text found across all reviewed pages. Codebase is clean.

**CityOne:** ✅ No TODO comments found. Site content appears production-ready; gaps are infrastructure (SEO/tracking), not content.

---

## INTERNAL LINK AUDIT — USS ACADEMY

- All 14 nav links present and consistent across: `calendar.html`, `share.html`, `blog.html`, `waivers.html`, `gallery.html`, `service-areas.html`
- `compete.html` and `host-a-class.html` orphan status: **RESOLVED this week** (nav links added across all 29 subpages)
- 3 waiver sub-pages (`waiver-class-registration.html`, `waiver-exam-registration.html`, `waiver-range.html`) now linked from `waivers.html`
- `404.html` links back to schedule and home — proper UX recovery
- **Zero known orphan pages** as of Apr 18, 2026

---

## RECOMMENDATIONS FOR NEXT WEEK

### Priority 1 — CityOne SEO Emergency
**Add full SEO head block to `cityone-transportation-site/index.html`:**
```html
<meta name="description" content="Cityone Transportation — premium car service for Orlando theme parks, hotels, and Port Canaveral. Book online or call for a quote.">
<link rel="canonical" href="https://www.cityonetransportation.com/">
<meta property="og:title" content="Cityone Transportation — The Blend">
<meta property="og:description" content="Premium car service. Disney, Universal, SeaWorld, Port Canaveral. Book online.">
<meta property="og:image" content="https://www.cityonetransportation.com/og-image.jpg">
<meta property="og:url" content="https://www.cityonetransportation.com/">
<meta name="twitter:card" content="summary_large_image">
```
Also add GA4 tracking and a `robots.txt` + `sitemap.xml`.

### Priority 2 — Rotate CityOne Admin Password
The password `#November302013` is in public git history. Create a new password and consider using environment-based authentication or Netlify Identity instead of a JS prompt.

### Priority 3 — Fix Calendar Notice Bar Duplicate Phone
Remove the second `| 407-305-8335 |` instance from `calendar.html` notice bar — simple one-line fix.

### Priority 4 — Canonicalize `share.html`
Change `<link rel="canonical" href="https://www.ussacademy.org/share">` to `https://www.ussacademy.org/share.html` to match all other pages, OR add a redirect in `_redirects`.

### Priority 5 — USS Academy Blog Content
`blog.html` exists at 119KB — verify it contains real published posts and is not a shell. If blog posts are present, add `BlogPosting` JSON-LD schema to each.

### Priority 6 — Google Reviews API Key Audit
The Google Reviews feed on the homepage fetches live data from Places API. Confirm the API key has domain restrictions set in Google Cloud Console to prevent unauthorized usage.

### Priority 7 — CityOne Sitemap & Robots
Create `sitemap.xml` and `robots.txt` for CityOne. Even a single-page site benefits from sitemap submission to Google Search Console.

### Priority 8 — Performance: USS Academy `index.html`
At 339KB, `index.html` is large. Consider:
- Moving schedule card data to an external JSON (loaded async)
- Lazy-loading images below the fold
- This is medium-term, not urgent

---

## COMMIT STATISTICS

| Metric | USS Academy | CityOne | Total |
|--------|-------------|---------|-------|
| Commits (7 days) | 67 | 15 | **82** |
| New files created | ~3 (calendar, 404, _headers) | ~1 (admin.html) | ~4 |
| Files modified | 37+ | 2 | **39+** |
| Estimated lines added | ~7,000+ | ~1,200+ | **~8,200+** |
| Estimated lines removed | ~1,800+ | ~200+ | **~2,000+** |
| SEO tags added to pages | 30 (Twitter Cards) | 0 | 30 |
| Booking integrations | 28+ buttons wired | 3 forms wired | 31 |

---

## EMPIRE HEALTH SCORECARD

| Property | SEO | Content | Booking/Conversion | Mobile | Security |
|----------|-----|---------|-------------------|--------|----------|
| USS Academy | A | A | A | A | B+ |
| CityOne | D | B+ | A | B+ | C |

**Overall Empire Grade: B+** — USS Academy is firing on all cylinders. CityOne needs its SEO foundation installed before its email automation gains traction.

---

*Report generated by POLY, Chief of Staff — MFS Empire*
*Next report: 2026-04-27*
