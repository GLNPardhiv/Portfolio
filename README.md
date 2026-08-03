# Portfolio Website

A single-page personal portfolio built with plain HTML and CSS — no frameworks, no JavaScript, no build step.

## Design Rationale

The dark purple-and-blue palette (`#7c5cff` / `#5b8dff` on `#0a0a12`) is set once in `css/base.css` as CSS custom properties, so every section picks up the same theme by reference. Cards share a reusable pattern — surface, border, and rounded radius — which is why info cards, project cards, skill boxes, stat boxes, and contact items read as one design system without any shared utility class.

The CSS is split per section (one file per HTML section) so editing the projects grid never touches the about section. `base.css` loads first because it declares the design tokens the others depend on.

## Layout Technique

CSS Grid does the heavy lifting: the projects grid is three columns on desktop and collapses to two then one at the tablet (≤768px) and mobile (≤480px) breakpoints. The fixed navbar is offset by a `--navbar-height` token that also drives `scroll-padding-top` and `scroll-margin-top`, so anchor links glide smoothly with `scroll-behavior: smooth` and land below the navbar rather than being hidden under it. The single kept animation — the navbar underline that grows from the left on hover — uses `transform: scaleX` so it animates without triggering layout.

## Known Limitations

- The projects filter buttons are visual only; clicking them does not filter the grid.
- The skills CSS defines percentage-bar rules that have no markup using them — leftover from an earlier design.
- Asset filenames in `css/` are descriptive hashes rather than semantic names.
- All images live in `css/` alongside the stylesheets rather than in a dedicated `img/` folder.
- The contact form has no submission handler.
- No test, linter, or build pipeline.
