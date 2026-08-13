# Purelane Shopify Build — Build Notes

## What I built

I converted the Purelane homepage prototype into Shopify sections on a clean Dawn-based development store, focusing first on the five requested homepage areas:

1. Hero
2. Shop / product grid
3. Best-selling combos
4. Bundles
5. Reviews rail

I also implemented and refined supporting areas from the prototype, including the announcement bar, header/navigation, ingredients, footer, coupon/club CTA, and the additional homepage sections needed to make the page feel like one consistent experience.

## What I flagged about the original prototype

The supplied prototype is a useful visual reference, but it is a single-page design prototype rather than production Shopify code. The main production concerns I treated as implementation problems rather than copying literally were:

- Content that should be controlled by Shopify needs to remain editable through the Theme Editor or Shopify data.
- Repeated card layouts should be rendered through reusable section/block structures rather than duplicated static markup.
- Navigation and section links need to work as real Shopify links/anchors.
- Animations need to survive section reordering and theme-editor changes.
- Responsive behavior needs to be handled with CSS breakpoints rather than relying on the prototype viewport.
- Motion should respect `prefers-reduced-motion`.
- Product presentation should be compatible with real Shopify product data rather than depending on the prototype's static content.

## Key implementation changes

### Hero

- Built the hero as a Shopify section.
- Added the 1 / 2 / 3 product-offer sequence.
- Added automatic cycling between the product states.
- Added manual controls for the three offer states.
- Added product-area hover pause/resume behavior.
- Added cursor/parallax movement for the product stage.
- Added reduced-motion handling.
- Kept the visual treatment, spacing, colors, typography hierarchy and promotional cards aligned with the prototype.

### Shop / product grid

- Kept the product presentation in Shopify's product-data model rather than hardcoding the product catalog.
- Styled the product cards to match the prototype's visual system.
- Accounted for states such as product images, pricing, compare-at pricing and sold-out/no-image scenarios.

### Combos and Bundles

- Built repeated bundle/combo cards as reusable structures.
- Added responsive horizontal/overflow behavior where required by the design.
- Added hover and CTA interactions without changing the underlying content structure.
- Kept the cards editable through Shopify section/block settings where applicable.

### Reviews

- Built the reviews as a horizontal rail matching the prototype's visual direction.
- Added continuous movement/rail behavior and polished the card transitions.
- Kept the background treatment consistent with the rest of the homepage instead of making the section feel visually disconnected.

### Global visual system

A major refinement pass was made to keep the homepage visually cohesive:

- Shared green/wave background treatment across sections.
- Consistent card borders, radii, shadows and spacing.
- Smooth interaction easing across navigation, buttons, cards and sliders.
- Header navigation hover underline animation.
- Sticky/header-aware smooth anchor scrolling.
- Responsive behavior for smaller screens.
- Reduced-motion support.

### Announcement bar

The original Dawn announcement-bar behavior was adapted into a continuous horizontal marquee so the announcement messages can move across the page in the same visual style as the reference.

## Why I changed some implementation details

I treated the supplied design as the visual specification, but did not copy prototype structure blindly. Where a prototype approach would make a production Shopify theme brittle, I used Shopify sections, blocks, product data, responsive CSS and state-based JavaScript instead.

The goal was to preserve the visual output while making the implementation usable from the Shopify Theme Editor.

## What I would do with more time

- Run a final pixel-comparison pass at 375px, tablet and desktop widths against the source prototype.
- Audit every section in Shopify's Theme Editor by adding, removing and reordering blocks.
- Run a full accessibility pass with keyboard-only navigation and screen-reader checks.
- Run Lighthouse/PageSpeed checks and optimize any remaining LCP, CLS or JavaScript issues.
- Replace any remaining presentation-only placeholders with final Shopify product/media data.
- Test the complete page on real mobile devices and across additional browsers.
- Add automated visual regression screenshots for the major breakpoints.

## Current status

The core homepage implementation is complete and the main requested sections have been built and visually refined. The remaining work I would prioritize is final production QA, accessibility/performance auditing, and another pixel-level comparison pass across all target breakpoints.
