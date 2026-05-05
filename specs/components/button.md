---
name: Button
tier: component
status: stable
last-updated: 2026-05-04
source: foundations/color.md, foundations/spacing.md, foundations/typography.md, foundations/borders.md, foundations/shadows.md, specs/Tokens/aliases.md
---

# Button

> Buttons are the primary mechanism for user action. Every button must be immediately recognizable as clickable, sized for touch, and clearly communicate its intent and priority. Only one high-emphasis button should appear per section.

---

## Variants

Five variants cover every action type in the product.

| Variant | Description | Example |
|---------|-------------|---------|
| `primary` | Brand-teal fill. The single most important action in a view. | "Modify search", "Book" |
| `action` | Red fill. High-urgency promotional CTAs — used for the primary search trigger or time-sensitive offers. | "Search" |
| `outline` | White background with teal border. Secondary action alongside a primary. | "Sign In", "Explore more add-ons" |
| `ghost` | Subtle teal fill, teal label. Tertiary actions that expand or reveal content. | "3 more options" |
| `link` | Text only, no background or border. Inline contextual actions embedded in content. | "View cancellation policy" |

> **One `action` or `primary` per section.** Never place two high-emphasis buttons side by side. Pair `primary` + `outline` or `action` + `outline`.

---

## Sizes

| Size | Min height | Padding (V × H) | Typography | Radius | Icon size |
|------|-----------|-----------------|------------|--------|-----------|
| `lg` | 52px | `Spacing/LG` × `Spacing/2XL` | `Typography/Body/LG` | `Radius/Pill` | `Icon/Size/Default` |
| `md` | 44px | `Spacing/MD` × `Spacing/XL` | `Typography/Label/MD` | `Radius/Pill` | `Icon/Size/Default` |
| `sm` | 32px | `Spacing/SM` × `Spacing/MD` | `Typography/Label/SM` | `Radius/Pill` | `Icon/Size/Compact` |

> **Touch target:** `sm` buttons are visually 32px but must have a 44×44px invisible hit area via padding or wrapper. Never reduce the hit area below 44px.

---

## Icon Placement

| Slot | Position | Gap | Usage |
|------|----------|-----|-------|
| `leading` | Icon left of label | `Spacing/XS` | Search icon, action icons — "Search", "Book" |
| `trailing` | Icon right of label | `Spacing/XS` | Expand/collapse — "3 more options ∨" |
| `icon-only` | No label | — | Compact toolbars only. Always include an accessible label. |

Icon size follows the size scale: `md` and `lg` use `Icon/Size/Default` (24px); `sm` uses `Icon/Size/Compact` (20px).

---

## Token Map — Primary

Teal fill. The brand CTA ("Book", "Modify search").

