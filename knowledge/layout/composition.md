# Composition

How sections, elements, and whitespace relate to each other across a page.
For grid mechanics, see `grids.md`. For type scale by context, see `../typography/typesetting.md`.

---

## Core idea

Layout is typesetting at the page scale. The same logic applies: choose structure from
the content's needs and audience, not from convention. A product page for a reflective
display and a SaaS dashboard pricing page have nothing in common compositionally — they
shouldn't look like they share a template.

---

## Content-driven composition

Before choosing any layout pattern, answer two questions:

1. **What is the content's job?** — To persuade, to inform, to impress, to orient?
2. **Who is reading, and how?** — Scanning quickly, studying deeply, comparing options,
   feeling an emotion?

These answers determine the compositional approach:

| Content job | Audience mode | Compositional approach |
|-------------|---------------|----------------------|
| Persuade / inspire | Emotional, scanning | Cinematic — scale extremes, asymmetry, dramatic whitespace, type as image |
| Inform / explain | Focused, reading | Editorial — clear columns, generous measure, structured hierarchy, content leads |
| Orient / navigate | Task-driven, scanning | Functional — density, alignment lanes, minimal decoration, clarity over expression |
| Impress / showcase | Evaluative, browsing | Expressive — break the grid, unexpected scale, tension, compositional risk |

**The default should never be "centered stack."** Centering is a specific choice appropriate
for specific content (a single hero statement, a call to action in isolation). It is not a
layout strategy.

---

## Compositional principles

### 1. Section variety is non-negotiable

No two consecutive sections should share the same compositional structure. If the hero is
a large headline left-aligned with a small descriptor right, the next section should not
also be a two-column split at the same proportions.

Vary across these axes:
- **Alignment**: left-anchored → centered → right-anchored → full-bleed
- **Proportion**: 50/50 → 70/30 → full-width → contained narrow
- **Density**: spacious → dense → spacious
- **Tone**: dark → light → dark (background color as scene change)

Think of sections as scenes in a film — each needs its own framing.

### 2. Scale contrast creates hierarchy

If the largest text is 80px and the body is 16px, that's a 5:1 ratio. Good for editorial.
But if the largest text is 48px and the body is 16px, that's only 3:1 — and both feel
"medium." The page flattens.

**For brand and product pages**: aim for at least 6:1 between the largest display element
and the body text. This isn't about making everything huge — it's about making the
hierarchy unmistakable at a glance.

**For functional pages**: 3:1 to 4:1 is appropriate. The hierarchy is structural, not dramatic.

### 3. Asymmetry is the default

Symmetry communicates stability, formality, completion. It's appropriate for:
- Centered hero statements (used sparingly)
- Formal/institutional contexts
- Closing moments (final CTA)

For everything else, asymmetry creates movement, tension, and visual interest. A 60/40
split is more interesting than 50/50. A left-anchored headline with right-aligned body
creates a diagonal reading path.

**Symmetry should be a deliberate choice, not a default.**

### 4. Whitespace is compositional, not decorative

Empty space on a page is not "unused." It creates:
- **Tension**: large empty area next to dense content = dramatic
- **Direction**: whitespace pulls the eye toward content
- **Pace**: generous spacing slows reading (contemplative); tight spacing accelerates it

A 900px-tall hero section with 144px text and 500px of empty space above it is not
"wasted space" — it's cinematic pacing. The emptiness is the design.

### 5. Background color as scene change

Alternating background colors between sections is one of the most powerful compositional
tools. It creates:
- Visual separation without borders or dividers
- Pacing and rhythm across the page
- Opportunities for contrast (light text on dark, dark text on light)

**Dark sections demand different typography.** Light text on dark backgrounds should be
slightly lighter weight than dark text on light backgrounds — the optical weight differs.

### 6. Break the grid intentionally

A grid provides structure. Breaking it provides emphasis. Both are necessary.

When to break:
- A hero image that bleeds full-width while text is contained
- A pull quote that extends wider than the body column
- A large number or word that overlaps its container
- An element positioned to create diagonal tension with another

**Every grid break must be clearly intentional.** One element slightly off-grid looks like
a mistake. One element dramatically off-grid looks like a decision.

