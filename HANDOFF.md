# HANDOFF.md

> **Hosting note:** this site is on **Vercel**, not GitHub Pages. The 2026-06-16 block below says GitHub Pages and is wrong — it predates the 2026-07-23 migration. See `connections.md` for the current pipeline.

## Session: 2026-08-04 — Section headlines retitled, SourceSifterr card added, work grid converted to a horizontal scroller

### Current state
Everything is shipped and live on www.ercoleautomations.com. Section 02 reads `RECENT PROJECTS`, section 05 reads `SOME THOUGHTS…`. The work grid is now a horizontal scroller (3 cards visible, 5 total) instead of a 2-column grid, mirroring the `.systems-grid` pattern already used in section 01. SourceSifterr is the first card: cream logo panel, gold `Available Now` chip, `Learn More` button linking to `/sourcesifterr`, and the whole card is clickable. Working tree is clean and synced with `origin/main` at `f03cbe9`. Nothing is blocked or in progress.

### Completed this session
- **Headlines**: `CASE STUDIES` → `RECENT PROJECTS`, `RECENT THOUGHTS` → `SOME THOUGHTS…` (`134070e`, `641d786`)
- **SourceSifterr card** (`f03cbe9`): new first card with `.badge-pill` and `.demo-btn--stretch` classes; logo added at `uploads/sourcesifterr-logo.png`
- **Horizontal scroller**: `.work-grid` converted; per-card inline grid/border overrides stripped in favour of CSS
- **Two latent CSS bugs fixed**: `.flow-nodes` needed `width: 100%` for `flex-wrap` to work at all inside a centring parent; `.flow-thumb` needed `min-height` instead of `height` so expansion panels stop overlapping the card title

### Immediate next tasks
- Nothing pending on the work grid.
- Optional, ~2 min: two typos on the SourceSifterr sales page in `sourcesifterr/index.html` — `In Case Your Wondering` should be `You're`, and `catagory` should be `category`.

### Running state
- Background processes: none
- Dev servers: none
- Open worktrees: none

### Deferred / open
- **Justin reviewed and explicitly declined these — do not re-raise**: the `02 — Selected Work` label repeating "Work" next to the `View All Work →` link; that link still being `href="#"` (dead); and the demo buttons not sharing a baseline across the card row.
- Copy mismatch, flagged but not acted on: the SourceSifterr card names "project managers" while the SourceSifterr landing headline still says "Chrome extension for spatial designers".

### Key files
- `index.html` — the entire site. Work grid markup ~line 1600; `.work-grid` / `.work-card` / `.badge-pill` / `.demo-btn--stretch` / `.flow-*` CSS ~lines 536-700.
- `connections.md` — the authoritative hosting record (Vercel, deploy ~15s).

### How to verify a change here
This is a static file with no build step and no root-absolute asset paths, so `open index.html` renders faithfully. For layout work, take a screenshot AND assert on measured geometry — each catches what the other misses. After pushing, curl the live URL for the changed string, and give any new binary asset its own request (a 200 on the HTML does not prove the asset shipped).

---

## Session: 2026-06-16 — Casting OS case study shipped and live

### Current state
The website has 4 case studies live on GitHub Pages in the correct order: Casting OS (full-width, top), Brand Deal Pipeline, Ad Cloning & Generation Pipeline, Content Clipping Pipeline (full-width, bottom). All interactive features are working: the "8 Workflows ▾" dropdown opens/closes, each workflow tag expands its tool-flow panel below the card, and clicking anywhere outside the dropdown dismisses it.

### Completed this session
- **index.html — work-grid reorder**: Casting OS card inserted at top (full-width), Content Clipping moved to bottom; border management updated across all 4 cards
- **index.html — Casting OS card**: Full interactive card with two-row flow visualization, Live System badge, "Request a Demo" CTA linking to Google Calendar booking
- **index.html — showWfFlow()**: Per-workflow expansion panel with complete tool-flow chains for all 8 workflows; WF6 includes YouTube channel stat fields, WF8 includes TikTok/Instagram profile fields with gold section headers
- **index.html — click-outside dismiss**: Document-level click handler to close `#casting-wf-dropdown`; fixed with `event.stopPropagation()` on toggle button to prevent self-cancellation
- **GitHub**: Pushed all 4 commits to `origin/main` — site is live

### Immediate next tasks
- No pending tasks — session is fully complete
- Potential future additions: add case studies for other client projects, or add a 5th card as the portfolio grows

### Running state
- Background processes: none
- Dev servers: none
- Open worktrees: none

### Deferred / open
- None

### Key files
- `index.html` — the entire site; work-grid starts around line 1463, JS for casting OS (showWfFlow, click-outside handler) is around lines 1960–2010

---
