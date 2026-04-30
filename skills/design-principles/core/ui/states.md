# Component States

How interactive elements behave across their full lifecycle. Designing for states is
designing for trust — users form judgments about quality from how an interface responds
to their actions, not just how it looks at rest.

---

## The state spectrum

Every interactive element exists somewhere on a spectrum of states. Thinking through
all of them prevents the common failure mode of designing only the "happy path" — the
default, resting appearance — and leaving every other moment undesigned.

Eight states worth considering for any interactive element:

| State | What it communicates | Design considerations |
|-------|---------------------|----------------------|
| **Default** | "I'm available" | The baseline. Should read as interactive without shouting. |
| **Hover** | "You're close" | A preview of interactivity. Subtle — a color shift, underline, or slight elevation change. Not all users see this (touch devices). |
| **Focus** | "I'm selected via keyboard" | Distinct from hover. Must be visible for accessibility. A ring, outline, or strong border — never rely on color alone. |
| **Active / Pressed** | "You're acting on me" | Brief but perceptible. Often a slight scale reduction or color deepening. Confirms the action registered. |
| **Disabled** | "I exist but I'm not available right now" | Reduced contrast, no pointer cursor. Consider whether to explain *why* — a disabled button with no context is a dead end. |
| **Loading** | "Working on it" | Replace the action label or show inline progress. Disable re-submission. Keep the element's footprint stable — no layout shift. |
| **Error** | "Something went wrong" | Position the message near the element, not in a banner 400px away. Red is conventional but not sufficient alone — pair with an icon or text for colorblind users. |
| **Success** | "Done" | Confirm completion where the action happened. Can be transient (fade after 2–3 seconds) or persistent depending on consequence. |

Not every element needs all eight. A static link might only need default, hover, focus,
and active. A form submit button benefits from all eight. The point is to **consider** each
state deliberately, not to implement them mechanically.

---

## Hover and focus are different problems

This is the most commonly collapsed distinction. Hover is a pointing-device behavior — it
signals proximity. Focus is a navigation behavior — it signals selection via keyboard or
assistive technology.

Designing hover without focus means keyboard users navigate blind. Designing focus
identically to hover means keyboard users can't tell whether they've reached an element
or are merely near it.

> **Universal:** Focus states must be visually distinct from hover states. A focused element
> must be identifiable without a mouse. [WCAG 2.4.7]

On touch devices, hover doesn't exist at all. Any functionality or information gated
behind hover is invisible to a significant portion of users.

> **Universal:** Never gate functionality or content behind hover alone. Every hover
> interaction must have a touch-accessible equivalent. [WCAG 2.1.1]

---

## Disabled vs. hidden

A common design decision: should an unavailable action be disabled (visible but inert) or
hidden entirely?

- **Disable** when the user needs to know the action exists and understand what would make
  it available. A grayed-out "Publish" button on a draft with validation errors teaches the
  interface's rules. Pair with a reason — tooltip, inline text, or contextual hint.
- **Hide** when the action is irrelevant to the current context and showing it would add
  noise. An admin-only action shouldn't appear grayed out for regular users — it should
  simply not exist in their view.

The wrong choice in either direction creates confusion: disabling everything looks broken;
hiding everything makes capabilities invisible.

---

## Loading as a design moment

Loading states reveal more about design quality than almost any other moment. The choices:

- **Skeleton screens** — show the shape of incoming content. Communicates structure and
  feels faster than a spinner. Best for content-heavy views where the layout is predictable.
- **Inline progress** — a progress bar or percentage within the triggering element. Best
  for actions with measurable progress (uploads, exports).
- **Spinners** — generic but universally understood. Best for short, indeterminate waits.
  Avoid for anything over ~3 seconds — users lose confidence.
- **Optimistic updates** — show the result immediately, reconcile with the server in the
  background. Feels instant. Only appropriate when the action almost always succeeds and
  failure is gracefully recoverable.

> **Universal:** Maintain spatial stability during loading. Elements must not jump, resize,
> or reflow when content arrives. Reserve the space before it's filled.

---

## Error proximity

> **Universal:** Error messages must appear near the element that caused them — not in a
> distant banner or toast. Users must be able to connect cause and effect without scanning
> the full interface.

In forms, inline validation below each field outperforms a summary at the top in nearly
every usability study. When a top-level summary is necessary (e.g., server errors affecting
multiple fields), it should still link or scroll to the specific fields involved.

> **Universal:** Error states must not rely on color alone. Pair color with an icon, border
> change, or text label so colorblind users can identify the error. [WCAG 1.4.1]

---

## State transitions

States don't just exist — they change. The transition between states is its own design
concern:

- **Default → Hover**: nearly instant. Any perceptible delay makes the interface feel laggy.
- **Active → Loading**: immediate. The user should never wonder if their click registered.
- **Loading → Success/Error**: should feel like a resolution, not an interruption. A brief
  pause (200–400ms) before showing the result can actually feel faster than an instant
  switch, because it suggests the system "did work."
- **Error → Default**: let the user correct the issue and try again without having to
  dismiss the error state manually. Clear error styling as the user begins editing.
