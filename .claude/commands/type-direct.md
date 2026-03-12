Analyze actual copy to produce a content-aware typographic direction, then render it on the Paper canvas as a real design — not a specimen card.

## Arguments
`$ARGUMENTS` — paste actual copy (headline, body, tagline, or full text block). Optionally suffix with `medium:poster`, `medium:editorial`, `medium:brand`, or `medium:digital` to specify the design medium.

## Your task

### Step 1 — Parse the input

Separate the content from any `medium:` tag in `$ARGUMENTS`.

If no medium is specified, infer it from the content:
- Short punchy headline with no body → likely poster
- Long structured prose with subheadings → likely editorial
- Wordmark-style single name or tagline → likely brand
- Paragraph with CTAs or navigation language → likely digital

### Step 2 — Read the content's register

Before opening the knowledge base, analyze the copy directly. For each dimension, write a one-line observation:

- **Vocabulary**: formal/informal, latinate/germanic, technical/lyrical, sparse/dense
- **Sentence rhythm**: short declarative / long compound / fragmented / flowing
- **Domain**: cultural, commercial, institutional, lyrical, journalistic, civic, scientific
- **Emotional temperature**: cool and distant / warm and intimate / urgent and commanding / playful and light
- **Scale signal**: how long is the text? Short = fewer hierarchy levels needed. Long = full system needed.

This register reading drives the font selection. Write it out explicitly before looking at the knowledge base.

### Step 3 — Read the knowledge base

1. `knowledge/typography/pairings.json` — find 2-3 candidates matching the content register (match primarily on `mood` and `use` fields, secondarily on `tags`). Note their IDs.
2. `knowledge/typography/rules.md` — pull 2-3 principles most relevant to this register and medium.
3. `knowledge/typography/graphic-contexts.md` — read the section for the inferred/specified medium. Note its key demands.
4. `knowledge/foundations/math.md` — read the spacing scale and ratio systems. Use these to inform the layout direction line in the brief.
5. `knowledge/layout/grids.md` — read the agent layout rules (Section 7). Use these to inform grid and spacing decisions.

### Step 4 — Select and justify the pairing

Choose one primary pairing. Write a typographic brief in the chat response:

```
CONTENT REGISTER
Vocabulary: ...
Rhythm: ...
Domain: ...
Temperature: ...

MEDIUM: [poster | editorial | brand | digital]

TYPOGRAPHIC DIRECTION
Display face: [Font Name]
  — Why: [how its character responds to this content]
Supporting face: [Font Name]
  — Why: [how it complements structurally]

SCALE SYSTEM
[Calibrate to content density — short punchy copy = 2–3 levels; dense long-form = 4–5 levels]
  Display: Xpx, weight Y, tracking Z
  Heading: Xpx, weight Y (if needed)
  Body: Xpx, line-height Y
  Caption/label: Xpx, tracking Z (if needed)

LAYOUT DIRECTION
[Grid, base unit, and body measure — e.g. "12-col modular grid, 8px baseline, 680px max-width body measure" or "single column, 8px base unit, 600px max-width, generous vertical spacing"]

SPACING DIRECTION
[One sentence on rhythm, breathing room, or density appropriate to medium]

COLOR DIRECTION
[One sentence — background, text, accent. Should serve the content's temperature.]

INTENT STATEMENT
[2–3 sentences: what the typography is arguing about this content. What it makes the text feel like.]
```

### Step 5 — Verify fonts

Call `get_font_family_info` for both selected faces. Confirm availability and note available weights.

### Step 6 — Render on Paper canvas

Produce TWO artboards side by side: a **meta card** (documentation) and the **real design** (deliverable).

1. Call `get_basic_info` to understand the file.
2. Create both artboards:
   - **Meta card**: 300 × [design height]px. Named `"Meta: [first 3 words]"`. This is the system's notes.
   - **Design artboard**: Sized to the medium (editorial: 800×1100, desktop: 1440×900, mobile: 390×844, poster: 800×1100 or larger). Named after the content. Use `relatedNodeId` to place it to the right of the meta card.

#### Meta card (left)

A compact documentation sidebar. Dark background (#1A1A18), light text. Build in sections:

- **Medium label** — small caps, 10px
- **Font pairing** — display face name (bold) + body face name
- **Scale** — the sizes and weights used, listed compactly
- **Contrast & mood** — from the pairing data
- **Reasoning** — 2-3 sentences: why this pairing for this content
- **Grid** — one line describing the layout structure used

Keep it dense and functional — this is a reference panel, not a design.

#### Design artboard (right)

**This is a real design, not a specimen.** It should look like something that could ship — a magazine page, a website section, a poster, a landing page. No meta-documentation visible. No font names, no mood tags, no system annotations.

Design choices should respond to the medium:

**Editorial:**
- Article opener layout. Headline, deck, attribution, body text.
- Include a placeholder image area (solid muted rectangle with no text — just a tonal block suggesting a photograph) if the layout benefits from one.
- Generous white space. Manuscript or asymmetric column grid.

**Digital / Web:**
- Section or page layout. Hero, body, navigation hints if appropriate.
- Responsive-aware proportions.

**Poster:**
- Display-dominant composition. Type as the primary visual element.
- Minimal body text. Scale contrast is the tool.

**Brand:**
- Wordmark or hero moment. Systematic, ownable feel.

Use the actual content text from the input. Add realistic supporting elements (image placeholders, dividers, pull quotes) that make the layout feel complete — but never fabricate content the user didn't provide.

3. **Apply fonts via `update_styles`** — batch by font family. Never trust write_html for font rendering.
4. **Screenshot at scale 2** to verify the design artboard.
5. Call `finish_working_on_nodes`.

## Output format

The written brief (Step 4) is presented in the chat response. The canvas shows two artboards: meta card (system notes) and design (real deliverable). The design must stand on its own — if the meta card were deleted, the design should still look intentional and complete.

## Judgment rules for content-aware pairing

- **The content is the client.** A lyrical poem needs different typography than a civic announcement with identical mood adjectives.
- **Register beats category.** A technically "warm" sans may feel wrong against terse bureaucratic prose. Trust the content reading.
- **Medium shapes the display logic.** The same content styled for a poster uses weight tension and scale drama. Styled for editorial, it needs system coherence. Styled for brand, it needs ownable character.
- **Short copy = expressive license.** 3 words can handle a more extreme, opinionated display face. 500 words cannot.
- **Avoid demonstrating versatility in the specimen.** The render should argue *one* strong typographic point of view, not a sampler.
- **Design like a designer, not like a system.** The deliverable artboard should look crafted, not generated. Every element should feel placed with intention.
