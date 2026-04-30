Derive a complete type scale and spacing system from a design context — ratio, base size, every hierarchy level, and spatial tokens.

Use this skill whenever you need to establish sizing and spacing for a design, set up a type scale, choose a scale ratio, or define the spatial rhythm for a layout. Also useful when reviewing or adjusting an existing scale that feels off.

## Arguments
`$ARGUMENTS` — a design context description. Examples:
- "luxury editorial magazine, 6 hierarchy levels"
- "dense SaaS dashboard, minimal hierarchy"
- "dramatic brand landing page, big hero moment"
- "mobile-first product UI, 390px viewport"

Can also include constraints: "base 15px", "8px grid", "ratio 1.333", or a specific medium.

## Your task

### Step 1 — Read the foundations

Read `../core/foundations/math.md` for the full ratio table, scale derivation method, spatial token system, and measure guidance.

Read `../core/typography/typesetting.md` for context-specific scale presets (Editorial, Product UI, Brand/Landing Page, Mobile).

### Step 2 — Choose the ratio

The ratio sets the personality of the hierarchy. Match it to the content's emotional register and hierarchy depth:

| Ratio | Value | Personality | Best for |
|-------|-------|-------------|----------|
| Minor Second | 1.067 | Dense, compact | Dashboards, data-heavy UI |
| Major Second | 1.125 | Gentle | Subtle differentiation, body-to-caption |
| Minor Third | 1.200 | Clear without drama | General purpose, balanced |
| Major Third | 1.250 | Editorial clarity | Editorial, marketing |
| Perfect Fourth | 1.333 | Strong hierarchy | Recommended default |
| Augmented Fourth | 1.414 | Dramatic | Poster, display contexts |
| Perfect Fifth | 1.500 | Very dramatic | Limited to 2-3 levels |
| Golden Section | 1.618 | Organic, flowing | Exhibition, art, brand hero |

**The ratio choice is a design decision, not a default.** Justify it from the content: a dense dashboard choosing Golden Section will have absurdly large headings; a dramatic poster choosing Minor Second will have no visual peaks.

### Step 3 — Derive the scale

Pick a **base size** (body text):
- 16px: web default, accessibility baseline
- 15px: editorial, slightly more refined
- 14px: product UI where density matters (accessibility floor — never go below)

Multiply up for larger levels, divide down for smaller. **Always round to whole pixels.**

Present the scale as a table:

```
Level       Size    Weight   Leading   Tracking    Notes
─────────   ──────  ──────   ───────   ────────    ─────
Hero        72px    800      0.95      -0.03em     Display face
Display     48px    700      1.05      -0.02em     Display face
H1          36px    700      1.15      -0.01em
H2          28px    600      1.25      0
Subhead     21px    500      1.35      0
Body        16px    400      1.65      0           Body face
Small       14px    400      1.55      0           Body face
Caption     12px    400      1.5       0.02em      Body face
Label       11px    600      1.4       0.1em       ALL CAPS
```

Adjust the number of levels to match the content's needs — a poster might only need 3 levels, a full editorial system might need 8.

### Step 4 — Define the spacing system

Use the 8px spatial grid from math.md. Map spacing tokens to the design context:

```
Token      Value    Use in this design
─────────  ──────   ──────────────────
space-1    4px      Icon gaps, micro-adjustment
space-2    8px      Label-to-value, tight component gaps
space-3    16px     Between related elements within a component
space-4    24px     Between components within a section
space-5    32px     Card padding, section separation (compact)
space-6    48px     Major section breaks
space-7    64px     Between major panels
space-8    96px     Page-level section separation
space-9    128px+   Hero breathing room, cinematic whitespace
```

Then specify how the tokens map to this design's structure:
- **Section padding**: which token(s)
- **Component gaps**: which token
- **Element gaps**: which token
- **Card/panel padding**: which token

### Step 5 — Verify the measure

At the chosen body size, calculate the reading measure:
- `max-width` should produce 55-75 characters per line
- At 16px body, ~640-680px max-width for body text
- At 15px body, ~600-640px
- At 14px body, ~560-600px

State the `max-width` value for the body text column.

### Step 6 — Check hierarchy contrast

Verify the heading-to-body ratio:
- Editorial/brand: aim for 2:1 or more (H1:body)
- Product UI: 1.5:1 is acceptable
- The largest element (hero/display) to body should be at least 3:1 for brand/editorial

If the ratios feel flat, step up to a more dramatic scale ratio and recalculate.

---

## Output format

Present the complete system:

```
SCALE SYSTEM
Ratio: [name] ([value])
Base: [size]px
Grid: [base unit]px

TYPE SCALE
[table from Step 3]

SPACING TOKENS
[table from Step 4]

STRUCTURE MAPPING
Section padding: space-[N] ([value]px)
Component gap: space-[N] ([value]px)
Element gap: space-[N] ([value]px)
Card padding: space-[N] ([value]px)

MEASURE
Body max-width: [value]px (~[N]ch)

HIERARCHY CHECK
H1:body = [ratio]:1
Display:body = [ratio]:1
```

This output plugs directly into the design brief (Step 3) when used within `/design`.
