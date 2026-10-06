# Style

Shared by every layout. `scripts/build_slides.py` uses the same values.

**Colors**

| Token | Hex | Role |
|---|---|---|
| `navy` | #1F3A6E | Header, primary |
| `blue` | #3B5FC4 | Accent, neutral or proposed |
| `teal` | #2A8A9A | Accent |
| `green` | #2E7D4F | Good, on track, done |
| `orange` | #C0582E | Attention, pending, at risk |
| `page` | #F6F7F9 | Slide background |
| `card` | #FFFFFF | Card fill |
| `border` | #D9DEE6 | Card border |
| `row-alt` | #F0F3F7 | Alternate table row |
| `text` | #1C2433 | Body text |
| `muted` | #4D5666 | Secondary text |
| `footer` | #6A7282 | Footer, captions |
| `panel-blue` | #E8EEFB | Light panel |
| `panel-green` | #E5F3F0 | Light panel |

Semantic colors: `green` means good, `orange` means attention, and `navy` or `blue` are neutral. The accent cycle is `navy`, `teal`, `blue`, `green`.

**Font:** Open Sans (fallback Arial).

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

- **Header bar:** `navy`, full width, top 0, height 1.17 in. Put `{title}` in white, left 0.67 in, vertically centred.
- **Accent line:** `blue`, full width, directly under the header, height 0.06 in.
- **Status pill (optional):** a rounded rectangle at the top right of the header with white bold `{status}` text.
  - `green`: on track or done.
  - `orange`: pending or at risk.
  - `blue`: proposed.
- **Content area:** left and right margins 0.67 in, top 1.5 in, bottom 6.4 in.
- **Footer:** `{footer text}` at bottom left and `{page number}` at bottom right, both 12 pt `footer`, 0.44 in from the bottom. Omit the footer text if none is given, but always show the page number.
- **Card:** `card` fill, 1 pt `border`, small corner radius, a 4–5 pt accent border on one side, inner padding about 0.2 in.
- **Panel:** `panel-blue` or `panel-green` fill, no border, the same padding.
- **Speaker notes:** if the request gives notes, put them in each slide's notes.
