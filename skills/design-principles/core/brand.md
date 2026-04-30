# Brand

Brand identity universals — the rules that apply once a positioning, palette, and type
choice are made. This module is *operational*: how to build a wordmark, an app icon, and
brand applications. For palette derivation see `color/mood-scene.md`. For type pairing
see `typography/pairings.json` and `typography/rules.md`.

---

## Universals

> **Universal:** Positioning precedes visuals. A wordmark designed before audience and
> tone are locked is decoration, not identity. Always answer "who is this for and what
> register is it in" before drawing.

> **Universal:** Identity components must hold up at extreme sizes — wordmark legible
> at 16px (browser tab) and 200px (poster); app icon legible at 60px (home screen) and
> 1024px (App Store master). If a mark only works at one size, it isn't an identity.

> **Universal:** App icon master is 1024×1024px, square, with no transparency. iOS will
> mask to a rounded square; Android may mask to circle, squircle, or rounded square
> depending on launcher. Design with a 12% safe inset on all sides so launcher masks
> never crop critical detail.

---

## Identity components

A brand system has a small, named set of identity components. Most apps need only three:

| Component | What it is | When it appears |
|-----------|------------|-----------------|
| **Wordmark** | The name set in the brand's display type, with custom tracking and optical adjustments | Headers, splash, marketing — anywhere the brand name is the brand |
| **Symbol / mark** | A standalone glyph (letterform, abstract shape, or icon) | App icon, favicon, monogram contexts where the wordmark won't fit |
| **Lockup** | Wordmark + symbol composed in a fixed relationship | Marketing, deck headers, partnership applications |

A brand can ship without a symbol if the wordmark is strong enough to also serve as the
app icon (a single-letter monogram derived from the wordmark is a common solution).

---

## Wordmark construction

A wordmark is the brand name set in a chosen display face, with deliberate adjustments
beyond what default type-setting produces.

**Process:**
1. Set the name at large size in the chosen display face — start at 200px+
2. Examine letterform pairs — adjust kerning where letter shapes create awkward gaps
   or collisions (T+a, V+a, W+o, P+a, L+y are common offenders)
3. Decide tracking — display type usually wants tighter tracking (-0.01em to -0.03em)
4. Consider optical alignment — periods, slashes, italics may need to shift baselines
5. Check at small sizes (16px, 24px, 32px) — does it hold up, or do letterforms collapse?
6. Lock it as a single shape — once final, treat it as an asset, not a re-typed string

**Keep:**
- Single weight (display weight, not body weight)
- Single case (all-caps, all-lowercase, or sentence — pick one and commit)
- Color from the brand palette (usually primary text color or primary accent)

**Avoid:**
- Multiple weights mid-name (looks indecisive)
- Drop shadows, gradients, outlines — these date wordmarks fast
- Forced unique letterforms unless the brand voice is genuinely playful (custom swashes
  on a "serious" brand read as branding-by-committee)

---

## App icon

The app icon is the brand at its smallest persistent size. Constraints are heavy:

**Master**: 1024×1024, no transparency, no rounded corners (the OS adds them).

**Visual safe area**: 12% inset on all sides → critical detail lives within the central
788×788 region.

**Detail floor**: Anything thinner than 8px at master scale will disappear at 60px.
Avoid hairlines, thin outlines, fine illustration.

**Contrast**: The icon must read on the user's home-screen wallpaper, which can be
anything. A high-contrast figure-on-ground composition (saturated mark on solid
background) is the safest pattern.

**Patterns that work:**
- **Monogram on solid color** — single letter from the wordmark, set in display face,
  filled. Simple, scales perfectly, ties tightly to wordmark.
- **Geometric symbol on solid color** — abstracted form (ridge, leaf, droplet) at
  large scale.
- **Photographic / illustrative** — only if the imagery is itself a brand element and
  it survives the 60px test. Most do not.

**Patterns that fail:**
- Multiple small elements (looks busy at 60px)
- Wordmark *in* the icon (the full name never fits — use a monogram)
- White on light, black on dark (no contrast against most wallpapers)
- Off-square crops (the OS will chop them)

---

## Brand surfaces — direction per surface

Brand applications behave differently per surface. A single visual direction rarely
serves all of them. Plan a direction per surface as a one-line creative brief, similar
to the per-format direction in `CLAUDE.md` Step 6 (asset inventory).

| Surface | Direction lens |
|---------|---------------|
| **Splash / launch** | Impression-first: the wordmark or symbol on a single mood-image background. Restraint. |
| **In-app chrome** | Function-first: wordmark only when contextually relevant (header on home), absent elsewhere — let the product be the brand expression. |
| **Marketing site / hero** | Impression-first: typographic scale, photography, atmospheric whitespace. |
| **Marketing site / product** | Clarity-first: structured content, screenshots, density. |
| **Social / OG image** | Impression-first at thumbnail scale: bold typography, single image, brand color. Test at 200×200. |
| **App icon** | Single-shape impression. The most constrained surface — see above. |
| **Deck / presentation** | Restraint: brand mark on intro and closing slides, not every slide (per `feedback_deck_starburst_restraint`). |
| **Email / transactional** | Function-first: wordmark in header, brand color sparingly. Reading is the point. |

Per-surface direction prevents one of the most common branding failures: copying the
splash treatment into every application surface, which makes the in-app experience feel
like a permanent ad for itself.

---

## Voice

This is design-principles, not a copy guide — but two things:

1. **Voice direction is one sentence**. e.g. "Direct, observational, second-person; no
   marketing-speak, no exclamation points." If you can't compress it to a sentence,
   it isn't decided yet.
2. **Voice ties to the chosen positioning.** A casual, day-tripper-focused outdoor app
   sounds different from a serious-hiker-focused one. The voice sentence should derive
   from the positioning, not from a brand-voice template.

---

## What's outside the scope of this module

- **Color palette derivation** — see `color/mood-scene.md` (brand track) and
  `color/oklch.md` (product track)
- **Type pairing selection** — see `typography/pairings.json` and `typography/rules.md`
- **Logo as illustration** — bespoke illustration / mascot work is a project, not a
  module concern
- **Trademark and legal** — out of scope; consult counsel before locking a name

---

## Sources

- Personal: PalMonte rework session, 2026-04-29 — module created when planning a
  brand+UI rebuild and finding identity guidance absent from the existing modules
  (color and typography existed; identity construction did not)
- [Apple HIG — App Icons](https://developer.apple.com/design/human-interface-guidelines/app-icons)
- [Material 3 — Adaptive icons](https://m3.material.io/styles/icons/designing-icons)
