# Color sources

External references for color knowledge in this module.

## OKLCH (product track)

- [oklch-skill by Jakub Krehel](https://github.com/jakubkrehel/oklch-skill) — the canonical OKLCH knowledge for this system. MIT licensed. Referenced (not vendored) — install via `npx skills add jakubkrehel/oklch-skill`.
- [oklch.fyi](https://oklch.fyi) — interactive OKLCH playground by Jakub Krehel
- [W3C CSS Color 4 — `oklch()`](https://www.w3.org/TR/css-color-4/#ok-lab) — spec reference
- [APCA Contrast](https://www.myndex.com/APCA/) — perceptual contrast algorithm, paired naturally with OKLCH

## Mood-driven palettes (brand track)

- The Paper MCP server's `paper-mcp-instructions` guide — the canonical mood word library and proven background × accent pairings for the brand track in this system. Loaded at session start via `get_guide({ topic: "paper-mcp-instructions" })`.

## Universals (both tracks)

- [WCAG 2.2 — Contrast (Minimum)](https://www.w3.org/TR/WCAG22/#contrast-minimum) — 4.5:1 normal text, 3:1 large text
- [WCAG 2.2 — Use of Color](https://www.w3.org/TR/WCAG22/#use-of-color) — color is never the sole information carrier
