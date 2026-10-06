# slide-skills

Reusable slide skills in the open `SKILL.md` format. Attach or install one in Claude, Copilot, ChatGPT or any agent, then ask for a slide by layout.

| Skill | Layouts |
|---|---|
| [`slides`](skills/slides/SKILL.md) | `table-kpi`, `scorecard`, `data-table-insights`, `step-flow`, `numbered-cards`, `milestone-timeline`, `lane-timeline`, `status-learnings` |

## Usage

> Using the attached SKILL.md, build a **scorecard** slide titled "…" from the attached screenshot.

All values come from what you provide. Missing values show as `[__]`.

## Themes

The skill ships with a basic default theme. To use your own colors, add a theme to your request and override only the tokens you want:

```
theme:
  primary: "#0B3D2E"
  accent: "#E07A1F"
  font: "Inter"
```

See the token list in [`SKILL.md`](skills/slides/SKILL.md#theme).
