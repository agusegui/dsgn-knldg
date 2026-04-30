# Mood-driven, scene-derived palettes

The **brand-track** approach to color. Used for editorial, marketing, brand systems, posters, print, and any work where emotional resonance matters more than systematic uniformity.

For systematic product/UI palettes (50–950 ramps, perceptual lightness, design tokens), use [oklch.md](oklch.md) instead.

---

## The method

1. **Commit to a mood word** — a physical condition or register: mineral, candlelit, bookish, foggy, alpine, brutalist, signage, hypertext, tropical, nocturnal, etc. The full mood library lives in the Paper MCP guide under "Design Quality."
2. **Derive every color from a specific object in that scene.** "Mineral" = limestone dust, weathered slate, oxidized copper. "Bookish" = plaster, oak pew, ink, candle flame. If you can't name a real reference for a role, the palette is abstract and will feel glued together.
3. **One intense, beautiful color moment is stronger than five.** Use accent color deliberately.
4. **Pick mood candidates from a mix of obvious and less-obvious options.** From the candidate list, pick anything *other than* your first instinct — first-instinct picks regress to the same few answers.

## Roles

| Role | Purpose | Guidance |
|------|---------|----------|
| **Background** | Dominant surface | Sets the temperature. Pure white (#FFF) is the everyday case for SaaS/product/marketing — not a stark choice. Off-white (cream, ivory, bone) is a specific aesthetic tied to moods like sun-bleached, candlelit, bookish, vintage. |
| **Text** | Primary reading | Near-black, not #000 unless intentional. Pull toward palette temperature: warm (#1A1814) or cool (#1A1D21). |
| **Secondary** | Captions, metadata | 40–50% lighter than text. Must pass 4.5:1 on background for body. Warm (#8A857D) or cool (#7A7F87). |
| **Accent** | Links, CTAs, emphasis | The strongest chromatic moment. Should feel earned, not random. One primary accent is usually enough. |
| **Dark** | Alternate sections, overlays | For dark-on-light contrast sections. Dark sections need slightly lighter text weight — optical weight differs on dark backgrounds. |
| **Surface** | Cards, panels, inputs | Subtle step from background, distinguishable but not competing. Usually 2–4% darker/lighter. |

## Color and contrast principles

**Body text is usually better in near-black than pure black (#000000) on white.**
Pure black creates harsher contrast that can fatigue readers over long passages. #1A1A1A, #222, or a slightly warm near-black is gentler. Pure black is still valid in some contexts — high-density UI, brand systems, or when warmth would feel wrong for the content.

**Secondary text: reduce by no more than 40% opacity before it becomes illegible.**
#999 on white = 2.85:1 contrast ratio. Fine for large labels, borderline for body. Below 12px, never go below #888.

**Warm backgrounds need warm text colors.**
A cool gray (#777) on a warm cream background looks slightly wrong. Pull the gray toward warm (#7A7570 instead of #777777). Same logic for cool backgrounds.

## Temperature consistency check

Review all colors together:
- Do the grays match the background temperature? (Warm bg → warm grays, cool bg → cool grays)
- Does the accent feel like it belongs in this palette, or from a different emotional register?
- In dark sections, is the text warm enough if the light sections use warm text?

## Pairings to avoid

These have become recent clichés or simply don't work:

- Warm off-white × red / orange / terracotta / burnt-sienna (overused)
- Warm off-white × fluorescent (fluorescent doesn't appear in pastoral, candlelit, sun-bleached scenes)
- Dark navy or charcoal × electric purple / lime / teal (overused 2019–2024 SaaS look)
- Pure white × muted earth tone (earth tones fall flat on pure white — they want a tinted ground from the same scene)
- Tinted warm ground × any high-chroma or saturated accent (the tint mutes the chroma)

## When NOT to use this method

- Building a 50–950 lightness ramp for design tokens
- Generating a multi-hue product palette where all hues need equal perceptual brightness
- Auditing an existing palette for hue drift or contrast failures
- Tailwind v4 `@theme` work
- Dark mode derivation that needs to be perceptually equivalent to light mode

For all of those, use [oklch.md](oklch.md) → `/oklch-skill`.

## Output format

When `/palette` runs in this method, the output plugs into the `/design` brief at Step 5:

```
COLOR PALETTE — mood-driven
Mood word: [mood]
Scene reference: [the actual scene the palette derives from]
Temperature: [warm / cool / neutral / high-contrast]

Background:   #______ — [object reference, e.g. "limestone dust"]
Text:         #______ — [object reference, e.g. "oxidized copper"]
Secondary:    #______ — [object reference]
Accent:       #______ — [object reference]
Dark:         #______ — [object reference]
Surface:      #______ — [object reference]

CONTRAST CHECK
Text on Background:      [ratio]:1 [pass/fail]
Secondary on Background: [ratio]:1 [pass/fail]
Text on Dark:            [ratio]:1 [pass/fail]
Accent on Background:    [ratio]:1 [pass/fail]

TEMPERATURE NOTE
[One sentence on temperature consistency across the palette]
```
