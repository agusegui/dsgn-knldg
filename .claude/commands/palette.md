Derive a color palette from content character — background, text, accent, and supporting roles with hex values.

Use this skill when choosing colors for a design, building a palette from scratch, or when a design needs color direction. Also useful when the current palette feels disconnected from the content's tone or when warm/cool temperature is mismatched.

## Arguments
`$ARGUMENTS` — content character description or design context. Examples:
- "warm editorial, literary tone, cream-paper feeling"
- "dark cinematic brand page for a film studio"
- "clean SaaS product, professional but not cold, blue-leaning"
- "brutalist portfolio, high contrast, raw"

Can also include constraints: "dark mode", "must include brand blue #2563EB", "accessible on white backgrounds".

## Your task

### Step 1 — Read content temperature

Before picking any colors, assess the content's emotional temperature:

- **Warm** (cream, amber, terracotta, warm grays) — literary, intimate, grounded, organic
- **Cool** (blue-gray, slate, steel, cool whites) — technical, precise, institutional, modern
- **Neutral** (true grays, balanced whites) — editorial, versatile, unobtrusive
- **High contrast** (near-black + white, minimal color) — dramatic, brutalist, authoritative
- **Saturated** (strong hues, vivid accents) — energetic, playful, commercial

The temperature must be consistent across the entire palette. A warm cream background with cool gray text looks subtly wrong — the grays need to be pulled warm too.

### Step 2 — Consult the rules

Read `knowledge/typography/rules.md` § "Color and contrast" for:
- Near-black vs. pure black guidance
- Warm background → warm text color matching
- Secondary text contrast ratios

Read `knowledge/ui/patterns.md` § "Universals" for:
- WCAG AA contrast requirements (4.5:1 normal text, 3:1 large text)
- Color independence — never use color as sole information carrier

### Step 3 — Build the palette

Define 5-6 colors with named roles:

| Role | Purpose | Guidance |
|------|---------|----------|
| **Background** | Dominant surface | Sets the temperature. Pure white (#FFF) is rarely the best choice — slightly warm (#FAFAF7, #F8F6F1) or cool (#F5F7FA) backgrounds are more refined. |
| **Text** | Primary reading | Near-black, not #000 unless intentional. Pull toward palette temperature: warm (#1A1814) or cool (#1A1D21). |
| **Secondary** | Captions, metadata | 40-50% lighter than text. Must pass 4.5:1 on background for small text. Warm (#8A857D) or cool (#7A7F87). |
| **Accent** | Links, CTAs, emphasis | The strongest chromatic moment. Should feel earned, not random. One accent color is usually enough. |
| **Dark** | Alternate sections, overlays | For dark-on-light contrast sections. Dark sections need slightly lighter text weight — optical weight differs on dark backgrounds. |
| **Surface** | Cards, panels, inputs | Subtle step from background. Should be distinguishable but not competing. Usually 2-4% darker/lighter than background. |

### Step 4 — Verify contrast ratios

For each text-on-background combination, verify WCAG AA compliance:
- Text on Background: must be ≥ 4.5:1
- Secondary on Background: must be ≥ 4.5:1 for body, ≥ 3:1 for large text only
- Text on Dark: must be ≥ 4.5:1
- Text on Surface: must be ≥ 4.5:1

If a combination fails, adjust the lighter color darker or the darker color lighter until it passes.

### Step 5 — Temperature consistency check

Review all colors together:
- Do the grays match the background temperature? (Warm bg → warm grays, cool bg → cool grays)
- Does the accent feel like it belongs in this palette, or is it from a different emotional register?
- In dark sections, is the text warm enough if the light sections use warm text?

---

## Output format

```
COLOR PALETTE
Temperature: [warm / cool / neutral / high-contrast]
Derived from: [content reasoning]

Background:   #______ — [description]
Text:         #______ — [description]
Secondary:    #______ — [description]
Accent:       #______ — [description]
Dark:         #______ — [description]
Surface:      #______ — [description]

CONTRAST CHECK
Text on Background:    [ratio]:1 [pass/fail]
Secondary on Background: [ratio]:1 [pass/fail]
Text on Dark (inverted): [ratio]:1 [pass/fail]
Accent on Background:  [ratio]:1 [pass/fail]

TEMPERATURE NOTE
[One sentence on temperature consistency across the palette]
```

This output plugs directly into the design brief (Step 5) when used within `/design`.
