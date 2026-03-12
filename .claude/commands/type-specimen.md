Create a font pairing specimen card on the Paper canvas.

## Arguments
`$ARGUMENTS` — e.g. `"Playfair Display" "Source Sans 3"` or a pairing slug from pairings.json.

Optional flags:
- `--content "your text here"` — use this text in the specimen instead of placeholder copy
- `--medium poster|editorial|brand|digital` — switches to graphic design layout mode

## Your task

1. **Parse arguments** — extract font names (or slug), and check for `--content` and `--medium` flags. If `--medium` is present, use **graphic design layout mode** (see below). Otherwise use the default reference card layout.

2. **Read knowledge base** — check `knowledge/typography/pairings.json` for existing data on this pairing. If found, use its logic, mood, use case, and typesetting notes. If not found, generate specimen content based on typographic judgment.

3. **Verify fonts** — call `get_font_family_info` for both fonts before writing anything.

4. **Get canvas context** — call `get_basic_info` to understand the current file. Note existing artboards to avoid placement conflicts.

5. **Read `knowledge/foundations/math.md`** for spacing scale and **`knowledge/layout/grids.md`** for layout guidance. The specimen card uses an internal 2-column structure with a fixed label lane on the left. All padding and gap values must be multiples of 8px (e.g. 8, 16, 24, 32, 48px). The 32px side padding used in the card template satisfies this. Do not introduce arbitrary spacing values.

6. **Create the artboard** — 800 × 1100px. Name it `"Heading Font + Body Font"` for reference card mode, or `"[Medium] — Heading Font + Body Font"` for graphic design mode.

7. **Choose the layout and write HTML** using `write_html` with `mode: "insert-children"`, one call per section:

   **Default reference card layout** (no `--medium` flag):
   - Category bar (colored strip with category label)
   - Font names row (heading font in its own face, body font in its own face)
   - Tags row (contrast level + mood pills)
   - Specimen area — use `--content` text if provided, otherwise placeholder. Heading ~36px, subheading ~14px, body paragraph ~14.5px.
   - Rationale section (why this works + use case + contrast metadata)

   **Graphic design layout mode** (`--medium` flag present):
   - Top strip — medium label in small caps monospace + font names in small type (less "card", more "document")
   - Display area — dominant, fills most of the card. Use `--content` text if provided, otherwise use the pairing's mood words as a short display headline. Display type at 72–96px, weight chosen for the medium (heavy for poster, regular for editorial, etc.)
   - Subhead / tagline — if content has a subhead or tagline, show it at 20–24px beneath display
   - Body block — if content includes body text, show it at 15–16px with generous line-height. If no body text provided, write one sentence of direction copy in the body face that feels appropriate to the mood.
   - Bottom panel — font names, contrast level, 2 mood words. Minimal, less metadata than reference card.

