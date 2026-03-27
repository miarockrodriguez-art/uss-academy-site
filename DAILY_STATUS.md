# MFS Empire — Daily Status Report
**Date:** 2026-03-27  
**Chief of Staff:** POLY

---

## USS Academy Site

**Status: ACTIVE — 2 commits today**

| Commit | Summary |
|--------|---------|
| v9.1 (today 06:27) | CCW→CWP rename sitewide, added Civilian Patrol Rifle class (AR-15/AK-47, 300m), added PPC Pistol Caliber Carbine class (100m), LE Firearms Instructor credential, competitive shooting + hunting options, contact form updated |
| v9.0 (yesterday 06:37) | Full 12-page site build — courses, schedule, contact, waivers, compete, host-a-class, blog, terms, privacy |
| Cloudflare deploy (yesterday 07:03) | GitHub Actions workflow added for Cloudflare Pages auto-deploy |

**File Structure: OK**
- `index.html` — present (225KB)
- 12 HTML pages total — all present
- `images/` — 22 images present (PNG, WEBP, JPG, favicon)
- `_redirects`, `netlify.toml`, `.github/` — all present

**Issues / PRs:** None open

**Flags:**
- Cloudflare Pages deploy workflow requires secrets: `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` must be set in repo settings to activate auto-deploy
- Image filenames still contain "CCW" (e.g. `USS+ACADEMY-+CCW+IN+ORLANDO*.webp`) — filenames only, not visible to users; no broken links

---

## Cityone Transportation Site

**Status: ACTIVE — 2 commits today**

| Commit | Summary |
|--------|---------|
| v7 (today 06:22) | Phones updated → Main: (407) 509-0880 / Line 2: (407) 963-8278. All old numbers removed. Slogan "Relax and Enjoy the Ride" added to header + footer. Rideshare renamed (Private Transfer → Orlando/Kissimmee Transfers, KSC Transfer → Kennedy Space Center Transfers). "Powered by Phoenix Blueprint" footer credit added. |
| v6 (today 02:20) | 16 changes — pricing tabs fixed, airline dropdown (40+ MCO airlines), form fields updated, logo C1X→C1T |

**File Structure: OK**
- `index.html` — present (299KB, single-file site with inline CSS/JS)

**Issues:** None open

**PRs: 1 OPEN — ACTION NEEDED**
- **PR #1** from Cloudflare bot: "Add Cloudflare Workers configuration"
  - Adds `wrangler.jsonc` for Cloudflare Workers/Pages auto-deploy
  - Framework: static | Deploy: `npx wrangler deploy`
  - **Decision required:** Merge to enable Cloudflare auto-deploy, or close if deploying elsewhere

---

## Summary

| Repo | Health | Open Issues | Open PRs | Action Needed |
|------|--------|-------------|----------|---------------|
| uss-academy-site | ✅ Healthy | 0 | 0 | Set Cloudflare secrets in repo settings |
| cityone-transportation-site | ✅ Healthy | 0 | 1 | Review/merge or close PR #1 (Cloudflare Workers) |

Both sites committed and active today. No broken links or missing files detected.
