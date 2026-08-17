# DESIGN.md template

Load this when writing the root agent-facing contract. Keep the final file under 60 lines because agents read it before every UI task. If Impeccable init already created `DESIGN.md`, update that file instead of creating another contract.

```markdown
# DESIGN.md: <Product>

Visual authority: `<brand board path>`; Open Design project: `<project id or not retained>`.
Quality review: Impeccable audit plus the surface-specific deterministic gate.

## Typography

| Role | Family | Weight |
|------|--------|--------|
| Display / headings | <family> | <weights> |
| UI body / labels | <family> | <weights> |
| Data / mono when used | <family> | <weights> |

## Colour tokens

- Canvas and foreground: `--bg: #...`; `--fg: #...` (<contrast ratio>)
- Primary: `--primary: #...`; `--primary-600: #...`
- Accent: `--accent: #...` (<licensed uses and contrast pair>)
- Semantic: `--muted`, `--surface`, `--border`, `--danger`, `--success`
- Scales: `--r-sm/md/lg`; `--s1..s5`
- Additional themes: <exact token overrides, or state that none ship>

## Iconography

- <grid, stroke, caps, joins, fill policy and asset source>

## Signature elements

- <motif>: allowed <placements>; forbidden <placements>.
- Repeat for 3 to 5 identity-bearing motifs.

## Mascot / logo

- Decision: <mascot chosen or declined by the user; state what carries personality>.
- Source of truth: <approved asset or board anchor>.
- Behavior when chosen: calm by default; expressive states require visible events; motion is 2 to 3 short iterations, never infinite; nothing animates beside edited text.

## Anti-patterns

- <project-specific never-list: palette, layout, illustration, motion and copy rules>.
```

Rules:
- Every hex must match the brand board token block exactly.
- Contrast ratios are commitments, not decoration.
- The mascot or logo decision is always explicit in the body, even when the user declines a mascot.
- Once code owns a token or asset, add its source path so the contract cannot drift silently.
