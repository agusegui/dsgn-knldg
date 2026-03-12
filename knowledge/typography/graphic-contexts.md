# Graphic Design Contexts — Typographic Logic by Medium

Reference for medium-specific typographic decisions. Consumed by `/type-direct` and `/type-pair`.

---

## Poster / Print

**What this medium demands:**
Typography is the composition. The display face carries the full emotional argument of the piece — it must be strong enough to work alone. Body text, if present, is a subordinate element, not an equal partner.

**Hierarchy logic:**
- Usually 1–2 levels, rarely 3. Depth is visual (scale and weight), not structural.
- The relationship between display and any supporting text is intentional contrast, not smooth transition.
- One typeface is often sufficient. Two should create deliberate tension, not harmony.

**What expressive choices are appropriate:**
- Extreme tracking (very tight on heavy display; very open on light caps) — both are legitimate.
- Weight extremes: ultra-heavy or ultra-thin display faces are natural here.
- Distortion, overlap, and composition-driven type placement.
- Type as image: letterforms as graphic objects.

**Pairing logic:**
- Choose the display face for its *character at scale*, not its legibility at body text size.
- If body text exists, it should recede — a quiet, unobtrusive grotesk or light humanist sans.
- Avoid pairings that create visual equality between levels. The display must dominate.

**Well-proven pairings in this context:**
- Heavy slab + light grotesk (stark industrial contrast)
- Condensed display serif + neutral sans
- Single typeface used at extreme scale contrast across weight

**Avoid:**
- Two expressive faces competing
- Text-weight serifs as display (they lack presence at scale)
- Safe, harmonious pairings — poster typography should argue

---

## Editorial / Publication

**What this medium demands:**
System thinking over individual moments. Typography must work across dozens of pages and multiple content types. Body legibility is non-negotiable. Hierarchy must be deep, consistent, and maintain rhythm across spreads.

**Hierarchy logic:**
- 4–6 levels minimum: display headline, section head, deck/standfirst, body, caption, label.
- Each level must be visually distinct but tonally related.
- Scale rhythm across pages matters more than any single pairing moment.

**What expressive choices are appropriate:**
- Strong display type for cover / feature openers — expressive is earned here.
- Body text faces require rigorous testing at the actual print or screen size.
- White space as editorial voice — generous leading and margins signal quality.

**Pairing logic:**
- Body face choice is the anchor. Choose it first for rhythm, legibility, and warmth at 10–14pt.
- Display can be more opinionated because it appears in bursts. Body must sustain.
- Transitional or humanist text serifs are workhorses here (Freight, Caslon, Minion, FF Meta Serif).
- Avoid purely display faces (Didones at high optical size, swash-heavy scripts) in running text.

**Well-proven pairings in this context:**
- Humanist serif (body) + geometric sans (headers/labels)
- Transitional serif (body) + condensed display serif (headlines)
- Text sans (body) + expressive serif (display) — works in modern magazine contexts

**Avoid:**
- Superfamilies that are too harmonious — editorial type needs textural interest across levels
- Geometric sans at body text size for long-form reading (too mechanical for sustained reading)
- Novelty or decorative faces below deck level

### Content element treatment — editorial context

In editorial design, different content types carry different voices. They should look
different. A blockquote in an editorial essay is not the same as a blockquote in API docs.

**Blockquotes / pull-quotes:**
The quoted voice is the star — often the reason the reader came. Treat accordingly:
- **Scale shift**: Pull-quotes should break the body rhythm. 1.5–2x body size minimum.
  The reader's eye should land here even when scanning.
- **Column break**: Let important quotes push wider than the body column, or indent
  asymmetrically. Breaking the grid signals importance.
- **Voice separation**: Consider a different typeface for quoted text vs. author commentary.
  The quote is someone else's voice — it should feel distinct, not just italicized body.
