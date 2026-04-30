Run the full design workflow: analyze content, consult every knowledge module, produce a structured design brief, then build on the Paper canvas.

Use this skill whenever starting a new design from scratch, building a landing page, creating a layout, or whenever the task involves designing something visual that will be rendered on the Paper canvas. This is the master workflow — it ensures every design decision is grounded in the knowledge system rather than habit.

## Arguments
`$ARGUMENTS` — description of what to design. Can include: the content/copy itself, the purpose, the audience, the medium, brand context, or any constraints. The more context, the better the brief.

If actual copy is provided, use it. If only a description is provided, work with that context to make informed decisions — but flag to the user where real copy would sharpen the choices.

## Why this workflow exists

Every step below consults a specific knowledge module. Skipping a step means that module's intelligence doesn't reach the design. The system only adds value when every layer is engaged — a design that skips the composition pass will default to centered stacks; one that skips the scale pass will pick sizes by feel instead of deriving them from math.

The brief is the design. The HTML is just execution.

---

## Step 1 — Content character

Before opening any knowledge file, read the content (or description) and write down:

- **Tone**: formal / informal / intimate / authoritative / playful / urgent
- **Audience**: who reads this, what do they expect?
- **Emotional register**: what should this *feel* like?
- **Era / cultural context**: does this reference a period, movement, or tradition?
- **Medium**: poster / editorial / brand / digital — infer if not stated
- **Scale signal**: how much content? Short = fewer hierarchy levels. Long = full system.

This drives every subsequent decision. Do not rush it — a misread here cascades through every choice below.

### Track inference

After characterizing the content, infer the **design track** — this gates which color philosophy and which sub-skills apply later:

- **Product / software** — SaaS UI, dashboards, design systems, mobile/web apps, Tailwind themes, product marketing pages where the surface is the product. Color: systematic, OKLCH-suitable.
- **Brand / editorial / print / content / marketing** — posters, editorial spreads, brand systems, decks, magazine-style content, marketing where the visual carries cultural or emotional reference. Color: mood-driven, scene-derived.

**Always state your inference and the signal that drove it**, then proceed unless the user corrects you. Examples:

> "I read this as **product track** because the brief mentions design tokens, dashboards, and a Tailwind theme."

> "I read this as **brand track** because this is a poster for a literary press with a 1960s reference."

For genuinely ambiguous briefs (e.g. a SaaS marketing landing page where brand expression matters as much as product clarity), ask the user explicitly which track to commit to.

If the track is **product**, surface this one-line note and continue: *"OKLCH may apply at Step 5. The canonical tool is `/oklch-skill` by Jakub Krehel — install with `npx skills add jakubkrehel/oklch-skill` if not present. See `../core/color/oklch.md` for when it applies."*

---

## Step 2 — Typography

**Consult:** `../core/typography/rules.md`, `../core/typography/pairings.json`, `../core/typography/classifications.md`, `../core/typography/typesetting.md`, `../core/typography/graphic-contexts.md`

Or run `/type-pair [content character keywords]` to get 3 ranked candidates with reasoning.

**The 3-candidate process is mandatory:**
1. Name 3 pairing candidates. Each must respond to the content character differently.
2. At least one candidate should feel unexpected — if all three are from the same genre, the process hasn't worked.
3. For each candidate, write: pairing names, why it fits this content, form model analysis (from `classifications.md`), and medium fit.
4. Choose one. State why it wins.

**Verify availability:** call `get_font_family_info` for both selected fonts before proceeding.

**Output for brief:** Pairing, source (pairings.json ID or reasoned), reasoning, form model, medium fit.

---

## Step 3 — Scale & spacing

**Consult:** `../core/foundations/math.md`

Or run `/scale [content character keywords]` to derive the full system.

1. Choose a **scale ratio** based on the content's emotional register and hierarchy depth (see the ratio table in math.md — Perfect Fourth 1.333 for strong hierarchy, Golden Section 1.618 for dramatic/organic).
2. Set a **base size** (usually 16px for web, 15px for editorial, 14px for product UI).
3. Derive the full **type scale**: multiply up for headings, divide down for captions. Round to whole pixels.
4. Set **spacing rhythm** from the same base unit or an 8px grid: section padding, group gaps, element gaps. Use the spatial token scale from math.md.

