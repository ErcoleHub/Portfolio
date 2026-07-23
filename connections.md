# connections.md

Tools, credentials, and integrations confirmed working in this project.

## Active MCP Servers

| Server | Purpose |
|--------|---------|
| n8n | Fetch workflow structures (WF1–WF8) for case study content |

## Wired Integrations

| # | Domain | Tool | Mechanism | Auth | Last checked |
|---|--------|------|-----------|------|--------------|
| 1 | Scheduling | Google Calendar | Booking link in "Request a Demo" CTA | Public link (no auth) | 2026-06-16 |
| 2 | Hosting | **Vercel** (NOT GitHub Pages) | push to `main` auto-deploys to **www.ercoleautomations.com** (primary) in ~30-60s | GitHub `ErcoleHub/Portfolio` → Vercel | 2026-07-23 |

> **Hosting reality, verified 2026-07-23.** The live site is on **Vercel**; primary domain is **www.ercoleautomations.com** (apex `ercoleautomations.com` 308-redirects to www). Pipeline: this repo → GitHub `ErcoleHub/Portfolio` → Vercel auto-deploy on push to `main`. It is **not** GitHub Pages. **`justinercole.com` and `www.justinercole.com` now 307-redirect to `www.ercoleautomations.com`** (path preserved). GoDaddy forwarding for ercoleautomations.com is OFF and its DNS points at Vercel; all Microsoft 365 email records were left untouched. SourceSifterr is live at `ercoleautomations.com/sourcesifterr`.
