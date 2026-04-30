---
name: design-principles
description: Open design language for product, brand, editorial, and marketing work. Use when designing landing pages, app UI, brand systems, posters, decks, mobile interfaces, or any visual surface — the skill produces a structured design brief (typography, scale, composition, color, assets, UI patterns) before any execution. Also use for design audits, type pairing, color palette generation, type scale derivation, layout composition planning, font specimen rendering, and brand bootstrapping. Triggers on design, design brief, design system, design language, typography, font pairing, type pair, type scale, type specimen, scale and spacing, ratio, layout, composition, grid, palette, color palette, mood word, oklch, brand identity, brand bootstrap, brand audit, design review, paper canvas, paper mcp, landing page, marketing page, app design, mobile design, poster, editorial spread, magazine layout, deck, slide, wordmark, app icon.
---

# Design Principles

A descriptive, fork-friendly design language. Knowledge-driven, not template-driven. Produces designs that are reasoned rather than generic.

This skill orchestrates a multi-pass design workflow. Each pass consults a specific knowledge module before making a decision. The output of all passes is a **design brief**; the brief then drives execution (Paper canvas if available, otherwise spec output).

## Folder map

```
SKILL.md          ← you are here. The orchestrator.
core/             ← universal design knowledge. Do not edit casually.
  foundations/    ← scale ratios, spatial systems, hierarchy
  typography/     ← pairings, classifications, typesetting, contexts
  layout/         ← composition, grids, anti-patterns
  color/          ← brand-track (mood-scene) + product-track (oklch pointer)
  ui/             ← states, patterns, accessibility universals
  mobile.md       ← single-file overlay: what changes when canvas is 390px
  brand.md        ← single-file overlay: brand identity construction
modes/            ← workflow modes the orchestrator routes to
  design.md            ← full pipeline (the master)
  design-review.md     ← post-build audit
  type-pair.md         ← font pairing suggestion
  type-specimen.md     ← specimen card on canvas
  type-direct.md       ← copy-driven typographic direction
  scale.md             ← type scale + spacing system
  compose.md           ← layout composition planning
  palette.md           ← brand-track palette derivation
local/            ← YOUR overrides. Local always wins over core.
```

## How to engage

When the user asks for design work, **route to a mode** based on what was asked:

| User asks for… | Run this mode |
|---|---|
| Full design (landing page, app, poster, etc.) | `modes/design.md` |
| Audit / review of an existing design | `modes/design-review.md` |
| Font pairing suggestions | `modes/type-pair.md` |
| Specimen card to test a pairing | `modes/type-specimen.md` |
| Typographic direction from real copy | `modes/type-direct.md` |
| Type scale + spacing system | `modes/scale.md` |
| Layout composition plan | `modes/compose.md` |
| Brand-track color palette (mood-driven) | `modes/palette.md` |
| Product-track color palette (systematic) | Defer to `/oklch-skill` (see `core/color/oklch.md`) |

For ambiguous requests, default to `modes/design.md` (the full pipeline) — it covers everything.

## The resolution rule — `local/` always wins over `core/`

Before consulting any `core/` file, check whether a corresponding file exists in `local/`. If it does, **use the local version.** This is the entire mechanism that makes the skill brand-aware after a fork or bootstrap.

| Decision | First check | Fall back to |
|---|---|---|
| Color palette | `local/palette.md` | mood-driven derivation via `core/color/mood-scene.md` |
| Type pairing | `local/type.md` | 3-candidate process via `core/typography/` |
| Voice / copy tone | `local/voice.md` | inferred from content character |
| UI components | `local/components.md` | `core/ui/` patterns |
| Layout signatures | `local/layout.md` | `core/layout/composition.md` |
| Brand overview (mood, era, register) | `local/overview.md` | inferred at Step 1 of `modes/design.md` |
| Logos, brand assets | `local/assets/` | request from user / placeholder |

If the user is starting from scratch (empty `local/`), gently surface the bootstrap option once, then proceed with `core/` defaults. Do not nag.

## Universals (apply to every mode)

> **Universal:** Body text contrast meets WCAG AA — 4.5:1 normal text, 3:1 large text. Non-negotiable.
>
> **Universal:** Color is never the sole information carrier. Pair with shape, weight, position, or label.
>
> **Universal:** Before writing any HTML for a new design, complete the full knowledge pass defined in `modes/design.md`. The brief is the design; the HTML is just execution.
>
> **Universal:** Never delete artboards on the Paper canvas — always create new ones alongside existing iterations. The canvas is working memory.

## Paper MCP — present vs. absent

This skill produces Paper canvas output when the Paper MCP server is available. Detect availability by attempting `get_basic_info` early in any execution mode that builds visuals.

- **Paper MCP available** → after the brief is approved, build the design on canvas using the rules in `modes/design.md` § "Building on Paper canvas"
- **Paper MCP not available** (Codex, Cursor without Paper MCP, etc.) → produce the brief as text output. Specify everything concretely (hex values, font sizes in px, layout sketches in spatial language) so a developer or designer can execute it manually or via code. Do not pretend to render on a canvas that doesn't exist.

## Brand bootstrapping (when `local/` is empty)

If the user has empty `local/` and is doing brand work for the first time, the skill can act as a brand bootstrapper. As decisions get made during real design work, offer to file them into `local/`:

> "You committed to Instrument Serif + Inter as the system pair, and the cobalt accent over white as the brand palette. Want me to file this into `local/type.md` and `local/palette.md` so future sessions inherit it?"

Confirm before writing. Keep `local/` files concise — they're commitments, not essays.

## Knowledge loop

This skill learns from conversation. When the user shares an insight, correction, or preference:

1. Identify whether it's universal (belongs in `core/`), brand-specific (belongs in `local/`), or ephemeral (no file).
2. State what you'd add and where, before writing.
3. Update existing entries rather than creating duplicates.

Universals are rare. Most knowledge is principles, and most brand-specific knowledge belongs in `local/`.

## Acknowledgments

Product-track color knowledge is provided by the [`oklch-skill`](https://github.com/jakubkrehel/oklch-skill) by **Jakub Krehel** (MIT). When OKLCH applies, this skill delegates to `/oklch-skill` rather than duplicating its content. Install it separately: `npx skills add jakubkrehel/oklch-skill`.

See `core/color/oklch.md` for the full integration rules and credit.

---

**License:** MIT. Fork freely.
**Source:** `https://github.com/aguasun/design-principles`
