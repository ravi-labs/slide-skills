---
name: slides
description: Build clean, editable 16:9 slides in one consistent style from named layouts (table-kpi, scorecard, data-table-insights, step-flow, numbered-cards, milestone-timeline, lane-timeline, status-learnings). Use for status updates, eval scorecards, metrics tables, proposals, timelines and summaries, especially when a screenshot or table of results is attached. The request supplies all titles, labels, text and data.
---

# Slides

This skill defines **style and structure only**. Every title, heading, label, column name, status value and number comes from the user's request or attached inputs. Never add your own wording.

Output editable PowerPoint slides (16:9, 13.333 × 7.5 in) built from native shapes, text boxes and tables. Never output a slide as a single image.

The request names a layout, for example:

> Using this skill, build a **scorecard** slide titled "…" from the attached screenshot.

## Pick a layout

| Layout | Use for |
|---|---|
| `table-kpi` | Status table with KPI tiles |
| `scorecard` | Headline result, small counts, results image |
| `data-table-insights` | Data table with 2–4 takeaway cards |
| `step-flow` | Process or proposal steps with supporting panels |
| `numbered-cards` | One headline message with 3–4 numbered points |
| `milestone-timeline` | Dated milestones on one line, with phases and a today marker |
| `lane-timeline` | Workstreams as bars against a plan (Gantt style) |
| `status-learnings` | Status table and next steps, plus numbered learnings |

Older names still work: `status-table` → `table-kpi`, `metrics-table` → `data-table-insights`, `proposal-flow` → `step-flow`.

## Rules

1. Fill every `{slot}` from the request or the attachments (screenshots, tables, pasted text).
2. Numbers come only from the attached inputs. Never invent, round up or estimate a value.
   - A derived value, such as a share or a ratio, is allowed only when it is computed from numbers in the attachments. Say how it was computed in your reply.
3. If a slot has no value, write `[__]` and list the empty slots in your reply.
4. Counts are flexible. Where a range is given (for example 3–5 cards), use as many as the request provides.
5. Leave out any optional element the request doesn't mention.
6. Keep to one idea per slide. If the content doesn't fit, split it into two slides. Don't shrink text below the type scale.

## Theme

Colors are set by a **theme**. Layouts refer only to the role tokens below, never to fixed colors, so any theme works with every layout.

**Default theme**

| Token | Default | Role |
|---|---|---|
| `primary` | #1F3A6E | Header bar, headings, neutral accent |
| `on-primary` | #FFFFFF | Text on `primary`, `accent`, `good` and `attention` fills |
| `accent` | #3B5FC4 | Accent line, highlights, "proposed" |
| `accent-2` | #2A8A9A | Second accent |
| `good` | #2E7D4F | Good, on track, done |
| `attention` | #C0582E | Attention, pending, at risk |
| `page` | #F6F7F9 | Slide background |
| `card` | #FFFFFF | Card fill |
| `border` | #D9DEE6 | Card border, gridlines |
| `row-alt` | #F0F3F7 | Alternate table row |
| `text` | #1C2433 | Body text |
| `muted` | #4D5666 | Secondary text |
| `footer` | #6A7282 | Footer, captions, axis lines |
| `panel` | #E8EEFB | Light panel |
| `panel-good` | #E5F3F0 | Light panel for positive content |

Semantic colors: `good` means positive, `attention` means a warning, and `primary` or `accent` are neutral. The accent cycle is `primary`, `accent-2`, `accent`, `good`.

**Using your own theme**

The user can supply a theme in the request or as an attached file, in any readable form, for example:

```
theme:
  primary: "#0B3D2E"
  accent: "#E07A1F"
  font: "Inter"
```

- Override only the tokens the user gives. Keep the default for every other token.
- Keep the meaning of each role: `good` must still read as positive and `attention` as a warning.
- Make sure text stays readable. If a supplied color gives poor contrast (for example light text on a light fill), say so in your reply and suggest a fix rather than silently changing it.
- If the user names a brand or uploads a logo or template, take colors from it only when the user asks you to.

