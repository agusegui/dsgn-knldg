# Grid & Layout Systems

Reference for grid structure, alignment, whitespace, and responsive behavior.
For spacing scale and ratio math, see `../foundations/math.md`.

---

## 1. Core Philosophy

Grid systems are structural logic that makes composition legible and trustworthy.
A well-constructed grid communicates before a word is read.

Influences: Josef Muller-Brockmann's _Grid Systems in Graphic Design_, Swiss International
Typographic Style, and contemporary 8px spatial systems.

**Form follows function.** A grid should be derived from the content's needs, not imposed
on top of them. Constraint enables creativity — a strict grid frees decisions about where
things go so energy can go into what things mean.

---

## 2. Grid Anatomy

| Term | Definition |
|------|-----------|
| Column | Vertical division of the layout. Content snaps to column edges. |
| Gutter | Fixed gap between columns. Never places content here. |
| Margin | Space between the content area and the artboard edge. |
| Module | Unit formed by a column x row intersection. The smallest addressable content cell. |
| Hang line | Horizontal guide where content begins. Creates consistent vertical rhythm. |
| Baseline | Invisible horizontal lines spaced by line-height. Type sits on these. |

### Grid Types

| Type | Structure | Best for |
|------|-----------|----------|
| Manuscript | Single wide column | Long-form reading, essays, books |
| Column | 2-12 vertical columns | Magazines, dashboards, responsive web |
| Modular | Columns + rows = modules | Complex layouts, data grids, print |
| Hierarchical | Freeform zones, not uniform columns | Posters, landing pages, editorial splash |

### Standard Column Counts

- **1-2 col**: Mobile, long-form text, minimal landing page
- **3-4 col**: Tablet, card layouts
- **6 col**: Mid-range dashboard or editorial
- **12 col**: Desktop — most flexible; components can span 2, 3, 4, 6, or 12 cols

---

## 3. Alignment Rules

1. **Snap to grid.** Every element's left or right edge aligns to a column edge or module boundary.
2. **Images fill whole columns.** An image spanning 1.7 columns is wrong. Span 1 or 2.
3. **Optical vs. mathematical alignment.** Numbers and punctuation hanging outside the column
   at large sizes look wrong when perfectly aligned. Use optical alignment — hang punctuation
   outside the margin slightly, or shift by 1-2px to balance visual weight.
4. **Never center arbitrary widths.** Centering is appropriate for headings, not for body text
   blocks or card containers.
5. **Vertical lanes in repeated elements.** Lists, tables, and nav items must form consistent
   vertical lanes. Icon slots must have fixed widths even when empty.
6. **Baseline alignment.** When two elements sit side by side at different sizes, align to the
   baseline of the smaller text.

---

## 4. Whitespace as Active Element

Whitespace is not emptiness — it is structure. Generous whitespace signals confidence and
hierarchy. Cramped whitespace signals anxiety or content overload.

**Hierarchy of whitespace:**
1. Largest gaps separate the most different things (page sections)
2. Medium gaps separate components
3. Small gaps separate related elements within components
4. Micro gaps separate parts within a single element

---

## 5. Responsive Grid

| Breakpoint | Columns | Gutter | Margin | Notes |
|-----------|---------|--------|--------|-------|
| Mobile (<768px) | 1-2 | 16px | 16px | Tile grid; max 2 cols |
| Tablet (768-1024px) | 4-8 | 20px | 24px | Cards may span 2 or 4 of 8 cols |
| Desktop (1024-1440px) | 12 | 24px | 32px | Standard; components span 2/3/4/6/12 |
| Wide (>1440px) | 12 | 24px | Auto | Max content width ~1280px; margins grow |

**Components respond at breakpoints.** A 3-col card grid collapses: 3-col -> 2-col -> 1-col.
Each state must be explicitly considered, not assumed.

---

## 6. Layout Checklist

Before finalizing any layout, verify:

- [ ] All spacing values are multiples of 4px (ideally 8px)
- [ ] Column count matches complexity of content
- [ ] Margins are consistent and derived from the grid
- [ ] Body text column width is 55-75ch (~550-750px)
- [ ] No element spans a fractional number of columns
- [ ] Images occupy whole-column widths
- [ ] Vertical lanes align across repeated rows (use fixed-width slots)
- [ ] Type scale derives from a ratio or interval, not arbitrary jumps
- [ ] Heading-to-body size ratio is at least 2:1
- [ ] Largest gaps separate the most structurally different zones
- [ ] Whitespace is deliberate — empty areas have a structural reason
- [ ] Responsive behavior is explicitly designed, not assumed
- [ ] The grid can be described in one sentence

---

## 7. Agent Layout Rules

These rules apply to every layout task.

1. **Declare the grid before placing.** Before writing any HTML, state the grid: column count,
   gutter width, margin width, and base spatial unit.

2. **Derive all dimensions from the grid.** Widths = column spans. Heights = spatial scale
   multiples. Never use arbitrary pixel values that aren't on the scale.

3. **Use the spacing scale strictly.** Padding and gap values must come from the scale table
   in `../foundations/math.md`. Do not invent intermediate values.

4. **Body text max-width is always set.** Never allow body text to run full-container-width
   unless the container is already within the 55-75ch range.

5. **Fixed-width slots for repeated rows.** In any list, table, or repeated component, give
   icon slots, indicator dots, and trailing actions a fixed width (and flex-shrink: 0).

6. **Images in whole columns only.**

7. **Vertical rhythm from line-height.** If body line-height is 24px (16px x 1.5), all
   vertical spacing should be a multiple of 24px to maintain baseline cadence.

8. **Whitespace must be intentional, not default.** When adding padding, ask: what is this
   spacing communicating?

9. **Document your grid.** At the end of any layout task, state the grid used so it can be
   reused or audited.
