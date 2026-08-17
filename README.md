# Data Viz for Humans

A skill that teaches AI agents why a chart helps a human understand, instead of just which chart to draw.

AI models default to pattern-matched chart choices: pie for shares, rainbow colors, 3D decorations, truncated axes. These choices fail because they ignore how human vision actually works. This skill replaces the pattern matching with a grounded model of human perception, a task-to-chart mapping, and hard audit checklists.

## What it contains

The skill package lives in `skills/data-viz-for-humans/`:

- SKILL.md: the core mental model, a 6-step workflow, invariant rules, and the anti-patterns AI models fall into.
- references/perception-science.md: why charts work, from the perception literature (pre-attentive processing, encoding accuracy hierarchy, working memory, Gestalt).
- references/task-to-chart.md: question-first mapping across the 9 visualization families, expanded from the FT Visual Vocabulary.
- references/design-and-honesty.md: design and deception rules turned into testable conditions.
- references/checklists.md: binary audits every chart must pass before it ships.
- examples/before-after.md: clanker-default vs fixed chart pairs with line-by-line rationale.
- validation/adversarial-test.md: how an unaided model's designs scored against the rules (the evidence the rules bite).

## Install

### Preferred: npx skills (Claude Code, Codex, and other supported agents)

The repo follows the open skills layout (`skills/<name>/SKILL.md`), so it installs through the skills CLI:

```
npx skills add Riloox/data-viz-for-humans@data-viz-for-humans -g -a claude-code -a codex -a hermes-agent --copy -y
```

- One `-a` flag per agent (comma-separated lists are rejected); `-a '*'` installs to every agent the CLI supports.
- `claude-code` targets `~/.claude/skills`, `codex` targets `~/.agents/skills` (the shared agent home), `hermes-agent` targets the Hermes profile skills dir.
- `-g` installs at user level; `--copy` materializes real files (default is symlinks; use it on Windows or if you move repos around).

### Hermes

Copy the `skills/data-viz-for-humans` directory to your profile skills dir:

```
Windows: %LOCALAPPDATA%\hermes\skills\
Linux/macOS: ~/.local/share/hermes/skills/ or ~/AppData/Local/hermes/skills/
```

### Manual (any agent)

Copy the `skills/data-viz-for-humans` directory to `~/.claude/skills/`, `~/.codex/skills/`, or `~/.agents/skills/`.

## Source

Research and canonical references are cited inside the reference documents. Key sources: Cleveland & McGill (JASA 1984, DOI 10.1080/01621459.1984.10478080), Larkin & Simon (Cognitive Science 1987), Tufte, Bertin, Munzner, Cairo, and the FT Visual Vocabulary (Financial-Times/chart-doctor).