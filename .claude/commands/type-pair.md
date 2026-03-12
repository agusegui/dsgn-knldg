Suggest font pairings for a use case, drawn from the knowledge base and your typographic judgment.

## Arguments
`$ARGUMENTS` — a brief description of the design context, e.g. "luxury editorial dark mode" or "friendly health app, 3 type sizes, web"

Optionally includes a medium keyword: `poster`, `editorial`, `brand`, or `digital`. If present, medium-specific logic overrides generic pairing logic.

## Your task

1. **Identify the medium** — scan `$ARGUMENTS` for `poster`, `editorial`, `brand`, or `digital`. If found, note it. If absent, infer from context clues (e.g. "publication", "magazine" → editorial; "logo", "identity" → brand; "app", "web", "UI" → digital; "print", "campaign" → poster).

2. **Read the knowledge base**
   - `knowledge/typography/pairings.json` — query for pairings matching the context, mood, and use tags
   - `knowledge/typography/rules.md` — load the relevant typesetting principles for this context
   - `knowledge/typography/typesetting.md` — check scale and rhythm guidance (references `knowledge/foundations/math.md` for ratios)
   - `knowledge/typography/graphic-contexts.md` — read the section for the identified medium. Note its key demands before evaluating candidates.

3. **Generate 3 pairing candidates**

   For each, provide:

   ```
   PAIRING N: Heading Font + Body Font
   Category: ...
   Contrast: ...
   Why it fits this brief: [2–3 sentences connecting the pairing's character to the stated use case]
   Medium fit: [How well this pairing serves the identified medium — is it proven in this context?]
   Typesetting starting point:
     - Heading/Display: Xpx, weight Y, tracking Z
     - Body: Xpx, line-height Y, weight Z
     - Notes: any pairing-specific quirks or medium-specific considerations
   Graphic design precedent: [Well-proven in [medium] | Limited precedent in this context | Strong print/editorial history]
   Source: [from knowledge base | reasoned suggestion]
   ```

4. **Rank them** — lead with the strongest fit, explain briefly why it beats the others for this specific brief and medium.

5. **Offer next steps:**
   - "Run `/type-direct [your copy] medium:[medium]` to get a direction built around actual content"
   - "Run `/type-specimen [Font A] [Font B]` to see any of these on the Paper canvas"

## Pairing judgment rules

When drawing from knowledge base AND reasoning:

- **Match on temperament first, structure second.** A warm-feeling brief needs warm typefaces regardless of classification.
- **Distinguish display use from text use.** Many serifs only work well at 32px+. Don't pair a display-only face as body text.
- **Check x-height compatibility.** Mismatched x-heights create visual friction between heading and body text.
- **Consider weight range.** If the use case needs multiple weight levels, confirm the font has them.
- **Dark mode caveat.** High-contrast serifs (Bodoni, Didot) lose their thin strokes at small sizes on dark. Flag this.
- **Superfamily pairings are almost always safe.** When in doubt, suggest one.
- **Avoid pairing two serifs of the same classification.** Old-style + old-style, or two Didones, creates confusion without contrast.
