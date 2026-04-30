# Mobile

What changes when the canvas is 390px wide, the input is a thumb, and the device is held one-handed.
This module covers what's distinctively mobile. For grid mechanics see `layout/grids.md`. For
component architecture see `layout/composition.md`. For state behavior see `ui/states.md`.

---

## Universals

> **Universal:** Touch targets are at least 44×44px on iOS, 48×48px on Android. This is
> the minimum hit area, not the minimum visible size — visible icons can be smaller as
> long as the underlying tappable region clears the floor.

> **Universal:** Body text is at least 16px. Captions and metadata are at least 14px.
> 12px text is acceptable only for legal fine print, never for primary content.

> **Universal:** Respect the safe area. No persistent controls within 44px of the top
> edge (status bar / notch / dynamic island) or within 32px of the bottom edge (home
> indicator on devices without a hardware button). Backgrounds and imagery may extend
> edge to edge; interactive elements may not.

---

## Reach and thumb zones

A one-handed grip on a phone gives the thumb a curved reach across the screen. The bottom
two-thirds is comfortable; the top third is a stretch. Plan reach accordingly:

- **Primary actions** (Start, Save, Confirm, Navigate) belong in the bottom third —
  ideally as a fixed bar or floating button above the home indicator.
- **Navigation between top-level destinations** belongs in a bottom tab bar, not a top
  bar or hamburger drawer.
- **Destructive actions** belong out of the comfortable thumb zone, or behind a confirm
  step — accidental taps are far more common on mobile than on desktop.
- **Dismiss / close** sits at the top-left or top-right; users reach for these
  intentionally, not by accident.

---

## Safe areas — concrete numbers

For 390×844 (iPhone 12/13/14/15 Pro):
- **Top safe area**: ~47px (status bar + notch / dynamic island padding)
- **Bottom safe area**: ~34px (home indicator)
- **Effective content height** above the bottom tab bar: ~680px once you account for top
  status (47), bottom indicator (34), and a 83px bottom tab bar

When the artboard is 844px tall, plan against ~680px of usable vertical space for content
that must coexist with persistent chrome. Above the fold means within the first ~640px,
not the first 844.

---

## Mobile type scale

A mobile-specific scale, distinct from `typography/typesetting.md` § Product UI which
targets dashboards. Mobile leans larger because reading distance is shorter and pixel
density is high.

| Role | Size | Notes |
|------|------|-------|
| Display / hero | 40–56px | Editorial moments, brand statements; bigger only for splash |
| H1 / page title | 28–34px | One per screen |
| H2 / section heading | 20–24px | Group headers within a screen |
| H3 / item title | 16–18px | Card / list-row titles |
| Body | 16px | Floor for paragraphs and primary text |
| Body small | 14px | Secondary descriptions, helper text |
| Caption | 13–14px | Metadata, timestamps, tags — nothing critical |
| Numerals (stat) | 24–32px | When a number is a hero element (distance, gain, time) |

Line-height: 1.25–1.35 for headings, 1.4–1.55 for body. On mobile, generous line-height
(1.5+) is more important than on desktop because columns are narrower and the eye needs
the extra leading to track lines.

Letter-spacing: tighten large display (-0.01em to -0.02em). Open small all-caps labels
(0.05em to 0.1em).

---

## Sheet anatomy

Bottom sheets are the dominant mobile pattern for secondary content (place details,
filters, action menus). Anatomy:

- **Handle / drag affordance**: 36×4px rounded bar, centered, top of sheet, ~8px
  from top edge. The handle is non-functional decoration that signals "this is draggable."
  Even non-draggable sheets benefit from including it for affordance consistency.
- **Header**: kicker (optional 12–14px caps label) + title (20–28px) + dismiss control
  if applicable. Avoid headers taller than ~96px — they eat scroll real estate.
- **Body**: scrollable. Inertia scrolling assumed.
- **Footer (sticky)**: primary action bar — sits above the bottom safe area. Can include
  one primary button (full-width or wide) and one supporting action (icon button).

**Stop heights** when the sheet is dismissable / resizable:
- **Peek** (1/4 screen, ~210px) — minimum useful preview, only the title and one piece
  of meta visible
- **Half** (1/2 screen, ~420px) — title + key meta + first action
- **Full** (≥3/4 screen, ~640px+) — full content, scrolls within the sheet

Do not animate sheets to arbitrary heights. Pick 2–3 stops and snap to them.

---

## Bottom tab bar

