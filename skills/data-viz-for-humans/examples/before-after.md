# Before and After: What the Clanker Defaults Look Like vs What Humans Need

Each example: the dataset (concrete numbers, renderable as-is), the unaided-model default ("before"), the rule each default choice violates, and the fixed design with the perception rationale line by line. The "before" designs are the documented defaults of AI models operating without this skill; see validation/adversarial-test.md for the live comparison.

## 1. Time series with seasonality and one spike

Dataset: monthly revenue in thousands of USD, 24 months.

```
190 175 185 200 210 225 210 195 205 220 235 410
205 185 195 215 225 780 215 200 210 230 245 430
```

Question: "Are the December peaks a real pattern, and what happened in month 18?"

**Before (clanker default):** a 3D stacked column chart of monthly revenue, rainbow palette, legend, gridlines on both axes, no annotation anywhere. The spike and the seasonality are both visible but equally styled, and the 3D perspective distorts the bar heights.

Fails: invariant rule 3 (3D, rainbow), design-and-honesty section 5 (rainbow), section 7 (no highlight, no annotation), checklists B (5-second test: is the message the seasonality or the spike? unclear) and D (colorblind).

**After:** a plain line chart. Single muted blue-grey line, x-axis to scale (24 months, labeled years), y-axis from zero in thousands. Exactly one highlight: month 18 is marked with a vermillion dot and a direct label "one-off contract". The December peaks need no annotation; the pattern itself is the message, and the eye reads it as a recurring shape.

Caption: "Monthly revenue, USD thousands, Feb 2024-Jan 2026, zero baseline, x-axis to scale. The December peaks are seasonal; the month-18 spike is a one-off contract, not a trend."

Rationale, line by line:
- Line, not bars: the question is about the path and the turning points, so slope is the channel (task-to-chart family 5).
- One muted color: everything except the answer is quiet (design section 7).
- The single annotation: change blindness means the reader will not find the spike on their own; marking it converts the chart into a message (perception principle 5).
- The caption states units, baseline, and the interpretation boundary between seasonal and one-off (design section 9).

## 2. Magnitude ranking with a long tail

Dataset: annual revenue by product, in thousands of USD.

```
A 12000  B 5400  C 3200  D 2100  E 1350  F 880
G 610    H 420   I 300   J 210   K 140   L 80
```

Question: "Which products matter, and how big is the gap between the leader and the long tail?"

**Before (clanker default):** a pie chart with 12 slices in a rainbow palette. The tail products are unreadable slivers, the exact gaps are impossible to judge, and the chart cannot be labelled without clutter.

Fails: invariant rule 3 (pie over 3 slices), perception principle 2 (angle/area are low-accuracy channels for magnitude), design section 5 (rainbow).

**After:** a horizontal ordered bar chart, sorted descending. Bars in muted grey; the top product in orange with a direct value label; every other bar carries its value label at the end. X-axis from zero.

Caption: "Annual revenue by product, USD thousands, FY2025, bars to scale from zero. Product A is 2.2x product B and roughly 150x the tail."

Rationale, line by line:
- Ranking and gap questions use length from a common baseline, the top channel (perception principle 2; task-to-chart family 3).
- Sorted descending: ranking questions require the order to be visual, not read off labels (task-to-chart family 3).
- One highlight: the answer (A dominates) pops; everything else is context.
- Direct labels: no legend lookup (design section 7); the labels also make the tail legible.

## 3. Part-to-whole with six units

Dataset: quarterly revenue share by business unit.

```
U1 40%  U2 25%  U3 15%  U4 10%  U5 7%  U6 3%
```

Question: "What is the revenue composition, and which units are marginal?"

**Before (clanker default):** a 3D donut with six rainbow slices and a legend. The 3D tilt distorts slice angles, the 7% and 3% units are nearly invisible, and the reader must cross-reference colors to the legend to identify anything.

Fails: invariant rule 3 (3D, donut over 3 slices), perception principle 2 (angle encoding), design sections 5 and 7 (rainbow, legend instead of labels).

**After:** a single 100% stacked horizontal bar, segments in Okabe-Ito-safe muted colors, every segment labeled directly with its percentage. The 3% segment is labeled too; it is small, but it is named.

Caption: "Revenue share by business unit, Q3 2026. U1+U2 are 65% of revenue; U5 and U6 together are 10%."

Rationale, line by line:
- Part-to-whole uses stacked length, not angle: a 100% bar keeps one linear scale for all shares (perception principle 2; task-to-chart family 7).
- Labels directly on segments: no legend, no color-dependence, so the chart works in grey-scale (design section 5, accessibility section 8).
- Sorted by share: the composition reads as a structure, not a scramble (Gestalt, perception principle 6).

## 4. Distribution with skew and an outlier cluster