8. **Apply fonts via update_styles** — CRITICAL. After all write_html calls, collect every text node ID from the responses and apply fontFamily in a single batched update_styles call. Group by font:
   - Heading font → specimen heading/display, font name display (heading face only)
   - Body font → all other text (category label, tags, subhead, body, rationale, metadata)
   - Keep `monospace` only for: card number (#N), "WHY THIS WORKS", "USE", "CONTRAST" labels, and medium label in GD mode

9. **Screenshot to verify** — call `get_screenshot` on the artboard at scale 2. Confirm both fonts are visually distinct and rendering correctly (serifs visible if serif, distinctive letter shapes present).

10. **Finish** — call `finish_working_on_nodes`.

## Card color system

Use these accent colors per category (or derive a fitting palette if the category is new):

| Category | Accent | Light BG |
|----------|--------|----------|
| Superfamily Harmony | #2D5A27 | #E8F0E6 |
| Classic Contrast | #8B1A1A | #F5E6E6 |
| Tension & Character | #B5651D | #F5EDE0 |
| Calligraphic Echo | #4A3728 | #F0EBE3 |
| Art Deco Echo | #1A1A2E | #E8E8F0 |
| Warm & Grounded | #6B4226 | #F2EBE0 |
| Digital-Native | #0A4D68 | #E0EEF5 |
| Scholarly Elegance | #3C1518 | #F0E6E7 |
| Transitional Warmth | #5C4033 | #EDE8E0 |
| Cross-Cultural | #8B4513 | #F5EBD8 |
| Geometric Precision | #2C3E50 | #E6EBF0 |
| Humanist Continuum | #3E2723 | #EDE7E3 |

For graphic design layout mode, derive a palette from the content's emotional temperature rather than strictly following the category table. A poster context might use near-black + off-white + one accent; an editorial context stays close to the reference card palette.

## HTML card template (reference card — default)

```html
<div style="width:800px;height:1100px;background:#FAFAF7;display:flex;flex-direction:column;padding:0;overflow:hidden;">

  <div layer-name="Category Bar" style="background:{lightBg};padding:14px 32px;border-bottom:1px solid #E4E2DC;display:flex;justify-content:space-between;align-items:center;flex-shrink:0;">
    <span style="font-size:11px;font-weight:700;letter-spacing:0.12em;text-transform:uppercase;color:{accentColor};">{category}</span>
    <span style="font-family:monospace;font-size:11px;color:#999;">#{id}</span>
  </div>

  <div layer-name="Font Names" style="padding:28px 32px 0;display:flex;align-items:baseline;flex-shrink:0;">
    <span style="font-size:24px;font-weight:700;color:#1A1A18;white-space:nowrap;">{headingFont}</span>
    <span style="color:#CCC;font-size:20px;margin:0 10px;flex-shrink:0;">+</span>
    <span style="font-size:18px;color:#555;white-space:nowrap;">{bodyFont}</span>
  </div>

  <div layer-name="Tags" style="padding:12px 32px 0;display:flex;gap:8px;flex-shrink:0;">
    <span style="padding:3px 10px;background:#F0EEE8;border-radius:12px;font-size:11px;color:#777;">Contrast: {contrast}</span>
    <span style="padding:3px 10px;background:#F0EEE8;border-radius:12px;font-size:11px;color:#777;">{mood}</span>
  </div>

  <div layer-name="Specimen" style="padding:32px;margin-top:20px;background:#FCFCFA;border-top:1px solid #F0EEE8;border-bottom:1px solid #F0EEE8;flex:1;">
    <div style="font-size:36px;font-weight:700;line-height:1.15;margin:0 0 8px;color:#1A1A18;letter-spacing:-0.01em;">{sampleHeading}</div>
    <div style="font-size:14px;font-weight:500;color:#888;margin:0 0 18px;">{sampleSub}</div>
    <div style="font-size:14.5px;line-height:1.7;color:#444;max-width:680px;">{sampleBody}</div>
  </div>

  <div layer-name="Rationale" style="padding:24px 32px;background:#F5F4F0;flex-shrink:0;">
    <div style="font-size:11px;font-family:monospace;letter-spacing:0.1em;text-transform:uppercase;color:#999;margin:0 0 8px;">Why this works</div>
    <div style="font-size:13px;line-height:1.65;color:#555;margin:0 0 16px;">{logic}</div>
    <div style="display:flex;gap:40px;">
      <div>
        <div style="font-family:monospace;font-size:10px;color:#999;text-transform:uppercase;letter-spacing:0.08em;">Use</div>
        <div style="margin:4px 0 0;color:#666;font-size:12px;">{use}</div>
      </div>
      <div>
        <div style="font-family:monospace;font-size:10px;color:#999;text-transform:uppercase;letter-spacing:0.08em;">Contrast</div>
        <div style="margin:4px 0 0;color:#666;font-size:12px;">{contrast}</div>
      </div>
    </div>
  </div>
</div>
```

## HTML card template (graphic design layout — `--medium` flag)

```html
<div style="width:800px;height:1100px;background:{bg};display:flex;flex-direction:column;padding:0;overflow:hidden;">

  <div layer-name="Top Strip" style="padding:20px 40px;display:flex;justify-content:space-between;align-items:center;flex-shrink:0;border-bottom:1px solid {borderColor};">
    <span style="font-family:monospace;font-size:10px;letter-spacing:0.14em;text-transform:uppercase;color:{mutedColor};">{medium}</span>
    <span style="font-size:11px;color:{mutedColor};">{headingFont} + {bodyFont}</span>
  </div>

  <div layer-name="Display" style="padding:60px 40px 40px;flex:1;display:flex;flex-direction:column;justify-content:center;">
    <div style="font-size:84px;font-weight:700;line-height:1.0;color:{textColor};letter-spacing:-0.02em;margin:0 0 24px;">{displayText}</div>
    <div style="font-size:22px;font-weight:400;color:{subColor};line-height:1.4;max-width:620px;">{taglineText}</div>
  </div>

  <div layer-name="Body Block" style="padding:0 40px 48px;flex-shrink:0;">
    <div style="font-size:15.5px;line-height:1.72;color:{bodyColor};max-width:640px;">{bodyText}</div>
  </div>

  <div layer-name="Bottom Panel" style="padding:20px 40px;border-top:1px solid {borderColor};display:flex;gap:32px;align-items:center;flex-shrink:0;">
    <span style="font-size:11px;font-weight:600;color:{textColor};">{headingFont}</span>
    <span style="font-size:11px;color:{mutedColor};">+</span>
    <span style="font-size:11px;color:{subColor};">{bodyFont}</span>
    <span style="margin-left:auto;font-size:10px;font-family:monospace;letter-spacing:0.08em;text-transform:uppercase;color:{mutedColor};">{contrast} · {mood1} · {mood2}</span>
  </div>
</div>
```

Note: font-family is intentionally omitted from the HTML — it will be applied via update_styles after creation.
