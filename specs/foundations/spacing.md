---
name: Spacing
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Spacing

Almosafer's spacing system is built on a **4px base unit**. All spacing values are multiples of 4 for consistency and predictability across the product.

---

## Scale

| Token | Value | Use Case |
|-------|-------|----------|
| `space-xs` | 4px | Icon spacing, tight gaps |
| `space-sm` | 8px | Form fields, small gaps |
| `space-md` | 12px | Button padding (vertical) |
| `space-lg` | 16px | Button padding, card padding |
| `space-xl` | 20px | Section margins |
| `space-2xl` | 24px | Component spacing, section gaps |
| `space-3xl` | 32px | Large section breaks |
| `space-4xl` | 40px | Page-level spacing, hero sections |

---

## Dos and Don'ts

### ✓ Do

- **Pick from the scale.** Always use tokens—never arbitrary values.
- **Stack consistently.** Consistent spacing creates visual rhythm and predictability.
- **Start compact.** When unsure, use smaller spacing values; add more if needed.
- **Document overrides.** If you must deviate, note why and with approval.

### ✗ Don't

- **Hardcode pixel values** (`padding: 16px`). Use CSS variables or design tokens.
- **Use `margin: 0`** to remove spacing. Restructure the layout instead.
- **Mix units** (`padding: 16px; margin: 1rem`). Stick to the scale.
- **Create new spacing values** outside the scale.
- **Use physical properties** (`left`, `right`, `top`, `bottom`) for layout. Use flexbox/grid with gap.

---

## Figma Variables

When building in Figma, create:
- `Spacing/XS` → 4px
- `Spacing/SM` → 8px
- `Spacing/MD` → 12px
- `Spacing/LG` → 16px
- `Spacing/XL` → 20px
- `Spacing/2XL` → 24px
- `Spacing/3XL` → 32px
- `Spacing/4XL` → 40px

Apply to component auto-layout spacing and padding.
