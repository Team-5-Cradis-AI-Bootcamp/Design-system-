---
name: Checkbox
tier: component
status: stable
last-updated: 2026-05-04
depends-on: foundations/color, foundations/spacing, foundations/borders, foundations/typography, foundations/icons, Tokens/aliases
---

# Checkbox

> A binary toggle for filters, settings, and consent. Tap the box or the label — both areas are interactive. Used in flight filters ("Direct Flights"), baggage selection, and form opt-ins.

---

## Anatomy

```
┌─────────────────────────────────────────┐
│  [ ]  Label text                        │
│   ↑     ↑                               │
│   box   label (clickable too)           │
└─────────────────────────────────────────┘

[ ]  unchecked  →  empty box, 1px border
[✓]  checked    →  filled box, white checkmark
[—]  indeterm.  →  filled box, white horizontal bar
```

| Part | Description |
|---|---|
| Box | 20×20px square. The visual checkbox itself. |
| Checkmark icon | 16×16px (Icon/Size/Inline). White, centered in box. Visible when checked. |
| Indeterminate bar | 12×2px white horizontal bar, centered. Visible when indeterminate. |
| Label | Body text to the right of the box, vertically centered. Clickable (extends touch target). |
| Touch target | 44×44px minimum, achieved by padding the entire row (box + gap + label) on mobile. |

---

## Tokens

### Layout

| Property | Token | Value |
|---|---|---|
| Box size | (literal) | 20 × 20 px |
| Box border radius | `Radius/Tight` | 4px |
| Box border width | (literal) | 1px |
| Box → label gap | `Spacing/SM` | 8px |
| Focus ring offset | (literal) | 2px outside the box |
| Focus ring width | (literal) | 2px |

### Typography (label)

| Slot | Style |
|---|---|
| Label | `Typography/Body/MD` (16/24, Regular) |

### Colors — by state

See full state matrices below. All values reference aliases — never primitives directly.

---

## States

The checkbox has two **value states** (unchecked, checked, indeterminate) crossed with five **interaction states** (default, hover, focus, active, disabled). Plus an orthogonal `error` flag for form validation.

### Unchecked

| State | Box border | Box fill | Label color | Notes |
|---|---|---|---|---|
| Default | `Color/Border/Default` (Neutral/300) | transparent | `Color/Text/Primary` | The resting state. |
| Hover | `Color/Border/Hover` (Primary/500) | `Color/Surface/Hover` (Neutral/100) | `Color/Text/Brand` (Primary/500) | Cursor over box or label. |
| Focus | `Color/Border/Focus` (Primary/500) + 2px focus ring `Color/Focus/Default` | transparent | `Color/Text/Primary` | Keyboard focus. |
| Active | `Color/Border/Selected` (Primary/500) | `Color/Surface/Active` (Neutral/200) | `Color/Text/Primary` | Mid-click / mid-tap. |
| Disabled | `Color/Border/Disabled` (Neutral/200) | transparent | `Color/Text/Disabled` (Neutral/300) | Not interactive. Cursor: `not-allowed`. |
| Error | `Color/Border/Error` (Error/500) | transparent | `Color/Text/Error` (Error/600) | Validation failure. Used with helper text below. |

### Checked

| State | Box border | Box fill | Checkmark | Label color | Notes |
|---|---|---|---|---|---|
| Default | none (0px) | `Color/Fill/Brand/Default` (Primary/500) | `Color/Text/On-Color` (Neutral/50) | `Color/Text/Primary` | The resting checked state. |
| Hover | none | `Color/Fill/Brand/Hover` (Primary/600) | `Color/Text/On-Color` | `Color/Text/Brand` (Primary/500) | Cursor over box or label. |
| Focus | none + 2px focus ring `Color/Focus/Default` | `Color/Fill/Brand/Default` | `Color/Text/On-Color` | `Color/Text/Primary` | Keyboard focus. |
| Active | none | `Color/Fill/Brand/Active` (Primary/700) | `Color/Text/On-Color` | `Color/Text/Primary` | Mid-click. |
| Disabled | none | `Color/Fill/Disabled` (Neutral/200) | `Color/Text/Disabled` (Neutral/300) | `Color/Text/Disabled` | Not interactive. |
| Error | 1px `Color/Border/Error` | `Color/Fill/Brand/Default` | `Color/Text/On-Color` | `Color/Text/Error` | Rare — usually error applies to unchecked "must accept" cases. |

