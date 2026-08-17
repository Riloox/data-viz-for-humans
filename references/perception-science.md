# Perception Science: Why Charts Work

Every rule in this skill traces back to one of these principles. Each entry states what the science says, what it forbids or requires in practice, and the source.

## 1. Pre-attentive processing

The human visual system extracts basic features (color, size, orientation, motion, shape, line ending, curvature) in parallel, subconsciously, before conscious attention is engaged. A stimulus that differs from its context on one of these features "pops out" and is selected for attentive processing.

- Requires: encode the answer to the chart's question as a pre-attentive difference. One highlighted element, one color pop, one annotation.
- Forbids: hiding the answer in the middle of a uniform-looking mass of marks, or asking the reader to compare values that differ only in a low-salience feature.
- Source: Pre-attentive processing (Wikipedia, "subconscious accumulation of information from the environment... highest salience selected for further analysis"); Treisman & Gelade feature-integration theory; Wolfe's guided search.

## 2. The encoding accuracy hierarchy (Cleveland & McGill)

Humans judge data encoded on different visual channels with very different accuracy. The experimental ranking:

1. position along a common scale (most accurate)
2. position on non-aligned scales
3. length
4. angle / slope
5. area
6. volume
7. color saturation
8. color hue (least accurate)

Replicated with 26,000+ judgments via Mechanical Turk (Heer & Bostock, CHI 2010): the ordering is robust across populations.

- Requires: choose the highest-ranked channel available for the comparison the question demands.
- Forbids: encoding a magnitude comparison as area (bubble charts) or angle (pies) when position or length is available (bars, dot plots, ordered bars).
- Source: Cleveland & McGill, "Graphical Perception: Theory, Experimentation, and Application to the Development of Graphical Methods", JASA 79(387), 1984, DOI 10.1080/01621459.1984.10478080. Heer & Bostock, CHI 2010.

## 3. Perceptual non-linearity of area and volume (Weber-Fechner)

Perceived magnitude grows sub-linearly for area and volume encodings: a circle with double the area of another is perceived as less than double. The same is true for sound and brightness. Linear channels (length, position) do not suffer this distortion.

- Requires: encode quantitative comparison in linear channels (length, position), never area or volume, when the reader must judge exact or proportional values.
- Forbids: proportional symbol maps or bubble charts for precise magnitude comparison; scaling glyph height and width together instead of height alone.
- Source: Weber-Fechner law; Cleveland & McGill's channel ranking.

## 4. Working memory and external cognition

Working memory holds roughly 4 chunks (Cowan; Miller's 7 +/- 2 framed the question). The brain cannot hold a column of numbers and compare them. Diagrams work because they are external cognition: they reduce search ("where is the biggest bar?" is answered by looking), support pattern recognition, and offload inference to perception.

- Requires: design so the view does the computation. A reader should never have to remember values from one part of the chart to interpret another part.
- Forbids: forcing mental arithmetic or cross-referencing between distant elements; splitting one comparison across two charts when one would do.
- Source: Larkin & Simon, "Why a Diagram Is (Sometimes) Worth Ten Thousand Words", Cognitive Science 11(1), 1987; Cowan, working memory capacity, 2001.

## 5. Change blindness and visual search asymmetry

Humans fail to notice changes that are not visually flagged, and search asymmetric targets easily (a red dot among grey dots) but symmetric ones slowly (a red-green boundary among other red-green items). This is why annotation exists.

- Requires: annotate the key event or value. A line chart of revenue is not a story until the announcement date or the anomalous month is marked. The annotation converts the chart into a message.
- Forbids: assuming the reader will "notice" the important element on their own.
- Source: Pre-attentive processing literature; change blindness (Rensink); storytelling-with-data practice (Knaflic) built on these results.

## 6. Gestalt grouping

Humans automatically group marks by proximity, similarity, enclosure, connection, and continuity. Grouping is perceived before attention; the designer controls which groups the reader sees.

- Requires: arrange marks so the groups the question cares about are the groups Gestalt rules create. Spacing encodes grouping (proximity); color similarity groups categories; enclosure or connection marks an explicit relationship.
- Forbids: fighting the groupings (e.g. equal spacing between unrelated and related bars, colors that imply similarity between dissimilar series).
- Source: Wertheimer; Gestalt principles as applied in information visualization (Ware, "Information Visualization: Perception for Design").

## 7. Color vision limits

Human color vision uses three cone classes; roughly 8% of males and 0.5% of females have some color vision deficiency. Red-green confusion is the most common. Hue is also the channel humans judge magnitudes worst on (see ranking above).

- Requires: colorblind-safe palettes for categorical data (e.g. Okabe-Ito: black, orange, sky blue, bluish green, yellow, blue, vermillion, reddish purple); redundant encoding (pair color with shape, size, or label so no information exists in color alone); perceptually uniform sequential scales for continuous data (no rainbows).
- Forbids: rainbow/spectral scales, encoding information solely as color, red vs green as the only distinguisher.
- Source: Okabe & Ito, "Color Universal Design"; ColorBrewer (Brewer et al.); Cleveland & McGill ranking.

## 8. Insight latency as the effectiveness metric

The value of a visualization is the reduction in time from data exposure to correct understanding and decision. Evaluation research measures insight, not ink.

- Requires: optimize for speed of the insight: the answer must be findable at a glance (5 seconds), not after study.
- Forbids: treating aesthetics, novelty, or data completeness as goals in themselves.
- Source: North, "Toward Measuring Visualization Insight", IEEE CG&A 2006; insight-based evaluation tradition.

## Reading notes

- These principles are about static, printed, screen-read charts. Interactivity (hover, zoom) cannot rescue a chart whose static form is wrong; the static form must carry the message.
- When a stakeholder questions a design rule, cite the principle: "we use bars not pie because position and length are judged more accurately than angle and area, Cleveland & McGill 1984."