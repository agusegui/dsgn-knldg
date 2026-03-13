# UI Design Patterns

Design-level awareness for interactive interfaces. Mostly thinking tools for making
informed decisions — but some rules are universals backed by accessibility standards
or research. These are marked with **Universal** and are non-negotiable.

---

## Universals

Rules that apply regardless of context, audience, or aesthetic direction.

> **Contrast ratios.** Text must meet WCAG AA minimums: 4.5:1 for normal text (below 18px
> or below 14px bold), 3:1 for large text (18px+ or 14px+ bold). This is the floor, not
> the target — higher contrast is almost always better for readability. [WCAG 1.4.3]

> **Color independence.** Never use color as the sole means of conveying information.
> Status indicators, form validation, data visualization, links within body text — all
> need a second visual channel (shape, icon, underline, pattern, text label). [WCAG 1.4.1]

> **Persistent labels.** Form fields must have visible labels that remain present during
> and after input. Placeholder text is not a label — it disappears on focus or input,
> leaving users without reference. [WCAG 1.3.1, 3.3.2]

See also: universals in `states.md` (focus visibility, hover-gating, error proximity,
spatial stability, error color-independence).

---

## Touch and pointer awareness

Interfaces serve two fundamentally different input modes: precise pointers (mouse, trackpad)
and imprecise touch (fingers, stylus). Designing for one and hoping the other works is
how small tap targets, hover-gated information, and invisible interactions happen.

**Touch target sizing.** Small visual elements can have large interactive areas — the hit
area doesn't need to match the visible boundary. But the interactive area should be
generous enough that users don't miss on the first tap. Icons, checkboxes, and close
buttons are the most common offenders.

**Hover as enhancement, not requirement.** Hover can enrich an experience (previews,
expanded labels, secondary actions) but must not be the only path to functionality.
(See universal in `states.md`: never gate functionality behind hover alone.)

**Pointer precision vs. touch forgiveness.** Dense interfaces (data tables, toolbars, small
controls) work with a mouse. On touch, they become a minefield. Consider whether the
same density is appropriate across input modes, or whether touch contexts need a more
spacious variant.

---

## Undo over confirmation

Confirmation dialogs ("Are you sure?") are a speed bump users learn to click through
without reading. They protect against accidental actions in theory; in practice, they
add friction to intentional actions and fail to prevent mistakes.

Undo is almost always a better pattern. Let the action happen, show a brief window to
reverse it ("Message deleted. Undo"), and move on. This respects the user's intent when
they meant to act, and offers recovery when they didn't — without interrupting flow in
either case.

Confirmation still has its place for truly irreversible, high-consequence actions (deleting
an account, sending a mass email, overwriting data with no backup). But it should feel
proportional to the consequence — a modal with clear language about what will be lost,
not a generic "Are you sure?" that reads like every other dialog.

---

## Labels, placeholders, and affordances

**Placeholders are not labels.** (See universal above.) Placeholder text disappears on
input, leaving users with no reference for what the field expects. This is a usability
problem for anyone who looks away from the screen and back, for users with short-term
memory challenges, and for anyone reviewing a partially filled form. Labels should be
persistent and visible — above the field, or floating.

**Affordance clarity.** Interactive elements should look interactive. A text link that
looks like a label, a button that looks like a badge, a clickable area with no visual
differentiation from its surroundings — these are all affordance failures. The user
shouldn't have to guess what's interactive.

The question isn't "is it clickable?" but "does it *look* clickable before the user
tries?" Underlines, button shapes, pointer cursors, and color contrast all contribute.

---

## Empty states

The first thing a user sees in a new account, an empty list, a search with no results,
or a filtered view that matches nothing — these are all empty states, and they're
frequently undesigned.

An empty state is a teaching moment. Instead of "No items found," consider:
- **What goes here** — explain what this space will contain.
- **How to fill it** — provide the action that creates the first item.
- **Why it matters** — context for why the user should care.

The worst empty state is a blank screen with no guidance. The second worst is a generic
message that adds no information ("Nothing to see here"). Both waste an opportunity to
orient the user.

---

## Progressive disclosure

Not everything needs to be visible at once. Progressive disclosure means showing the
essential information and controls first, and revealing complexity on demand.

This isn't about hiding things — it's about pacing. A settings page with 40 visible
options overwhelms. The same 40 options organized into sensible groups, with advanced
settings collapsed by default, respects both novice and expert users.

The risk of over-applying progressive disclosure: hiding things so aggressively that users
don't know they exist. If a feature is core to the product's value, it shouldn't be behind
two clicks and a menu. Disclosure works best for genuine complexity — edge cases, advanced
configuration, secondary workflows.

---

## Visual clichés to be aware of

Certain visual patterns have become so associated with AI-generated or template-driven
design that they read as generic regardless of execution quality. This isn't about banning
any specific technique — it's about awareness. If a design uses one of these, it should
be a deliberate choice, not an unconscious default.

Patterns that currently signal "template" or "AI-generated" to trained eyes:

- **Purple-to-blue gradients** as the default accent palette. Ubiquitous in SaaS landing
  pages since ~2018. Not wrong, but instantly familiar in a way that works against
  distinctiveness.
- **Frosted glass / glassmorphism** as a primary surface treatment. Was novel in 2020,
  became wallpaper by 2023. Often used decoratively without serving hierarchy or legibility.
- **Neon accents on dark backgrounds.** The "developer tool" aesthetic. Powerful when
  earned by context, generic when defaulted to.
- **Identical card grids** — three or four cards at the same size, same structure, same
  visual weight. Communicates "we have N things" but creates no hierarchy. See
  `../layout/composition.md` for alternatives.
- **Decorative sparklines and abstract data visualizations** that don't represent real data.
  Users have learned to ignore these — they signal decoration, not information.
- **Centered-everything layouts** where every section is a centered headline, centered
  paragraph, centered button. See `../layout/composition.md` on asymmetry.
- **Oversized ghost numbers** ("01" at 80–120px in a near-background color) used as
  decorative anchors. They add visual weight without adding information. If a number
  isn't serving hierarchy or navigation, it's decoration pretending to be design.

The antidote isn't avoiding these entirely — it's noticing when they're being used out of
habit rather than intention, and asking whether a different choice would serve the content
better.

---

## Density as a design variable

Interfaces exist on a density spectrum from spacious (marketing pages, onboarding) to
compact (data tables, code editors, trading dashboards). Density isn't inherently good or
bad — it's a response to the user's task.

- **Low density** — appropriate when the user is reading, exploring, or making infrequent
  decisions. Generous whitespace, larger type, fewer visible options. Reduces cognitive load
  but increases scrolling.
- **High density** — appropriate when the user needs to compare, scan, or act on many items
  quickly. Tighter spacing, smaller type, more visible data. Increases efficiency but
  raises the learning curve.

The common mistake is applying uniform density across an entire product. A dashboard's
data table should be dense; its empty state should not be. A settings page can be denser
than a welcome screen. Match density to the user's mode at each moment.
