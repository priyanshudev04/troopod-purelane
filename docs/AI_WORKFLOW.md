# Purelane Shopify Build — AI Workflow Notes

## How I used AI

I used AI as a development partner during the implementation, primarily for:

- Translating visual differences between the prototype screenshots and the Shopify implementation into concrete CSS/Liquid changes.
- Iterating on section structure and Shopify Liquid.
- Debugging CSS behavior and responsive layout issues.
- Refining animations, transitions and hover states.
- Comparing the rendered result against the supplied visual reference and identifying mismatches.
- Producing focused implementation changes while keeping the existing codebase intact where possible.

I did not treat AI output as automatically production-ready. I used the browser/Theme Editor result as the source of truth and iterated based on the rendered output.

## What I delegated

I delegated the repetitive implementation work around:

- CSS styling and responsive adjustments.
- Liquid markup scaffolding for sections.
- Animation/transition implementations.
- Small navigation and scrolling fixes.
- Repeated card styling patterns.
- Announcement-bar marquee behavior.
- Refactoring small pieces of markup when the rendered result exposed a problem.

For visual work, I supplied screenshots of the current implementation and the target and used the differences to drive the next iteration.

## Where AI failed / needed correction

The main failure mode was that a technically valid change could still be visually wrong.

Examples from this build included:

- A CSS underline animation initially expanding from the center instead of left-to-right.
- Some section backgrounds initially looked like separate blocks rather than one continuous homepage background.
- Navigation behavior needed to be checked against the actual page structure instead of assuming a generic Shopify collection URL.
- A marquee implementation duplicated a single announcement when only one announcement block existed, which exposed the need to configure the actual announcement content in the Theme Editor.
- Some animation changes could accidentally override existing component behavior, so the rendered Shopify page had to be checked after each pass.

These are exactly the cases where I would not blindly accept an agent's output. I validate the implementation in the browser and correct the generated code against the visual and functional requirements.

## What I would systematise for 20 similar projects

If I had to repeat this workflow at scale, I would standardise:

1. **Design-to-section mapping**
   - Identify every requested section.
   - Identify which values should come from Shopify.
   - Identify reusable card patterns.
   - Identify interactions and responsive states before coding.

2. **Section contract**
   - Define the Liquid inputs/settings/blocks for every section.
   - Define empty, loading, sold-out and no-image states.
   - Define desktop/mobile behavior.

3. **AI implementation loop**
   - Give the agent one section at a time.
   - Require it to preserve existing class/API contracts.
   - Ask for a minimal diff when fixing an existing section.
   - Render immediately after every significant change.

4. **Automated QA checklist**
   - Theme Editor add/remove/reorder test.
   - 375px / tablet / desktop visual check.
   - Keyboard/focus check.
   - Reduced-motion check.
   - Product-data edge cases.
   - Lighthouse/performance check.

5. **Visual regression**
   - Capture reference screenshots at fixed breakpoints.
   - Capture the implementation at the same breakpoints.
   - Compare them before calling a section complete.

The main lesson from this build is that AI is very good at producing implementation volume, but the quality of the final result depends on having a precise spec and a tight render → compare → correct QA loop.
