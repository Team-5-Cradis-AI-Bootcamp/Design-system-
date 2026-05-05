---
name: Icons
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Icons

Icons communicate actions, status, and concepts at a glance. Almosafer uses a consistent icon system based on a 24px grid with clear sizing hierarchy.

---

## Size Scale

| Token | Size | Usage |
|-------|------|-------|
| `icon-xs` | 16px | Inline badges, small indicators |
| `icon-sm` | 20px | Form fields, small UI elements |
| `icon-md` | 24px | Standard buttons, navigation, headers |
| `icon-lg` | 32px | Cards, sections, emphasis |
| `icon-xl` | 48px | Hero sections, large components |

---

## Grid System

All icons are drawn on a **24px base grid** with:
- **Safe area:** 20px (4px padding inside 24px frame)
- **Stroke weight:** 2px (consistent line thickness)
- **Corner radius:** 2px (subtle rounding on corners)

Scale icons by multiples of 4px for consistency:
- 16px (24px − 8px)
- 20px (24px − 4px)
- 24px (base)
- 32px (24px + 8px)
- 48px (24px × 2)

---

## Naming Convention

Use clear, semantic names following this pattern:

**Format:** `{action}_{object}_{state}`

**Examples:**
- `arrow_back` — navigation back
- `arrow_forward` — navigation forward
- `check_circle` — success confirmation
- `error_circle` — error state
- `close` — close/dismiss action
- `menu` — open menu
- `search` — search action
- `filter` — filter option
- `calendar` — date picker
- `clock` — time picker
- `location` — location/map
- `star` — favorite/rating
- `star_filled` — filled favorite
- `heart` — like action
- `heart_filled` — filled like
- `share` — share action
- `download` — download file
- `upload` — upload file
- `settings` — settings/gear
- `info` — information
- `warning` — warning state
- `user` — profile/account
- `logout` — sign out

---

## Dos and Don'ts

### ✓ Do

- **Use the 5 defined sizes.** Never scale to arbitrary sizes (18px, 22px, etc.).
- **Match icon size to context.** 16px for inline, 24px for navigation, 48px for hero.
- **Keep consistent stroke weight.** 2px across all icons.
- **Use semantic names.** `close` not `x`, `search` not `magnifying_glass`.
- **Maintain 2px corner radius.** Rounded, friendly appearance.

### ✗ Don't

- **Create custom sizes.** Use the scale—scale by 4px increments only.
- **Mix stroke weights.** Keep all icons at 2px thickness.
- **Use decorative icons.** Icons should communicate action or status.
- **Forget padding.** Icons have 2px internal padding within the 24px grid.
- **Invent new icon names.** Use the naming convention consistently.

---

## Color Usage

Icons inherit text color by default. Apply semantic colors only when needed. All color values are defined in [`color.md`](./color.md) — reference tokens by name, never hardcode hex values.

| Token | Usage |
|-------|-------|
| `Primary/500` | Interactive icons, navigation, CTAs |
| `Neutral/700` | Disabled, secondary icons |
| `Success/500` | Confirmation, positive actions |
| `Warning/500` | Alerts, non-critical issues |
| `Error/500` | Errors, destructive actions |
| `Action/500` | Promotional or attention-grabbing actions (optional) |

> See [`color.md`](./color.md) for the full palette including 50–900 shade ramps for each color. Use lighter shades (100–300) for backgrounds and disabled states; darker shades (700–900) for hover, pressed, or high-contrast contexts.

---

## Figma Variables

Create these in Figma:

**Icon Sizes**
- `Icon/XS` → 16px
- `Icon/SM` → 20px
- `Icon/MD` → 24px
- `Icon/LG` → 32px
- `Icon/XL` → 48px

**Icon Grid**
- `Icon/Grid/Base` → 24px
- `Icon/Grid/SafeArea` → 20px
- `Icon/Grid/StrokeWeight` → 2px
- `Icon/Grid/CornerRadius` → 2px

Apply icon size tokens to icon components. Use Material Design Icons or similar library aligned to the 24px grid.
