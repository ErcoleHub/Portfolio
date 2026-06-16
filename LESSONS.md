# LESSONS

Lessons learned across sessions — non-obvious failures, surprising behaviors, and root causes worth remembering.

---

## 2026-06-16 — Vanilla JS click-outside-to-dismiss: toggle button must stopPropagation

### Always call event.stopPropagation() on the dropdown toggle button
When adding a document-level click handler to dismiss a dropdown, the toggle button's click bubbles up to the document immediately after running `toggleDropdown`. The listener fires, sees the dropdown is `open` (just set), finds the click target is outside `dd.contains(e.target)` because the button is a sibling of the dropdown — not inside it — and closes it. Net result: dropdown opens and closes on the same click. Fix: add `event.stopPropagation()` to the button's onclick so the click never reaches the document handler.

### Use dd.contains(e.target), not expandable.contains(e.target)
The simpler containment check (`dd.contains(e.target)`) is more reliable than traversing to the parent `.flow-expandable` with `.closest()`. Since button clicks are stopped before they reach the document handler, you only need to distinguish "click was inside the dropdown panel" vs. "click was outside everything" — `dd.contains()` covers that cleanly.

---
