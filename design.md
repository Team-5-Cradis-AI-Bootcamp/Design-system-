---
name: Design
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Design

> A warm, trusted travel marketplace anchored on `neutral-50` canvas and teal confidence. One system for hotels, flights, activities, transport.

---

## Philosophy

Almosafer serves explorers and planners across hotels, flights, activities, and transport. We build trust through clarity and reliability. Complexity is hidden; possibilities are visible. Every design choice should empower confident decisions—whether booking a flight, finding a hotel, or discovering an experience.

---

## Atmosphere

| Dimension | Direction |
|-----------|-----------|
| Tone | Professional yet approachable. Trustworthy, not stiff. |
| Voice | Clear, direct, empowering — never pushy or corporate jargon |
| Emotion | Excitement balanced with reassurance. Adventure backed by competence. |
| Density | Search tight and focused. Content spacious and browseable. |
| Imagery | Photography showcases destinations. UI enables decisions. |

---

## Color Attitude

→ [`color.md`](./specs/foundations/color.md)

- `neutral-50` is the canvas. Everything lives on it.
- `primary-500` (#0C9AB0) is used sparingly — calls to action, highlights, moments of delight.
- `primary-100` through `primary-200` for hover states, tinted surfaces, and soft backgrounds.
- `neutral-900` is the default text color. Never invent a grey outside the scale.
- `neutral-100` through `neutral-300` carry borders, dividers, and disabled states.
- We do not invent colors. Every value must trace back to `color.md`.

---

## Typography Attitude

→ [`typography.md`](./specs/foundations/typography.md)

- Type is quiet. Photography is loud.
- `display-xl` and `display-lg` lead hero moments — both at weight 600.
- `body-md` is the default reading size. `body-sm` for supporting copy.
- `caption-md` for metadata — dates, labels, legal.
- `body-lg` is reserved for CTAs and primary actions.
- Open Sans is the system font. No exceptions.

---

## Spacing Attitude

→ [`spacing.md`](./specs/foundations/spacing.md)

- `space-lg` (16px) is the base unit for component padding.
- `space-sm` and `space-md` for tight internal gaps — icons, tags, inline elements.
- `space-2xl` and `space-3xl` for separating sections and components.
- `space-4xl` for hero breaks and full-page rhythm.
- Never hardcode a `px` value. If it's not on the scale, it doesn't exist.

---

## Grid & Layout Attitude

→ [`grid.md`](./specs/foundations/grid.md)

- Mobile is the primary canvas. Design at 375px first, scale up from there.
- Three breakpoints, no in-betweens: `bp-mobile` (≤599px), `bp-tablet` (600–1199px), `bp-desktop` (≥1200px).
- Touch targets are 44px minimum on mobile. No exceptions.
- Hidden content on small screens is restructured content — never disappeared.
- Desktop content tops out at 1200px. We don't sprawl edge-to-edge on ultra-wide screens.
- Spacing scales with the breakpoint. Tight on mobile, generous on desktop.

---

## Icon Attitude

→ [`icons.md`](./specs/foundations/icons.md)

- Icons clarify. They never decorate.
- 24px is the base grid. Sizes scale in 4px steps — no in-between values.
- `icon-md` (24px) for navigation and buttons. `icon-sm` (20px) for forms. `icon-xs` (16px) for inline cues.
- `icon-lg` (32px) and `icon-xl` (48px) are reserved for cards and hero moments.
- Stroke is 2px. Corners are 2px. Always.
- Icons inherit text color by default. Semantic colors (`Success/500`, `Warning/500`, `Error/500`) only signal status — never decoration.
- Names describe action — `close` not `x`, `search` not `magnifying_glass`. Use the existing set; don't invent new ones.

---

## Shadow Attitude

→ [`shadows.md`](./specs/foundations/shadows.md)

- Surfaces sit flat by default. Shadows earn their lift.
- `shadow-xs` for hover and subtle borders. `shadow-sm` for cards, dropdowns, tooltips.
- `shadow-md` for modals and floating panels. `shadow-lg` for high-priority overlays only.
- All shadows trace to `Neutral/900` with opacity. Never pure black. Never an invented grey.
- One shadow per element. Don't stack.
- If you reach for a shadow to create a border, use a border instead.

---

## Border Radius Attitude

→ [`aliases.md`](./aliases.md)

- Soft corners signal trust. Sharp edges are intentional, never default.
- `Radius/Default` (8px) is the standard — buttons, inputs, small cards.
- `Radius/Container` (12px) for hotel cards, modals, larger components.
- `Radius/Tight` (4px) for badges and tight UI. `Radius/Circle` (50%) for avatars and perfect circles. `Radius/Pill` (9999px) for pill buttons and toggle switches.
- One radius per component. Don't mix corner sizes within an element.
- No 6px, no 10px, no 15px. The scale or nothing.

---

## What we are not

- Not a dashboard product — avoid data-heavy patterns.
- Not a brand campaign — the UI is not an ad.
- Not minimal for minimalism's sake — warmth requires presence.
