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
| `/palette [context]` | Derives a color palette from content character |

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
  ui/
    states.md                Component states (hover, focus, disabled, loading, error)
    patterns.md              Interaction patterns, accessibility universals, visual cliches
```

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
