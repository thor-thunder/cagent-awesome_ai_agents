---
name: canvas-design
description: Create museum-quality visual art as a single-page PDF or PNG, driven by an explicit aesthetic philosophy. Use when the user wants a poster, art piece, design-forward one-pager, or visual manifesto — not generic AI-styled UI work.
---

## Activation

```block
auto-trigger: canvas, poster, art piece, visual art, museum quality, magazine quality, aesthetic, philosophy, design-forward, one-pager, manifesto, pdf artwork, png artwork, illustration, composition, typography poster, branding artwork
terminate-on: "ship it", "that's the one", "done", both <movement>.md and <movement>.{pdf,png} delivered, user approves the visual, user pivots to non-design topic
parallel-mcp: (none)
```

## Purpose

Produce sophisticated, design-forward artwork that looks labored over by a top-of-field visual designer. The output is 90% visual design, 10% essential text — repeating patterns, perfect shapes, museum or magazine quality.

## Two-step workflow

### Step 1 — Define an aesthetic philosophy

Coin a 1–2 word movement name. Then write 4–6 paragraphs of philosophy explaining how the movement manifests visually through:

- space (negative space, density, breathing room)
- color (palette, restraint, contrast strategy)
- scale (relative sizing, dominance)
- composition (rhythm, balance, asymmetry)
- hierarchy (what the eye lands on first, second, third)

The philosophy must emphasize craftsmanship and the appearance of meticulous labor. Save as `<movement>.md`.

### Step 2 — Visual expression

Translate the philosophy into a single-page PDF or PNG. Constraints:

- 90% visual design, 10% essential text — text is accent, not focus.
- Minimal, design-forward typography. No Inter, no centered-purple-gradient AI-slop look.
- Repeating patterns and perfect shapes; no cartoony or amateurish moves.
- Output suitable for museum or magazine reproduction.

Deliver both: `<movement>.md` + `<movement>.{pdf,png}`.

## Anti-patterns to avoid

- Excessive centered layouts.
- Purple gradients.
- Uniform rounded corners on everything.
- Default web-app aesthetic.
- Stock-photo or clipart-tier imagery.

## Tools

`Write`, `Read`, `Bash` (for image/PDF rendering tools), and any plotting/SVG/HTML→PDF stack the project already uses.

---
*Adapted from `ComposioHQ/awesome-claude-plugins/canvas-design/skills/canvas-design/SKILL.md`.*