---

## Anti-patterns

These are not "rules to never break" — they are defaults to avoid. Each is acceptable in
the right context, but none should be the automatic first choice.

### The centered stack
```
        [Label]
    [Large Heading]
  [Body paragraph text]
     [Button] [Button]
```
This is the most common landing page template. It's appropriate for a single hero moment
but becomes monotonous when repeated across sections. If the page has 4+ sections and
all of them are centered stacks, the composition has failed.

**When it works:** A single, isolated statement (manifesto, closing CTA).
**When it fails:** As the organizing principle for an entire page.

### The three-card grid
Three equal cards in a row is the default "features section." It communicates
"we have three things" but nothing about the relative importance of those things, and
nothing about the brand's visual identity.

**Alternatives:**
- One large feature (2/3 width) + two stacked smaller features (1/3 width)
- Sequential reveals — one feature per section, each with its own compositional treatment
- A single scrolling row with varying card sizes
- No cards at all — features as editorial text blocks with typographic hierarchy

### The uniform section rhythm
Every section has the same padding, same internal structure, same alignment. The page
reads as a list, not a composition.

**Fix:** Vary section height, padding, and internal layout deliberately. Some sections
should be tall and spacious (contemplative). Others should be compact and dense
(informational). The rhythm should feel scored, not metronomic.

### The equal spec strip

N items, same size, same weight, evenly spaced in a row with labels beneath.
The most templated section pattern in product page design. Treats all data points
as equally important when they rarely are.

**The fix isn't a specific alternative — it's asking better questions:**
- Which of these specs matters most? Give it dominance through scale.
- Can these specs live inside the sections they belong to instead of being
  extracted into their own section?
- Does the hierarchy serve the reader, or does it serve the layout's symmetry?

Any presentation that differentiates by importance — through scale, grouping,
or integration into narrative content — will outperform equal repetition.

### Medium everything
All headings between 32–48px, all body at 16px, all spacing at 40–60px. Nothing is
notably large or notably small. The page has no visual peaks or valleys.

**Fix:** Push at least one element to an extreme — a 120px+ headline, a 200px ghost
number, a full-bleed image, a section with 140px padding. Create peaks.

---

## Context scales (compositional)

### Brand / Product page
- Hero type: 96–160px
- Section headings: 36–56px
- Body: 15–17px
- Section padding: 80–140px, varied
- At least one dark section
- At least one full-bleed moment
- Asymmetric by default

### Editorial / Article
- Display type: 48–80px
- Section headings: 24–36px
- Body: 16–18px in a constrained measure (55–75ch)
- Section padding: 48–80px, consistent
- Content-led — images and pull quotes break the column
- Clear reading flow is the priority

### Product UI / Dashboard
- Page title: 24–32px
- Section headings: 18–20px
- Body: 14–15px
- Section padding: 24–40px, compact
- Alignment lanes and density over expression
- Symmetry is acceptable here — it communicates order

---

## Component architecture — establish a vocabulary, then arrange it

Section variety (principle 1 above) governs how sections *differ*. Component architecture
governs what they *share*. Both are necessary. A page where every section invents its own
internal structure feels fragmented — like six designers worked on six sections. A page
with a consistent component vocabulary but varied arrangements feels cohesive and intentional.

### Vary arrangement, not structure

The key distinction: **components** are the reusable building blocks (cards, content blocks,
feature items, media blocks). **Arrangement** is how those components sit on the page
(asymmetric grid, stacked, side-by-side, full-bleed). Vary the arrangement per section.
Keep the component vocabulary tight.

A card that appears at 2/3 width in the features section and at 1/3 width in the security
section is the same component at different scales — that's cohesion. A features section
using horizontal rows while the security section uses vertical cards with completely
different padding, radius, and type hierarchy — that's fragmentation.

### Define the component vocabulary early

Before writing HTML, name 2-4 component types the page will use. Each gets:
- **Shared surface treatment**: background color, border-radius, padding
- **Shared type hierarchy**: how heading, description, and metadata relate inside the block
- **A size range**: can it flex from 1/3 to full-width? Or is it fixed?

