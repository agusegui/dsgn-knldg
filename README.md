# Design Principles

> An open design language. A single installable Claude Code skill — forkable as your brand's design language, or used as-is to bootstrap brand decisions while you work.

Knowledge-driven, not template-driven. Produces designs that are reasoned rather than generic. Plays well with the Paper MCP canvas; degrades gracefully on platforms without it (Codex, Cursor, etc.).

---

## Install

```bash
npx skills add aguasun/design-principles
```

That's it. The skill lives at `~/.claude/skills/design-principles/` after install, and auto-triggers when design work appears in conversation. You can also invoke modes explicitly: `/design`, `/palette`, `/type-pair`, `/scale`, `/compose`, `/design-review`, `/type-specimen`, `/type-direct`.

The skill's source of truth is `skills/design-principles/SKILL.md` in this repo.

## Three ways to use it

**1. As-is.** Install and start designing. Generic mood-driven palettes for brand work, OKLCH delegation for product work, full knowledge base for typography, scale, composition.

**2. Fork it for a brand.** Fork this repo, edit `skills/design-principles/local/` with your brand's commitments (palette, type, voice, components, layout, brand overview). Push as `<your-handle>/<your-design-language>` and install via `npx skills add <your-handle>/<your-design-language>`. Anyone using your fork gets your brand baked in.

**3. Bootstrap brand decisions in flight.** Install the generic version, work on real designs. When you commit to a font pairing, palette, or voice, the skill offers to file the decision into `local/`. Over time, your working copy becomes the brand's design language. Fork the repo whenever you want to publish it.

The override rule is simple: **`local/` always wins over `core/`**. Files in `local/` override the equivalent universal knowledge. See [`skills/design-principles/local/README.md`](skills/design-principles/local/README.md) for the full list of override files and what they commit.

---

## Skills (modes)

| Skill | What it does |
|-------|-------------|
| `/design [brief]` | Full pipeline — content character, track inference, typography, scale, composition, color, asset inventory, UI patterns. Produces a brief, then builds on the Paper canvas if available. |
| `/design-review` | Post-build audit against every knowledge module |
| `/type-pair [context]` | 3-candidate font pairings with reasoning |
| `/type-specimen [fonts]` | Render a specimen card on the canvas |
| `/type-direct [copy]` | Copy-driven typographic direction, rendered |
| `/scale [context]` | Type scale + spacing system from a ratio |
| `/compose [context]` | Layout composition — approach, section plan, sketches |
| `/palette [context]` | Brand-track palette — mood word + scene + hex with roles |

## Two color tracks

The skill distinguishes two design tracks early in `/design` and routes color decisions accordingly:

- **Product / software / design system** — SaaS UI, dashboards, design tokens, Tailwind themes. Color is systematic. **Delegates to [`/oklch-skill`](https://github.com/jakubkrehel/oklch-skill)** by Jakub Krehel — install separately: `npx skills add jakubkrehel/oklch-skill`.
- **Brand / editorial / print / content / marketing** — posters, editorial spreads, brand systems, marketing pages. Color is mood-driven and scene-derived. Stays in this skill via `/palette`.

Step 1 of `/design` infers the track from the brief and surfaces the inference for confirmation.

## Knowledge modules

```
skills/design-principles/
  SKILL.md                       <- master orchestrator
  core/                          <- universal design knowledge
    foundations/math.md          Scale ratios, spatial systems, hierarchy signals
    typography/                  Pairing principles, classifications, contexts, typesetting
    layout/                      Composition (content-driven), grids
    color/                       Track-aware: mood-scene (brand) + oklch pointer (product)
    ui/                          States, patterns, accessibility universals
    mobile.md                    Single-file overlay: mobile-specific universals
    brand.md                     Single-file overlay: brand identity construction
  modes/                         <- workflow definitions (one per skill above)
  local/                         <- YOUR overrides. Empty by default.
```

## Knowledge loop

The skill learns from conversation. When you share insights, corrections, or preferences while working, the skill offers to file them — into `core/` (if universal), `local/` (if brand-specific), or skipped (if ephemeral). Confirms before writing.

- **Universals** are non-negotiable — accessibility standards, research-backed rules
- **Principles** are strong defaults that context can override
- **Local commitments** are brand-specific and override both

## Paper MCP

The skill produces visual output on the [Paper](https://paper.design) canvas via the Paper MCP server. Connect Paper MCP for full canvas rendering. On platforms without Paper MCP, the skill produces the brief as text — every value (hex, px, ratio, sketch) specified concretely so a developer or designer can execute manually.

## Key design rules

- **Never delete artboards** — always create new ones alongside existing iterations
- **Pre-design knowledge pass** — every new design runs through all 7 modules before any HTML
- **3-candidate process** — typography selection always considers 3 options with reasoning
- **Component architecture** — establish 2–4 reusable component types before building
- **Clone hygiene** — after cloning any canvas node, immediately restyle inherited text
- **Local overrides core** — committed brand decisions in `local/` always win

## Contributing

Knowledge contributions to `core/` are welcome — open a PR with the principle, the source/citation, and one example of where it would have changed an outcome. Brand-specific stuff stays in your own fork's `local/`.

## License

MIT — fork freely.

## Acknowledgments

Product-track color knowledge is provided by the [`oklch-skill`](https://github.com/jakubkrehel/oklch-skill) Claude Code skill, created and maintained by **[Jakub Krehel](https://github.com/jakubkrehel)** (MIT). Jakub also built [oklch.fyi](https://oklch.fyi), the interactive reference that makes OKLCH approachable. This system is meaningfully better because his work is open and well-documented — thank you.

When OKLCH applies, `/design` delegates to `/oklch-skill` rather than duplicating its content. The decision rules and integration points are documented in [`skills/design-principles/core/color/oklch.md`](skills/design-principles/core/color/oklch.md).
