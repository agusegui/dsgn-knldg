# Local — your overrides layer

This folder is the **customization layer** for `design-principles`. It's empty by default. Files you put here override the equivalent knowledge in [`../core/`](../core/) when the skill resolves a question.

## Resolution rule

When the skill needs to make a decision (palette, type, composition, etc.), it looks here first. If a relevant file exists in `local/`, the skill uses it. Otherwise it falls back to `core/`. **Local always wins.**

This means:

- `local/palette.md` with committed brand colors → `/palette` uses those instead of generating a mood-driven palette.
- `local/type.md` with a chosen pairing → `/type-pair` skips the 3-candidate process and uses the committed pairing.
- `local/voice.md` with copy samples → the skill writes in your voice instead of generic placeholder copy.

## What goes here

The files below are suggestions, not requirements. Add only the ones you've actually committed to. Leave the rest empty so the skill keeps using core defaults.

| File | What it commits |
|------|-----------------|
| `overview.md` | Brand identity in one page — mood word, scene reference, era, voice in one paragraph |
| `palette.md` | Committed color palette with hex values, roles, reasoning. Overrides Step 5 of `/design`. |
| `type.md` | Committed type pairing, scale ratio, scale table, weights. Overrides Step 2 + 3. |
| `voice.md` | Copy/tone samples. Used wherever the skill writes placeholder content. |
| `components.md` | Brand-specific UI patterns (button shapes, card treatments, motion language). |
| `layout.md` | Brand-specific compositional choices (preferred grid, signature compositions, anti-patterns). |
| `assets/` | Logo SVGs, brand photography, custom icons. The skill uses `paper-asset://` paths to drop these on the canvas. |

## Three ways to populate this folder

1. **Fork the repo** and edit `local/` directly. Push as `<your-handle>/<your-design-language>`. Anyone who installs your fork gets your brand baked in.
2. **Bootstrap on the fly** — start working with the generic skill, and when you commit a brand decision in conversation ("we're committing to Söhne + Editorial New for everything"), the skill offers to file it into `local/` so future sessions inherit the decision.
3. **Hand-write** the files directly using the templates above as a starting point.

## What does NOT go here

- Universal design knowledge (math, type pairing principles, contrast universals) — that belongs in `core/`. If you find yourself wanting to write a generic principle here, it belongs upstream as a contribution to core.
- Files specific to a single project (this design language is brand-level, not project-level). Project-specific decisions go in your project repo, not here.

## Compatibility

When `core/` evolves upstream, your `local/` files keep working unless the resolution rule changes. Pin to a specific `core/` version (via Git tag) if you want stability across upstream updates.
