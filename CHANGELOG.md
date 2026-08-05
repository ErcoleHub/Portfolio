# CHANGELOG

## 2026-06-16 — Add Casting OS case study with interactive 8-workflow expansion

- **index.html (work-grid)**: Reordered cards — new Casting OS card added as full-width first entry, Content Clipping Pipeline moved to last position; updated `border-bottom` on Brand Deal and Ad Cloning to preserve grid separators
- **index.html (Casting OS card)**: Added full-width card with two-row flow chain (main stack: Intake Form → 8 Workflows → Airtable → Gmail → Slack; enrichment row: YouTube API → Perplexity AI → Claude API → InsightIQ), Live System badge, and "Request a Demo" CTA
- **index.html (JS — showWfFlow)**: Added `castingWfFlows` data object and `showWfFlow()` function for per-workflow tool-flow expansion panel; WF6 and WF8 include inline data-field sub-panels (channel stats / TikTok + Instagram fields)
- **index.html (JS — click-outside)**: Added `document.addEventListener('click', ...)` handler to dismiss `#casting-wf-dropdown` when clicking anywhere outside it; added `event.stopPropagation()` to toggle button to prevent self-cancellation race condition
- **index.html**: Pushed to `origin/main` — site live on GitHub

## 2026-08-04 — Section headlines retitled, SourceSifterr card added, work grid converted to a horizontal scroller

- **index.html (section headlines)**: Section 02 `CASE STUDIES` → `RECENT PROJECTS`; section 05 `RECENT THOUGHTS` → `SOME THOUGHTS…`. Matching CSS and HTML section comments renamed. `#work` and `#thoughts` ids and all nav anchors left untouched. Commits `134070e` (retitle) and `641d786` (corrected `..` to a proper `&hellip;`)
- **index.html (SourceSifterr card)**: New first card in `.work-grid`. Title `SourceSifterr`, result "Sourcing admin eliminated for interior designers, set designers, and project managers", category `Chrome Extension · Claude API · Google Sheets · Google Slides`. Copy derived from this site's own SourceSifterr `og:description` rather than written fresh
- **index.html (.badge-pill)**: New class — solid gold chip reading `Available Now`, distinguishing a purchasable product from the cyan hairline `Live System` labels on the four client-system cards. The first attempt reused `.flow-badge` and rendered correctly but was too subtle to read at a glance (13px tall, 55% opacity)
- **index.html (.demo-btn--stretch)**: New class — `Learn More` button occupying the same slot as the other cards' `Request a Demo`, linking to `sourcesifterr/index.html`. Uses a stretched-link `::after` covering the card so the whole card stays clickable while the button remains a real anchor, avoiding a nested `<a>`
- **index.html (.work-grid)**: Converted from `grid-template-columns: repeat(2, 1fr)` to a horizontal scroller (`grid-auto-flow: column`, `grid-auto-columns: calc(100% / 3)`, scroll snap, thin styled scrollbar), mirroring the existing `.systems-grid` pattern in section 01. Per-card inline `grid-column` and border overrides removed; borders now come from CSS. Tablet breakpoint uses `grid-auto-columns: 82%`
- **index.html (.flow-nodes — bug fix)**: Added `width: 100%`. `flex-wrap: wrap` was already set but never fired, because the centring parent `.flow-thumb` sized the row to max-content. Long flow chains clipped at the card edge once cards narrowed to 447px. Latent bug, masked by the previous full-width layout
- **index.html (.flow-thumb — bug fix)**: Fixed `height` → `min-height: 300px`. In a narrow card the expanded workflow panel wraps to more rows and was spilling over the card title
- **uploads/sourcesifterr-logo.png**: New asset, `SourceSifterrLogoMAIN.png` from the AIOS `clients/emily-ercole/sourcing-portal/brand/` folder. Thumb background set to `#F6F4EF`, sampled from the PNG's own palette, so the cream logo reads as a deliberate light panel
- **Verification**: Headless-Chrome probe at 1440/1024/700px with both dropdowns and an expansion panel open — 0px flow-row clipping, 0px dropdown clipping, 0px expansion overlap, no vertical scrollbar, horizontally scrollable at every width. Post-deploy, the logo asset and `/sourcesifterr/` were each confirmed HTTP 200 with their own requests
- **Commit** `f03cbe9`: pushed to `origin/main`, live on www.ercoleautomations.com via Vercel
