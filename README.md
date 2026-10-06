# slide-skills

Reusable skills for building clean, editable slides. Each skill follows the open `SKILL.md` format, so it works in Claude, in code agents (Claude Code, Copilot, Codex, Cursor) and as an attachment in chat tools.

## Skills

| Skill | What it does | Layouts |
|---|---|---|
| [`slides`](skills/slides/SKILL.md) | 16:9 status, eval, metrics, proposal and timeline slides in one style | `table-kpi`, `scorecard`, `data-table-insights`, `step-flow`, `numbered-cards`, `milestone-timeline`, `lane-timeline`, `status-learnings` |

## Layout

```
slide-skills/
├── .claude-plugin/          # Claude Code plugin + marketplace manifest
└── skills/
    └── slides/
        ├── SKILL.md         # entry point: rules, layout picker, build steps
        ├── references/      # layouts, style, deck JSON spec
        ├── scripts/         # build_slides.py (python-pptx)
        ├── examples/        # sample deck JSON and example prompts
        └── requirements.txt
```

## Use it

**Claude Code**

```
/plugin marketplace add ravi-labs/slide-skills
/plugin install slide-skills@slide-skills
```

**Claude app:** zip the `skills/slides` folder and upload it under Settings → Capabilities → Skills.

**Chat tools (ChatGPT, Copilot):** attach `SKILL.md` and the files under `references/`, then ask for a slide by layout.

**Script only:**

```bash
pip install -r skills/slides/requirements.txt
python skills/slides/scripts/build_slides.py skills/slides/examples/sample-deck.json -o sample.pptx
```

All values come from what you provide. Missing values show as `[__]`, and the script lists them.