Dataset: age of 500 survey respondents.

```
18-30: 210   31-40: 140   41-50: 75   51-60: 40
61-70: 22    71-80: 8     81+: 5
```

Question: "What does the age profile look like, and is 'average' a fair summary?"

**Before (clanker default):** a pie chart of the age bands in rainbow colors, or a bar chart of the bands with default auto-scaled bins and no labels. Both hide the skew. A model then reports "the average age is 38" as if it summarized the shape.

Fails: pie-for-distribution (perception principle 2; task-to-chart family 4), rainbow (design section 5), aggregate dishonesty (design section 4: mean hides shape).

**After:** a histogram of the 7 bands on the natural age axis, single muted color, count labels on the bars. Two annotated lines on the axis: the mean (dashed, labeled) and the median (solid, labeled), with a caption note that the mean sits above the median because of the right skew. The 71+ bars get a small bracket: "5+8 respondents, 2.6% of sample, oldest cohort".

Caption: "Age distribution of 500 respondents, one-year bands as surveyed, counts labeled. Mean 38 vs median 34: the mean is pulled up by the right skew. The 71+ cohorts are 2.6% of the sample."

Rationale, line by line:
- Distribution questions use shape: bins and quantiles, not mean markers (task-to-chart family 4).
- Mean and median both shown and labeled: the honest answer to "is average fair?" is visible in one glance (design section 4).
- Bands and counts in the caption: binning decisions are stated, not hidden (design section 9).
- Outliers marked, not buried: the smallest cohort is still a visible fact (task-to-chart family 4 notes).

## 5. Correlation with outliers

Dataset: 2,000 employees, years of experience (0-35) vs salary (USD 30,000-250,000). Positive correlation, ~10 legacy-pay outliers with high experience and low salary.

Question: "How does salary scale with experience, and are the outliers a pattern or noise?"

**Before (clanker default):** a 3D scatterplot with points colored by a rainbow salary scale. Occlusion hides density, the 3D rotation makes the trend hard to judge, and the outliers blend into the cloud.

Fails: invariant rule 3 (3D, rainbow), design section 6 (occlusion masquerading as density), perception principle 3 (color hue for magnitude).

**After:** a flat 2D scatterplot, points in grey at 30% alpha (density stays visible), fitted trend line in orange, axes labeled "Years of experience" and "Annual salary (USD thousands)". One annotation: a dashed ellipse around the outlier region labeled "legacy pay bands (n=13)".

Caption: "2,000 employees, FY2025 payroll. r = 0.62. The trend line is a linear fit; the 13 outliers below it are legacy pay bands, not a second pattern."

Rationale, line by line:
- Correlation uses two position axes, the most accurate channel (perception principle 2; task-to-chart family 2).
- Alpha instead of opacity: 2,000 points must show density, not lie about it (design section 6).
- The trend line is the answer to "how does salary scale"; the annotation names the outliers so they are read as identified facts, not noise (perception principle 5).
- Caption states n, r, and the fit so the claim is auditable (design section 9).

## 6. Full workflow walkthrough

Dataset: delivery performance by regional warehouse.

```
Warehouse  Distance served (km)  Avg delivery (days)
W1         40                    1.8
W2         90                    2.5
W3         60                    2.0
W4         120                  6.9
W5         150                  3.2
```

Question from the business: "Did we get faster, or is W4 just farther away?" The data is one quarter of averages.

Step 1, Question: "Does delivery time track distance, and does any warehouse deviate from that relationship?" The comparison is W4's delivery time against the time-distance relationship defined by the other warehouses.

Step 2, Channel: correlation (time vs distance) uses position, the top channel.

Step 3, Chart type: a scatterplot of distance (x) vs delivery days (y), with a fitted line through the four healthy warehouses, and W4 plotted in the same space.

Step 4, Design: grey points for the healthy four, orange point for W4 with a direct label, fitted line in muted blue, axes zeroed, "Distance served (km)" and "Avg delivery (days)" labels, no grid.

Step 5, Honesty: axes untruncated, no dual axes, the fit is stated as "fit through W1-W3, W5", the caption notes these are quarterly averages and n=1 quarter.

Step 6, Verify: 5-second test: the orange point visibly floats far above the line, and the label says W4. Squint test: the outlier is the only thing that survives blur. Colorblind test: W4 is larger and labeled, not color-only. Honesty: the caption reveals the fit definition. Grandmother test: "W4 is slower than distance explains, by a lot." 

Caption: "Delivery time vs distance served, Q3 quarterly averages. Fit line through W1-W3 and W5. W4 averages 6.9 days against a fitted 3.1 at its distance: about 3.8 days slower than the relationship predicts."

Done. One insight, one highlight, every claim traceable to a mark.