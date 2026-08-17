# iOS Screens Checklist

Load this before delivery. Fix every P0 failure; annotations do not turn a failure into a pass.

## P0: must pass

- [ ] Every screen uses the verified anatomy: phone 390x844, viewport 368x822, Dynamic Island 118x34 at top 11, status bar height 54 with time 9:41 and home indicator 134x5 at bottom 8
- [ ] No horizontal overflow or clipping inside any `.viewport`: `scrollWidth <= clientWidth`
- [ ] All tap targets measure at least 44px; 43.5px is the subpixel-rendering tolerance
- [ ] Icons are inline SVG with 1.8 to 2px round strokes. There are zero emoji and zero text glyphs used as graphics
- [ ] Form controls have visible labels, accessible names and adjacent error text when invalid
- [ ] Body text is at least 15px, secondary text at least 12.5px and body contrast at least 4.5:1
- [ ] Content clears the island and home-indicator safe areas; fixed CTAs overlap neither fields nor scrollable content
- [ ] Root screens share identical tab anatomy with exactly one active tab; pushed screens have a back affordance and no tab bar
- [ ] Content is plausible and complete: no lorem ipsum, placeholder boxes or unexplained empty controls
- [ ] The `:root` tokens match `DESIGN.md` exactly; frame chrome is the only allowed derived exception
- [ ] The mascot or logo decision matches `DESIGN.md`. When chosen, SVG geometry is copied verbatim from the approved board
- [ ] Calm is the default mascot state. Expressive states require their visible trigger; Resting is licensed only for the empty state; Pleased appears only on a success confirmation
- [ ] Mascot motion uses 2 to 3 short iterations, never loops infinitely, honors reduced motion and never sits beside text being edited
- [ ] Impeccable audit and polish have run; no actionable P0 or P1 remains and deterministic detector exceptions have a specific written reason

## P1: should pass

- [ ] Primary CTA has pressed, focus and disabled states
- [ ] A list flow includes an instructive empty state
- [ ] A form flow includes one realistic error-state example
- [ ] Every screen has a number, title and one-line intent on the board
- [ ] Corner radii come from `--r-sm`, `--r-md` or `--r-lg`
- [ ] Color dominance and accent budget match the approved contract
- [ ] At 375, 768, 1024 and 1440 CSS px, only the screen rail scrolls horizontally
- [ ] A dark variant exists only when the brief asked for one and supplied complete tokens