**Output for brief:** Ratio name + value, base size, derived scale table (level → size, weight, leading, tracking), spacing token values.

---

## Step 4 — Layout & composition

**Consult:** `../core/layout/composition.md`, `../core/layout/grids.md`

Or run `/compose [content character + medium]` to plan the full composition.

1. Answer the two core questions from composition.md:
   - What is the content's job? (persuade / inform / orient / impress)
   - Who is reading, and how? (scanning / studying / comparing / feeling)
2. Derive the **compositional approach**: cinematic / editorial / functional / expressive
3. **Define the component vocabulary** (see composition.md § "Component architecture"):
   - Name 2-4 component types the page will reuse (e.g., feature card, content block, media block)
   - For each: surface treatment (bg, radius, padding), internal type hierarchy, size range
   - Decide containment: which content groups live in cards vs. directly on the section surface?
   - Plan asset integration: which images go inside components (structural) vs. standalone (decorative)?
4. Plan **section variety** — 1-line description per section. Sections vary *arrangement* of components, not the components themselves.
5. Write a **layout sketch** per section — describe spatial arrangement in concrete terms, not adjectives. Include which components from the vocabulary appear and at what size. (See composition.md § "Layout sketch" for format.)
6. Identify the **scale peak** — the single largest visual moment on the page.
7. Choose a **grid**: manuscript / column / modular / hierarchical (consult grids.md).

**Output for brief:** Compositional approach, component vocabulary, section plan with layout sketches, scale peak, grid choice with column count/gutter/margin.

---

## Step 5 — Color palette (router by track)

**Consult:** `../core/color/README.md` for the philosophy split. Then route by track from Step 1.

### Brand / editorial / print / content / marketing track

**Consult:** `../core/color/mood-scene.md`. Or run `/palette [content character keywords]`.

Method:
1. Commit to a **mood word** — a physical condition or register (mineral, candlelit, bookish, signage, etc). The full mood library lives in the Paper MCP guide.
2. Derive every color from a specific object in that scene. If you can't name a real reference for a role, the palette is abstract and will feel glued together.
3. Define 5–6 colors with named roles (background, text, secondary, accent, dark, surface).
4. Verify temperature consistency — warm grounds need warm grays.
5. Verify WCAG AA contrast (4.5:1 normal, 3:1 large).

**Output for brief:** mood word, scene reference, 5–6 hex values with named roles + object references, contrast check.

### Product / software / design system track

**Consult:** `../core/color/oklch.md` for the integration rules and decision logic.

This system **delegates** to `/oklch-skill` (by Jakub Krehel — `https://github.com/jakubkrehel/oklch-skill`) for systematic palettes. `/design` provides:

- The **base color(s)** — derived from content character or supplied by the brand
- **Role assignment** — which step in the ramp serves background, surface, text, accent
- **Integration with the brief**

`/oklch-skill` provides:

- The lightness ramp (50–950) with perceptual uniformity
- Multi-hue palettes with consistent chroma percentage
- Dark mode derivation
- Contrast remediation via L
- Gamut clamping and Tailwind v4 `@theme` patterns

**Routing logic:**

| Situation | Action |
|---|---|
| `/oklch-skill` is available in the skills list | Hand off explicitly: "Use `/oklch-skill` to generate the ramp from base color [X] at chroma [Y%]." |
| `/oklch-skill` not installed | Mention once: "OKLCH is the right tool here — install with `npx skills add jakubkrehel/oklch-skill`." Then offer the mood-driven fallback or proceed with manual oklch values from `../core/color/oklch.md` reference patterns. |
| User provides an existing palette to audit | Always point to `/oklch-skill` regardless of original track. Its hue-drift, contrast-via-L, and gamut diagnostics are the right tools. |

**Output for brief:** base color(s), role assignment for each step, palette ramp output (or pointer to `/oklch-skill` output), contrast verification.

### Universals (both tracks)

- Color is never the sole information carrier — pair with shape, weight, position, label.
- WCAG AA contrast: 4.5:1 normal text, 3:1 large text and non-text UI.

---

## Step 6 — Asset inventory

Inventory all available images, illustrations, icons, patterns from the canvas or user context.

