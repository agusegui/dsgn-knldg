# Design Principles

A modular design knowledge system for Paper. Teaches Claude how to make better design decisions — typography, scale, composition, color, and UI patterns — grounded in curated knowledge rather than habit.

## What this does

When you open this project in Claude Code with Paper MCP connected, you get 8 design skills backed by a structured knowledge base. The skills consult the knowledge modules before making decisions, producing designs that are intentional and reasoned rather than generic.

The system is **descriptive, not prescriptive**. It presents options with context so you can make informed decisions. The only hard rules are accessibility universals (WCAG contrast, focus visibility, etc.).

## Setup

1. Clone this repo
2. Open it in Claude Code
3. Make sure Paper MCP is connected (check with `/mcp`)
4. Start designing — use the skills below or just describe what you need

## Skills

### Full workflow
| Skill | What it does |
|-------|-------------|
| `/design [brief]` | Full pipeline: analyzes content, consults every knowledge module, produces a design brief, then builds on the Paper canvas |
| `/design-review` | Post-build audit against all knowledge modules — typography, scale, composition, color, UI patterns |

### Typography
| Skill | What it does |
|-------|-------------|
| `/type-pair [context]` | Suggests 3 font pairings ranked by fitness for your use case |
| `/type-specimen [fonts]` | Renders a specimen card on the canvas for a font pairing |
| `/type-direct [copy]` | Analyzes actual content, produces a typographic direction, renders a real design on canvas |

### Planning (no canvas output)
| Skill | What it does |
|-------|-------------|
| `/scale [context]` | Derives a complete type scale and spacing system from a ratio |
| `/compose [context]` | Plans layout composition — section variety, layout sketches, grid choice |
| `/palette [context]` | Brand-track palette — mood-driven, scene-derived. For product/UI palettes, see `/oklch-skill` below |

### Optional — product-track color
| Skill | What it does |
|-------|-------------|
| `/oklch-skill` | Systematic OKLCH palettes — perceptually-uniform ramps, contrast remediation, dark mode, Tailwind v4 themes. **Created by [Jakub Krehel](https://github.com/jakubkrehel/oklch-skill)** (MIT). Install separately: `npx skills add jakubkrehel/oklch-skill`. See `knowledge/color/oklch.md` for when it applies. |

## Knowledge modules

```
knowledge/
  foundations/math.md        Scale ratios, spatial systems, hierarchy signals
  typography/
    rules.md                 Pairing principles, typeface selection, typesetting rules
    pairings.json            Curated pairing database with mood/use tags
    classifications.md       Form model framework (Dynamic, Rational, Geometric)
    typesetting.md           Context-specific type scales and rhythm
    graphic-contexts.md      Medium-specific demands (poster, editorial, brand, digital)
  layout/
    composition.md           Content-driven composition, component architecture, anti-patterns
    grids.md                 Grid types and responsive behavior
  color/
    README.md                Module overview — two-philosophy color, routed by track
    mood-scene.md            Brand-track: mood-driven, scene-derived palettes
    oklch.md                 Product-track: pointer to /oklch-skill (Jakub Krehel)
    sources.md               External references (oklch-skill, oklch.fyi, WCAG, APCA)
  ui/
    states.md                Component states (hover, focus, disabled, loading, error)
    patterns.md              Interaction patterns, accessibility universals, visual cliches
```

## Tracks

The system distinguishes two design tracks early in `/design`:

- **Product / software** — SaaS UI, design systems, dashboards, Tailwind themes. Color is systematic; OKLCH is the right tool.
- **Brand / editorial / print / content / marketing** — posters, editorial spreads, brand systems, marketing pages. Color is mood-driven and scene-derived.

Step 1 of `/design` infers the track from the brief and routes Step 5 (color) accordingly. Future sub-skills will likely fork along the same axis.

## How the knowledge loop works

The system learns from conversation. When you share insights, corrections, or preferences while working, Claude will offer to file them into the relevant module. This means the knowledge base improves over time.

- **Universals** (marked with `> **Universal:**`) are non-negotiable — accessibility standards, research-backed rules
- **Principles** are strong defaults that context can override

When adding knowledge, most things are principles. Universals are rare.

## Key design rules

These are in CLAUDE.md but worth knowing:

- **Never delete artboards** — always create new ones alongside existing work
- **Pre-design knowledge pass** — every new design runs through all 7 knowledge modules before any HTML is written
- **3-candidate process** — typography selection always considers 3 options with reasoning, never defaults to a familiar face
- **Component architecture** — establish 2-4 reusable component types before building, vary arrangement not structure
- **Clone hygiene** — after cloning any canvas node, immediately audit and restyle inherited text

## Acknowledgments

The product-track color philosophy in this system is delivered by the [`oklch-skill`](https://github.com/jakubkrehel/oklch-skill) Claude Code skill, created and maintained by **[Jakub Krehel](https://github.com/jakubkrehel)** (MIT). Jakub also built [oklch.fyi](https://oklch.fyi), the interactive reference that makes OKLCH approachable. This system is meaningfully better because his work is open and well-documented — thank you.

When OKLCH applies (product-track work, palette audits, Tailwind themes), `/design` delegates to `/oklch-skill` rather than duplicating its content. The decision rules and integration points are documented in [`knowledge/color/oklch.md`](knowledge/color/oklch.md).
