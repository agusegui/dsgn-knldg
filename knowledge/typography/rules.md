# Typesetting Rules

Core principles for pairing, setting, and judging type. Add notes with [source: ...] tags.

---

## Pairing principles

**Contrast is the engine, harmony is the goal.**
A good pairing creates clear hierarchy through contrast (serif vs sans, weight, scale) while feeling like the two fonts belong in the same room. If they fight for attention, the pairing fails.

**Match on x-height, not classification.**
Two fonts with wildly different x-heights will look like they come from different documents when set together, regardless of how theoretically compatible they are.

**Superfamily pairings are almost always safe.**
Fonts designed together (DM Serif Display + DM Sans, IBM Plex Serif + IBM Plex Sans) share proportions by design. Use them when cohesion matters more than personality.

**One expressive face, one neutral face.**
If the heading font has a strong personality (Fraunces, Bodoni, Cormorant), the body font should be calm and get out of the way. Two expressive faces fight.

**Avoid pairing two fonts of the same classification — unless their personalities diverge sharply.**
Old-style + old-style, geometric + geometric: usually confusion. But two slabs from completely different eras (one 19th-century Antique, one contemporary), or two geometric sans with markedly different details, can create interesting tension when set with clear weight and scale contrast. The rule isn't "never same classification" — it's "never same classification *and* same personality." [source: hoeflerco.com/journal/typographic-doubletakes]

**Warmth pairs with warmth, even across categories.**
Lora (warm serif) + Fira Sans (warm humanist) work because they share temperament. Coldly geometric serifs + warm humanist sans often clash in feeling even if the forms are compatible.

**Form model is the deepest pairing logic: stay close or go far, never in between.**
Every typeface has a form model — Dynamic (broad-nib, calligraphic), Rational (pointed-pen or constructed), or Geometric (drawn, monoline). Same-model pairings are inherently harmonious. Opposite-model pairings (Dynamic + Geometric) create strong, productive contrast. Adjacent-model pairings (Dynamic + Rational, Rational + Geometric) are the hardest to execute — similar enough to feel like they should work, different enough to create low-level dissonance. When a pairing feels almost right but not quite, the form model is often where to look. See `classifications.md` for the full framework. [source: kupferschrift.de, Noordzij]

---

## Typeface selection — derive from content, not habit

Before choosing any typeface, engage with the content:

1. **Read the content's character** — what is its era, tone, cultural origin, emotional
   register? A mid-century French essay, a brutalist portfolio, and a wellness app should
   never start from the same typeface.
2. **Name 3 candidate families with reasoning.** No single default. Each candidate should
   respond to the content's character differently. Write one sentence per candidate
   explaining why it fits.
3. **At least one candidate must feel risky or unexpected.** If all three candidates are
   from the same genre (e.g. three condensed sans-serifs, three geometric sans), the
   process hasn't worked — it's producing variations on the same idea, not genuinely
   different responses to the content. Push one candidate toward a typeface you wouldn't
   normally reach for. The risky candidate often wins. [added after a session where three
   "safe condensed display" candidates produced a generic result for a brand that demanded
   personality]
4. **Choose and justify.** Pick the strongest candidate and state why it wins over the
   other two. This prevents autopilot selection.
5. **Content category informs classification.** Premium technology and precision hardware
   lean toward clean sans-serifs — geometric or grotesque. Decorative serifs (Didone,
   high-contrast display faces) serve fashion, luxury editorial, and cultural contexts
   where ornament is earned by the content. Matching classification to content category
   is as important as matching mood.

### Overused typefaces

Faces listed here have been relied on too heavily in this system. They are not banned —
but they require **explicit justification** tied to the content's character to use again.
If you catch yourself reaching for one out of convenience, that's the signal to stop and
run the 3-candidate process above.

- **Instrument Serif** — safe, modern, polite. Tends to flatten everything into the same
  voice. Reach for something with more personality or historical specificity instead.
- **DM Serif Display + DM Sans** — a superfamily pair that's become the path of least
  resistance. Perfectly fine when cohesion genuinely matters more than personality (e.g.
  product UI, dense systems). But for brand, editorial, and expressive contexts it
  flattens everything into "polished contemporary" regardless of the content's character.
  If you're reaching for it, check whether `pairings.json` has something that actually
  responds to the brief's tone. [added after a session where this pairing produced a
  landing page indistinguishable from one made without the design-principles system]

---

## Anchor typeface — start with body, not headline

**Choose the body face first. Everything else must earn its place beside it.**
The anchor is the face that carries 90% of the reading. Lock it, then find a headline face that complements it — not the other way around. [source: jessicahische.is/talkingtype]

