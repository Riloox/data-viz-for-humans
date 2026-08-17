# Data Viz for Humans

A skill that teaches AI agents why a chart helps a human understand, instead of just which chart to draw.

AI models default to pattern-matched chart choices: pie for shares, rainbow colors, 3D decorations, truncated axes. These choices fail because they ignore how human vision actually works. This skill replaces the pattern matching with a grounded model of human perception, a task-to-chart mapping, and hard audit checklists.

## What it contains

- SKILL.md: the core mental model, a 6-step workflow, invariant rules, and the anti-patterns AI models fall into.
- references/perception-science.md: why charts work, from the perception literature (pre-attentive processing, encoding accuracy hierarchy, working memory, Gestalt).
- references/task-to-chart.md: question-first mapping across the 9 visualization families, expanded from the FT Visual Vocabulary.
- references/design-and-honesty.md: design and deception rules turned into testable conditions.
- references/checklists.md: binary audits every chart must pass before it ships.
- examples/before-after.md: clanker-default vs fixed chart pairs with line-by-line rationale.

## Install

### Hermes

Copy the `data-viz-for-humans` directory to your profile skills dir:

```
Windows: %LOCALAPPDATA%\hermes\skills\
Linux/macOS: ~/.local/share/hermes/skills/ or ~/AppData/Local/hermes/skills/
```

### Claude Code

Copy the `data-viz-for-humans` directory to `~/.claude/skills/`. It is auto-discovered.

### Codex CLI

Copy the `data-viz-for-humans` directory to `~/.codex/skills/`. To force-load it in a repo, add to `AGENTS.md`:

```
@skills data-viz-for-humans
```

### Any agent

Copy the `data-viz-for-humans` directory to `~/.agents/skills/` (shared skill home used by several CLIs).

## Source

Research and canonical references are cited inside the reference documents. Key sources: Cleveland & McGill (JASA 1984, DOI 10.1080/01621459.1984.10478080), Larkin & Simon (Cognitive Science 1987), Tufte, Bertin, Munzner, Cairo, and the FT Visual Vocabulary (Financial-Times/chart-doctor).