**Font:** Open Sans by default (fallback Arial). A theme can set `font`.

**Type scale**

| Element | Size | Weight |
|---|---|---|
| Title | 30 pt | Extra bold |
| Hero number | 60 pt | Extra bold |
| KPI number | 26 pt | Extra bold |
| Intro or headline | 16–17 pt | Regular |
| Heading | 14–15 pt | Bold |
| Body or table | 12–13 pt | Regular |
| Footer | 12 pt | Regular |

**Frame (every slide)**

- **Header bar:** `primary`, full width, top 0, height 1.17 in. Put `{title}` in `on-primary`, left 0.67 in, vertically centred.
- **Accent line:** `accent`, full width, directly under the header, height 0.06 in.
- **Status pill (optional):** a rounded rectangle at the top right of the header with `on-primary` bold `{status}` text.
  - `good`: on track or done.
  - `attention`: pending or at risk.
  - `accent`: proposed.
- **Content area:** left and right margins 0.67 in, top 1.5 in, bottom 6.4 in.
- **Footer:** `{footer text}` at bottom left and `{page number}` at bottom right, both 12 pt `footer`, 0.44 in from the bottom. Omit the footer text if none is given, but always show the page number.
- **Card:** `card` fill, 1 pt `border`, small corner radius, a 4–5 pt accent border on one side, inner padding about 0.2 in.
- **Panel:** `panel` or `panel-good` fill, no border, the same padding.
- **Speaker notes:** if the request gives notes, put them in each slide's notes.

---

## Layout: `table-kpi`

A table across the top and a row of KPI tiles below it. Use it for workstream status updates.

- **Optional `{status pill}`:** the overall status.
- **Table, full content width:** `{columns}` × `{rows}`.
  - Each header cell has its own fill from the accent cycle, with `on-primary` bold text.
  - Rows alternate `card` and `row-alt`.
  - Keep label and status columns narrow (about 10–17%) and split the remaining width between the text columns.
  - Any status column is bold with semantic colors.
  - Keep cells to three lines or fewer.
- **KPI row:** 2–4 equal tiles.
  - Each tile is a card with a thick top border from the accent cycle.
  - Each holds a `{value}` (KPI number) and a `{label}` (body, `muted`).

## Layout: `scorecard`

A headline result on the left and a results image on the right, with optional panels below. Use it for evaluation or test runs.

- **Left column (about 1/3 width):**
  - A hero card with a thick semantic left border, holding `{label}`, `{hero value}` (hero number, semantic color) and `{sub-label}`, for example the threshold.
  - 2–4 small cards in a row, each with a `{value}` (KPI number, semantic color) and a `{label}`.
  - Optional `{detail line}` in body, `muted`, for example the date, counts processed and exclusions.
- **Right column (about 2/3 width):** an image placeholder (`card` fill, thin border) for `{image}`, with an optional `{caption}` underneath (body, `footer` color).
- **Optional bottom row:** 1–2 panels side by side, each with a `{heading}` and `{text}`.

## Layout: `data-table-insights`

A data table on the left and insight cards on the right. Use it for aggregate metrics such as cost, tokens or latency.

- **Left (about 60% width):** a table with a `primary` header row and `on-primary` bold text: `{columns}` × `{rows}`.
  - Rows alternate. Right-align the numbers.
  - Indent sub-rows where the request says so.
  - Show durations as minutes and seconds (for example "3m 13s").
  - Highlight the key values in bold `accent`.
  - Optional `{summary line}` under the table, in body, `muted`, for example totals and counts.
- **Right (about 40% width):** 2–4 stacked cards.
  - Each card has a thick left border from the accent cycle, or a semantic color (`attention` for a watch item).
  - Each holds a `{heading}` (bold, `primary`) and `{text}` of one or two sentences.
  - Common card patterns are a baseline comparison, the biggest driver, and the long tail (max compared with median). Use them only when the request asks for them.

## Layout: `step-flow`

An intro, a sequence of steps, and supporting panels. Use it for proposals and operating models.

