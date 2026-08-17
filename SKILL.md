---
name: data-viz-for-humans
description: Use when creating any chart or choosing between visualization types. Grounds chart choices in human perception science.
version: 1.0.0
author: Riloox
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [visualization, charts, perception, design, communication, data]
---

# Data Viz for Humans

Use this skill when you will render any chart, choose between chart types, or review a visualization. It grounds every decision in how human vision and cognition actually work, so the chart communicates instead of decorates.

## The core mental model

A chart is a perceptual prosthesis. It converts a data question into a visual pattern the human eye can detect pre-attentively, in well under a second, before conscious thought. The chart offloads working memory onto the page, turning "compare these 12 numbers" into "see the tallest bar".

The job of a chart is not to display data. The job is to make one insight effortless to see. Everything in the chart exists to serve that insight; anything that competes with it is noise.

Human vision is a parallel pattern engine, ordered by perceptual accuracy (Cleveland & McGill 1984):

position (common scale) > length > angle/slope > area > volume > color saturation > color hue

This ordering is the single most important fact in this skill. When you encode data on a high-accuracy channel, humans judge it correctly and instantly. When you encode it on a low-accuracy channel (angle, area, color hue), humans misread it. Bar charts work because they use length from a common baseline. Pie charts fail because they use angle and area.

## The 6-step workflow

Always run these steps in order before rendering.

### Step 1: Question

Name the exact question a human needs answered, as a full sentence.

- Bad: "show the sales data"
- Good: "which product grew the most last quarter?"
- Good: "how does salary scale with years of experience?"

If the question does not name a comparison, you are not ready to chart. A table may be the honest answer.

### Step 2: Channel

Map the comparison type to the highest-accuracy perceptual channel:

| Comparison type | Channel | Preferred chart |
| --- | --- | --- |
| Magnitude comparison | length from common baseline | bar / column |
| Ranking | position or length | ordered bar, lollipop, dot strip |
| Trend over time | slope | line |
| Distribution | shape, bins, quantiles | histogram, boxplot, violin |
| Part-to-whole | stacked length | stacked bar, 100% bar, treemap |
| Correlation | position | scatter + trend |
| Deviation from baseline | position vs reference | diverging bar, bullet, spine |
| Geospatial | position on map, then size/color | choropleth, symbol map, dot density |
| Flow between nodes | connection + width | sankey, chord, network |

Full mapping with edge cases: references/task-to-chart.md.

### Step 3: Chart type

Implement the channel with the simplest chart that does it. Fewer marks beat fancier marks. If a plain bar or line answers the question, nothing else is needed. Choose 3D, bubbles, or radar only when they are the best available channel, which is almost never.

### Step 4: Design for perception

- Magnitude bars start at zero. Cropped line/scatter axes are allowed only when labeled, and never to exaggerate.
- One highlight per chart: the element that carries the answer gets the pre-attentive pop (stronger color, annotation, arrow). Everything else stays muted.
- Direct labels instead of legends when space allows. Position the label at the end of a line or above a bar.
- Colorblind-safe palette, no rainbow for continuous data, no color-only encodings.
- Rules and tests: references/design-and-honesty.md.

### Step 5: Honesty check

Run the lie detector in references/design-and-honesty.md: axis integrity, bins, aggregates, truncation, dual axes, 3D, color encoding of continuous data, cherry-picked windows. State axis, bin, and aggregation decisions in the caption anyway.

### Step 6: Verify as a human

Run the six audits in references/checklists.md. The chart is not finished until it passes: 5-second test, squint test, colorblind test, honesty test, grandmother test, one-message test. If it fails the 5-second test, the insight is not visible, and the chart has failed.

## Invariant rules

1. The accuracy hierarchy is absolute: position > length > angle > area > volume > color. Never encode a magnitude comparison as angle or area when position or length is available.
2. Bars start at zero on magnitude axes. Never truncate a magnitude axis to exaggerate a difference.
3. Never: 3D charts; pie/donut with more than 3 slices or whenever magnitudes matter; rainbow color scales for continuous data; dual axes comparing unrelated series; log axes without a stated reason and labeled ticks.
4. One chart answers one question. More questions mean small multiples or separate charts.
5. Every stated insight must be traceable to marks actually present in the chart (DIRECT claim). Anything inferred beyond the marks (causes, forecasts, domain knowledge) must be labeled as inference, so the reader can tell chart fact from model speculation.
6. Know the reader: data literacy, color vision, context, screen vs print, attention budget. A chart is a communication act, not data storage.

## Anti-patterns: what AI models default to, and why each is wrong

- Pie chart whenever the word "share" appears. Angle and area are low-accuracy channels; use a 100% stacked bar or treemap.
- Rainbow colormaps for continuous data. Hue is the least accurate channel and hostile to color-blind readers. Use sequential or perceptually uniform scales.
- 3D perspective. It distorts perceived magnitudes and adds zero information.
- Truncated y-axis to make a small difference look dramatic. This is deception, and it fails the lie-factor test.
- Visual overload: five colors, four fonts, gridlines everywhere. A chart must be quiet except for the message.
- Legends when direct labels fit. The legend forces a second lookup that direct labels eliminate.
- Overplotting without a remedy. Use alpha, jitter, binning, or sampling so density is visible.
- Dual axes. The human eye compares the lines, not the scales, and the comparison is wrong whenever the scales differ.
- One default template for every question. Chart type is a decision, not a habit.
- Claims the chart does not show. Every insight you state about a chart must be visible in it, or labeled as your inference.

## When to read the references

- references/perception-science.md: when you need the why, or when someone asks why a pie chart is wrong. Cite the science.
- references/task-to-chart.md: when the question is unusual, or the obvious chart is not in the quick reference above.
- references/design-and-honesty.md: when choosing colors, axes, or annotations, or when auditing an existing chart for deception.
- references/checklists.md: always, before declaring a chart done. Run the audits.

## Verification

Before a chart is finished, every item in references/checklists.md must pass. A chart that fails the 5-second test is not finished, regardless of how complete its data is.