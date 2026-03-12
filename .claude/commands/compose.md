Plan the layout and composition for a design — compositional approach, section plan, layout sketches, grid choice, and scale peak.

Use this skill whenever you need to plan a page layout, design section structure, choose a grid system, or when a design feels like it's defaulting to centered stacks and equal-card grids. Also useful when reviewing a layout that feels "template-like" and needs compositional direction.

## Arguments
`$ARGUMENTS` — a content description, design brief excerpt, or the content itself. Should include:
- What the content's job is (persuade, inform, orient, impress)
- Who reads it and how (scanning, studying, comparing, feeling)
- The medium (poster, editorial, brand, digital)
- Number of sections or content blocks (if known)

Examples:
- "SaaS landing page, 5 sections: hero, features, social proof, pricing, CTA. Audience is CTOs scanning quickly."
- "Long-form editorial article, 2000 words with pull quotes and images. Readers study deeply."
- "Poster for a film festival. Single statement. Viewers feel, don't read."

## Your task

### Step 1 — Read the knowledge base

Read `knowledge/layout/composition.md` for compositional approaches, anti-patterns, and the layout sketch format.

Read `knowledge/layout/grids.md` for grid types, alignment rules, and responsive behavior.

Read `knowledge/foundations/math.md` § "Ratio-Based Proportions" for deriving layout proportions from the format's own ratio.

### Step 2 — Answer the two core questions

From composition.md:

1. **What is the content's job?**
   - Persuade / inspire → Cinematic
   - Inform / explain → Editorial
   - Orient / navigate → Functional
   - Impress / showcase → Expressive

2. **Who is reading, and how?**
   - Emotional, scanning → large scale, asymmetry, dramatic whitespace
   - Focused, reading → clear columns, generous measure, structured hierarchy
   - Task-driven, scanning → density, alignment lanes, minimal decoration
   - Evaluative, browsing → break the grid, unexpected scale, tension

Write out the answers and the resulting **compositional approach**.

### Step 3 — Plan section variety

For each section in the design, write a 1-line description of its compositional role. No two consecutive sections should share the same structure.

Vary across these axes:
- **Alignment**: left-anchored → centered → right-anchored → full-bleed
- **Proportion**: 50/50 → 70/30 → full-width → contained narrow
- **Density**: spacious → dense → spacious
- **Tone**: dark → light → dark (background color as scene change)

Think of sections as scenes — each needs its own framing.

### Step 4 — Write layout sketches

For each section, write a **layout sketch** — one sentence (or two) describing the specific spatial arrangement. This is the most important step.

The layout sketch describes *where things go*, not *how they feel*:

**Good layout sketches:**
- "Hero text spans 8 of 12 columns left-aligned; CTA group anchored to the bottom-right of the remaining 4 columns with 140px breathing room above"
- "Full-bleed dark section, 3 metrics in a row at 4-col each, numbers at 64px centered above 13px labels, 96px vertical padding"
- "Testimonial quote bleeds 2 columns wider than body text on both sides; attribution right-aligned below, portrait circle overlapping the quote's bottom edge by 40px"

**Bad layout sketches:**
- "Clean hero section with bold typography" (adjectives, no spatial information)
- "Features section with cards" (describes content, not arrangement)
- "Cinematic testimonial area" (mood word, not a layout)

**If you can't describe it in spatial terms, you haven't designed it yet.**

### Step 5 — Identify the scale peak

Every page needs one moment of extreme visual scale — the single largest element. This is usually a hero headline, a feature number, a full-bleed image, or a dramatic whitespace section.

Name it, state its approximate size, and describe why it earns the peak.

### Step 6 — Choose the grid

From grids.md:

| Grid type | When to use |
|-----------|-------------|
| Manuscript | Single long-form reading column |
| Column (2-12) | Most layouts — flexible, structured |
| Modular | Complex layouts with both horizontal and vertical rhythm |
| Hierarchical | Posters, editorial splash, art direction |

Specify: type, column count (if applicable), gutter width, margin width, base spatial unit.

For Paper canvas artboards, derive margins from the format ratio:
- 800px artboard → ~32-40px margins
- 1440px artboard → ~48-80px margins
- 390px mobile → 16-20px margins

### Step 7 — Run the composition checklist

From composition.md, verify:
- [ ] Each section has a describable compositional strategy
- [ ] No two consecutive sections share the same structure
- [ ] At least one moment of extreme scale
- [ ] Centering is used sparingly and intentionally
- [ ] Whitespace rhythm varies — some sections spacious, some dense
- [ ] Background color or tonal shift creates pacing
- [ ] A first-time viewer would know this is designed, not templated

Flag any checklist failures and revise the plan before outputting.

---

## Output format

```
COMPOSITIONAL APPROACH
Content job: [persuade / inform / orient / impress]
Audience mode: [scanning / studying / comparing / feeling]
Approach: [cinematic / editorial / functional / expressive]

GRID
Type: [manuscript / N-column / modular / hierarchical]
Columns: [N] | Gutter: [N]px | Margin: [N]px | Base unit: [N]px

SECTION PLAN
1. [Section name] — [compositional role]
   Layout: [spatial layout sketch]
   Tone: [light/dark] | Density: [spacious/medium/dense]

2. [Section name] — [compositional role]
   Layout: [spatial layout sketch]
   Tone: [light/dark] | Density: [spacious/medium/dense]

[...continue for all sections]

SCALE PEAK
[Element name] — [size]px — [why it earns the peak]

CHECKLIST
[pass/fail for each item, with notes on any revisions made]
```

This output plugs directly into the design brief (Step 4) when used within `/design`.