- Optional `{status pill}`. Use `accent` for a proposal.
- Optional `{intro}`: one sentence at 16 pt, full width.
- **Step row:** 3–5 cards with small right-arrow shapes in `footer` color between them.
  - Each card has a thick top border from the accent cycle.
  - Each holds a `{step label}` (bold, in the border color, for example "1 · {STEP}") and `{step text}`.
- **Optional panel row:** 1–3 panels, each with a `{heading}` and `{text}`, for example who owns what and what stays locked.
- Optional `{closing line}`: bold, `primary`, 13 pt.

## Layout: `numbered-cards`

A one-line message, a row of numbered cards, and an optional note band. Use it for summaries and drivers.

- Optional `{status pill}`.
- `{headline}`: one or two sentences at 17 pt, full width. Bold the key phrase only.
- **Card row:** 3–4 equal cards.
  - Each card has a thick `primary` top border.
  - Each holds a small `{number}` (bold, `accent`), a `{heading}` (15 pt bold, `primary`) and `{text}` (one or two sentences).
- Optional **note band:** a full-width `panel` with a bold `{lead-in}` followed by `{text}`.
- Optional `{source note}` appended to the footer text.

## Layout: `milestone-timeline`

A single horizontal timeline with dated milestones and labels that alternate above and below the line.

- **Phase bands (optional):** 1–3 `panel` bars along the top, each with a bold `primary` `{phase label}`. Each spans the dates of its phase.
- **Axis:** a thin line in `footer` color across the full content width, about 60% of the way down the timeline area.
- **Milestones:** 5–10 markers placed proportionally by date.
  - Small circles: `primary` for normal events, `good` for an approval or completion, `accent` for a target date.
  - Use a `good` diamond for the final go-live.
  - Each label is `{date}` in bold over `{event}`, in body text. Alternate labels above and below the line so they never overlap.
  - Color the label text to match its marker when the marker is `good` or `accent`.
- Optional **today marker:** a dashed `attention` vertical line with "`{today label}`" in bold `attention`.
- Optional **pattern bar:** a card with a thick `primary` left border and one bold `primary` `{pattern line}`.
- Optional `{caveat}`: one line of body text in `footer` color.

## Layout: `lane-timeline`

A Gantt-style chart: one row per workstream with bars across shared date columns.

- **Date header:** `{period labels}` (weeks or months) across the top in `muted`, with thin vertical gridlines.
- **Lanes:** 3–5 rows. Each has a `{lane label}` in bold `primary` on the left (about 15% of the width).
- **Bars:**
  - Solid fill from the accent cycle for completed work.
  - Hatched or lighter fill for a dependency or wait.
  - A dashed outline for planned or future work.
  - Put the bar's `{label}` inside the bar, or just after it if the bar is short.
- **Markers:** diamonds for go-live dates. Show the planned date as an outlined `muted` diamond and the current date as a solid `good` one, with an optional `{slip label}` between them in `attention`.
- Optional dashed `attention` today line and a 2–3 item legend under the chart.

## Layout: `status-learnings`

A status table and next-step path on the left, with numbered learnings on the right.

- **Left (about 40% width):**
  - A `{heading}` (15 pt bold, `primary`).
  - A two-column table with a `primary` header row and `on-primary` bold text. Rows alternate. Color the status cells semantically.
  - An optional `panel-good` with a thick `good` left border holding a bold `{lead-in}` and a `{path}` line.
- **Right (about 60% width):**
  - A `{heading}`.
  - 3–5 stacked `card` cards. Each holds `{n} · {title}` (bold, `accent`) above one line of `{text}`.
- Optional `{closing line}`: bold, `primary`, full width.

---

---

## Output

- Produce a downloadable, editable .pptx that follows this spec, using native shapes, text boxes and tables.
- If you are working in another slide tool, recreate the same layout, colors and type scale there.

Before finishing, check that:

- every value traces back to the request or the attachments;
- every derived value shows how it was computed;
- no text overflows its box;
- the frame, footer and page number are identical on every slide.
