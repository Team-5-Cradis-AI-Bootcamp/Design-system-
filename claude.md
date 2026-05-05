---
name: Claude
tier: meta
status: stable
last-updated: 2026-05-02
---

# Claude

> **READ THIS FIRST. Every session. No exceptions.**
> This file governs how Claude works inside the Almosafer design system. Follow it precisely.

---

## 1. Before any UI change

1. **Read the relevant spec first.**
   - Color question → [`specs/foundations/color.md`](./specs/foundations/color.md)
   - Spacing question → [`specs/foundations/spacing.md`](./specs/foundations/spacing.md)
   - Typography question → [`specs/foundations/typography.md`](./specs/foundations/typography.md)
   - Shadows question → [`specs/foundations/shadows.md`](./specs/foundations/shadows.md)
   - Borders question → [`specs/foundations/borders.md`](./specs/foundations/borders.md)
   - Grid question → [`specs/foundations/grid.md`](./specs/foundations/grid.md)
   - Icons question → [`specs/foundations/icons.md`](./specs/foundations/icons.md)
   - Design principles → [`DESIGN.md`](./DESIGN.md)
   - Component question → [`specs/components/`](./specs/components/)

2. **No spec exists?** Write the spec first, then build.

3. **When in doubt, do less.** A smaller correct change beats a larger wrong one.

---

## 2. Token rules — non-negotiable

```
✗  #FF385C
✓  primary-500

✗  #222222
✓  neutral-900

✗  16px
✓  space-lg

✗  64px / 500 / 1.1
✓  display-lg
```

- Every color must trace back to a shade in `color.md`.
- Every spacing value must trace back to a token in `spacing.md`.
- Every type style must trace back to a token in `typography.md`.
- Every shadow must trace back to a token in `shadows.md`.
- Every border radius must trace back to a token in `borders.md`.
- `neutral-50` is the canvas. No other value is ever used as a background default.
- We do not invent colors, spacing, type styles, shadows, or borders outside the defined scales.

---

## 3. Component rules

- Every component spec lives in [`specs/components/`](./specs/components/).
- No component is built without a spec file.
- Each spec must declare: token usage, states, and usage rules.
- States to cover for every interactive component: default, hover, focus, active, disabled.

---

## 4. Figma rules

- Build components using only tokens defined in the foundation files.
- Layer names must match token names — e.g. `primary-500`, `space-lg`, `body-md`.
- No hardcoded hex values in any Figma fill, stroke, or style.
- No hardcoded px values for spacing that isn't on the scale.
- Auto layout spacing values must match `spacing.md` tokens exactly.
- Text styles must map 1:1 to tokens in `typography.md`.
- Shadow effects must map to tokens in `shadows.md`.
- Border radius values must map to tokens in `borders.md`.

---

## 5. When a token doesn't exist

**Stop. Do not edit any file.**

Tell the user exactly what is missing and wait for explicit approval before touching anything.

| Situation | What to say |
|-----------|-------------|
| Color not in scale | "This color is not in `color.md`. Do you want me to add it?" |
| Spacing value not in scale | "This spacing value is not in `spacing.md`. Do you want me to add it?" |
| Type style not in scale | "This type style is not in `typography.md`. Do you want me to add it?" |
| Shadow not in scale | "This shadow is not in `shadows.md`. Do you want me to add it?" |
| Border radius not in scale | "This border radius is not in `borders.md`. Do you want me to add it?" |
| Component not specced | "There is no spec for this component. Do you want me to write one in `specs/components/` before building?" |

No file — spec, foundation, or otherwise — is created, edited, or deleted without the user explicitly saying yes.

> **When in doubt, ask. Never assume approval.**

---

## 6. Files at a glance

**Main**
- [`DESIGN.md`](./DESIGN.md) — philosophy, atmosphere, design attitudes
- [`specs/foundations/`](./specs/foundations/) — all token scales and rules

**Foundations**
- [`color.md`](./specs/foundations/color.md) — full color scale (Primary, Neutral, Success, Warning, Error)
- [`spacing.md`](./specs/foundations/spacing.md) — 4px base scale, usage rules
- [`typography.md`](./specs/foundations/typography.md) — Open Sans, type scale, tokens
- [`shadows.md`](./specs/foundations/shadows.md) — elevation system, 5 shadow levels
- [`borders.md`](./specs/foundations/borders.md) — border radius scale
- [`grid.md`](./specs/foundations/grid.md) — responsive breakpoints
- [`icons.md`](./specs/foundations/icons.md) — icon sizing, naming, grid

**Components**
- [`specs/components/`](./specs/components/) — all component specs (Button, Card, Form inputs, etc.)

---

## 7. Propagating changes across GitHub and Figma

When you ask Claude to change, add, or remove a token, style, or component, do all of the following in one turn:

1. Update the relevant spec file under `specs/foundations/` or `specs/components/`.
2. Update the corresponding Figma object via MCP — variable, text style, component, or shadow.
3. Show the markdown diff and confirm the Figma write succeeded.
4. Stop. Do not run `git add`, `git commit`, or `git push`. User reviews and ships manually.

Both sides must end the operation in agreement. If the Figma write fails, revert the markdown change and explain why.

If a change requires inventing a new token (a color not in `color.md`, spacing not in `spacing.md`, etc.), **STOP per §5** and ask before adding it.

---

## 8. Final reminder

> If a rule above and your judgment disagree, **the rule wins.**
> Drift starts when one exception is made silently.
