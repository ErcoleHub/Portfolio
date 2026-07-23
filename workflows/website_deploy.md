# Website Deploy Workflow

## Overview
Static portfolio site (`index.html`) → GitHub (`ErcoleHub/Portfolio`) → Vercel auto-deploy → live at **www.ercoleautomations.com**.
Every push to `main` triggers a live deploy in ~30 seconds.

## Domains (verified 2026-07-23)
- **Primary domain: `www.ercoleautomations.com`** — the canonical Production domain, served by **Vercel** from this repo. Apex `ercoleautomations.com` 308-redirects to it.
- **`justinercole.com` and `www.justinercole.com` now 307-redirect to `www.ercoleautomations.com`** (path preserved). Both are Vercel domains on this same project; they no longer serve content directly.
- GoDaddy `ercoleautomations.com` forwarding is OFF; DNS points at Vercel (A `@` → 216.198.79.1, CNAME `www` → `4d84ea7390e1fe85.vercel-dns-017.com`). All Microsoft 365 email records (MX, autodiscover, DKIM, DMARC, SRV) were left untouched.
- SourceSifterr is live at `ercoleautomations.com/sourcesifterr` (landing, `/walkthrough`, `/privacy`, `/terms`), migrated 2026-07-23. Still reachable via the justinercole.com redirect.

## Ongoing Editing Workflow

1. Open project in Claude Code (terminal: `claude` from this directory, or VS Code extension)
2. Describe the change in plain language:
   - "Update the hero headline to say X"
   - "Add a new project card to the work section"
   - "Change the accent color from gold to blue"
3. Claude Code creates a feature branch, edits `index.html`, commits, and pushes the branch
4. Vercel auto-generates a **preview URL** (e.g. `portfolio-abc123.vercel.app`) — review the change there
5. Approve ("looks good") or request changes
6. Once approved, Claude Code merges to `main` → Vercel deploys to production in ~30 seconds

## Repo Info
- GitHub: https://github.com/ErcoleHub/Portfolio
- Branch: `main`
- Vercel: connect at vercel.com → Import → ErcoleHub/Portfolio

## Vercel Setup (one-time)
1. vercel.com → "Add New Project" → Import from GitHub
2. Select `ErcoleHub/Portfolio`
3. Framework: **Other** (static)
4. Build command: *(leave empty)*
5. Output directory: `.`
6. Deploy
7. Add custom domain `justinercole.com` in Vercel project settings

## File Structure
- `index.html` — entire site (HTML + embedded CSS + JS)
- `uploads/` — image assets
- `og-image-v2.png` — social sharing image
- `.gitignore` — excludes `.env`, `.tmp/`, credentials
- `tools/` — Python scripts for automation (WAT framework)
- `workflows/` — this file and other SOPs

## What NOT to commit
- `.tmp/` files (gitignored)
- `.env` (gitignored)
- `credentials.json`, `token.json` (gitignored)