The bottom tab bar is the primary navigation pattern on mobile. Conventions:

- **3–5 destinations** — fewer than 3 doesn't justify the bar (use a single back button
  or top nav); more than 5 forces tiny touch targets and unrecognizable icons.
- **Persistent labels** — never icon-only. Even universally recognized icons (home,
  search) gain clarity from labels, and they remove guesswork for first-time users.
  Per `ui/patterns.md`, persistent labels are a universal.
- **Single active state** — only one tab visible as active at a time. Active state should
  use color, weight, OR fill — not all three. (Per `feedback_highlight_minimalism`.)
- **Fixed height of ~83px** including the home-indicator safe area. Visible tab content
  sits in the top ~49px of that band.
- **Tap targets ≥ 64×44** per tab — plenty of horizontal room divided across 3–5 tabs;
  vertical room is tighter, so the touch region must extend into the safe area.

---

## Top app bar (when it exists)

Bottom tab handles primary nav, so the top app bar's job is contextual: title of current
screen, back button, and screen-specific actions.

- **Height**: 44–56px, plus the 47px status bar above
- **Title style**: 17–20px medium, OR centered editorial larger title (28–32px) on key
  screens — choose one and apply consistently per screen type
- **No more than 2 trailing actions**. Beyond 2, use an overflow menu.
- **Back button**: left side, with chevron. Replace with close (×) when the screen is a
  modal sheet rather than a navigation push.

When a screen has a hero image or full-bleed media at the top, the bar can be transparent
and float — but its controls still need a contrast-safe background (frosted blur or a
solid pill behind the icon). Floating icons on photographs without a backing fail
accessibility constantly.

---

## Gestures and affordances

Gestures save space but hide functionality. On mobile, every gesture should also have a
visible affordance for discoverability:

- **Swipe to delete** → also expose a delete action via long-press menu or a clear "edit
  mode" with explicit X buttons
- **Pull to refresh** → spinner appears on pull, but include a manual refresh in the
  overflow menu for the same action
- **Drag handle** on sheets → makes the sheet feel draggable; add a top-right close
  for explicit dismiss
- **Pinch to zoom** → only on map / image surfaces; if it's enabled, also expose +/−
  zoom controls for accessibility

The rule: gestures are progressive enhancement, not the only access path.

---

## Density and tap separation

On dense lists (search results, settings, history), maintain tap separation so the user
doesn't fat-finger the wrong row:

- **Minimum row height** for a tappable list row: 56px
- **Minimum vertical separation** between two adjacent tap targets: 8px (so the hit area
  of row N ends before row N+1's hit area begins)
- **Trailing actions** on rows (chevron, plus, save) get 44×44 hit areas even when the
  visible icon is 20×20

For non-tappable items (read-only metadata rows in a detail screen), these floors don't
apply — those can be more compact.

---

## Imagery on mobile

Mobile portrait orientation favors **vertical imagery**: 4:5, 3:4, or full-bleed
390×wide-x-tall. Wide landscape images crop poorly into hero positions on mobile and
should be avoided unless the imagery is itself a panorama (mountain ridge, lake horizon).

For full-bleed hero imagery:
- Plan for content overlay — the bottom 40–60% of the image will be covered by a sheet
  or overlaid copy, so important subject matter belongs in the upper third
- Use a subtle gradient overlay (top: transparent → bottom: 40% black) when light text
  needs to sit over photography
- Test contrast in both portrait *and* landscape rotations if the app supports rotation

---

## What does NOT change on mobile

These principles from desktop carry through unchanged:
- Type scale ratios (`foundations/math.md`)
- Color palette derivation (`color/mood-scene.md`, `color/oklch.md`)
- Section variety and asymmetry (`layout/composition.md`)
- Component vocabulary and slot thinking (`layout/composition.md`)
- State spectrum (`ui/states.md`) — focus is still distinct from active

The mistake is treating mobile as "desktop scaled down." Mobile has its own physical
constraints (thumb, viewport, attention), but the visual system is the same.

---

## Sources

- [Apple Human Interface Guidelines — Layout](https://developer.apple.com/design/human-interface-guidelines/layout)
- [Material 3 — Layout & Touch targets](https://m3.material.io/foundations/layout/applying-layout/touch-targets)
- [WCAG 2.5.5 — Target Size (Enhanced)](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- Personal: PalMonte rework session, 2026-04-29 — module created when planning a
  mobile-first brand+UI rebuild and finding mobile-specific guidance scattered across
  layout, ui, and typography modules
