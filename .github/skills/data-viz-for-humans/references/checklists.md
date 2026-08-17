# Checklists: The Six Audits

Run every audit before a chart ships. Each item is binary: pass or fail. Any fail means the chart is not finished.

## A. Pre-chart checklist

Run before rendering.

- [ ] The question is written as one sentence naming the comparison (who compared to whom, over what).
- [ ] The comparison type maps to a top-3 accuracy channel (position, length, slope), not area/angle/color.
- [ ] The chart type is the simplest one that implements the channel.
- [ ] The reader is named: their literacy, context, screen, attention budget. The chart is designed for that reader.
- [ ] One message per chart. If a second question exists, a second chart is planned (or small multiples).
- [ ] Every claim to be made about this data can be pointed to in the chart once rendered.

## B. The 5-second test

- [ ] A person who knows the domain but not this analysis can name the message within 5 seconds of first sight.
- [ ] The highlight dominates: exactly one element draws the eye, and it is the answer.
- [ ] The axis, units, and baseline are readable without a second pass.

## C. The squint test

- [ ] Squinting the eyes (blurring the image), the chart still shows its structure: the grouping, the ordering, the standout.
- [ ] No element appears as noise at arm's length.

## D. The colorblind test

- [ ] The chart conveys the same information in grey-scale (no information exists in color alone).
- [ ] Red and green are never the only distinguishers.
- [ ] Continuous data does not use a rainbow scale.

## E. The honesty test

- [ ] Bars start at zero (or the crop is labeled and justified).
- [ ] No dual axes, no 3D, no log axis without reason and label.
- [ ] Bins and aggregates are named in the caption and were reviewed at 2-3 settings.
- [ ] The time window is stated and defensible.
- [ ] Uncertainty is shown where it matters.
- [ ] Every stated insight is traceable to a mark in the chart (DIRECT), or explicitly labeled as inference.

## F. The grandmother test

- [ ] A person with no data experience, given 10 seconds, understands what the chart is about and what it claims.
- [ ] Technical devices (log axes, boxplots, diverging scales) are either avoided or explained within the chart itself.
- [ ] The caption is written: what is measured, units, window, scale, takeaway.

## Result

All boxes ticked: the chart communicates. Any box unticked: fix the chart and re-run the audits. Do not ship a chart that fails the 5-second test, no matter how correct the data is.