Example vocabulary for a product page:
- **Feature card**: rounded surface, padding-32, heading + description + optional image
- **Content block**: no surface (lives on the section background), number + heading + description
- **Media block**: image with optional caption overlay

Three components, arranged differently per section, is enough for most pages.

### Content containment — when to use cards

Cards (contained surfaces with background, padding, radius) are appropriate when:
- Content items are **peers** that need visual equivalence (features, pricing tiers)
- Items contain **mixed media** (image + text together inside a boundary)
- The section background is busy or dark and items need a **reading surface**

Cards are not appropriate when:
- Content is a **linear sequence** (steps, timeline, specs list) — use flat list patterns
- Items are **subordinate to a primary element** (supporting details under a heading)
- The section is already a clean reading surface — adding card backgrounds creates
  visual noise without structural benefit

The default instinct to "put it in a card" often comes from uncertainty about layout.
If the content can live directly on the surface with clear typographic hierarchy, it
should. Cards are for containment, not decoration.

### Asymmetric card grids over equal grids

When using cards, prefer asymmetric arrangements:
- **One large (2/3) + two stacked small (1/3)** — creates hierarchy within a set of peers
- **One full-width hero card + row of compact cards below** — establishes importance
- **Staggered sizes** — large, medium, small in a masonry-like flow

Equal-size card grids (three 1/3 cards in a row) are the most common anti-pattern in
agent-generated designs. They communicate "we have three things" without signaling
which matters most. If the items genuinely are equal, vary the *internal* treatment
(one gets an image, the others are text-only) to avoid visual monotony.

### Asset integration — images inside components, not beside them

Product images embedded *inside* a card or content block feel structural — the image
is part of the component's content. Product images placed *beside* a text block feel
decorative — they illustrate rather than integrate.

For product pages: prefer structural integration. A feature card with the product
screenshot inside it, text below, communicates "this is what the feature looks like."
The same screenshot floating next to a text block communicates "here's a picture, and
here's some text." The first approach is stronger.

When an image IS the content (hero product shots, portfolio pieces), it should own its
space — full-width or dominant in an asymmetric split. When an image SUPPORTS the
content (showing what a feature does, demonstrating a detail), embed it inside the
content component. [added after a session where a product landing page treated all
images as side-by-side decorations rather than integrating them into feature cards,
creating a page that looked like a brochure with illustrations rather than a product
page with demonstrations]

---

## Layout sketch — mandatory pre-build step

Before writing any HTML, write a **layout sketch**: one sentence per section describing
the specific compositional structure — not the content, the *spatial arrangement*.

A good layout sketch sentence is actionable and auditable:
- Bad: "Hero section — cinematic, dramatic whitespace"
- Good: "Hero text overlaps the product image at the midpoint, breaking the grid;
  CTA anchored bottom-left with 140px breathing room above"

Bad sketches use adjectives (cinematic, clean, bold). Good sketches use spatial
relationships (overlaps, anchored, bleeds, offset by, spans 8 of 12 columns).

**If you can't describe the layout in spatial terms, you haven't designed it yet —
you're about to default to a template.** This is the single most common failure mode
in agent-generated layouts. [added after a session where a brief calling for "cinematic
composition" produced centered stacks and equal-card grids]

---

## Composition checklist

Before finalizing a page layout:

- [ ] Can you describe each section's compositional strategy in one sentence?
- [ ] Do any two consecutive sections share the same structure? (They shouldn't.)
- [ ] Is there at least one moment of extreme scale (very large or very small)?
- [ ] Is centering used sparingly and intentionally, not as the default?
- [ ] Does the whitespace rhythm vary — some sections spacious, some dense?
- [ ] Is there a background color or tonal shift creating visual pacing?
- [ ] Would a first-time viewer know this is a designed page, not a template?

### Post-build composition audit

After the first build pass, screenshot the full page and ask:

> "Would a designer look at this and know it wasn't a template?"

If the answer is no — or even "maybe" — identify the weakest section and redesign it
before moving on. The audit is not optional. A page that passes the checklist above
but still *feels* like a template has a composition problem that the checklist didn't
catch — usually uniform section rhythm or lack of a genuine scale peak. [added after
a session where a checklist-passing page still read as generic]
