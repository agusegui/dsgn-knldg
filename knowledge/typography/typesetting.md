# Typesetting Systems

Context-specific type scale guidance. For scale math and ratios, see `../foundations/math.md`.

---

## Context Scales

### Editorial (magazine, longform, cultural)

Recommended ratio: Major Third (1.250) to Perfect Fourth (1.333).

```
Display:    56-80px   weight 700-900   tracking -0.02em   leading 1.05
H1:         36-48px   weight 700       tracking -0.01em   leading 1.15
H2:         24-28px   weight 600       tracking 0         leading 1.25
Subhead:    15-16px   weight 500       tracking 0         leading 1.45
Body:       15-16px   weight 400       tracking 0         leading 1.7
Caption:    12-13px   weight 400       tracking 0.02em    leading 1.5
Label:      10-11px   weight 600       tracking 0.1em     ALL CAPS
```

### Product UI (SaaS, apps, dashboards)

Recommended ratio: Minor Second (1.067) to Minor Third (1.200), or 4px interval.

```
Page title: 24-32px   weight 600-700   tracking -0.01em   leading 1.2
Section H:  18-20px   weight 600       tracking 0         leading 1.3
Body:       14-15px   weight 400       tracking 0         leading 1.55
Small body: 13px      weight 400       tracking 0         leading 1.5
Label:      11-12px   weight 500-600   tracking 0.04em    leading 1.4
Micro:      10px      weight 500       tracking 0.08em    ALL CAPS only
```

### Brand / Landing Page

Recommended ratio: Augmented Fourth (1.414) to Golden Section (1.618).

```
Hero:       72-120px  weight 700-900   tracking -0.03em   leading 0.95-1.05
H1:         48-64px   weight 700       tracking -0.02em   leading 1.1
H2:         32-40px   weight 600-700   tracking -0.01em   leading 1.15
Body:       16-18px   weight 400       tracking 0         leading 1.7
CTA label:  14-16px   weight 600       tracking 0.05em    leading 1
```

### Mobile (390px viewport)

Reduce display sizes by ~20%. Body text never below 14px.
Line heights slightly tighter due to shorter line lengths (1.55-1.65 for body).

---

## Responsive Scaling

Don't scale everything linearly. Body text stays stable; headings and display scale.

```
             Mobile   Tablet   Desktop
Body text:   15px     15px     16px
H1:          28px     36px     48px
Display:     40px     56px     80px
```

---

## Widows & Orphans

**Widow** — a single word (or very short fragment) stranded alone on the last line of a text block.
**Orphan** — a single line of a paragraph isolated at the top or bottom of a column or page.

In static design and web layout, widows are the more common offender — especially in
centered hero copy, captions, and short-measure text blocks.

### The CSS-first fix

Modern CSS handles this automatically and should be the default approach in production:

```css
/* Headings, hero text, short blocks — balances line lengths evenly */
text-wrap: balance;

/* Body paragraphs — optimizes last-line breaks to prevent widows */
text-wrap: pretty;
```

`balance` redistributes text so no line is dramatically shorter than others — ideal for
headlines and centered copy. `pretty` is lighter-touch: it only intervenes to prevent
widows, preserving normal rag otherwise. Both are supported in all modern browsers.

**Prefer these over manual max-width hacks or `&nbsp;` tricks.** They adapt to viewport
changes, font loading, and dynamic content — manual fixes don't.

**Paper supports `text-wrap: balance`** — both via inline styles in `write_html` and via
`update_styles` with `{ textWrap: "balance" }`. Use it on all centered hero text and
short-measure blocks. Confirmed working March 2026.

### Fallback for design tools without text-wrap support

When working in tools where CSS text-wrap isn't available:

1. **Micro-edit copy** — add or remove a word to shift the break naturally.
2. **Adjust the text element's own width** — widen or narrow the text box itself, not its
   parent container. Changing a container's width to fix one child's text reflow will
   misalign other children in the same layout column.
3. **Soft line break** — force a break at a better position (last resort, fragile).

**Never adjust a shared container's width to fix a single text element's reflow.**
This is the most common mistake — it solves the widow but breaks vertical alignment
with sibling content. Always prefer `text-wrap` or text-element-level adjustments.

### Where to watch for widows

- Centered hero headlines and subtitles (most visible)
- Card descriptions and captions at constrained widths
- Pull quotes and callout text
- Any text block under ~60 characters per line

---

## Universals

Rules backed by readability research or accessibility standards. Not style preferences.

- **Body text must be 14px or above on screen.** Below 14px, most text faces lose
  legibility. 16px is the accessibility-recommended baseline. [WCAG, readability research]
- **Line height on body text must be at least 1.4.** Below this, lines collide visually
  and reading speed drops measurably. 1.5+ is preferred; see line height section above
  for context-specific guidance. [WCAG 1.4.12]
- **Negative letter-spacing on body text is always harmful.** It reduces legibility at
  reading sizes. Negative tracking is a display-size tool only (48px+).
- **All-caps text requires positive tracking.** Caps with zero or negative tracking reads
  as a mistake. Minimum 0.04em; see size and scale section above.
- **Display-only faces must not be used at body size.** High-contrast serif faces
  (Bodoni, Didone, Cormorant below 15px) lose their thin strokes on screen. Use them
  at 28px+ only.

---

## Common Mistakes

Patterns that are almost always wrong but have occasional valid exceptions. If you're
reaching for one of these, have a reason.

- Two heading levels with less than 4px difference in size — creates ambiguous hierarchy
- Pure black (#000000) body text on pure white — harsh contrast that fatigues readers
  over long passages. Near-blacks (#1A1A1A, #222) are gentler. *Exception: short UI
  labels, high-density interfaces, and brand systems that use true black deliberately.*
- More than 3 different font weights of the same face in active use — usually means
  hierarchy is being built through weight collection rather than clear differentiation.
  *Exception: information-dense UIs (dashboards, data tools) may need 4–5 weights to
  serve distinct roles.*
- Body font used at display size without verifying it holds up — text-optimized faces
  can look bland or structurally weak at large sizes
- Widows in hero/centered text — use `text-wrap: balance` in Paper and production
- Not using `text-wrap: pretty` on body paragraphs
- Adjusting a parent container's width to fix a child's text reflow — breaks sibling alignment
