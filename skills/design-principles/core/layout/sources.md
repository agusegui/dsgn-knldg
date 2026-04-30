# Layout Sources

Annotated bibliography of layout and grid system resources.

---

## A Closer Look at Grid Systems — Smashing Magazine / Nick Babich (2017)
- URL: https://www.smashingmagazine.com/2017/12/building-better-ui-designs-layout-grids/
- Date accessed: 2026-03-08
- Quality: medium — broad overview aimed at UI designers; good on anatomy, grid types, and responsive behavior; not deeply theoretical
- Key extracts:
  - Grid anatomy: columns, gutters, margins, modules, hang lines — each term has a precise structural definition, not interchangeable
  - Four grid types: manuscript (single column), column, modular (column + row), hierarchical (freeform zones)
  - 12-col reasoning: divides cleanly into halves, thirds, and quarters — most flexible for responsive component layout
  - Baseline grid = typographic tool: "a baseline grid aligns text elements horizontally across columns, creating visual rhythm"
  - Responsive grid: 12-col desktop -> 8-col tablet -> 1-2-col mobile; layout grids define how components respond at breakpoints
  - Mobile default: tile grid (equal column + row heights), max 2 columns, images sized to one grid unit
- Grid rules extracted: see grids.md Sections 2 and 5

## Five Simple Steps to Designing Grid Systems — Mark Boulton Journal (2005, Part 1)
- URL: https://www.markboulton.co.uk/journal/five-simple-steps-to-designing-grid-systems-part-1/
- Date accessed: 2026-03-08
- Quality: high — foundational practitioner article; unusually rigorous on ratio-based grid construction; predates most "8px grid" discourse but aligns with it structurally
- Key extracts:
  - "Start from the format's own ratio" — A4 = 1:1.414 (sqrt(2)); subdivide continuously by that ratio to derive column widths
  - Rational ratios (1:2, 2:3) -> structured/clear/architectural; irrational ratios (1:sqrt(2), 1:1.618) -> dynamic/organic/flowing
  - Margins derived from the same ratio as the grid create "inherent harmony between content and page"
  - Continuous subdivision: each division is self-similar to the whole — same principle as A-series paper (A4->A5->A6)
  - "The grid is a tool for creative decision making, not a prison for content" — grids as framework, not constraint
  - Self-similar proportional grids feel coherent at any scale because every zone echoes the whole
- Grid rules extracted: see `../foundations/math.md` Section 4
