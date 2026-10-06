# Deck spec (JSON)

`scripts/build_slides.py` turns this JSON into an editable .pptx. A full example is in `examples/sample-deck.json`.

```json
{
  "footer": "optional footer text",
  "first_page": 1,
  "slides": [ { "layout": "table-kpi", "title": "…", "...": "…" } ]
}
```

## Fields every slide can use

| Field | Meaning |
|---|---|
| `layout` | One of the eight layouts. The older names `status-table`, `metrics-table` and `proposal-flow` also work. |
| `title` | Header text |
| `pill` | `{"text", "tone"}`. Tone is `good`, `attention`, `neutral` or `proposed`. |
| `source_note` | Added to the footer after a `·` |
| `notes` | Speaker notes |

`tone` also accepts the colour names `navy`, `blue`, `teal`, `green` and `orange`.

## Text options

- Wrap text in `**double asterisks**` to make it bold.
- A table cell can be a string or `{"text", "tone", "bold"}`.
- Cells in a column whose header contains "status" are coloured automatically: done or approved values in green, pending or at-risk values in orange.

## Fields per layout

| Layout | Fields |
|---|---|
| `table-kpi` | `columns[]`, `rows[[…]]`, `widths[]` (column fractions, optional), `kpis[{value, label}]` |
| `scorecard` | `hero{label, value, sub_label, tone}`, `chips[{value, label, tone}]`, `detail`, `image` (file path, optional), `caption`, `panels[{heading, text, tone: blue/green}]` |
| `data-table-insights` | `columns[]`, `rows[{cells[], key, indent}]`, `summary`, `cards[{heading, text, tone}]` |
| `step-flow` | `intro`, `steps[{label, text}]`, `panels[{heading, text, tone}]`, `closing` |
| `numbered-cards` | `headline`, `cards[{number?, heading, text}]`, `note{lead_in, text}` |
| `milestone-timeline` | `start`, `end` (ISO dates), `phases[{label, start, end}]`, `milestones[{date, label, event, kind}]`, `today{date, label}`, `pattern`, `caveat` |
| `lane-timeline` | `start`, `end`, `periods[{label, date}]`, `lanes[{label, bars[], markers[]}]`, `today{date, label}`, `legend{done, wait, planned}` |
| `status-learnings` | `left_heading`, `columns[2]`, `rows[[…]]`, `path{lead_in, text}`, `right_heading`, `learnings[{title, text}]`, `closing` |

### Milestone `kind`

| Kind | Marker |
|---|---|
| `event` (default) | Navy dot |
| `approval` | Green dot |
| `target` | Blue dot |
| `golive` | Green diamond |

### Lane bars and markers

- **Bar:** `{start, end, label, style, tone}`. `style` is `done` (solid), `wait` (hatched) or `planned` (dashed outline).
- **Marker:** `{date, label, kind, note}`. `kind` is `planned` (outlined diamond) or `current` (green diamond). `note` is shown in orange, for example a slip label.

## Missing values

Put `[__]` where a value is unknown. The script lists every `[__]` slot after it saves the file.
