# Design and Honesty: Rules as Tests

Every rule below is a test with a pass condition. If a condition fails, the chart is not finished. Decorative taste has no place in this reference; these rules are consequences of the perception science.

## 1. Data-ink ratio (Tufte)

Remove every element that is not data or a necessary carrier of data (gridlines, borders, backgrounds, shadows, gradients, logos, decoration). If the chart's message survives the removal, the element was wasted ink.

- Pass: the chart has no element that can be deleted without losing information or legibility.
- Fail: drop shadows, 3D, glossy fills, decorative backgrounds, unnecessary gridlines, unlabeled axes, chart title saying what the axis labels already say.

## 2. Lie factor (Tufte)

Lie factor = (size of effect shown in the graphic) / (size of effect in the data). A truthful chart shows effects in proportion. 

- Pass: lie factor between 0.95 and 1.05 for the effect the chart claims to show.
- Fail: a 10% data difference rendered as a 2x visual difference. Common causes: truncated axis, 3D perspective, starting bars above zero, non-zero-based bubbles.

## 3. Axis integrity

- Bars and columns: baseline at zero. Always.
- Lines and scatter: cropping is allowed only when the visible band is the message (e.g. stock price around 95-105) and the crop is labeled, and the crop must never exaggerate a difference the chart claims to show. When in doubt, show zero.
- Log scale: only for orders of magnitude, power-law, or multiplicative series. The axis must be labeled "log scale" and ticks must be at powers of ten.
- Time axis: must be to scale. Irregularly spaced data drawn at regular intervals is deception.
- Dual y-axes: forbidden for comparing two series. If two series must appear together, normalize both to indices (change relative to a base) or use small multiples. The eye compares lines, and separate scales make that comparison wrong. The one exception: a Pareto cumulative-share line on a secondary 0-100% axis is the same data normalized to its own total, not a second measure, so the shape of the line is a legitimately comparable statement.

- Pass: every axis stated in the caption (scale, units, baseline, binning).
- Fail: any of the above violated.

## 4. Binning and aggregation

- Histograms: bin width changes the story. Test 2-3 widths; pick the one that shows the real shape without inventing spikes. State bins in the caption.
- Aggregates: mean hides shape; median hides outliers; totals hide distributions. Pick the aggregate that answers the question, and show the shape when the question is about shape.
- Cherry-picking: the time window must be stated and must not be chosen to flatter a claim. If the window excludes a relevant event, that is deception (Cairo).

- Pass: bins and aggregates named in the caption; the chosen window is defensible to a skeptic.
- Fail: auto-bins with no review, "average" presented for a skewed distribution, windows that conveniently exclude inconvenient facts.

## 5. Color rules

- Categorical data: colorblind-safe palette (Okabe-Ito 8: black, orange, sky blue, bluish green, yellow, blue, vermillion, reddish purple). Never red vs green as the only distinguisher.
- Continuous data: sequential scale (single hue, increasing lightness) or diverging scale with a meaningful midpoint. Perceptually uniform if possible (e.g. viridis family). Never rainbow/spectral.
- Redundant encoding: no information may exist in color alone. Pair color with shape, size, position, or direct label.
- Max roughly 6-8 distinct categorical colors; beyond that, group or use another channel.

- Pass: the chart works in grey-scale (redundant encoding), and a red-green colorblind simulation removes no information.
- Fail: rainbow colors, color-only encodings, more than 8 categorical colors, light pastels on light backgrounds.

## 6. Overplotting

- Thousands of points at the same spot hide density and invent the illusion of emptiness.
- Remedies: alpha transparency, jitter for discrete axes, binning (hexbin, 2D histogram), or sampling with a stated rule. Density contours for smooth fields.

- Pass: no region of the chart hides the number of points it contains.
- Fail: a scatter of 5,000 points where the eye sees 50.

## 7. Highlight and annotation

- One pre-attentive highlight per chart: the element carrying the answer. Everything else muted.
- Annotation for the events that matter: dates, thresholds, outliers. The chart becomes a message when the key event is marked.
- Direct labels over legends when space allows: label the line end, the bar top, the dot.

- Pass: a reader who sees the chart for 2 seconds names the message; the chart carries labels, not only a legend.
- Fail: everything equally styled; the answer buried; a legend the reader must cross-reference to understand anything.

## 8. Accessibility

- Contrast: text and marks must be legible at typical viewing distance, not just at 100% zoom.
- No information conveyed by color, hover, or interactivity alone: the static export must carry the full message.
- Fonts: two at most, plain weights for data, bold only for the message.

- Pass: the chart printed in black and white still answers its question.
- Fail: "the pattern is visible when you hover" as a design justification.

## 9. Caption discipline

Every chart ships with a caption that states: what is measured, in what units, over what window, with what scale and binning, and what the takeaway is. If a caption cannot be written, the chart is not ready.

- Pass: a skeptic can audit every claim from the caption alone.
- Fail: no caption, or a caption that merely repeats the title.

## Lie detector quick list (Cairo, "How Charts Lie")

1. Truncated or stretched axes?
2. Cherry-picked time window?
3. Dubious aggregate (mean for skewed, total without scale)?
4. Ratio trick (per-capita switched to raw, or vice versa)?
5. Overplotting hiding density?
6. Dual axes comparing unrelated measures?
7. 3D or perspective distortion?
8. Color encoding magnitude on a rainbow?
9. Missing uncertainty?
10. Would the intended message survive an audit by someone who wants it to be false?

If any answer is "yes", fix it before showing anyone.