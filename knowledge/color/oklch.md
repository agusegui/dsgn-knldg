# OKLCH — systematic palettes for product work

> **Credit:** OKLCH knowledge in this system is provided by the [`oklch-skill`](https://github.com/jakubkrehel/oklch-skill) Claude Code skill, created and maintained by **Jakub Krehel** (MIT). When OKLCH applies, this system **delegates** to that skill rather than duplicating its content. The interactive reference [oklch.fyi](https://oklch.fyi) is also Jakub's work.

This document is a **pointer**, not a copy. It explains *when* OKLCH applies in this system, *how* `/design` delegates to it, and the decision rules — but the OKLCH knowledge itself (conversion, palette generation, contrast remediation, gamut, Tailwind theming) lives upstream and stays there.

---

## What OKLCH is, briefly

A perceptually-uniform color space. Equal lightness steps look equally bright. Hue stays constant across the lightness range. Contrast can be fixed by adjusting L alone (chroma has negligible effect). It's the right tool for systematic UI palettes, design tokens, dark mode derivation, and accessibility audits.

For the actual algorithms, thresholds, and CSS patterns, refer to the upstream skill once installed.

## Install

```
npx skills add jakubkrehel/oklch-skill
```

Once installed, the skill is invokable as `/oklch-skill` and auto-triggers on relevant color work (its description triggers on: oklch, color conversion, palette generation, contrast ratio, gamut, display p3, design tokens, hue drift, chroma, dark mode colors).

## When OKLCH applies in this system — **product track only**

- Building a palette for a SaaS product, dashboard, design system, or any product UI
- Generating a 50–950 lightness ramp for one or more brand hues
- Deriving dark mode from a light palette (perceptually equivalent)
- Auditing an existing palette for hue drift, contrast failures, or gamut issues
- Building or migrating a Tailwind v4 `@theme` color scale
- Any work where colors will be referenced as design tokens or CSS variables in code

## When OKLCH does NOT apply — **brand track**

- Editorial layouts, posters, print
- Marketing pages where the palette is mood-derived from a scene
- Brand systems where colors carry cultural or emotional reference
- Any work where the mood-and-scene method (see [mood-scene.md](mood-scene.md)) produces the right result

Mood palettes don't have ramps. Forcing a candlelit-amber into a 50–950 scale destroys what makes it feel candlelit. Use [mood-scene.md](mood-scene.md) for that work.

## How `/design` delegates to `/oklch-skill`

Three trigger points, and three only:

| Trigger | Action |
|---|---|
| **Step 1 — track decision** | If product track, surface a one-line note: "OKLCH may apply at Step 5 — `/oklch-skill` is the canonical tool. Install with `npx skills add jakubkrehel/oklch-skill` if not present." Then proceed. |
| **Step 5 — color pass (product track only)** | If `/oklch-skill` is in the available-skills list, hand off explicitly: "Use `/oklch-skill` to generate the palette ramp. This system contributes the base color (from content character) and role assignment." If not installed, mention install once and offer the mood-driven fallback. |
| **User-supplied palette audit** | When the user provides an existing palette and asks for review (hue drift, contrast remediation, ramp validation), always point to `/oklch-skill` regardless of which track the original palette came from — its diagnostics are unmatched. |

The restraint matters as much as the surfacing: **don't suggest OKLCH for editorial/marketing/brand work**, and don't auto-pull it into the workflow when the mood-driven approach is producing the right result.

## Decision rule

| Signal in the brief | Tool |
|---|---|
| "build a palette for our product / dashboard / design system" | `/oklch-skill` |
| "derive a brand palette for a poster / editorial / marketing page" | `/palette` (mood-driven) |
| "audit this palette for accessibility / hue drift / contrast" | `/oklch-skill` |
| "the brand has a primary color, build the rest of the palette around it" | `/oklch-skill` (systematic ramp from base) |
| "I want a candlelit / mineral / signage / brutalist palette" | `/palette` (mood-driven) |
| "convert these hex tokens to oklch" | `/oklch-skill` |
| "design a magazine spread" | `/palette` (mood-driven) |

## What this system contributes around OKLCH

`/oklch-skill` is excellent at color math. It does not know about your content character, brand voice, or the larger design brief. When `/design` delegates, it provides:

- The **base color(s)** — derived from content character (Step 1) or supplied by the brand
- **Role assignment** — which color in the ramp serves background vs. text vs. accent vs. surface
- **Integration with the brief** — the palette plugs into Steps 5–6 of the design brief alongside type, scale, composition

OKLCH handles the systematic generation, contrast checks, and gamut work. This system handles everything around it.

## Acknowledgments

Thanks to **Jakub Krehel** for building and open-sourcing the `oklch-skill`, and for [oklch.fyi](https://oklch.fyi) — the interactive reference that makes OKLCH approachable. This system is better because his work is available.

## Reference (for traceability)

This document was authored against upstream `oklch-skill` at commit [`e2b2fe5`](https://github.com/jakubkrehel/oklch-skill/commit/e2b2fe59c120236369ea1e536278969cdfb11272) (verified 2026-04-29). The upstream skill is the source of truth. If the upstream surface changes significantly (new modes, renamed skill, etc.), update this pointer.

License: MIT — see the [upstream LICENSE](https://github.com/jakubkrehel/oklch-skill/blob/main/LICENSE).
