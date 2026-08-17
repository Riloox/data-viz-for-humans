# Adversarial Validation: Unaided-Model Designs vs Skill Rules

Method: a fresh subagent (deepseek-v4-flash, no access to this or any skill, no style guides) designed visualizations for the same 5 datasets used in examples/before-after.md, purely from training-data instinct. Full JSON output from 2026-08-17 11:29 UTC. Each choice is scored against this skill's rules. A model's choice can PASS, WARN (legal but against the spirit), or FAIL (violates an invariant rule or a checklist item).

## TIME_SERIES: 24 months of revenue, December seasonality, one spike (month 18)

| Choice | Verdict | Rule |
| --- | --- | --- |
| Line chart, zero baseline, chronological time axis | PASS | family 5, axis integrity |
| Month-18 anomaly flagged with annotation and callout | PASS | change blindness, annotation rule |
| No 3D | PASS | invariant rule 3 |
| Thin vertical bar layer under the line ("so they recede") | FAIL | data-ink: removable with zero information loss; the line already carries the path |
| Three simultaneous accents (orange December points, red anomaly, dashed moving average) | WARN | one-highlight rule: the anomaly is the answer; the other accents split attention |
| Legend block instead of direct labels | WARN | direct labels over legends when space allows |

## MAGNITUDE_RANKING: 12 products, $50K to $12M

| Choice | Verdict | Rule |
| --- | --- | --- |
| Horizontal ordered bars, sorted descending, value labels on bars | PASS | family 3, ranking uses length |
| Sequential color gradient duplicating length | WARN | redundant encoding of the same magnitude; harmless reinforcement here, length alone suffices |
| Cumulative-share line on a secondary 0-100% axis | PASS | Pareto exception, codified in v1.0.1: same data normalized, not an unrelated measure |
| Log-scale variant offered with a stated reason | PASS | log rule: stated reason required; noted, not silently applied |

## PART_TO_WHOLE: 6 business units, 40/25/15/10/7/3%

| Choice | Verdict | Rule |
| --- | --- | --- |
| Donut chart with 6 slices | FAIL | invariant rule 3: pie/donut forbidden past 3 slices; angle/area is a low-accuracy channel for shares |
| Side table added "for exact-share verification" | FAIL | a chart that needs a second artifact to be accurate has failed its job; the chart must carry the message |
| Explicit rejection of a 3D pie | PASS | invariant rule 3 |
| Direct labels on slices with leader lines | PASS | direct labels over legends |

## DISTRIBUTION: n=500 age survey, right-skewed, old-age outlier cluster

| Choice | Verdict | Rule |
| --- | --- | --- |
| Histogram with 5-year equal-width bins + companion boxplot | PASS | family 4, bins stated and equal |
| Median and mean both drawn and annotated as skewed-right | PASS | honesty: mean alone would hide the shape |
| Outlier cluster highlighted and named, n stated in title | PASS | outliers shown, not buried |

## CORRELATION: 2,000 employees, experience vs salary

| Choice | Verdict | Rule |
| --- | --- | --- |
| Alpha-blended scatter + OLS trend line with CI band | PASS | family 2, overplotting rule |
| Outlier cluster isolated, annotated, not removed | PASS | integrity: investigated as a business question |
| Axes cropped to data range with an explicit "not at zero" note | PASS | labeled crop is legal for scatters |

## Score

8 PASS, 4 WARN, 2 FAIL (donut for 6 slices; chartjunk bar layer under a line chart).

## What this proves

The unaided model has absorbed a good deal of correct visualization advice from its training data: it picks lines for time, scatters for correlation, alpha for overplotting, and annotates outliers. It is not a naive clanker on simple cases.

The failures are categorical and inconsistent, which is the case for a written skill: (1) it still reaches for the donut the moment the word "share" appears, the exact anti-pattern this skill forbids, and then papers over the accuracy problem with a supplementary table; (2) it decorates with a redundant layer whose removal loses nothing; (3) it cannot justify its exceptions, because it has no rule system, so the Pareto secondary-axis instinct is unexamined rather than principled.

The value of the skill is therefore twofold: it converts inconsistent instinct into auditable rules, and it codifies the legitimate exceptions (labeled axis crops, same-data Pareto normalization) so rules are not applied as superstition.

## Known limitation

The subagent shares the model family of this authoring session. A human expert review of the skill and its examples remains the gold standard; the checklists in references/checklists.md are written to be run by either.

## Change log

- v1.0.1: dual-axis rule gains its one legitimate exception: a Pareto cumulative-share line on a secondary axis is acceptable because it is the same data normalized to the same total, not an unrelated measure. Applied to SKILL.md invariant rule 3, references/design-and-honesty.md section 3, and references/task-to-chart.md family 6.