---
name: Alias Tokens
tier: aliases
status: stable
last-updated: 2026-05-02
maintainer: Design Systems Team
source: foundations/color.md, foundations/spacing.md, foundations/typography.md, foundations/borders.md, foundations/shadows.md, foundations/icons.md, foundations/grid.md
convention: property-first (Material 3 / Carbon / Nord pattern)
---

# Alias Tokens — Almosafer Design System

> **The contract between Figma, code, and AI.** Every alias token is defined here with what it resolves to, when to use it, and when not to. If a token isn't in this file, it doesn't exist at the alias layer.

## Naming convention

**Format:** `{Foundation}/{Property}/{Role-or-State}`

- **Foundation** — Color, Spacing, Typography, Radius, Elevation, Icon, Breakpoint
- **Property** — what the token applies to (Text, Border, Surface, Size, etc.)
- **Role / State / Step** — the variant within that property (Primary, Subtle, Hover, LG, etc.)

**Reads as a sentence:** `Color/Text/Error` → *"Color, applied to Text, in the Error role."*

**Token forms:**
- **Figma:** `Color/Text/Primary` — slash-separated, mirrors variable collection nesting.
- **CSS:** `--color-text-primary` — kebab-case.

**Layer rule:**
- Components reference **aliases** (this file), never primitives.
- Aliases reference **primitives** (foundation files), never each other.
- Semantic / component tokens (next layer, not in this file) will reference aliases.

---

## 1 · Color — Background