**Text face checklist before committing:**
- **Weight range**: Needs inbetween weights (450–600), not just light/regular/bold. More weights = more hierarchy options without visual jumps.
- **X-height**: Generous, but not so high that caps and lowercase lose distinction — that breaks reading rhythm at small sizes.
- **True italic**: A sloped roman is not an italic. A real italic has calligraphic structure and maintains even color (matching weight) alongside the roman.
- **Spacing**: Text type must feel loose enough to read naturally. If you feel like adding letter-spacing to 16px body copy, the face is too tightly spaced for body use.
- **Even color**: No heavy spots where strokes join. Good text type has invisible micro-corrections so no letter visually "pops" against its neighbors.

**Il1 test for any sans-serif considered for body use.**
Type a capital I, lowercase l, and number 1 side by side. If you can't distinguish them, the face has a legibility problem at text sizes. (Helvetica famously fails this.) Two-story 'a' and 'g' also read faster in body text than single-story equivalents. [source: jessicahische.is/talkingtype]

---

## Size and scale

**The minimum readable body size is 14px for display, 16px for accessibility.**
Below 14px, most text faces lose their character. Below 12px, forget about it unless it's all-caps labels at very high contrast.

**A 2:1 ratio between heading and body is the baseline for clear hierarchy.**
If your H1 is 18px and body is 16px, there's no hierarchy — just confusion. Product UI
can work at 1.5:1 when density matters; editorial and brand contexts want 3:1 or more.
See `../foundations/math.md` for the full scale.

**Display type wants negative tracking. Body type wants none.**
At 48px+, letters benefit from slight negative tracking (-0.01em to -0.03em). This tightens the texture and makes large type look intentional. Never apply negative tracking to body text.

**All-caps needs air. Always.**
Caps text with zero tracking looks like a mistake. Minimum 0.08em, ideally 0.10–0.15em. This applies to labels, tags, category names, any UI text set in caps.

---

## Line height

**Body text: 1.55–1.75.** The wider the measure (characters per line), the more leading you need. Long lines need 1.75. Short columns can work at 1.5.

**Display headings: 1.0–1.2.** Tight leading on big type creates density and authority. More than 1.3 on a display heading starts to look accidental.

**Subheadings and callouts: 1.3–1.5.** Between the two extremes.

**High-contrast serifs (Bodoni, Didone) at text size: push line height up.**
The thin strokes create visual noise at small sizes. More breathing room compensates.

---

## Weight and hierarchy

**Bold doesn't mean heavy — it means differentiated.**
In a humanist sans, medium (500) can read as bold enough for hierarchy. Forcing 700 everywhere is amateur.

**Default to 3 weights of the same face in one design.**
Regular, medium/semibold, bold. More than that often signals hierarchy confusion rather
than intent. But information-dense interfaces (dashboards, data tools, complex editorial)
can legitimately use 4–5 weights when each serves a distinct, identifiable role.

**Weight and size are two different hierarchy tools. Use both.**
A smaller, bolder label can outrank a larger, lighter heading when you want that.

---

## Color and contrast

