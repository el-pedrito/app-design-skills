# DESIGN.md: Brewlog

Visual authority: `examples/brewlog-brand.html`; Open Design project: `brewlog-design-direction-e354`, run `045a7016-eaf6-4d7a-a36d-f6f4ca37da0e`.
Quality review: Impeccable audit and polish, then the deterministic iOS browser gate.

## Typography

| Role | Family | Use |
|------|--------|-----|
| Display | Iowan Old Style, Palatino, Georgia, serif | Titles and origin names, 19px minimum |
| Body | SF / Segoe UI / system sans | Interface copy, 17px default, 15px floor |
| Data | SF Mono, Menlo, Consolas, monospace | Every dose, ratio, time and temperature |

## Colour tokens

- `--primary: #6B3C2A`; `--primary-600: #4E2A1D`; surface contrast 9.1:1 and 12.6:1
- `--accent: #D18F2C`; use as fill only; `--fg` on accent is 6.4:1
- `--bg: #F6F3EE`; `--fg: #1E1815`; foreground on background is 15.9:1
- `--muted: #6B6058`; contrast is 5.5:1 on background and 6.1:1 on surface
- `--surface: #FFFFFF`; `--border: #E2DACE`; border is never text
- `--danger: #9E2B1E`; `--success: #3E6B3A`; white contrast is 7.5:1 and 6.2:1
- Radii: `--r-sm: 4px`, `--r-md: 10px`, `--r-lg: 20px`
- Spacing: `--s1: 4px`, `--s2: 8px`, `--s3: 16px`, `--s4: 24px`, `--s5: 40px`
- Light theme only. No unlisted color may enter a screen.

## Iconography

- 24x24 grid, 1.75px open strokes, round caps and joins, no fills or perspective.
- Icons inherit `currentColor`; graphics are inline SVG, never emoji or text glyphs.

## Signature elements

- Spec line: mono brew parameters on one line; never prose or display headings.
- Extraction bar: once per brew record or full-width timer; never decoration, loading or navigation.
- Notched record: brew entries and saved recipes only; never controls, sheets or onboarding.
- Tick baseline: separators, steppers and stats axes; never card outlines or two honey ticks in one view.

## Mascot / logo

- Decision: user chose the geometric V60 dripper mascot and horizontal mark plus wordmark lockup.
- Source of truth: `examples/brewlog-brand.html#mascot`, 32x32 keyline, 2.3px stroke, no fill.
- Calm: static default. Pleased: save confirmation only, two bursts. Focused: running timer only.
- Resting: empty log only, above its sentence, never a loading state.
- Motion: 2 to 3 iterations at 380ms, no bounce or infinite loop, disabled under reduced motion.
- One mascot per screen. Never animate it beside text being edited. Honey drip only during the timer.

## Principles and anti-patterns

- Area ratio is 60% paper and white, 30% ink and roast, at most 10% honey; practical honey target is about 3%.
- Honey is reserved for rating fill, extraction marker and running timer, one honey element per screen, never text.
- Numbers use mono, interface words use sans, expressive titles use serif. Copy is precise and second-person.
- Never brown-on-brown, gradients, glass blur, heavy shadows, bounce, parallax, placeholder coffee or dark mode.
- Never hand-drawn, photographic or emoji-style mascots; never reading text below 15px or targets below 44px.
