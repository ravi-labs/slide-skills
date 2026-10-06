---
name: slides
description: Build clean, editable 16:9 PowerPoint slides and decks in one consistent style from named layouts (table-kpi, scorecard, data-table-insights, step-flow, numbered-cards, milestone-timeline, lane-timeline, status-learnings). Use for status updates, eval scorecards, metrics tables, proposals, timelines and delay summaries, especially when a screenshot or table of results is attached.
---

# Slides

This skill defines **style and structure only**. Every title, label, status and number comes from the user's request or attachments. Never add your own wording.

Output editable PowerPoint slides (16:9, 13.333 × 7.5 in) built from native shapes, text boxes and tables. Never output a slide as a single image.

## Rules

1. Fill every slot from the request or the attachments (screenshots, tables, pasted text).
2. Numbers come only from the attachments. Never invent, round up or estimate a value.
   - A derived value, such as a share or a ratio, is allowed only when it is computed from attached numbers. Say how it was computed.
3. If a value is missing, write `[__]` and list the missing slots in your reply.
4. Leave out any optional element the request doesn't mention.
5. Keep to one idea per slide. If the content doesn't fit, split it into two slides. Don't shrink text below the type scale.

## Pick a layout

| Layout | Use for |
|---|---|
| `table-kpi` | Workstream status table with KPI tiles |
| `scorecard` | Headline result, small counts, results screenshot |
| `data-table-insights` | Metrics table with 2–4 takeaway cards |
| `step-flow` | Proposal or process steps, with ownership panels |
| `numbered-cards` | One headline message with 3–4 numbered reasons |
| `milestone-timeline` | Dated milestones on one line, with phases and a today marker |
| `lane-timeline` | Workstreams as bars against a plan (Gantt style) |
| `status-learnings` | Status table and next steps, plus numbered learnings |

The older names `status-table`, `metrics-table` and `proposal-flow` map to `table-kpi`, `data-table-insights` and `step-flow`.

Read these as needed:

- `references/layouts.md`: the slots and placement for each layout.
- `references/style.md`: colours, type scale and the frame used on every slide.
- `references/deck-spec.md`: the JSON format for the build script.

## Build

**If you can run Python (preferred):**

1. Write a deck spec JSON following `references/deck-spec.md`. Start from `examples/sample-deck.json`.
2. Run `pip install -r requirements.txt`, then `python scripts/build_slides.py deck.json -o deck.pptx`.
3. Report any `[__]` slots the script lists.

**If you can't run Python** (for example in a chat tool without code execution), build the slides directly from `references/layouts.md` and `references/style.md`.

Before finishing, check that:

- every value traces back to the request or attachments;
- no text overflows its box;
- the frame, footer and page number match on every slide.
