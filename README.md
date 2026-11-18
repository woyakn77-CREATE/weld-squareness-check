# Weldment Squareness Check

A shop-floor tool that tells a welder whether a rectangular frame is square, using only a tape measure.

**Live demo:** https://woyakn77-create.github.io/weld-squareness-check/

## Problem

Checking a welded frame for square usually means a large framing square or an angle gauge, and the result is a judgment call. Cross-corner (diagonal) measuring is faster and more sensitive, but the operator needs to know what diagonal to expect and how much variation the angle tolerance allows. Doing that trigonometry at the bench does not happen.

## What it does

- Takes length, width and the allowed corner angle (for example ±0.5°).
- Returns the nominal diagonal and the min and max diagonal that keep each corner in tolerance, in decimals and as fractions rounded to 1/32" (min rounds up, max rounds down, so the fraction never passes a bad part).
- Shows the largest allowed difference between the two diagonals as a quick check.
- Grades a measured diagonal as in or out of tolerance, with its angle off square, on a visual scale.
- Accepts fractions as typed (`48 1/2`, `48-1/2`), switches between inches and millimeters, and runs in English or Spanish.
- Explains the cross-corner method, including the checks diagonals do not catch (unequal sides, twist).

## How cross-corner measuring works

A rectangle has two equal diagonals. When a frame racks into a parallelogram, one diagonal grows and the other shrinks. For a frame of length L and width W with a corner error δ:

```
d² = L² + W² ± 2·L·W·sin(δ)
```

1. Lay the frame flat. Diagonals do not detect twist.
2. Confirm both lengths match and both widths match. Equal diagonals only prove square when opposite sides are equal.
3. Use the same reference point at all four corners.
4. Measure corner 1 to 3 (diagonal A) and corner 2 to 4 (diagonal B).
5. Enter each one. Both in the green band means square within tolerance.
6. To correct, pull or clamp across the long diagonal.

## Built with

Single HTML file, plain JavaScript and inline SVG. No build step, no data leaves the browser. Built with Claude.

Portfolio version: generic labels and no company branding. The default tolerance is an example only; always use the drawing.
