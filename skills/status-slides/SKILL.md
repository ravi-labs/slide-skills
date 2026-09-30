---
name: status-slides
description: Build clean, editable 16:9 status-update slides in one consistent style. Use when asked to create a status table, eval scorecard, run metrics table, or proposal flow slide, especially when a screenshot of results is attached.
---

# Status Slides

Build editable PowerPoint slides (16:9, 13.333 × 7.5 in) from native shapes, text boxes and tables. Never output a slide as a single image.

There are four slide types. The request names one, for example:

> Build a **scorecard** slide titled "Evaluation: Latest Run" from the attached screenshot.

## Ground rules

1. **Numbers come only from what the user attaches** (screenshots, tables, pasted text). Never invent, round up or "estimate" a value.
2. If a value isn't visible, write `[__]` and list the missing values in your reply.
3. Text in `"quotes"` below is example wording. Replace it with the user's content and keep the length similar.
4. One idea per slide. If the content doesn't fit, split it into two slides. Don't shrink the text below the sizes given here.

## Shared style (every slide)

**Colors**

| Role | Hex |
|---|---|
| Navy (header, primary) | #1F3A6E |
| Blue (accent) | #3B5FC4 |
| Teal (accent) | #2A8A9A |
| Green (good / on track) | #2E7D4F |
| Orange (attention / pending) | #C0582E |
| Page background | #F6F7F9 |
| Card background | #FFFFFF |
| Card border | #D9DEE6 |
| Alternate row | #F0F3F7 |
| Body text | #1C2433 |
| Muted text | #4D5666 |
| Footer text | #6A7282 |
| Light blue panel | #E8EEFB |
| Light green panel | #E5F3F0 |

**Font:** Open Sans (fallback Arial).

**Type scale**

| Use | Size | Weight |
|---|---|---|
| Slide title | 30 pt | Extra bold |
| Hero number | 60 pt | Extra bold |
| KPI number | 26 pt | Extra bold |
| Card heading | 14–15 pt | Bold |
| Body / table | 12–13 pt | Regular |
| Footer | 12 pt | Regular |

**Frame (every slide)**

- Header bar: navy rectangle, full width, top 0, height 1.17 in.
- Accent line: blue rectangle, full width, directly under the header, height 0.06 in.
- Title: white, left 0.67 in, vertically centred in the header.
- Optional status pill: rounded rectangle at the top right of the header, white bold text. Green = "On track", orange = "At risk / Pending", blue = "Proposed".
- Content area: left and right margins 0.67 in, top 1.5 in, bottom 6.4 in.
- Footer: "FOR INTERNAL USE ONLY." at bottom left and the page number at bottom right, both 12 pt footer grey, 0.44 in from the bottom.
- Cards: white fill, 1 pt border (#D9DEE6), small corner radius, a colored accent border of 4–5 pt on one side, inner padding about 0.2 in.

---

## Type 1: `status-table`

A workstream status update.

- Status pill: overall status.
- Table, full content width, four columns sized roughly 17% / 10% / 36.5% / 36.5%:
  - Header cells, each with its own fill and white bold text: **Workstream** (navy), **Status** (blue), **This period** (teal), **Next two weeks** (green).
  - One row per workstream. Rows alternate white and light grey.
  - The Status cell is bold and colored: green for On track or Ongoing, orange for Pending or At risk.
  - Keep each cell to three lines or fewer.
- Under the table, a row of 4 equal **KPI tiles**. Each tile is a white card with a thick top border (navy, green, teal and blue, in that order), a big KPI number and a short grey label such as "cost per email (was $[__] est.)".

## Type 2: `scorecard`

Headline results of an evaluation or test run, taken from a results screenshot.

- **Left column (about 1/3 width):**
  - A hero card with a thick green left border. It reads "Overall [metric]", then the headline score as the hero number in green, then "Required: [threshold]".
  - Under it, three small cards in a row: passed (green number), needs review (orange number), could not evaluate (navy number).
  - One muted line with the run date, items processed out of the total, and the failed and blocked counts.
- **Right column (about 2/3 width):** a white placeholder box with a thin border where the user pastes the screenshot. Under it, the caption "[Tool name] dashboard, run [run ID]".
- **Bottom row:** two panels side by side.
  - Light blue panel, heading "How each item is scored": the scoring methods shown in the screenshot, in plain words.
  - Light green panel, heading "Suite growing: [old] → [new]": where new test cases come from and who confirms them.

## Type 3: `metrics-table`

Aggregate run statistics (cost, tokens, latency and so on) with takeaways.

- **Left (about 60% width):** a table with a navy header row and white bold text, for example Per item | Average | Median | Min | Max.
  - Rows alternate white and light grey. Right-align the numbers.
  - Indent sub-metrics, for example Prompt and Completion tokens under Total tokens.
  - Show durations as minutes and seconds, for example "3m 13s".
  - Make the Average value bold blue for the key rows.
  - Under the table, one muted line of totals and the run count (total ÷ average).
- **Right (about 40% width):** three stacked cards, each with a thick left border, a bold navy heading and one or two sentences.
  - Blue, "Baseline": today's average compared with any earlier estimate.
  - Teal, "[X]% of [metric] is [part]": the biggest driver, with X computed from the table.
  - Orange, "Watch the long tail": max compared with median.

## Type 4: `proposal-flow`

A proposed process or operating model.

- Status pill: blue "Proposed".
- One intro sentence at 16 pt, full width.
- A row of 3–5 step cards with small grey right-arrow shapes between them.
  - Each card has a thick top border, cycling through navy, teal, blue and green.
  - Each has a bold label such as "1 · ADJUST" in the border color, and one short line about who does what.
- Below, two panels side by side:
  - Light green, "[Group A] owns": what they control.
  - Light blue, "[Group B] keeps locked": what stays protected.
- A closing line, bold navy, 13 pt, for example "Every change is versioned, scored and reversible."

---

## Building it

- **ChatGPT:** produce a downloadable .pptx that follows this spec.
- **VS Code / code agent:** write a Python script using `python-pptx`:
  - Set `prs.slide_width = Inches(13.333)` and `prs.slide_height = Inches(7.5)`, and use a blank layout.
  - Draw every element with `add_shape`, `add_textbox` and `add_table`, using the positions and colors above.
  - Keep one helper per slide type (`build_status_table`, `build_scorecard`, `build_metrics_table`, `build_proposal_flow`) that takes a plain dict of content, so the same script is reused each week.

Before finishing, check that:

- every number traces back to the attached input;
- no text overflows its box;
- the footer and page number are on every slide.