For each asset, assign a role:
- **Hero** (dominant visual)
- **Background** (overlay/texture)
- **Inline** (content flow)
- **Omitted** (doesn't serve this design)

Faces and portraits are powerful on impression surfaces — almost never omit when available.

For multiple deliverables, write a 1-line creative direction per format:
- Reading surfaces → clarity-first
- Impression surfaces → impact-first
- Functional surfaces → density-first

**Output for brief:** Asset list with roles. If no assets provided, note this and suggest what types would strengthen the design.

---

## Step 7 — UI patterns (if interactive)

**Consult:** `../core/ui/states.md`, `../core/ui/patterns.md`

Only required when the design includes buttons, forms, navigation, or interactive components.

1. Which states matter for this design's components? (default, hover, focus, active, disabled, loading, error, success)
2. Check universals: contrast ratios (4.5:1 normal text, 3:1 large), color independence, persistent labels, touch targets.
3. Identify key accessibility considerations.

**Output for brief:** State decisions, interactive patterns, accessibility notes.

---

## The design brief

Compile all outputs into a single brief. Present it to the user before building. The brief must contain:

1. **Content character** (Step 1) — including the inferred **track** (product or brand) and the signal that drove the inference
2. **Typography** — pairing, reasoning, form model, scale context (Step 2)
3. **Scale & spacing** — ratio, base size, derived scale table, spacing tokens (Step 3)
4. **Composition** — approach, section plan with layout sketches, scale peak, grid (Step 4)
5. **Color palette** — for brand track: mood word + scene + hex with roles. For product track: base color, role assignment, and either OKLCH ramp output (if `/oklch-skill` available) or a clear note that it would benefit from one. (Step 5)
6. **Asset inventory** — assets with roles (Step 6)
7. **UI patterns** — state/accessibility decisions (Step 7, if applicable)

**A brief missing any applicable section is incomplete. Do not write HTML until it's done.**

---

## Building on Paper canvas

Once the brief is complete and the user approves:

### Canvas setup
1. Call `get_basic_info` to understand the current file and existing artboards.
2. Create artboard(s) sized to the medium:
   - Mobile: 390 x 844px
   - Desktop: 1440 x 900px
   - Editorial/Poster: 800 x 1100px
   - Or custom dimensions if the brief specifies
3. Name artboards clearly — include version if iterating (e.g., "v2 — Editorial Dark").
4. **Never delete existing artboards.** Always create new ones alongside.

### Build pass
1. Write HTML section by section using `write_html` with `mode: "insert-children"`.
2. Follow the layout sketches from the brief — each section's spatial arrangement was already designed.
3. All spacing values must come from the scale tokens in the brief.
4. Body text `max-width` must constrain to 55-75ch (~550-680px).

### Font application
After all HTML is written, apply fonts via `update_styles` in a single batched call per font family. Never rely on `write_html` for font rendering.

### Text hygiene
After writing each text block:
- Apply `textWrap: "balance"` to all headings, hero text, blockquotes, short-measure blocks.
- Apply `textWrap: "pretty"` to all body paragraphs.
- Never adjust container width to fix text reflow.

### Clone hygiene
If cloning any node from the canvas: immediately audit and restyle all inherited text within the clone. Cloned nodes carry their original styles — font family, color, size, weight — and these almost never match the new design's system.

### Screenshot verification
Call `get_screenshot` on the artboard at scale 2. Verify:
- Both fonts are rendering correctly (serifs visible, distinctive letterforms present)
- Scale hierarchy is clear
- Spacing rhythm follows the brief's tokens
- No system-ui or sans-serif fallback text survived

### Finish
Call `finish_working_on_nodes`.

---

## Red flags — signs the workflow was skipped

- Reaching for familiar typefaces (DM Serif Display + DM Sans, Inter, Montserrat) without the 3-candidate process producing them as the justified winner
- No scale ratio mentioned — sizes chosen by feel
- Compositional approach not stated — sections default to centered stacks
- Layout sketch missing or uses adjectives ("cinematic", "clean") instead of spatial relationships ("overlaps", "bleeds full-width", "offset 2 columns right")
- Same pairing, spacing, or palette reused across unrelated projects
- No reference to any `../core/` file in the reasoning
- **Track not stated at Step 1** — the brief jumps straight to typography without committing to product or brand
- **Mood-driven palette applied to a product UI brief** (e.g. SaaS dashboard styled with a candlelit-amber palette and no perceptual ramp)
- **OKLCH applied to editorial / poster / brand work** where the mood-and-scene method was the right tool