| Property | State | Token | Resolved value |
|----------|-------|-------|----------------|
| Background | Default | `Color/Fill/Brand/Default` | `Primary/500` (#0C9AB0) |
| Background | Hover | `Color/Fill/Brand/Hover` | `Primary/600` (#008296) |
| Background | Active | `Color/Fill/Brand/Active` | `Primary/700` (#00677B) |
| Background | Disabled | `Color/Fill/Disabled` | `Neutral/200` (#E0E0E0) |
| Label | Default | `Color/Text/On-Color` | `Neutral/50` (#FFFFFF) |
| Label | Disabled | `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) |
| Border | All | none | — |
| Focus ring | Focus | `Color/Focus/Default` | `Primary/500` (#0C9AB0) |
| Shadow | Default | `Elevation/Resting` | none |
| Shadow | Hover | `Elevation/Subtle` | `shadow-xs` |
| Border radius | All | `Radius/Pill` | 9999px |

---

## Token Map — Action

Red fill. High-urgency CTA ("Search").

| Property | State | Token | Resolved value |
|----------|-------|-------|----------------|
| Background | Default | `Color/Fill/Action/Default` | `Action/500` (#EF4550) |
| Background | Hover | `Color/Fill/Action/Hover` | `Action/600` (#D23241) |
| Background | Active | `Color/Fill/Action/Active` | `Action/700` (#9E2631) |
| Background | Disabled | `Color/Fill/Disabled` | `Neutral/200` (#E0E0E0) |
| Label | Default | `Color/Text/On-Color` | `Neutral/50` (#FFFFFF) |
| Label | Disabled | `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) |
| Border | All | none | — |
| Focus ring | Focus | `Color/Focus/Default` | `Primary/500` (#0C9AB0) |
| Shadow | Default | `Elevation/Resting` | none |
| Shadow | Hover | `Elevation/Subtle` | `shadow-xs` |
| Border radius | All | `Radius/Pill` | 9999px |

---

## Token Map — Outline

White background, teal border ("Sign In", "Explore more add-ons").

| Property | State | Token | Resolved value |
|----------|-------|-------|----------------|
| Background | Default | `Color/Surface/Default` | `Neutral/50` (#FFFFFF) |
| Background | Hover | `Color/Surface/Hover` | `Neutral/100` (#F5F5F5) |
| Background | Active | `Color/Surface/Active` | `Neutral/200` (#E0E0E0) |
| Background | Selected | `Color/Fill/Brand/Default` | `Primary/500` (#0C9AB0) |
| Background | Disabled | `Color/Fill/Disabled` | `Neutral/200` (#E0E0E0) |
| Label | Default | `Color/Text/Brand` | `Primary/500` (#0C9AB0) |
| Label | Hover | `Color/Text/Brand-Hover` | `Primary/600` (#008296) |
| Label | Selected | `Color/Text/On-Color` | `Neutral/50` (#FFFFFF) |
| Label | Disabled | `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) |
| Border | Default | `Color/Border/Brand` | `Primary/500` (#0C9AB0) |
| Border | Hover | `Color/Border/Hover` | `Primary/500` (#0C9AB0) |
| Border | Selected | `Color/Fill/Brand/Default` | `Primary/500` (#0C9AB0) |
| Border | Disabled | `Color/Border/Disabled` | `Neutral/200` (#E0E0E0) |
| Border width | All | 1px | — |
| Focus ring | Focus | `Color/Focus/Default` | `Primary/500` (#0C9AB0) |
| Border radius | All | `Radius/Pill` | 9999px |

> **Selected state** applies when `outline` is used as a filter chip and is in the active/selected toggle state — e.g. "Round Trip" selected. Background becomes brand fill, label becomes `On-Color`.

---

## Token Map — Ghost

Subtle teal fill, teal label ("3 more options").

| Property | State | Token | Resolved value |
|----------|-------|-------|----------------|
| Background | Default | `Color/Fill/Brand/Subtle` | `Primary/100` (#ECF7F9) |
| Background | Hover | `Color/Fill/Brand/Subtle-Hover` | `Primary/200` (#CEEBEF) |
| Background | Active | `Color/Fill/Brand/Subtle-Hover` | `Primary/200` (#CEEBEF) |
| Background | Disabled | `Color/Fill/Disabled` | `Neutral/200` (#E0E0E0) |
| Label | Default | `Color/Text/Brand` | `Primary/500` (#0C9AB0) |
| Label | Hover | `Color/Text/Brand-Hover` | `Primary/600` (#008296) |
| Label | Disabled | `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) |
| Border | All | none | — |
| Focus ring | Focus | `Color/Focus/Default` | `Primary/500` (#0C9AB0) |
| Border radius | All | `Radius/Pill` | 9999px |

---

## Token Map — Link

Text only. No background, no border, no padding ("View cancellation policy").

| Property | State | Token | Resolved value |
|----------|-------|-------|----------------|
| Label | Default | `Color/Text/Brand` | `Primary/500` (#0C9AB0) |
| Label | Hover | `Color/Text/Brand-Hover` | `Primary/600` (#008296) |
| Label | Active | `Color/Text/Brand` | `Primary/500` (#0C9AB0) |
| Label | Disabled | `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) |
| Underline | Default | none | — |
| Underline | Hover | `Color/Text/Brand-Hover` | 1px underline |
| Focus ring | Focus | `Color/Focus/Default` | `Primary/500` (#0C9AB0) |
| Background | All | none | — |
| Padding | All | 0 | — |

> `link` inherits the typography of its surrounding context. It does not define its own size or spacing.

---

## States

All interactive variants share this state model.

| State | Visual change |
|-------|---------------|
| Default | Base token values as defined above |
| Hover | Background and/or label shift to hover token; `Elevation/Subtle` shadow on filled variants |
| Focus | 2px focus ring using `Color/Focus/Default`, 2px offset from the button edge |
| Active | Background shifts to active token; slight scale-down `transform: scale(0.98)` |
| Disabled | `Color/Fill/Disabled` fill or `Color/Border/Disabled` border; `Color/Text/Disabled` label; `cursor: not-allowed`; `opacity: 1` (full opacity — color token already signals disabled) |
| Loading | Replace label with spinner; keep button dimensions locked; disable pointer events |

---

## Anatomy

```
┌─────────────────────────────────┐
│  [leading-icon]  Label  [trailing-icon]  │
└─────────────────────────────────┘
        ↑ padding-block              ↑ padding-inline
```

- **Container** — sets background, border, radius, shadow
- **Leading icon** (optional) — `Icon/Size/Default` or `Icon/Size/Compact`; gap = `Spacing/XS`
- **Label** — single line; never wraps
- **Trailing icon** (optional) — `Icon/Size/Default` or `Icon/Size/Compact`; gap = `Spacing/XS`

---

## Usage Rules

### ✓ Do

- **Use `action` for the single highest-urgency CTA per view** — the search trigger, the booking initiator.
- **Use `primary` for the main progression action** — "Book", "Confirm", "Continue".
- **Use `outline` for secondary actions** — always paired alongside a `primary` or `action`.
- **Use `ghost` for expansion actions** — "Load more", "See all options", "Show filters".
- **Use `link` for inline contextual navigation** — policy links, help text, in-context anchors.
- **Size `lg` for full-width hero actions** (search bar, sticky booking footer).
- **Size `md` as the default** for all standalone actions.
- **Size `sm` for filter chips and compact toggles** only.
- **Always label icon-only buttons** with an `aria-label`.
- **Keep labels short** — 1–3 words. Verb-first: "Book", "Search", "Sign In".

### ✗ Don't

- **Never use two `action` or two `primary` buttons side by side.**
- **Never use `ghost` as the primary action** — it reads as tertiary.
- **Never wrap button text.** If the label is too long, shorten it.
- **Never invent a new variant** to handle an edge case — map it to one of the five variants.
- **Never hardcode colors, spacing, or radius.** Every value must trace back to a token.
- **Never use `link` as a form submit trigger** — use a button variant.
- **Never remove the focus ring** — it is required for keyboard and accessibility.
- **Never disable a button without explanation** — show a tooltip or inline error explaining why.

---

## Accessibility

| Requirement | Rule |
|-------------|------|
| Touch target | Minimum 44×44px for all sizes, including `sm` |
| Focus indicator | 2px solid `Color/Focus/Default`, 2px offset — never hidden or overridden |
| Contrast (filled) | `Color/Text/On-Color` on `Fill/Brand` → 4.87:1 ✓; on `Fill/Action` → 4.52:1 ✓ |
| Contrast (outline/ghost) | `Color/Text/Brand` on `Color/Surface/Default` → 4.58:1 ✓ |
| Disabled | Use `aria-disabled="true"` not the `disabled` attribute when the button should remain focusable for explanation |
| Loading | Add `aria-busy="true"` and `aria-label="Loading…"` during loading state |
| Icon-only | Always include `aria-label` describing the action |

---

## Figma Component Properties

When building in Figma, expose these properties per button instance:

| Property | Type | Values |
|----------|------|--------|
| `Variant` | String enum | `primary`, `action`, `outline`, `ghost`, `link` |
| `Size` | String enum | `lg`, `md`, `sm` |
| `State` | String enum | `default`, `hover`, `focus`, `active`, `disabled`, `loading` |
| `Icon leading` | Boolean | true / false |
| `Icon trailing` | Boolean | true / false |
| `Label` | Text | Button label string |
| `Selected` | Boolean | true / false — applies to `outline` filter chip usage only |

**Token bindings in Figma:**
- Fill → `Color/Fill/Brand/Default`, `Color/Fill/Action/Default`, etc. per variant and state
- Label text style → `Typography/Body/LG`, `Typography/Label/MD`, `Typography/Label/SM`
- Label color → `Color/Text/On-Color`, `Color/Text/Brand`, etc. per variant
- Corner radius → `Radius/Pill` (9999px)
- Padding → `Spacing/LG` vertical × `Spacing/2XL` horizontal for `lg`; `Spacing/MD` × `Spacing/XL` for `md`; `Spacing/SM` × `Spacing/MD` for `sm`
- Icon gap → `Spacing/XS` (4px)
- Shadow → `Elevation/Subtle` on hover for filled variants
- Focus ring → `Color/Focus/Default`, 2px stroke, 2px offset
