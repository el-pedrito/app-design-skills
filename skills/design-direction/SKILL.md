---
name: design-direction
description: Establish a product's global art direction before screens exist as a standalone HTML brand board and durable DESIGN.md. Covers semantic tokens, typography, iconography, the user-settled mascot or logo decision, app icons, signature elements and anti-patterns. Open Design generates the artifact; Impeccable critiques, audits and polishes it before delivery. Use for art direction, DA, brand identity, mood boards, visual identity, brand colors, mascot direction, or before screen generation for an app without a settled identity.
license: MIT
compatibility: Requires the Open Design MCP (github.com/nexu-io/open-design) and Impeccable (github.com/pbakaus/impeccable) in the target project. Missing dependencies stop the workflow and trigger installation guidance.
metadata:
  version: "0.3"
---

# Design Direction

Produce a **single standalone HTML brand board** that settles how the product feels before any screen is drawn. Its `:root` tokens and root `DESIGN.md` are the same durable design contract. Downstream skills consume that contract instead of re-inventing the identity.

Open Design owns generation. Impeccable owns critique, technical audit and polish. This skill remains authoritative for token fidelity, the mascot or logo decision and the required board contents.

## Brief (collect or confirm before building)

- **Product**: name, one-line purpose and audience.
- **Mood**: 3 to 5 adjectives. If missing, propose them from the purpose and confirm.
- **References**: a site or app for Open Design `brand-extract`, an Open Design system to lean on, or mood words alone.
- **Mascot or logo**: wanted or declined. This is the USER's call, never the agent's. If the brief is silent, ASK before generation: "Do you want a small character in the identity, or should the logo and visual system carry it alone?" Never let generation silently decide.

## Workflow

0. **Require both layers.** Verify that Open Design exposes `list_skills`, `create_project` and `start_run`. Verify that the Impeccable skill or CLI is available in the target project. If Open Design is missing, STOP and point to https://github.com/nexu-io/open-design. If Impeccable is missing, STOP and point to `npx impeccable install`. An explicit user override may generate a neutral board without Open Design or an unreviewed draft without Impeccable, but it cannot be called final.
1. Resolve the direction inputs. If a reference exists, use Open Design `brand-extract`; otherwise pick 1 or 2 matching Open Design systems as inspiration, never as a straitjacket.
2. **Generate through Open Design.** Create a project, then start the `frontend-design` skill with the full brief, mood words, reference or design system, required board structure and settled mascot decision. State the decision literally, for example `mascot: yes, geometric and stroke-consistent` or `mascot: declined by the user`. Generation never re-decides it. Poll the run and fetch the artifact.
3. The board MUST contain, in order:
   - **Identity**: product name, one-line essence and mood words.
   - **Palette**: 4 to 6 core swatches with name, hex and role. Declare semantic `:root` tokens at the top: `--primary`, `--primary-600`, `--accent`, `--bg`, `--fg`, `--muted`, `--surface`, `--border`, `--danger`, `--success`, radius and spacing scales and font stacks.
   - **Typography**: display, body and data stacks plus the scale in use. System stacks only, no CDN.
   - **Iconography**: grid, stroke width, corner style and 5 to 6 sample inline SVG icons.
   - **Mascot / logo**: this section is always present and records the user's decision. When chosen, include the geometric stroke-consistent character, 3 to 4 licensed states, calm as the default, expressive states only after visible events, 2 to 3 iteration motion bursts, no infinite loops, no animation beside edited text, a black-on-white reproduction check and a mark plus wordmark lockup. When declined, record what carries personality instead.
   - **App icon concepts**: 2 to 3 routes at icon proportions, including the mascot route when licensed.
   - **Signature elements**: 3 to 5 distinctive motifs, with allowed and forbidden placements for each.
   - **Principles and anti-patterns**: 4 to 6 behavioral rules, dominance ratios, accent budget, copy tone and a project-specific never-list.
4. Every board color must resolve to the `:root` contract. Use real content, no lorem ipsum, no emoji and no text glyph used as a graphic.
5. **Run the Impeccable review layer.** Run `/impeccable critique <board>` for hierarchy and distinctiveness, then `/impeccable audit <board>` for measurable quality. Resolve every actionable P0 and P1, use `/impeccable polish <board>` for the final pass, then run `npx impeccable detect <board>`. Do not waive a finding without a specific written reason.
6. **Run browser QA after Impeccable.** At 375, 768, 1024 and 1440 CSS px, verify no document-level horizontal overflow, readable masthead and intentional component behavior. Check body contrast at 4.5:1 or better and the black-on-white reproduction specimen when a mascot was chosen.

## Handoff (two artifacts)

- **Board for human validation**: `docs/design/<product>-brand.html`, or the user-provided path.
- **Contract for agents and code**: root `DESIGN.md`, using `references/design-md.md`. Keep it under 60 lines with exact tokens, contrast commitments, typography, iconography, signature elements, the mascot or logo decision, behavior rules and anti-patterns. If Impeccable init already created `DESIGN.md`, update that file instead of creating a second contract.
- Tell the user that the board and `DESIGN.md` express the same contract. Run `ios-screens` next and copy the tokens and mascot geometry verbatim.

## Gotchas

- Decide dominance on the board so screens do not re-litigate it.
- A mascot without a one-ink reproduction pass will fail as a small app icon later.
- Keep the board concise. A direction that needs ten pages is not settled.
- Impeccable improves the artifact but does not get to override the user's mascot decision or the exact token contract.
