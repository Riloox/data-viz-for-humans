# Task to Chart: Question-First Mapping

Expanded from the Financial Times Visual Vocabulary (Financial-Times/chart-doctor, verified August 2026; PDFs available in 9 languages including Spanish). The vocabulary defines 9 visualization families. Each family below states the human question it answers, the best encoding channel, recommended chart types, and what never to use.

## 1. Deviation

Question: "How does each value differ from a reference, target, or baseline?"

- Channel: position against a reference line (zero line, target, budget).
- Types: diverging bar, diverging stacked bar, spine chart (difference from a baseline), surplus/deficit filled line, bullet chart (value vs target).
- Never: area chart of raw values when the question is about the gap; bars without a visible reference line; a plain line when the deviation band is the message.
- Notes: diverging bars need the reference at zero and both directions on the same scale. Do not encode the baseline twice.

## 2. Correlation

Question: "Do two variables move together, and how strongly?"

- Channel: position (x and y).
- Types: scatterplot (with fitted trend if the trend itself is the question), connected scatterplot (x-y over time), XY heatmap (dense paired data), bubble (only when a third dimension is genuinely the question, and even then prefer a faceted scatter).
- Never: 3D scatter (occlusion destroys the pattern); two line charts on separate axes (the eye compares lines, not scales); a bar chart of one variable to answer a correlation question.
- Notes: with thousands of points, use alpha, hexbin, or density contours so overplotting does not hide the shape. Label outliers rather than leaving them to be found.

## 3. Ranking

Question: "What is the order, and how big are the gaps?"

- Channel: position or length.
- Types: ordered bar, ordered column, dot strip plot, lollipop, slope (before/after ranking, e.g. league tables over two time points), ordered proportional symbol (only when magnitude does not need precise comparison).
- Never: pie ranked by slice size; unordered bars when the question is about order; area charts for ranking.
- Notes: sort by the ranking variable, never by dataset order. If the gaps are tiny, the chart's message is that the ranking exists, not that gaps exist; say so.

## 4. Distribution

Question: "How is this variable spread; where is the mass; are there outliers?"

- Channel: shape, bins, quantiles.
- Types: histogram, boxplot, violin, dot plot, dot strip plot, barcode plot, cumulative curve, population pyramid (two distributions mirrored), plus density for smooth shape.
- Never: a line chart of raw values to show "the data"; a pie; a bar chart with hundreds of bars (use histogram bins); mean-only markers that hide the shape.
- Notes: bin width changes the story. Test 2-3 bin widths and pick the honest one; state the bin width and count in the caption. Boxplots hide multimodal shapes: if the data look bimodal, show a histogram or violin instead of only a boxplot. Always show outliers explicitly.

## 5. Change over time

Question: "How does this variable evolve; where are the changes, cycles, or turning points?"

- Channel: slope (line), or length (columns) when individual magnitudes matter more than the path.
- Types: line, column (few discrete time points), line + column (two series of different kinds), slope (change between two points), area (cumulative or magnitude volume; area for cumulative sums is acceptable, not for comparing magnitudes), fan chart (projections with uncertainty), connected scatterplot (two variables over time), calendar heatmap (daily intensity), timeline variants (Priestley, circle, seismogram) for events over time.
- Never: pie for time; area charts for comparing absolute magnitudes between series (area overlap misleads); dual axes for two series on different scales (see honesty reference); a stacked area when relative share is the question.
- Notes: annotate the turning points and events (change blindness). If the x-axis is time, the x-axis must be to scale; irregularly spaced data on a regular time axis is deception. For seasonal data, show at least two full cycles so the pattern is visible.

## 6. Magnitude

Question: "How much, and compared to how much?"

- Channel: length from a common baseline (position).
- Types: bar, column, paired bar/column (two groups side by side), lollipop, dot plot, proportional stacked bar (part-to-whole with magnitude), isotype pictograms (when counting units matters, e.g. public communication), proportional symbol (only for order-of-magnitude feel, never precise comparison).
- Never: pie for magnitude; bubble for precise comparison (area channel); log axis without a stated reason; bars not starting at zero.
- Notes: bars must start at zero; the baseline is the lie detector. When bars exceed about 20, switch to a dot strip or lollipop so labels fit and the tail stays readable. Radar and parallel coordinates belong here only for special multivariate comparison; most readers cannot judge them, so they fail the grandmother test.

## 7. Part-to-whole

Question: "What share of the total does each part hold?"

- Channel: stacked length (100% stacked bar), or area subdivision (treemap) for many parts.
- Types: stacked column, proportional (100%) stacked bar, treemap (many parts with labeled area), donut/pie (only 2-3 parts, approximate shares, no precision needed), arc chart, gridplot, waterfall (how the total is built from deltas), venn (set overlaps, never proportions).
- Never: pie/donut for more than 3 slices or when exact shares matter; 3D pie; stacked bars without a total label; treemaps when the question is about one part among few (use bars).
- Notes: if one part dominates, everyone else is invisible in a pie; a 100% stacked bar with labeled values fixes it. For flows of proportion, see family 9.

## 8. Spatial

Question: "How does this vary across geography?"

- Channel: position on the map; then color (rates) or size (counts).
- Types: choropleth (rate/ratio, e.g. per capita), proportional symbol (count/magnitude), dot density (raw events), flow map (migration or routing), contour map (continuous field), heat map, equalised cartogram (distorted area = equal population, honest about density), scaled cartogram (area = value).
- Never: choropleths of raw counts (population differences dominate; normalize or use symbols); drawing conclusions from map areas that are population artifacts; rainbow color fills.
- Notes: choropleths compare regions of wildly different size poorly; prefer symbol maps for counts. Color scale must be sequential or diverging with a meaningful midpoint, never rainbow. If regions are tiny, aggregate honestly or switch to a cartogram.

## 9. Flow

Question: "What moves between nodes, and how much?"

- Channel: connection and connection width (the thickness carries the magnitude).
- Types: sankey (river/flow between stages), chord (circular flow matrix), network (nodes and links with width/color by strength).
- Never: arrows whose width mismatches the value; 3D network layouts (occlusion); a pie of totals when the question is about edges.
- Notes: sort nodes to minimize crossings, label the biggest flows, and let the reader trace any path. Thickness is the same as length accuracy: keep widths proportional and labeled.

## Special cases

- Uncertainty: show it (error bars, fan charts, confidence intervals, distribution plots). Hiding uncertainty is deception.
- Comparing many distributions: boxplots or violins per group, ordered by median when meaningful.
- Lots of categories (20+): treemap, dot strip, lollipop, or a sorted tail-truncated bar with a labeled "other" group.
- Zero and negative values: diverging bars or a spine; both directions need the same scale and a visible zero.
- Projections: fan chart for ranges, dashed lines for point forecasts, and always split historical from projected so the reader never mistakes one for the other.
- Large datasets: bin (histogram, hexbin), aggregate (by period, by cohort), or sample with alpha. Showing every point is not always honest; hiding density is.
- Time + magnitude + share all in one question: small multiples, not one chart. One chart, one question.

## Source

FT Visual Vocabulary, Financial-Times/chart-doctor repository, visual-vocabulary directory (README.md and PDFs), verified 2026-08-17.