# design-principles

A modular design knowledge system for teaching agents how to design better.
Built on curated knowledge, mathematical foundations, and Paper MCP canvas integration.

## System philosophy

This system is **descriptive, not prescriptive**. It presents options with context so the
agent (or designer) can make informed decisions. The only prescriptive rules are true
universals (e.g., 4-8px spacing for web, minimum contrast ratios).

The system grows organically through conversation. When the user shares insights, corrections,
articles, or preferences during any conversation, extract and file the knowledge into the
appropriate module. No special syntax required — listen for knowledge pills naturally.

### Universals vs. principles

The system distinguishes two levels of authority:

- **Universal** — non-negotiable. Backed by accessibility standards (WCAG), readability
  research, or usability evidence with no valid counterargument. Marked with `> **Universal:**`
  blockquotes or under `## Universals` headings. An agent must never reason its way out of
  a universal.
- **Principle** — strong default. Almost always correct, but context can override. The agent
  can depart from a principle when it has a specific reason tied to the content, audience,
  or medium. Everything not marked as a universal is a principle.

When adding knowledge, consider which level it belongs to. Most design knowledge is
principles. Universals are rare — if you're unsure, it's a principle.

---

## Module structure

```
knowledge/
  foundations/       <- math: scales, ratios, spacing systems
    math.md
  typography/        <- pairings, rules, classifications, contexts
    pairings.json
    rules.md
    classifications.md
    typesetting.md
    graphic-contexts.md
    sources.md
  layout/            <- grids, spacing, composition, responsive
    grids.md
    composition.md
    sources.md
  ui/                <- component states, interaction patterns, visual awareness
    states.md
    patterns.md
    sources.md
  color/             (future)
  hierarchy/         (future)
```

### Module relationships

- **Foundations** is the shared math layer. All other modules reference it for scale
  derivation, spatial rhythm, and proportional logic.
- **Typography** and **Layout** are distinct disciplines that share the math layer.
  Typography concerns typeface selection, pairing, and typesetting. Layout concerns
  grid structure, spatial composition, and responsive behavior.
- **UI** concerns how interactive elements behave — component states, interaction
  patterns, and visual awareness. It intersects with layout (density, affordances)
  and typography (labels, error messages) but focuses on behavior and response.
- Each module tracks its own **sources**.

---

## Skills available

| Skill | Purpose |
|-------|---------|
| `/design` | Full design workflow — knowledge pass, brief, build on canvas |
| `/design-review` | Post-build audit against all knowledge modules |
| `/type-pair` | Suggest font pairings for a use case |
| `/type-specimen` | Create a specimen card on the Paper canvas |
| `/type-direct` | Analyze actual copy, produce a typographic direction, render on canvas |
| `/scale` | Derive a type scale and spacing system from content character |
| `/compose` | Plan layout composition — approach, section plan, layout sketches |
| `/palette` | Derive a color palette from content character |

---

## Knowledge loop

This system learns from conversation. When working in this folder:

1. **Listen for knowledge pills** — insights, corrections, preferences, rules shared by the
   user during normal conversation. These don't need special formatting.
2. **Offer to file them** — when you detect actionable knowledge, confirm with the user
   before writing it into a module. Say what you'd add and where.
3. **Route to the right module** — infer whether it's foundations (math, universal), typography,
   layout, or a future module based on content.
4. **Update, don't duplicate** — check existing files before adding. If a rule already exists,
   refine it rather than creating a new entry.
