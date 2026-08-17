---
name: ios-screens
description: Generate a multi-screen iOS prototype as one standalone HTML page with verified iPhone frames, Dynamic Island, status bar, home indicator, safe areas, semantic design tokens, mascot-state rules and a P0 quality gate. Open Design generates the visual artifact; Impeccable audits and polishes it before the deterministic browser gate. Use for iOS mockups, iPhone UI, wireframes, app prototypes and multi-screen flows.
license: MIT
compatibility: Requires the Open Design MCP (github.com/nexu-io/open-design) and Impeccable (github.com/pbakaus/impeccable) in the target project. Missing dependencies stop the workflow and trigger installation guidance.
metadata:
  version: "0.3"
---

# iOS Screens

Produce a **single standalone HTML file** showing 5 to 8 app screens side by side, each inside the verified iPhone frame and sharing one token set. The `:root` block is an implementation handoff. Open Design owns generation, Impeccable owns review and this skill owns iPhone geometry, design-contract fidelity and mascot semantics.

## Brief (collect or confirm before building)

- **App**: name and one-line purpose.
- **Screens**: ordered list, 5 to 8 per page. Split beyond 8. If missing, propose the core loop and confirm it.
- **Brand contract**: root `DESIGN.md` from `design-direction` is authoritative. Copy its tokens verbatim and honor its anti-patterns. Use the linked brand board for SVG geometry and visual examples. If no identity exists, propose `design-direction` first instead of inventing tokens ad hoc.
- **Mode**: light by default. Add dark only when the brief requests it and defines hardened tokens.

## Workflow

0. **Require both layers.** Verify that Open Design exposes `list_skills`, `create_project` and `start_run`. Verify that Impeccable is installed in the target project. If Open Design is missing, STOP and point to https://github.com/nexu-io/open-design. If Impeccable is missing, STOP and point to `npx impeccable install`. Explicit user override may produce a neutral fallback or an unreviewed draft, but neither can be called final.
1. Copy `assets/iphone-frame.html` as the base. **Never rebuild the frame from memory.** Its anatomy is fixed: phone 390x844, viewport 368x822, Dynamic Island 118x34 at top 11, status bar height 54 and home indicator 134x5 at bottom 8. Replace the seed tokens and page metadata from the contract.
2. **Generate through Open Design.** Pick the design system from the brief, run brand extraction when a reference exists, create the project and start `frontend-design`. The prompt must include the app brief, ordered screens, complete frame base, exact `DESIGN.md` contract, settled mascot decision and approved mascot geometry. Require the generator to keep frame anatomy and token names unchanged while building only inside the viewports. Poll and fetch the artifact.
3. Review the output and fix content directly. Use realistic domain content, no lorem ipsum and no unlabeled empty boxes. Use inline SVG icons with 1.8 to 2px round strokes, never emoji or text glyphs as graphics. Root screens use a large-title navbar and identical tab bar; pushed screens use a back chevron and no tab bar.
4. **Apply the mascot contract when chosen.** Copy approved SVG paths verbatim. Calm is the default state. Focused or equivalent persists only while its visible event is active. Resting belongs to the licensed empty state. Pleased or equivalent appears only on a visible confirmation after success, so omit it when no confirmation screen exists. Motion is 2 to 3 short iterations, never infinite, disabled under reduced motion and never adjacent to text being edited. Respect the board's mascot count and accent budget.
5. **Run the deterministic checklist.** Load `references/ios-checklist.md`, verify every P0 and fix failures rather than annotating them.
6. **Run the Impeccable review layer.** Run `/impeccable audit <screens>` and resolve every actionable P0 and P1. Run `/impeccable polish <screens>`, then `npx impeccable detect <screens>`. Impeccable supplements the checklist; it does not decide frame dimensions, safe-area anatomy or mascot licensing.
7. **Run rendered browser QA.** If `file://` is blocked, serve the directory with `python3 -m http.server`. At board widths 375, 768, 1024 and 1440 CSS px, allow horizontal scrolling only inside the screen rail. For every `.viewport`, verify `scrollWidth <= clientWidth`, no clipping, no content or fixed-CTA overlap, tap targets at least 44px (43.5px measured tolerance), body text at least 15px and secondary text at least 12.5px. Screenshot and inspect each screen, fix and re-check.

## Gotchas

- Status bar time is **9:41**. Battery, signal and Wi-Fi are inline SVG.
- No CDN fonts or assets. The artifact must render offline.
- Nothing sits under the island or home indicator. A root tab bar carries its bottom safe-area padding.
- Tab bar has 3 to 5 identical items across root screens with exactly one active item.
- Do not invent frame dimensions or radii.
- Tokens remain semantic and exact: `--primary`, `--surface`, `--fg`, `--muted`, `--danger` and the rest of the approved contract.
- Primary carries the identity. Accent and danger remain rare and event-bound.

## Fallback without Open Design (explicit user override only)

Build from the verified base by hand and apply steps 3 through 7 unchanged. State that the visuals use neutral defaults. The Impeccable and deterministic quality gates still apply.

## Delivery

- One file: `docs/design/<app>-screens.html`, or the user-provided path.
- Report the Open Design run, Impeccable result and browser-gate result.
- Tell the user that the token block is ready to translate into SwiftUI, UIKit or React Native constants.