### Indeterminate

Visually identical to **Checked** in every interaction state, but the icon is replaced with a 12×2px white horizontal bar (centered). Used by "Select all" controls in tables/lists where some children are checked.

| State | Same as Checked? |
|---|---|
| Default, Hover, Focus, Active, Disabled, Error | ✓ Yes — only the icon glyph changes (bar instead of checkmark). |

---

## Variation Matrix (full)

13 cells × all primary value × interaction states:

| | Default | Hover | Focus | Active | Disabled | Error |
|---|---|---|---|---|---|---|
| **Unchecked** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Checked** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Indeterminate** | ✓ | (= Checked Hover) | (= Checked Focus) | (= Checked Active) | (= Checked Disabled) | (= Checked Error) |

= **18 distinct visual variants**, of which **13** need unique Figma component variants (Indeterminate's interaction states reuse Checked visuals with a different glyph).

---

## Behavior

- Clicking the **box** OR the **label** toggles the value (unchecked ↔ checked). Clicking an **indeterminate** checkbox checks it (becomes checked).
- The label is part of the touch target. Mobile rows extend full-width to give a 44px tap area.
- Keyboard: `Space` toggles. `Tab` moves focus.
- Screen readers announce: label text, checked / unchecked / mixed (indeterminate), and the disabled state.

---

## Usage Rules

### ✓ Do
- **Use a clear, action-oriented label.** "Include baggage" not "Baggage option".
- **Pair multiple checkboxes in a vertical list** when they're independent options. Use `Spacing/MD` (12px) between rows.
- **Show validation errors below the checkbox**, not inline with the label, using `Typography/Caption/MD` and `Color/Text/Error`.
- **Use `Indeterminate`** only as a parent of a list of checkboxes (mixed children).

### ✗ Don't
- **Don't use a checkbox for "yes / no"** — use a Switch or Radio.
- **Don't make the label a link.** Keep the label plain. Put external links in a separate area.
- **Don't show focus ring on click** — it's keyboard-only. Pointer interactions get hover + active, not focus.
- **Don't shrink the box below 20×20.** Touch target stays 44×44 even on small screens.
- **Don't invent a checkbox color.** All states resolve to the alias tokens listed above.

---

## Figma Implementation

This spec is implemented as a **Component Set** in Figma named `Checkbox` with three component properties:

| Property | Type | Values |
|---|---|---|
| `Value` | Variant | `Unchecked` · `Checked` · `Indeterminate` |
| `State` | Variant | `Default` · `Hover` · `Focus` · `Active` · `Disabled` · `Error` |
| `Label` | Text (instance) | string — defaults to `"Label"` |

All visual properties bind to the variables and styles already in the file:

| Component layer | Bound to |
|---|---|
| Box fill | One of `Color/Fill/Brand/{Default, Hover, Active}`, `Color/Fill/Disabled`, or transparent (per state) |
| Box stroke | One of `Color/Border/{Default, Hover, Focus, Selected, Disabled, Error}` (per state) |
| Box stroke weight | `1px` literal |
| Box corner radius | `Radius/Tight` |
| Checkmark icon fill | `Color/Text/On-Color` (or `Color/Text/Disabled` when disabled) |
| Indeterminate bar fill | Same as checkmark fill |
| Label text | `Typography/Body/MD` text style |
| Label color | One of `Color/Text/{Primary, Brand, Disabled, Error}` (per state) |
| Box → label gap | `Spacing/SM` (auto-layout) |
| Focus ring (effect or stroke) | `Color/Focus/Default` |

> **Building this component:** ask Claude to "build the Checkbox in Figma" — the build script will create the 13 variants with all bindings applied, using only the tokens listed in this spec.
