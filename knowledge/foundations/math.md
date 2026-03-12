# Design Math

Shared mathematical foundations used across typography, layout, and spacing.
All modules reference this file for scale derivation, spatial rhythm, and proportional systems.

---

## 1. Scale Ratios

Type sizes, spacing, and grid proportions can all derive from a single ratio.
Choose a ratio based on the design's emotional register and hierarchy depth.

| Name | Ratio | Feel | Hierarchy depth |
|------|-------|------|-----------------|
| Minor Second | 1.067 | Dense, compact | UI, dashboards |
| Major Second | 1.125 | Gentle | Body-to-caption differentiation |
| Minor Third | 1.200 | Clear without drama | General purpose |
| Major Third | 1.250 | Editorial clarity | Editorial, marketing |
| Perfect Fourth | 1.333 | Strong hierarchy | Recommended default |
| Augmented Fourth | 1.414 | Dramatic | Poster, display contexts |
| Perfect Fifth | 1.500 | Very dramatic | Limited to 2-3 levels |
| Golden Section | 1.618 | Organic, flowing | Exhibition, art book |

---

## 2. Scale Derivation

### Ratio-based (default)

Pick a **base size** and a **ratio**. Multiply up for larger levels, divide down for smaller.
Always round to the nearest whole number.

**Example: base 16px, ratio 1.333 (Perfect Fourth)**

| Level | Calculation | Result |
|-------|------------|--------|
| Caption | 16 / 1.333 | 12px |
| Body | base | 16px |
| Subhead | 16 x 1.333 | 21px |
| Heading | 16 x 1.333^2 | 28px |
| Display | 16 x 1.333^3 | 38px |
| Hero | 16 x 1.333^4 | 50px |

### Interval-based (alternative)

Use fixed **4px or 8px steps** instead of a ratio. Useful for product UI where predictability
matters more than dramatic hierarchy.

**Example: 8px interval**
```
Caption:  12px
Body:     16px
Subhead:  24px
Heading:  32px
Display:  40px
Hero:     48px
```

**Example: 4px interval (finer control)**
```
Caption:  12px
Small:    14px
Body:     16px
Large:    20px
Subhead:  24px
Heading:  32px
```

### Rules for both modes

- All sizes must be whole numbers (round to nearest integer)
- Never use non-integer font sizes
- Below 12px, text is effectively unreadable unless all-caps at high contrast
- **Heading-to-body ratio:** 2:1 or more creates clear hierarchy in editorial and brand
  contexts. Product UI can work at 1.5:1 when density matters, but below that the
  heading reads as body text with emphasis rather than a distinct hierarchical level.

---

## 3. Spatial Systems

A consistent spatial unit prevents arbitrary spacing decisions and makes designs feel
cohesive. The most common bases are **8px** and **4px**.

**8px base** — the default in this system. Clean multiples, aligns well to most screen
densities. Half-steps of 4px are permitted for micro-adjustments within components, but
not as primary spacing between sections.

**4px base** — finer granularity. Useful when 12px (common in UI) falls awkwardly between
8 and 16. Some systems prefer 4px as the fundamental unit with 8px as the first "real"
step. Either base works — what matters is consistency within a project.

The token scale below uses 8px as its base, but the values are compatible with a 4px
system (every value is a multiple of 4).

| Token | Value | Use |
|-------|-------|-----|
| space-1 | 4px | Inner padding, icon gap, micro-adjustment |
| space-2 | 8px | Between label and value, tight component gap |
| space-3 | 16px | Between related elements within a component |
| space-4 | 24px | Between components within a section |
| space-5 | 32px | Section separation, comfortable card padding |
| space-6 | 48px | Major section breaks |
| space-7 | 64px | Hero breathing room, between major panels |
| space-8 | 96px | Page-level section separation |
| space-9 | 128px+ | Hero whitespace, cinematic breathing room |

**Gestalt rule:** Tighter spacing signals "these belong together." Looser spacing signals
"these are different things." Never use the same gap between items that have different
relationships.

---

## 4. Ratio-Based Proportions

Derive layout proportions from the same ratio as the format. This creates harmony between
content and container that arbitrary divisions can't achieve.

**Method:**
1. Identify the format's own ratio — A4 is 1:1.414; a 16:9 screen is 1:1.778
2. Subdivide the format continuously by that ratio to find natural column widths
3. Use the same ratio to set margins — margins derived from the format ratio create
   inherent harmony between content field and edge

**Rational vs. irrational ratios:**
- **Rational (1:2, 2:3, 3:4)** — structured, clear, architectural feeling
- **Irrational (1:1.414 / sqrt(2), 1:1.618 / golden section)** — dynamic, organic, flows naturally

**Continuous subdivision:** divide, then divide again by the same ratio. Each subdivision
is self-similar to the whole. This is why A-series paper (A4 -> A5 -> A6) always feels
proportionally correct regardless of size.

**Practical examples:**
- 800px card -> ~566px content column (800 / 1.414) with equal side margins
- 1440px desktop -> ~890px max content width (1440 / 1.618)

---

## 5. Measure (Characters Per Line)

The ideal reading measure for body text is **55-75 characters per line**.

- Below 45 characters: too short, choppy reading rhythm
- Above 85 characters: too long, eyes lose the next line
- At 800px wide with 32px padding = 736px — constrain body to ~640-680px
- At 390px (mobile), the viewport constrains naturally

Approximate: 1ch ~ 8-10px at 16px body size, depending on the typeface.

---

## 6. Hierarchy Signals

Universal tools for creating visual hierarchy, ordered strongest to weakest:

1. Size difference
2. Weight difference
3. Color / value difference
4. Spacing above/below
5. Case (all-caps, small-caps)
6. Font family switch

In practice, the best hierarchy uses 2-3 of these simultaneously on key elements.
Never use all 6 on the same element.