5. **Canvas feedback loop** — when working on the Paper canvas, use the results (what worked,
   what didn't) to inform the knowledge base. If a spacing value or pairing consistently
   fails in practice, note it.

---

## Paper MCP — Critical Workflow Rules

### Non-destructive canvas work — absolute rule

**Never delete an artboard to replace it with a new version.** Always create new artboards
alongside existing ones. The user's canvas is their working surface — destroying previous
iterations removes context they need for comparison, decision-making, and iteration history.

When exploring a new direction:
1. Create a new artboard next to the existing one.
2. Name it clearly to distinguish versions (e.g. "v2 — Editorial", "v3 — Dark Cinematic").
3. Let the user decide what to keep or discard.

This applies even when the user criticizes a design — "improve this" means iterate, not replace.

### Pre-design knowledge pass — mandatory

> **Universal:** Before writing any HTML for a new design, complete the full knowledge pass
> below. Each step consults a specific module in the `knowledge/` folder. The design brief
> is the output. Do not start building until the brief is complete.
>
> This system only adds value when every layer is engaged. Skipping a module produces
> the same result as not having it. That defeats the entire purpose of this project.

**Step 1: Content character** *(from brief or context)*
- Extract and write down: tone, audience, emotional register, era, medium, cultural context
- This drives every subsequent decision — do not rush it

**Step 2: Typography** → `knowledge/typography/`
- Read `rules.md` § "Typeface selection — derive from content, not habit"
- Consult `pairings.json` — search by mood tags, use-case tags, and classification
- Or run `/type-pair` with the content character keywords from Step 1
- Apply the **3-candidate process**: name 3 pairings, 1 sentence each, choose and justify
- Check `classifications.md` → what form model does each candidate use? Does the pairing
  cross form models intentionally (Dynamic + Geometric = productive tension) or accidentally?
- Check `typesetting.md` → what context scale fits? (Brand, Editorial, Product UI)
- Check `graphic-contexts.md` → what does this medium demand?
- Verify availability with `get_font_family_info`
- **Output for brief:** Pairing name, pairings.json ID or /type-pair source, reasoning,
  form model analysis, typesetting scale

**Step 3: Scale & spacing** → `knowledge/foundations/math.md`
- Choose a **scale ratio** based on the content's emotional register and hierarchy depth
  (e.g. Perfect Fourth 1.333 for strong hierarchy, Golden Section 1.618 for dramatic)
- Derive the full **type scale** from base size + ratio (round to whole pixels)
- Set **spacing rhythm**: section padding, group gaps, element gaps — derived from the
  same base unit or an 8px spatial grid
- **Output for brief:** Ratio name + value, base size, derived scale table, spacing values

**Step 4: Layout & composition** → `knowledge/layout/`
- Consult `composition.md` → answer the two core questions:
  1. What is the content's job? (persuade / inform / orient / impress)
  2. Who is reading, and how? (scanning / studying / comparing / feeling)
- Derive **compositional approach** (cinematic / editorial / functional / expressive)
- Plan **section variety** — 1-line description per section, no two consecutive sections
  share the same structure
- Write a **layout sketch** per section — describe spatial arrangement in concrete terms,
  not adjectives. See `composition.md` § "Layout sketch" for the format and examples.
- Identify **scale peak** — the single largest visual moment on the page
- Consult `grids.md` → what grid type fits? (manuscript / column / modular / hierarchical)
- **Output for brief:** Compositional approach, layout sketch, scale peak, grid choice

**Step 5: Color palette** *(future module — use judgment + content character)*
- 5–6 hex values with named roles (background, text, accent, secondary, dark, card)
- Derive from content, brand assets, and imagery — not from habit
- Warm backgrounds need warm text colors (see `typography/rules.md` § Color and contrast)
- **Output for brief:** Palette with roles

**Step 6: Asset inventory** *(from canvas or user context)*
- Inventory all available images, illustrations, icons, patterns
- For each asset, assign a role per deliverable:
  **Hero** (dominant), **Background** (overlay/texture), **Inline** (content flow), **Omitted**
- Faces and portraits are powerful on impression surfaces — almost never omit when available
- For multiple deliverables, write a separate 1-line creative direction per format:
  Reading surfaces → clarity-first | Impression surfaces → impact-first | Functional → density
- **Output for brief:** Asset list with roles, per-format direction if multi-deliverable

**Step 7: UI patterns** → `knowledge/ui/` *(if design includes interactive elements)*
- Consult `states.md` → which states matter for this design's components?
  (default, hover, focus, active, disabled, loading, error, success)
- Consult `patterns.md` → check universals (contrast ratios, color independence,
  persistent labels, touch targets)
- Only required for designs with buttons, forms, navigation, or interactive components
- **Output for brief:** Key state decisions, accessibility considerations

### The design brief

The brief is the output of the knowledge pass. It must contain:

1. **Content character** (Step 1)
2. **Typography** — pairing, source, reasoning, form model, scale (Step 2)
3. **Scale & spacing** — ratio, derived scale, spacing rhythm (Step 3)
4. **Composition** — approach, section plan, scale peak, grid (Step 4)
5. **Color palette** — hex values with roles (Step 5)
6. **Asset inventory** — assets with roles, format directions (Step 6)
7. **UI patterns** — state/accessibility decisions (Step 7, if applicable)

**A brief missing any applicable section is incomplete. Do not write HTML until it's done.**

### Red flags that indicate the knowledge pass was skipped

- Reaching for DM Serif Display + DM Sans, Inter, or any superfamily without checking
  whether the content demands more personality
- Reaching for Oswald, Bebas Neue, Montserrat, or other overexposed display faces
  without the 3-candidate process producing them as the justified winner
- No scale ratio mentioned — sizes chosen by "feel" instead of derived from math
- Compositional approach not stated — sections default to centered stacks
- Same pairing, spacing, or palette reused across unrelated projects
- No reference to any `knowledge/` file in the reasoning
- Layout sketch missing or uses only adjectives ("cinematic", "clean") instead of
  spatial relationships ("overlaps", "bleeds full-width", "offset 2 columns right")

### Clone hygiene — mandatory post-clone step

> **Universal:** After cloning any node from the canvas into a new design, immediately
> audit and restyle all inherited text within the clone.

Cloned nodes carry their original styles — font family, color, size, weight. These
almost never match the new design's typographic system. `system-ui` or `sans-serif`
text surviving into a finished design is a process failure.

**After every clone operation:**
1. Identify all Text nodes within the cloned subtree
2. Restyle font-family, font-weight, font-size, color to match the design brief
3. Remove or restyle any artifact backgrounds (gray fills from placeholder frames)
4. Verify with a screenshot before moving on

This step is not optional. A design with mixed font systems looks broken regardless
of how strong the layout is. [added after a session where cloned product cards kept
system-ui fonts and gray backgrounds through to the final design]

### Font verification

Before writing with a new pairing, confirm availability:
```
get_font_family_info(["Font Name One", "Font Name Two"])
```
All Google Fonts are available in Paper by unquoted family name. Local system fonts vary.

### Artboard sizing defaults

- Specimen card: 800 x 1100px
- Mobile preview: 390 x 844px
- Desktop preview: 1440 x 900px

### Screenshot for verification

After applying fonts, always screenshot the specimen node at scale 2 to verify rendering:
```
get_screenshot(nodeId, scale: 2)
```

### Text hygiene — mandatory post-write step

After writing any text block, **before moving on to the next group:**

1. Apply `textWrap: "balance"` to all headings, hero text, blockquotes, and short-measure blocks.
2. Apply `textWrap: "pretty"` to all body paragraphs.
3. **Never adjust container width to fix text reflow.** Changing a container's width to
   balance a headline breaks vertical alignment with other content in the same column.
   Use CSS `text-wrap` instead — it adapts without side effects.

These rules exist in `knowledge/typography/typesetting.md`. Consult that file if unsure.

---

## Pairing data schema

When adding to `typography/pairings.json`, use this shape:

```json
{
  "id": "unique-slug",
  "heading": "Font Name",
  "body": "Font Name",
  "headingClass": "classification-slug",
  "bodyClass": "classification-slug",
  "classConfidence": "high | medium | low",
  "category": "Category Label",
  "contrast": "Low | Low-Medium | Medium | Medium-High | High | Very High",
  "mood": ["word1", "word2", "word3"],
  "use": ["context1", "context2"],
  "avoid": ["situation1"],
  "logic": "Why the pairing works — the typographic reasoning.",
  "typesetting": {
    "headingSize": "36-72px",
    "bodySize": "14-16px",
    "lineHeight": "1.6-1.75",
    "notes": "Any size-specific considerations."
  },
  "sources": ["url or 'personal'"],
  "tags": ["serif+sans", "superfamily", "high-contrast"]
}
```

Classification slugs: `humanist-serif`, `transitional-serif`, `rational-serif`,
`contemporary-serif`, `inscribed-serif`, `humanist-sans`, `grotesque-sans`,
`neo-grotesque-sans`, `gothic-sans`, `geometric-sans`
