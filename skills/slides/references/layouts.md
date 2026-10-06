# Layouts

Each layout lists its slots. Fill every `{slot}` from the request or attachments.

## Layout: `table-kpi`

A table across the top and a row of KPI tiles below it. Use it for workstream status updates.

- **Optional `{status pill}`:** the overall status.
- **Table, full content width:** `{columns}` × `{rows}`.
  - Each header cell has its own fill from the accent cycle, with white bold text.
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

- **Left (about 60% width):** a table with a `navy` header row and white bold text: `{columns}` × `{rows}`.
  - Rows alternate. Right-align the numbers.
  - Indent sub-rows where the request says so.
  - Show durations as minutes and seconds (for example "3m 13s").
  - Highlight the key values in bold `blue`.
  - Optional `{summary line}` under the table, in body, `muted`, for example totals and counts.
- **Right (about 40% width):** 2–4 stacked cards.
  - Each card has a thick left border from the accent cycle, or a semantic color (`orange` for a watch item).
  - Each holds a `{heading}` (bold, `navy`) and `{text}` of one or two sentences.
  - Common card patterns are a baseline comparison, the biggest driver, and the long tail (max compared with median). Use them only when the request asks for them.

## Layout: `step-flow`

An intro, a sequence of steps, and supporting panels. Use it for proposals and operating models.

- Optional `{status pill}`. Use `blue` for a proposal.
- Optional `{intro}`: one sentence at 16 pt, full width.
- **Step row:** 3–5 cards with small grey right-arrow shapes between them.
  - Each card has a thick top border from the accent cycle.
  - Each holds a `{step label}` (bold, in the border color, for example "1 · {STEP}") and `{step text}`.
- **Optional panel row:** 1–3 panels, each with a `{heading}` and `{text}`, for example who owns what and what stays locked.
- Optional `{closing line}`: bold, `navy`, 13 pt.

## Layout: `numbered-cards`

A one-line message, a row of numbered cards, and an optional note band. Use it for summaries and drivers.

- Optional `{status pill}`.
- `{headline}`: one or two sentences at 17 pt, full width. Bold the key phrase only.
- **Card row:** 3–4 equal cards.
  - Each card has a thick `navy` top border.
  - Each holds a small `{number}` (bold, `blue`), a `{heading}` (15 pt bold, `navy`) and `{text}` (one or two sentences).
- Optional **note band:** a full-width `panel-blue` with a bold `{lead-in}` followed by `{text}`.
- Optional `{source note}` appended to the footer text.

## Layout: `milestone-timeline`

A single horizontal timeline with dated milestones and labels that alternate above and below the line.

- **Phase bands (optional):** 1–3 `panel-blue` bars along the top, each with a bold `navy` `{phase label}`. Each spans the dates of its phase.
- **Axis:** a thin grey line across the full content width, about 60% of the way down the timeline area.
- **Milestones:** 5–10 markers placed proportionally by date.
  - Small circles: `navy` for normal events, `green` for an approval or completion, `blue` for a target date.
  - Use a `green` diamond for the final go-live.
  - Each label is `{date}` in bold over `{event}`, in body text. Alternate labels above and below the line so they never overlap.
  - Color the label text to match its marker when the marker is `green` or `blue`.
- Optional **today marker:** a dashed `orange` vertical line with "`{today label}`" in bold `orange`.
- Optional **pattern bar:** a card with a thick `navy` left border and one bold `navy` `{pattern line}`.
- Optional `{caveat}`: one line of body text in `footer` grey.

## Layout: `lane-timeline`

A Gantt-style chart: one row per workstream with bars across shared date columns.

- **Date header:** `{period labels}` (weeks or months) across the top in `muted`, with thin vertical gridlines.
- **Lanes:** 3–5 rows. Each has a `{lane label}` in bold `navy` on the left (about 15% of the width).
- **Bars:**
  - Solid fill from the accent cycle for completed work.
  - Hatched or lighter fill for a dependency or wait.
  - A dashed outline for planned or future work.
  - Put the bar's `{label}` inside the bar, or just after it if the bar is short.
- **Markers:** diamonds for go-live dates. Show the planned date as an outlined `muted` diamond and the current date as a solid `green` one, with an optional `{slip label}` between them in `orange`.
- Optional dashed `orange` today line and a 2–3 item legend under the chart.

## Layout: `status-learnings`

A status table and next-step path on the left, with numbered learnings on the right.

- **Left (about 40% width):**
  - A `{heading}` (15 pt bold, `navy`).
  - A two-column table with a `navy` header row and white bold text. Rows alternate. Color the status cells semantically.
  - An optional `panel-green` with a thick `green` left border holding a bold `{lead-in}` and a `{path}` line.
- **Right (about 60% width):**
  - A `{heading}`.
  - 3–5 stacked white cards. Each holds `{n} · {title}` (bold, `blue`) above one line of `{text}`.
- Optional `{closing line}`: bold, `navy`, full width.
