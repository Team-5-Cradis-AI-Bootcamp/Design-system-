---
name: Border Radius
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Border Radius

Border radius creates visual softness and helps distinguish component types. Almosafer uses a 4-step scale for consistency across all rounded elements.

---

## Scale

| Token | Value | Usage |
|-------|-------|-------|
| `radius-none` | 0px | Sharp corners—rare, only when sharpness is intentional |
| `radius-sm` | 4px | Small buttons, minor UI elements, tight spacing |
| `radius-md` | 8px | Standard buttons, form inputs, small cards |
| `radius-lg` | 12px | Cards, modals, larger components |
| `radius-circle` | 50% | Perfect circles, circular avatars, status dots |
| `radius-pill` | 9999px | Pill-shaped buttons, toggle switches, rounded rectangles |

---

## Usage Guidelines

### Small Radius (4px)
- Badges, small pill buttons, tight UI elements
- Input focus indicators, thin borders

### Medium Radius (8px)
- Primary buttons, form inputs, small cards
- Most common radius in the system

### Large Radius (12px)
- Hotel/flight cards, section containers
- Modals, panels, large components

### Full Radius (50% and 9999px)
- **50% (Circle):** Profile avatars, circular icons, status dots
- **9999px (Pill):** Pill-shaped buttons, toggle switches, full-width rounded rectangles

---

## Dos and Don'ts

### ✓ Do

- **Pick from the scale.** Always use one of the 6 values.
- **Match component purpose.** Larger components use larger radius.
- **Maintain consistency.** If a button is 8px, all buttons are 8px.
- **Combine with shadows.** Rounded corners work best with subtle elevation.

### ✗ Don't

- **Create custom radius values.** No 6px, 10px, or 15px.
- **Mix radius sizes on one component.** Keep corners uniform unless intentional.
- **Over-round small elements.** 4px is usually the max for compact UI.
- **Use full radius (50%) for non-circular shapes.** Use specific pixel values instead.

---

## Figma Variables

Create these in Figma:
- `Border Radius/None` → 0px
- `Border Radius/SM` → 4px
- `Border Radius/MD` → 8px
- `Border Radius/LG` → 12px
- `Border Radius/Circle` → 50%
- `Border Radius/Pill` → 9999px

Apply to component corner radius in Figma's design panel.
