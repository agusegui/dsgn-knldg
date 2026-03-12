Audit a design against every knowledge module — typography, scale, composition, color, and UI patterns. Returns a structured review with specific findings and suggestions.

Use this skill after building a design on the Paper canvas, when something feels off about a layout, when reviewing someone else's design, or when iterating on a design that needs improvement. This is the post-build counterpart to `/design` — it checks whether the design brief was executed faithfully and whether the result holds up visually.

## Arguments
`$ARGUMENTS` — one of:
- A node ID or artboard name to screenshot and review
- "review current" to review the most recently created artboard
- A description of what to focus on (e.g., "the typography feels wrong", "spacing is inconsistent")

## Your task

### Step 1 — Capture the design

Call `get_screenshot` at scale 2 on the target artboard. If no specific target is given, call `get_basic_info` to find the most recent artboard, then screenshot it.

Also call `get_tree_summary` to understand the node structure, and `get_children` on the artboard to inspect the hierarchy.

### Step 2 — Typography audit

**Consult:** `knowledge/typography/rules.md`, `knowledge/typography/typesetting.md`, `knowledge/typography/classifications.md`

Check:
- [ ] **Font pairing**: Do the fonts create clear hierarchy through contrast while feeling like they belong together? Check form model compatibility (classifications.md).
- [ ] **Scale**: Are heading-to-body ratios at least 2:1 (editorial/brand) or 1.5:1 (product UI)? Is there a clear hierarchy with no ambiguous levels?
- [ ] **Body text**: Is it ≥14px? Is line-height ≥1.5 for body? Is measure within 55-75ch?
- [ ] **Display text**: Tight leading (1.0-1.2)? Negative tracking at 48px+?
- [ ] **All-caps text**: Has positive tracking (≥0.08em)?
- [ ] **Weight use**: No more than 3 weights per face in active use (unless information-dense UI)?
- [ ] **Text wrap**: `balance` on headings/short blocks, `pretty` on body paragraphs?
- [ ] **Font rendering**: No system-ui or sans-serif fallback text surviving? Both fonts visually distinct?

### Step 3 — Scale & spacing audit

**Consult:** `knowledge/foundations/math.md`

Check:
- [ ] **Scale ratio**: Can the sizes be derived from a single ratio? Or are they arbitrary?
- [ ] **Spacing grid**: Are all padding/gap values multiples of 4px (ideally 8px)?
- [ ] **Gestalt grouping**: Tighter spacing between related items, looser between unrelated? Never the same gap for different relationships?
- [ ] **Consistency**: Same spacing token used for the same relationship across sections?
- [ ] **No arbitrary values**: No spacing that doesn't fit the grid (e.g., 37px padding, 15px gap)?

### Step 4 — Composition audit

**Consult:** `knowledge/layout/composition.md`, `knowledge/layout/grids.md`

Check:
- [ ] **Section variety**: Do any two consecutive sections share the same structure?
- [ ] **Scale peak**: Is there at least one moment of extreme visual scale?
- [ ] **Centering**: Is it used sparingly and intentionally, or is it the default?
- [ ] **Asymmetry**: Does the layout use asymmetric proportions (60/40, 70/30) rather than defaulting to 50/50?
- [ ] **Whitespace**: Is it compositional (creating tension, direction, pace) or just padding?
- [ ] **Grid alignment**: Do elements snap to a grid? No fractional column spans?
- [ ] **Background pacing**: Do color/tonal shifts create visual rhythm between sections?
- [ ] **Anti-patterns**: Centered stack repeated? Three-equal-card grid? Uniform section rhythm? Medium everything?

### Step 5 — Color & contrast audit

**Consult:** `knowledge/typography/rules.md` § Color and contrast, `knowledge/ui/patterns.md` § Universals

Check:
- [ ] **WCAG AA**: Text on all backgrounds ≥4.5:1 contrast? Large text ≥3:1?
- [ ] **Temperature**: Warm backgrounds have warm text/grays? No cool-on-warm mismatch?
- [ ] **Color independence**: Is color never the sole means of conveying information?
- [ ] **Near-black vs. pure black**: Is body text using a near-black unless pure black is intentional?

### Step 6 — UI patterns audit (if interactive)

**Consult:** `knowledge/ui/states.md`, `knowledge/ui/patterns.md`

Check:
- [ ] **Focus states**: Visually distinct from hover? (Universal)
- [ ] **Hover gating**: No functionality gated behind hover alone? (Universal)
- [ ] **Error proximity**: Error messages near the element that caused them? (Universal)
- [ ] **Persistent labels**: Form fields have visible labels, not just placeholders? (Universal)
- [ ] **Touch targets**: Interactive areas generous enough for touch input?
- [ ] **Empty states**: Designed, not blank?
- [ ] **Affordance clarity**: Interactive elements look interactive?

### Step 7 — Synthesis

Compile findings into three categories:

1. **Universal violations** — non-negotiable issues that must be fixed (accessibility, contrast, focus states)
2. **Principle departures** — strong defaults being broken without apparent justification (may be intentional — flag, don't demand)
3. **Opportunities** — things that work but could be stronger (composition, hierarchy, expression)

For each finding, state:
- What the issue is (specific, not vague)
- Where it occurs (node name or section)
- What the knowledge base recommends
- A concrete suggestion for improvement

---

## Output format

```
DESIGN REVIEW — [artboard name]

SUMMARY
[2-3 sentence overall assessment]

UNIVERSAL VIOLATIONS (must fix)
1. [issue] — [location] — [recommendation]
2. ...

PRINCIPLE DEPARTURES (review intent)
1. [issue] — [location] — [knowledge base reference] — [suggestion]
2. ...

OPPORTUNITIES (could be stronger)
1. [observation] — [suggestion]
2. ...

STRONGEST ELEMENTS
[1-2 things the design does well — what to preserve in iteration]
```
