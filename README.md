# Data Viz for Humans

## Charts that humans can actually read.

AI models choose charts by pattern matching. The word "share" triggers a pie, continuous data gets a rainbow, 3D depth distorts the numbers, and the one insight the chart exists to show gets buried under everything else.

This skill replaces those instincts with the science of how human vision works. Every chart it produces answers one question, encodes it on the perceptual channel humans judge most accurately, and passes an audit that catches a lie.

```
 "share of revenue"                 "share of revenue"
 pie, 6 rainbow slices              single 100% stacked bar
 reader squints at the legend       segments labeled, colorblind-safe
 reader cannot find the 3%          reader reads it in 3 seconds
```

## Install

```bash
npx skills add Riloox/data-viz-for-humans@data-viz-for-humans -g -a claude-code -a codex -a hermes-agent --copy -y
```

Works with every agent the skills CLI supports: Claude Code, Codex, Hermes, OpenCode, and more.

Hermes without the CLI: copy `skills/data-viz-for-humans` to your profile skills dir (`%LOCALAPPDATA%\hermes\skills\` on Windows, `~/.local/share/hermes/skills/` on Linux/macOS).

## What's inside

- `SKILL.md` — the mental model, a 6-step workflow, invariant rules, and the anti-patterns AI models default to.
- `references/perception-science.md` — why charts work: the encoding-accuracy hierarchy (Cleveland & McGill), pre-attentive processing, working memory, Gestalt. Each principle with its source.
- `references/task-to-chart.md` — question-first mapping across the 9 visualization families, expanded from the FT Visual Vocabulary.
- `references/design-and-honesty.md` — Tufte and Cairo turned into testable rules: data-ink, lie factor, axis integrity, color, overplotting.
- `references/checklists.md` — six binary audits every chart must pass: 5-second, squint, colorblind, honesty, grandmother, pre-chart.
- `examples/before-after.md` — clanker-default vs fixed chart pairs with line-by-line rationale.
- `validation/adversarial-test.md` — how an unaided model scored against the rules: 8/14 compliant, and both hard failures were the exact anti-patterns this skill forbids.

## The one rule that matters

```
position > length > angle > area > volume > color
```

Humans judge magnitudes from position and length with near-perfect accuracy, and from angle, area, or color with steadily worse reliability. That is why bars beat pies and why rainbows are never the answer. Cleveland & McGill, JASA 1984; replicated at scale by Heer & Bostock, 2010.

## Credits

Perception science: Cleveland & McGill, Larkin & Simon, Heer & Bostock, Tufte, Bertin, Munzner, Cairo. Task taxonomy: the FT Visual Vocabulary (Financial-Times/chart-doctor).

## License

MIT.