Page-level surfaces. The outermost layer of any view.

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Background/Default` | `Neutral/50` (#FFFFFF) | The outermost background of any view. | Inside a card or modal — use `Surface/*`. |
| `Color/Background/Subtle` | `Neutral/100` (#F5F5F5) | Secondary page backgrounds, alternating sections, app shell behind cards. | Default page bg. |
| `Color/Background/Brand` | `Primary/50` (#F5FBFC) | Brand-tinted page sections, promotional bands. | Default content areas. |
| `Color/Background/Inverse` | `Neutral/900` (#333333) | Dark hero sections, footers, full-bleed dark sections. | Standard content. |

---

## 2 · Color — Surface

Container surfaces — cards, modals, dropdowns. Anything that sits on top of a Background.

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Surface/Default` | `Neutral/50` (#FFFFFF) | Cards, modals, dropdowns, popovers on a default page bg. | Page-level backgrounds — use `Background/*`. |
| `Color/Surface/Subtle` | `Neutral/100` (#F5F5F5) | Nested containers, subtle panels, table zebra rows. | Top-level cards. |
| `Color/Surface/Hover` | `Neutral/100` (#F5F5F5) | Hover on a list item, table row, selectable surface. | Hover on buttons — use `Fill/Brand/Hover`. |
| `Color/Surface/Active` | `Neutral/200` (#E0E0E0) | Pressed/active state on a selectable surface. | Active on buttons. |
| `Color/Surface/Selected` | `Primary/50` (#F5FBFC) | Selected list item, selected nav item, selected filter chip. | Form fields. |
| `Color/Surface/Selected-Hover` | `Primary/100` (#ECF7F9) | Selected list item, on hover. | Standalone hover. |
| `Color/Surface/Disabled` | `Neutral/200` (#E0E0E0) | Disabled component fill (button, chip, switch track). | Anything functional. |
| `Color/Surface/Inverse` | `Neutral/900` (#333333) | Dark tooltips, dark snackbars, inverse-themed surfaces. | Standard surfaces. |

---

## 3 · Color — Text

All text colors, including text in feedback contexts.

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Text/Primary` | `Neutral/900` (#333333) | Body copy, headlines, default text. | On a colored or inverse background. |
| `Color/Text/Secondary` | `Neutral/700` (#666666) | Sub-text, descriptions, metadata (price labels, hotel descriptions). | Headlines, primary copy. |
| `Color/Text/Tertiary` | `Neutral/500` (#808080) | Muted text, helper text, low-emphasis info. | Body copy. |
| `Color/Text/Placeholder` | `Neutral/400` (#999999) | Input placeholders. | Anything functional. |
| `Color/Text/Disabled` | `Neutral/300` (#BDBDBD) | Disabled controls and disabled text. | Anything functional. |
| `Color/Text/Brand` | `Primary/500` (#0C9AB0) | Standalone links in body copy, brand-coloured text. | Buttons (use `Fill/Brand` + `Text/On-Color`). |
| `Color/Text/Brand-Hover` | `Primary/600` (#008296) | Brand text/link on hover. | Default state. |
| `Color/Text/Action` | `Action/500` (#EF4550) | Promotional text, "Limited offer", attention-grabbing labels. | Errors — use `Text/Error`. |
| `Color/Text/Success` | `Success/700` (#617A2F) | Success message text on a light surface. | On `Fill/Success` (use `Text/On-Color`). |
| `Color/Text/Warning` | `Warning/700` (#996D00) | Warning message text on a light surface. | On `Fill/Warning` (use `Text/On-Color`). |
| `Color/Text/Error` | `Error/600` (#B4111C) | Error message text under form fields. | Body copy that happens to be in an error state. |
| `Color/Text/Info` | `Primary/700` (#00677B) | Info message text on a light surface. | On `Fill/Info` (use `Text/On-Color`). |
| `Color/Text/On-Color` | `Neutral/50` (#FFFFFF) | Text on any saturated `Fill/*` (Brand, Action, Success, Error). | On neutral surfaces. |
| `Color/Text/On-Inverse` | `Neutral/50` (#FFFFFF) | Text on `Surface/Inverse` or `Background/Inverse`. | Standard surfaces. |

---

## 4 · Color — Border

All border colors. Status borders (Success, Warning, Error, Info) live here, not under Fill.

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Border/Subtle` | `Neutral/200` (#E0E0E0) | Default 1px borders, dividers, card outlines. | Form fields — too weak. |
| `Color/Border/Default` | `Neutral/300` (#BDBDBD) | Form inputs, stronger dividers. | Page-level dividers — too strong. |
| `Color/Border/Strong` | `Neutral/400` (#999999) | Emphasised borders, segmented controls. | Casual borders. |
| `Color/Border/Hover` | `Primary/500` (#0C9AB0) | Hover state on inputs, cards, selectable items. | Default state. |
| `Color/Border/Focus` | `Primary/500` (#0C9AB0) | The 2px focus ring on any interactive element. | Anything other than focus. |
| `Color/Border/Selected` | `Primary/500` (#0C9AB0) | Selected card, selected radio, selected filter. | Hover state. |
| `Color/Border/Disabled` | `Neutral/200` (#E0E0E0) | Disabled inputs and disabled bordered elements. | Functional elements. |
| `Color/Border/Brand` | `Primary/500` (#0C9AB0) | Brand-emphasised borders. | Default borders. |
| `Color/Border/Action` | `Action/500` (#EF4550) | Promotional borders (sale callouts). | Errors. |
| `Color/Border/Success` | `Success/500` (#A1CC4F) | Success banner borders, success form-field outlines. | Casual emphasis. |
| `Color/Border/Warning` | `Warning/500` (#FFB600) | Warning banner borders. | Critical errors. |
| `Color/Border/Error` | `Error/500` (#E11523) | Error banner borders, error form-field outlines. | Standard borders. |
| `Color/Border/Info` | `Primary/500` (#0C9AB0) | Info banner borders. | Required actions. |
| `Color/Border/Inverse` | `Neutral/700` (#666666) | Borders on inverse-themed surfaces. | Standard surfaces. |

---

## 5 · Color — Fill

Saturated coloured backgrounds — CTAs, badges, banners, status fills.

### Fill — Brand

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Fill/Brand/Default` | `Primary/500` (#0C9AB0) | Primary button background, primary CTA, brand fill on icons/badges. | Secondary actions. |
| `Color/Fill/Brand/Hover` | `Primary/600` (#008296) | Primary CTA on hover. | Default state. |
| `Color/Fill/Brand/Active` | `Primary/700` (#00677B) | Primary CTA pressed/active. | Default or hover. |
| `Color/Fill/Brand/Subtle` | `Primary/100` (#ECF7F9) | Light brand-tinted fills — info banner bg, brand badge bg. | Strong brand emphasis. |
| `Color/Fill/Brand/Subtle-Hover` | `Primary/200` (#CEEBEF) | Brand-subtle fill on hover. | Default state. |

### Fill — Action

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Fill/Action/Default` | `Action/500` (#EF4550) | Promotional CTAs ("Book now", "Limited offer"), urgency labels, sale badge fills. | Errors — use `Fill/Error/*`. |
| `Color/Fill/Action/Hover` | `Action/600` (#D23241) | Action CTA on hover. | Default state. |
| `Color/Fill/Action/Active` | `Action/700` (#9E2631) | Action CTA pressed/active. | Default or hover. |
| `Color/Fill/Action/Subtle` | `Action/100` (#FEF0F1) | Subtle promotional fills (sale banners, deal callouts). | Strong action emphasis. |

### Fill — Status

| Token | Resolves to | Use when |
|---|---|---|
| `Color/Fill/Success/Default` | `Success/500` (#A1CC4F) | Success icons, status dots, saturated success accents. |
| `Color/Fill/Success/Subtle` | `Success/100` (#F7FBF1) | Success banner background, success badge fill. |
| `Color/Fill/Warning/Default` | `Warning/500` (#FFB600) | Warning icons, status dots, saturated warning accents. |
| `Color/Fill/Warning/Subtle` | `Warning/100` (#FFF9EB) | Warning banner background. |
| `Color/Fill/Error/Default` | `Error/500` (#E11523) | Error icons, validation marks, saturated error accents. |
| `Color/Fill/Error/Subtle` | `Error/100` (#FDECED) | Error banner background, form-field error fill. |
| `Color/Fill/Info/Default` | `Primary/500` (#0C9AB0) | Info icons, info accents. |
| `Color/Fill/Info/Subtle` | `Primary/100` (#ECF7F9) | Info banner background, tip badge. |

### Fill — Disabled

| Token | Resolves to | Use when |
|---|---|---|
| `Color/Fill/Disabled` | `Neutral/200` (#E0E0E0) | Disabled fill on any control regardless of role. |

---

## 6 · Color — Focus

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Color/Focus/Default` | `Primary/500` (#0C9AB0) | The 2px focus ring on any interactive element on light surfaces. | Anything other than focus. |
| `Color/Focus/Inverse` | `Neutral/50` (#FFFFFF) | Focus ring on inverse/dark surfaces. | Light surfaces. |

---

## 7 · Color — Overlay

Scrim and overlay surfaces. Uses `Neutral/900` with opacity.

| Token | Resolves to | Use when |
|---|---|---|
| `Color/Overlay/Light` | `Neutral/900 @ 24%` | Subtle scrim (image hover, gentle dim). |
| `Color/Overlay/Medium` | `Neutral/900 @ 50%` | Modal backdrop (default). |
| `Color/Overlay/Strong` | `Neutral/900 @ 80%` | Photo lightbox, full-screen takeovers. |

---

## 8 · Spacing

Pick by **semantic size**. Use the same token for padding, gap, and margin — the CSS property is decided in component spec or CSS.

| Token | Resolves to | Use when |
|---|---|---|
| `Spacing/XS` | `space-xs` (4px) | Ultra-tight gaps—icon + label stacked, badge padding |
| `Spacing/SM` | `space-sm` (8px) | Tight gaps—form rows, compact lists, inline spacing |
| `Spacing/MD` | `space-md` (12px) | Default compact spacing—button vertical padding, dense input |
| `Spacing/LG` | `space-lg` (16px) | **DEFAULT** — standard padding, card padding, section gaps |
| `Spacing/XL` | `space-xl` (20px) | Comfortable spacing—generous component padding |
| `Spacing/2XL` | `space-2xl` (24px) | Spacious padding—modal padding, large card padding |
| `Spacing/3XL` | `space-3xl` (32px) | Major spacing—component-to-component gap |
| `Spacing/4XL` | `space-4xl` (40px) | Page-level spacing—hero sections, major section breaks |

---

## 9 · Typography

Five categories mirroring the foundation type scale. Implemented as **text styles** (not variable aliases — same reasoning as Elevation effect styles in §11). Each text style binds `fontFamily` / `fontStyle` / `fontSize` / `lineHeight` directly to typography primitives in the `Primitives` collection. See [`typography.md`](../foundations/typography.md) for the full primitive-binding table.

### Typography — Display

| Token | Resolves to | Use when |
|---|---|---|
| `Typography/Display/XL` | `display-xl` — 34 / 600 / 1.2 | Page hero ("Book Hotels in Jeddah"). |
| `Typography/Display/LG` | `display-lg` — 26 / 600 / 1.23 | Major section heading ("Recommended for You"). |
| `Typography/Display/MD` | `display-md` — 22 / 600 / 1.27 | Sub-section heading. |

### Typography — Heading

| Token | Resolves to | Use when |
|---|---|---|
| `Typography/Heading/LG` | `heading-lg` — 20 / 600 / 1.3 | Card titles, sub-sections. |
| `Typography/Heading/MD` | `heading-md` — 18 / 600 / 1.33 | Form section titles, secondary card emphasis. |

### Typography — Body

| Token | Resolves to | Use when |
|---|---|---|
| `Typography/Body/LG` | `body-lg` — 18 / 600 / 1.33 | Emphasized body, CTAs, primary actions, strong emphasis. |
| `Typography/Body/MD` | `body-md` — 16 / 400 / 1.5 | Standard paragraph text. |
| `Typography/Body/SM` | `body-sm` — 14 / 400 / 1.43 | Secondary descriptions, dense content, metadata. |

### Typography — Label

| Token | Resolves to | Use when |
|---|---|---|
| `Typography/Label/MD` | `label-md` — 14 / 600 / 1.43 | Form field labels, control labels. |
| `Typography/Label/SM` | `label-sm` — 12 / 600 / 1.33 | Badge text, tag labels, inline pill labels. |

### Typography — Caption

| Token | Resolves to | Use when |
|---|---|---|
| `Typography/Caption/MD` | `caption-md` — 12 / 400 / 1.33 | Helper text, error messages, disclaimers, fine print, image captions. |

---

## 10 · Radius

Mapped by **purpose**.

| Token | Resolves to | Use when | Don't use when |
|---|---|---|---|
| `Radius/None` | `radius-none` (0px) | Sharp corners, full-bleed surfaces. | Standard components. |
| `Radius/Tight` | `radius-sm` (4px) | Badges, small chips, focus rings, indicators. | Buttons, cards. |
| `Radius/Default` | `radius-md` (8px) | **Standard** — buttons, inputs, small cards. | Larger surfaces. |
| `Radius/Container` | `radius-lg` (12px) | Cards, modals, panels, larger components. | Buttons, inputs. |
| `Radius/Circle` | n/a — applied per-component as `width / 2` | Perfect circles, circular avatars, status dots. | Non-circular shapes. |
| `Radius/Pill` | `radius-pill` (9999px) | Pill buttons, toggle switches, rounded rectangles. | Perfect circles. |

> **Implementation note:** `Radius/Circle` has **no Figma variable** because variables can only store px (not `%`). Circular avatars set `borderRadius = width / 2` directly in code or in the Figma component's design panel — no token reference needed.

---

## 11 · Elevation

Shadow tokens mapped to **elevation purpose**. Implemented as **effect styles**, not variables (Figma variables can't reference effect styles, and effect styles are how multi-layer shadows are bundled).

| Token (Figma effect style) | Bound primitives in `Primitives/Shadow/*` | Use when | Don't use when |
|---|---|---|---|
| `Elevation/Resting` | (no layers — flat) | Flat surfaces, default cards on a tinted bg. | Anything floating above content. |
| `Elevation/Subtle` | 1 layer | Hover-state lift, soft depth on inline elements. | Modals, dropdowns. |
| `Elevation/Raised` | 3 layers | **Default elevated** — cards, dropdowns, tooltips. | Modals (use Floating). |
| `Elevation/Floating` | 3 layers | Modals, floating panels, popovers. | Cards. |
| `Elevation/Overlay` | 3 layers | High-priority modals, full-screen overlays, sheets. | Standard cards. |

See [`shadows.md`](../foundations/shadows.md) for the full per-layer breakdown of which primitives each style binds. Designers apply by effect-style name; code references via the underlying `Shadow/*` primitives.

---

## 12 · Icon — Size

Mapped by **placement context**.

| Token | Resolves to | Use when |
|---|---|---|
| `Icon/Size/Inline` | `icon-xs` (16px) | Inline with text (badges, body copy, small indicators). |
| `Icon/Size/Compact` | `icon-sm` (20px) | Form field icons, dense UI elements. |
| `Icon/Size/Default` | `icon-md` (24px) | **Standard** — buttons, navigation, headers, list items. |
| `Icon/Size/Prominent` | `icon-lg` (32px) | Section headers, card emphasis, feature highlights. |
| `Icon/Size/Hero` | `icon-xl` (48px) | Hero sections, empty states, large feature blocks. |

---

## 13 · Breakpoint

Responsive breakpoints for layout decisions.

| Token | Resolves to | Use when |
|---|---|---|
| `Breakpoint/Mobile` | `bp-mobile` (max-width: 599px) | Mobile-first base styles, single-column layouts. |
| `Breakpoint/Tablet` | `bp-tablet` (600px–1199px) | Tablet and landscape phone layouts, two-column patterns. |
| `Breakpoint/Desktop` | `bp-desktop` (min-width: 1200px) | Desktop layouts, multi-column grids, sidebars. |

---

## CSS variable naming

| Figma | CSS |
|---|---|
| `Color/Text/Primary` | `--color-text-primary` |
| `Color/Fill/Brand/Hover` | `--color-fill-brand-hover` |
| `Spacing/LG` | `--spacing-lg` |
| `Typography/Heading/LG` | `--typography-heading-lg` |
| `Radius/Container` | `--radius-container` |
| `Elevation/Raised` | `--elevation-raised` |
| `Icon/Size/Default` | `--icon-size-default` |
| `Breakpoint/Mobile` | `--breakpoint-mobile` |

