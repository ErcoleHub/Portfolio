# Website Deploy Workflow

## Overview
Static portfolio site (`index.html`) → GitHub (`ErcoleHub/Portfolio`) → Vercel auto-deploy.
Every push to `main` triggers a live deploy in ~30 seconds.

## Ongoing Editing Workflow

1. Open project in Claude Code (terminal: `claude` from this directory, or VS Code extension)
2. Describe the change in plain language:
   - "Update the hero headline to say X"
   - "Add a new project card to the work section"
   - "Change the accent color from gold to blue"
3. Claude Code edits `index.html`, commits, and pushes to `main`
4. Vercel auto-deploys — no manual action needed

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
