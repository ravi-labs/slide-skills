# Prompt template: 3-slide timeline summary

Use this template with the `slides` skill to explain where time went on a project, show the timeline, and say what happens next. Replace every `<…>` and delete any optional line you don't need.

In VS Code Copilot (Agent mode), keep `SKILL.md` in your workspace and paste everything below the line.

---

```
#file:SKILL.md

Using the attached SKILL.md as the rules, build a 3-slide editable 16:9 PowerPoint deck.

Build it by writing a small python-pptx script in out/, running it, and saving out/<deck-file-name>.pptx. Use native shapes, text boxes and tables only (no slide images). Theme: <default | list overrides, e.g. primary: "#xxxxxx">. Use exactly the text below and don't add or reword anything. Put [__] for anything missing and list it at the end.

Deck footer (all slides): "<footer text>"
Page numbers: 1–3.

---

SLIDE 1
Layout: numbered-cards
Title: "<Project>: Where the Time Went"
Status pill: "<e.g. Target date Mon DD>" (tone: <good | attention | proposed>)
Headline: "**<About N weeks>** since <starting event> on <date>. <One sentence on how the time built up.>"
Cards:
  1. Heading: "<cause 1>"   Text: "<one or two sentences>"
  2. Heading: "<cause 2>"   Text: "<one or two sentences>"
  3. Heading: "<cause 3>"   Text: "<one or two sentences>"
  4. Heading: "<cause 4, optional>"   Text: "<one or two sentences>"
Note band (optional): lead-in "<e.g. Also running in parallel:>" text "<work that ran alongside>"
Source note (optional, this slide only): "<e.g. Based on tracker history>"
Speaker notes: "<what you'll say>"

---

SLIDE 2
Layout: milestone-timeline
Title: "Timeline: <start> to <end milestone>"
Timeline range: <YYYY-MM-DD> to <YYYY-MM-DD>
Phase bands (optional, 1–3):
  - "<phase 1 label>": <YYYY-MM-DD> to <YYYY-MM-DD>
  - "<phase 2 label>": <YYYY-MM-DD> to <YYYY-MM-DD>
Milestones (date | label | event | kind = event, approval, target or golive):
  - <YYYY-MM-DD> | "<Mon DD>" | "<what happened>" | event
  - <YYYY-MM-DD> | "<Mon DD–DD>" | "<what happened>" | event
  - <YYYY-MM-DD> | "<Mon DD>" | "<approval or sign-off>" | approval
  - <YYYY-MM-DD> | "<~Mon DD>" | "<next target>" | target
  - <YYYY-MM-DD> | "<Mon DD>" | "<go-live or launch>" | golive
  (5–10 milestones. For a date range, use a mid-range date to place the marker and keep the range in the label.)
Today marker (optional): <YYYY-MM-DD>, label "Today"
Pattern bar (optional): "Pattern: <step> → <step> → <step>"
Caveat (optional): "<e.g. Approximately to scale.>"
Speaker notes: "<what you'll say>"

---

SLIDE 3
Layout: status-learnings
Title: "Where We Are & What Changes Next Time"
Left heading: "Status today"
Table columns: "Item" | "Status"
Rows (tone in brackets: good, attention, accent, or none):
  - "<item>" | "<status>" [<tone>]
  - "<item>" | "<status>" [<tone>]
  - "<item>" | "<status>" [<tone>]
Path panel (optional): lead-in "Path:" text "<step> → <step> → **<final milestone>**."
Right heading: "<e.g. Process learnings>"
Learnings (3–5):
  1. "<title>" — "<one line>"
  2. "<title>" — "<one line>"
  3. "<title>" — "<one line>"
Closing line (optional): "<e.g. Goal: fewer late surprises, not blame for the past.>"
Speaker notes: "<what you'll say>"

---

When done, tell me the file path and list any [__] slots or text that overflowed its box.
```

## Tips

- Keep each card and learning to one or two short sentences, or the text will overflow.
- In chat tools that can't run code (for example ChatGPT without code execution), drop the python-pptx line and ask for a downloadable .pptx instead.
- Keep filled-in copies with real project data in your own private workspace, not in this repo.
