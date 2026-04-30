Derive a brand-track color palette from content character — mood word, scene reference, and 5–6 hex values with named roles.

Use this skill for **brand, editorial, print, content, and marketing work** — anywhere the palette should carry cultural or emotional reference. The method is mood-driven and scene-derived: commit to a mood, derive every color from a real object in that scene.

> **For product / software / design system work**, use [`/oklch-skill`](https://github.com/jakubkrehel/oklch-skill) by Jakub Krehel instead — install with `npx skills add jakubkrehel/oklch-skill`. OKLCH gives systematic ramps, perceptual uniformity, and accessibility-grade contrast that mood palettes can't. See `knowledge/color/oklch.md` for the decision rules.

## Arguments
`$ARGUMENTS` — content character description or design context. Examples:
- "warm editorial, literary tone, cream-paper feeling"
- "dark cinematic brand page for a film studio"
- "brutalist portfolio, high contrast, raw"
- "candlelit chapel mood for a wine label"

Can also include constraints: "must include brand color #2563EB", "accessible on warm cream backgrounds".

## Your task

### Step 1 — Confirm the track

If the brief is clearly product/UI/design-system work, stop and redirect to `/oklch-skill`. This skill is for brand, editorial, print, content, and marketing work specifically.

### Step 2 — Commit to a mood word

A mood word is a physical condition or register: mineral, candlelit, bookish, foggy, alpine, brutalist, signage, hypertext, tropical, nocturnal, chapel, gallery, editorial, etc. The full mood library lives in the Paper MCP guide ("Design Quality" section).

Pick **anything other than your first instinct**. First-instinct picks regress to the same few answers. State 3–5 mood candidates, then commit to one.

### Step 3 — Derive every color from a real scene

For the chosen mood, name the scene and the specific objects in it. Examples:
- "mineral" — limestone dust, weathered slate, oxidized copper, wet stone
- "bookish" — plaster, oak pew, ink, candle flame, foxed paper
- "candlelit" — warm amber, oxblood, hot wax, soot

If you can't name a real reference for a role, the palette is abstract and will feel glued together.

### Step 4 — Consult the rules

Read `knowledge/color/mood-scene.md` for:
- Role definitions (background, text, secondary, accent, dark, surface)
- Color and contrast principles (near-black vs. pure black, secondary text limits, warm-cool matching)
- Pairings to avoid (recent clichés)
- Temperature consistency

Read `knowledge/ui/patterns.md` § "Universals" for:
- WCAG AA contrast (4.5:1 normal, 3:1 large)
- Color independence

### Step 5 — Build the palette

Define 5–6 colors with named roles, each tied to a specific object reference:

| Role | Purpose |
|------|---------|
| **Background** | Dominant surface — sets the temperature |
| **Text** | Primary reading color (near-black, not #000 unless intentional) |
| **Secondary** | Captions, metadata, muted elements |
| **Accent** | The strongest chromatic moment — earned, not random |
| **Dark** | Alternate sections, overlays |
| **Surface** | Subtle step from background for cards/panels |

### Step 6 — Verify contrast and temperature

For each text-on-background combination, verify WCAG AA:
- Text on Background: ≥ 4.5:1
- Secondary on Background: ≥ 4.5:1 body, ≥ 3:1 large
- Text on Dark: ≥ 4.5:1
- Text on Surface: ≥ 4.5:1

If a combination fails, adjust the lighter color darker or the darker lighter until it passes.

Then check temperature consistency: warm grounds need warm grays, cool grounds need cool grays, accents must belong to the same emotional register.

---

## Output format

```
COLOR PALETTE — mood-driven (brand track)
Mood word: [mood]
Scene reference: [actual scene the palette derives from]
Temperature: [warm / cool / neutral / high-contrast]

Background:   #______ — [object reference]
Text:         #______ — [object reference]
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

This output plugs directly into the `/design` brief at Step 5.