- **Decorative marks**: An oversized opening quotation mark (" or a custom glyph) anchors
  the quote visually and signals its role instantly.
- **Tonal shift**: A subtle background color or generous vertical padding sets the quote
  apart without needing a heavy border.
- **What to avoid**: Left-border-only treatment is the generic blog default. It's
  acceptable for product docs and utilitarian contexts. In editorial work it reads as
  undesigned — a CSS reset that nobody styled.

**Asides / book references:**
- Inline with imagery when available (book cover, author portrait).
- Smaller type, different weight or style — clearly subordinate but visually interesting.

**Callouts / key statements:**
- Can inherit pull-quote treatment at reduced scale.
- Or use weight/color contrast within the body column rather than breaking out.

The general principle: **the more literary or emotional the content, the more expressive
the element treatment.** Match the design's ambition to the content's ambition.

---

## Brand Identity

**What this medium demands:**
Typeface as voice. The typography must be *ownable* — specific enough to be associated with this entity over time. It must work from wordmark/logotype scale down to fine print, and across all brand touchpoints consistently.

**Hierarchy logic:**
- System versatility: headline, body, UI label, caption — all from the same family or a tightly controlled pair.
- Weight range is critical. A family with 6+ weights enables full brand expression. A 2-weight family forces external pairing.
- The type should feel consistent whether it's on a billboard or a business card.

**What expressive choices are appropriate:**
- Distinctiveness at display scale: cut, optical correction, idiosyncratic letterforms that are memorable.
- The display and body versions can (and often should) come from a single superfamily.
- Custom lettering or modified standards are a brand-specific consideration — flag when a pairing might benefit from optical size variants.

**Pairing logic:**
- Personality consistency across weights is the test. If the Light weight feels like a different brand than the Bold, the family has an identity problem.
- Versatility across media: screen, print, environmental — confirm the face works in all three.
- Avoid faces with licensing restrictions that would limit brand use cases.
- Geometric sans families often work well here — clear, ownable, systematizable (Futura, Neue Haas Grotesk, Aktiv Grotesk, GT Walsheim).

**Well-proven pairings in this context:**
- Superfamily only (one family, multiple weights) — cleanest for brand consistency
- Humanist sans (brand voice) + transitional serif (long-form/editorial subsidiary)
- Geometric display serif + matching geometric sans from same foundry

**Avoid:**
- Novelty or period-specific faces (dates quickly, reduces ownable shelf life)
- Faces too similar in character (no typographic contrast = no visual system)
- Free Google Fonts that every competitor also uses — undermines ownable character

---

## Digital / Web

**What this medium demands:**
Responsive hierarchy, scan-path design, and conversion logic. Typography must work at multiple viewport sizes. Contrast ratios must meet accessibility standards (WCAG AA at minimum). Rendering varies across browsers and operating systems.

**Hierarchy logic:**
- H1–H6 maps to content structure, but visual hierarchy is shaped by scale, weight, and color — not just level.
- Scan path matters: the eye moves in F and Z patterns. Strong display type anchors entry; body structure guides completion.
- Mobile-first often means body size drives everything up — 16px body minimum, generous line-height (1.6–1.75).

**What expressive choices are appropriate:**
- Variable fonts are ideal: single file, responsive weight/width axes, performance advantages.
- System font fallbacks should always be considered even when loading web fonts.
- Display faces on web require testing at target pixel sizes — hinting behavior varies.

**Pairing logic:**
- Web-optimized body faces: Source Serif 4, Lora, Libre Baskerville, Georgia (system), Inter, IBM Plex Sans.
- High-contrast serifs (Bodoni, Didot) lose thin strokes on screen at body size — use only at display scale.
- Contrast ratio: dark text on light must hit 4.5:1 for normal text, 3:1 for large text.
- Performance matters: a second font load adds latency. Justify every additional typeface.

**Well-proven pairings in this context:**
- Humanist sans + transitional serif (versatile, proven legible on screen)
- Geometric sans (display) + humanist sans (body) — all-sans for product UI
- Variable serif (display + body from one file)

**Avoid:**
- Decorative or script faces at body text size
- Faces that render poorly at subpixel sizes — test at 14px before committing
- Pairing two faces with similar x-heights and no weight differentiation
- Loading more than 2 font families + their weights — performance and cognitive overhead

---

## Quick Reference: Medium Comparison

| | Poster | Editorial | Brand | Digital |
|---|---|---|---|---|
| **Hierarchy depth** | 1–2 | 4–6 | 2–4 | 3–5 |
| **Body legibility priority** | Low | Critical | High | Critical |
| **Expressive license** | Maximum | Controlled | Moderate | Low |
| **System coherence needed** | Low | High | Critical | High |
| **Primary selection criterion** | Character at scale | Reading rhythm | Ownable personality | Screen performance |
| **One face sufficient?** | Often | Rarely | Often | Sometimes |
