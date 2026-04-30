# Color

Two color philosophies coexist in this system. Which one applies depends on the design **track** — a decision made early in the `/design` workflow.

## Track-aware

- **Brand / editorial / print / content / marketing** → mood-driven, scene-derived palettes. See [mood-scene.md](mood-scene.md).
- **Product / software / design systems** → systematic OKLCH palettes. See [oklch.md](oklch.md).

## Why two

Brand work and product work ask different things from color. A poster wants the precise bone-and-ink of a candlelit chapel. A SaaS dashboard wants eleven lightness steps that are perceptually equal across six hues. One tool forced to do both produces compromise palettes that fail at both jobs.

## Universals (apply to both philosophies)

> **Universal:** Text contrast meets WCAG AA — 4.5:1 for normal text, 3:1 for large text and non-text UI. Non-negotiable, regardless of track.
>
> **Universal:** Color is never the sole information carrier. Always pair with shape, weight, position, or label.

## How `/design` routes

Step 1 of the workflow infers the track from content character (e.g. "SaaS dashboard" → product, "literary cover" → brand) and states the inference for the user to confirm or correct. Step 5 (color pass) then routes to the correct tool — see [mood-scene.md](mood-scene.md) and [oklch.md](oklch.md) for the trigger logic.