**Body text is usually better in near-black than pure black (#000000) on white.**
Pure black creates harsher contrast that can fatigue readers over long passages.
#1A1A1A, #222, or a slightly warm near-black is gentler. That said, pure black is a
valid choice in some contexts — high-density UI, brand systems, or when warmth would
feel wrong for the content.

**Secondary text: reduce by no more than 40% opacity before it becomes illegible.**
#999 on white = 2.85:1 contrast ratio. Fine for large labels, borderline for body. Below 12px, never go below #888.

**Warm backgrounds need warm text colors.**
A cool gray (#777) on a warm cream background looks slightly wrong. Pull the gray toward warm (#7A7570 instead of #777777).

---

## Structural harmony checklist (pairing fine-tuning)

**Allographs signal personality — match or deliberately contrast them.**
The single-story 'a' and 'g' read as geometric and modern; double-story reads as traditional and humanist. Pairing a single-story sans with a double-story serif creates a legible contrast. Pairing two fonts that disagree on allograph style without intention can feel unresolved. [source: https://type-ed.com/resources/rag-right/2017/10/18/3-steps-to-great-typeface-pairs]

**Axis orientation affects whether paired fonts feel related.**
Humanist typefaces have a diagonal stress axis (following the pen's natural angle). Geometric and modern faces have a vertical axis. Pairing fonts from opposite ends of this spectrum can feel jarring in body text. Shared axis = cohesion; opposing axis = contrast. [source: https://type-ed.com/resources/rag-right/2017/10/18/3-steps-to-great-typeface-pairs]

**Character width rhythm should feel compatible at the same setting.**
Fonts with very different average character widths will create clashing texture when set at the same size. Before committing to a pairing, set a few lines of each at the intended body size and look at the overall texture — do they look like they're from the same universe? [source: https://type-ed.com/resources/rag-right/2017/10/18/3-steps-to-great-typeface-pairs]

**Think in skeletons, not styles.**
Strip the visual "clothes" (serifs, ornaments, stylistic details) and compare the underlying skeleton: x-height, letter width, bowl proportions. Two very different-looking faces can pair beautifully if their skeletons are compatible. This is why superfamily pairs feel like family even when stylistically distinct. [source: jessicahische.is/talkingtype]

**Pairing proximity: sibling → cousin → distant relative.**
Siblings share skeleton, contrast, width, and mood — superfamilies. Cousins share skeleton and mood but diverge in style — often from the same designer or era. Distant relatives share only mood — emotionally coherent but structurally unrelated. All three can work; risk increases as you move toward distant relative territory. [source: jessicahische.is/talkingtype]

**The real rule isn't "don't use similar fonts" — it's "make each font's purpose clear."**
Two nearly identical typefaces can coexist if each has an unambiguous, exclusive job. The problem with using similar fonts isn't similarity — it's ambiguity. [source: hoeflerco.com/journal/how-to-use-clashing-fonts]

**Give each font a non-overlapping size altitude.**
Assign each typeface in a design a specific size range it owns exclusively. When fonts share a size, roles blur and hierarchy collapses. Segregating by altitude is especially important with eccentric or high-personality faces — the separation accentuates each font's uniqueness rather than letting them compete. [source: hoeflerco.com/journal/typographic-doubletakes]

**Or divide by semantic function instead of size.**
Two similar fonts can work at the same size if they serve structurally different content roles — body text vs. annotations, primary narrative vs. supporting commentary. The font choice is dictated by the content's purpose, not its size. Even visually similar fonts will reveal useful differences (weight, x-height, ascender proportions) once assigned separate functions. [source: hoeflerco.com/journal/how-to-use-clashing-fonts]

**Cross-mix roman and italic to differentiate close pairs.**
When two related typefaces are used together, alternating — pairing one font's roman with the other's italic — adds variety and further separates the voices. This works in both directions and deepens the distinction without needing dramatic contrast. [source: hoeflerco.com/journal/how-to-use-clashing-fonts]

**Synchronize rhythm with tracking when mixing.**
Fonts with different natural spacing create visual discontinuity even when well-matched in weight. Careful tracking — tightening a loose face or opening a tight one — can unify the rhythm across a composition. The goal: letters and spaces feel like they breathe at the same rate. [source: hoeflerco.com/journal/typographic-doubletakes]

**Eccentric pairs need one shared characteristic as an anchor.**
Strange bedfellows — typefaces that seem incompatible — can cohere if they share a single motif: a shared angle of incline, a geometric approach, an era, a level of visual weight. That one point of contact is enough to make the pairing feel intentional rather than accidental. [source: hoeflerco.com/journal/typographic-doubletakes]

**The casting director test: personalities cannot clash.**
Think of the two fonts as actors being cast in the same film. They need different roles (contrast), but they must inhabit the same world (harmony). A Didone and a geometric sans can coexist in a fashion context. The same Didone next to a rustic slab sends contradictory signals. [source: https://type-ed.com/resources/rag-right/2017/10/18/3-steps-to-great-typeface-pairs]

---

## Specific pairing notes

**Cormorant Garamond at body size:** needs at minimum 1.7 line height. Its dramatic thin strokes at small sizes require extra breathing room. Don't use below 15px.

**Bodoni/Didone at body size:** almost always a mistake. These are display faces. Use at 28px+. Below that, the thin strokes break.

**Josefin Sans:** its geometric vintage character gets stronger as size increases. At small sizes it reads as generic. Use at 13px+ with generous tracking.

**Use the right optical size cut for the right size.**
When a family ships with Display, Text, or Caption variants — use them. Display cuts have higher contrast, tighter spacing, and more personality, optimized for large sizes. Text cuts have open counters, reduced contrast, and looser spacing for legibility at small sizes. Using a Display cut at body size looks anemic and breaks at small sizes. Using a Text cut at headline size looks bland and clunky. Read naming conventions: "Fine," "Display," or "Titling" = large sizes only; "Text" or "ScreenSmart" = body and smaller. [source: typographica.org/books/size-specific-adjustments-to-type-designs, hoeflerco.com/journal/how-to-use-clashing-fonts]

**When mixing fonts from the same historical source, start from the extreme ends.**
Two families built on the same foundation will overlap most in their middle weights and widths. Their hairlines, ultras, condensed, and extended styles are where they diverge — those are the cuts least likely to clash and most likely to create useful contrast. [source: hoeflerco.com/journal/how-to-use-clashing-fonts]

**Fraunces optical size:** use `font-variation-settings: 'opsz' 144` at large sizes to access maximum expressiveness. At body size, reduce opsz toward 9 for better legibility.

**DM Sans:** unusually versatile for a geometric sans. Works well at body size even without typographic warmth around it. The 400 weight reads lighter than expected — use 450–500 for body text.
