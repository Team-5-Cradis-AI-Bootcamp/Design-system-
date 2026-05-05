---
name: Shadows
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Shadows

Shadows create depth and hierarchy in Almosafer's interface. Use the elevation system to distinguish interactive elements, floating content, and layered components.

> **Shadow color** is sourced from [`color.md`](./color.md) — all shadows use the `Neutral/900` token with varying opacity. Never use pure black or invent new shadow colors.
>
> **Notation:** `Neutral/900 @ 12%` means the `Neutral/900` color token applied at 12% opacity.

---

## Elevation Levels

| Token | Value | Usage |
|-------|-------|-------|
| `shadow-xs` | `0px 1px 2px Neutral/900 @ 12%` | Subtle depth—hover states, borders |
| `shadow-sm` | `0px 2px 4px -1px Neutral/900 @ 20%, 0px 4px 5px 0px Neutral/900 @ 14%, 0px 1px 10px 0px Neutral/900 @ 12%` | Cards, dropdowns, tooltips |
| `shadow-md` | `0px 3px 5px -1px Neutral/900 @ 20%, 0px 6px 10px 0px Neutral/900 @ 14%, 0px 1px 18px 0px Neutral/900 @ 12%` | Modals, floating panels |
| `shadow-lg` | `0px 5px 5px -3px Neutral/900 @ 20%, 0px 8px 10px 1px Neutral/900 @ 14%, 0px 3px 14px 2px Neutral/900 @ 12%` | High-priority modals, overlays |
| `shadow-none` | `none` | Flat surfaces, no elevation |

Color always references `Neutral/900` from [`color.md`](./color.md). Opacity values (12%, 14%, 20%) define elevation depth and stay fixed — only the color token changes if `Neutral/900` is updated upstream.

### Implementation note

In CSS, resolve the token to its hex equivalent with opacity:
- `Neutral/900 @ 12%` → `rgba(51, 51, 51, 0.12)` (or `rgb(from var(--color-neutral-900) r g b / 12%)` in modern CSS)

In Figma, link the shadow's color to the `Neutral/900` variable and set the opacity slider to the specified percentage.

---

## Usage Guidelines

**Use shadows to:**
- Elevate interactive elements (buttons, cards, dropdowns)
- Create layered UI (modals over content)
- Indicate focus or hover states on subtle elements
- Separate floating content from the background

**Avoid:**
- Stacking multiple shadows on one element
- Using shadows as borders (use borders instead)
- Shadows on text (reduces readability)

---

## Dos and Don'ts

### ✓ Do

- **Pick from the scale.** Use defined shadow tokens only.
- **Build upward.** Start with `shadow-xs` for subtle depth, increase if needed.
- **Combine with spacing.** Shadows work best with consistent padding and gaps.
- **Test on all backgrounds.** Ensure shadows remain visible on white, gray, and colored backgrounds.
- **Use the shared color token.** Shadow color always references `Neutral/900` from [`color.md`](./color.md).

### ✗ Don't

- **Create custom shadows.** Stay within the 5 levels.
- **Layer shadows.** One shadow per element.
- **Darken text with shadows.** Use color contrast instead.
- **Use shadows on every element.** Reserve for layered, interactive, or elevated content.
- **Hardcode shadow colors.** Don't use `rgba(0, 0, 0, ...)` or arbitrary hex values — always reference `Neutral/900`.

---

## Figma — Two Layers

Shadows use a **two-layer** model. The `Primitives` collection holds atomic primitives (one variable per unique value, no duplication) under the `Shadow/` group. The 5 effect styles below stack those primitives into reusable elevation tokens.

### Layer 1 — Primitives (`Primitives` collection, 21 variables under `Shadow/`)

| Group | Variables | Type | Scope |
|---|---|---|---|
| `Shadow/color/` | `N900-12`, `N900-14`, `N900-20` | COLOR (rgba 51,51,51 with the named alpha) | `EFFECT_COLOR` |
| `Shadow/y/` | `1, 2, 3, 4, 5, 6, 8` | FLOAT | `EFFECT_FLOAT` |
| `Shadow/blur/` | `2, 4, 5, 10, 14, 18` | FLOAT | `EFFECT_FLOAT` |
| `Shadow/spread/` | `-3, -1, 0, 1, 2` | FLOAT | `EFFECT_FLOAT` |

Color values are sourced from `Neutral/900` (`#333333`) at three opacities (12%, 14%, 20%). All other shadow numbers come from the spec table above.

### Layer 2 — Effect styles (bound to primitives)

Every drop-shadow layer in every elevation style binds its `color`, `offsetY`, `radius` (blur), and `spread` to the primitives above. Designers apply these styles by name; the variables provide single-source-of-truth values.

| Effect style | Layers | y / blur / spread / color (bound primitives) |
|---|---|---|
| `Shadows/None` | 0 | — |
| `Shadows/XS` | 1 | `y/1, blur/2, spread/0, color/N900-12` |
| `Shadows/SM` | 3 | `y/2, blur/4, spread/-1, color/N900-20` + `y/4, blur/5, spread/0, color/N900-14` + `y/1, blur/10, spread/0, color/N900-12` |
| `Shadows/MD` | 3 | `y/3, blur/5, spread/-1, color/N900-20` + `y/6, blur/10, spread/0, color/N900-14` + `y/1, blur/18, spread/0, color/N900-12` |
| `Shadows/LG` | 3 | `y/5, blur/5, spread/-3, color/N900-20` + `y/8, blur/10, spread/1, color/N900-14` + `y/3, blur/14, spread/2, color/N900-12` |

> **Note:** Shadow color binds to `Shadow/color/N900-{12,14,20}` rather than directly to `Color/Neutral/900`. Figma's variable binding for effect color uses the variable's full RGBA, so the alpha must be baked into the bound variable. If `Color/Neutral/900` ever changes, the three `Shadow/color/*` primitives must be manually re-synced (their RGB values must equal the new Neutral/900 RGB).
