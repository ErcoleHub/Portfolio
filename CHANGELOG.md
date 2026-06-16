# CHANGELOG

## 2026-06-16 — Add Casting OS case study with interactive 8-workflow expansion

- **index.html (work-grid)**: Reordered cards — new Casting OS card added as full-width first entry, Content Clipping Pipeline moved to last position; updated `border-bottom` on Brand Deal and Ad Cloning to preserve grid separators
- **index.html (Casting OS card)**: Added full-width card with two-row flow chain (main stack: Intake Form → 8 Workflows → Airtable → Gmail → Slack; enrichment row: YouTube API → Perplexity AI → Claude API → InsightIQ), Live System badge, and "Request a Demo" CTA
- **index.html (JS — showWfFlow)**: Added `castingWfFlows` data object and `showWfFlow()` function for per-workflow tool-flow expansion panel; WF6 and WF8 include inline data-field sub-panels (channel stats / TikTok + Instagram fields)
- **index.html (JS — click-outside)**: Added `document.addEventListener('click', ...)` handler to dismiss `#casting-wf-dropdown` when clicking anywhere outside it; added `event.stopPropagation()` to toggle button to prevent self-cancellation race condition
- **index.html**: Pushed to `origin/main` — site live on GitHub
