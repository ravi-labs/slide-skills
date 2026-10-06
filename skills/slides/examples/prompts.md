# Example prompts

Attach `SKILL.md` (or install the skill), then ask for slides by layout.

## One slide from a screenshot

> Using the slides skill, build a **scorecard** slide titled "…" from the attached screenshot. Take every number from the screenshot. Put `[__]` for anything you can't read, and list those slots.

## Rebuild a deck from screenshots

> Using the slides skill, build an N-slide editable .pptx. I've attached one screenshot per slide. Copy all titles, dates, labels and text exactly as they appear in the screenshots.
>
> - Slide 1: `numbered-cards`
> - Slide 2: `milestone-timeline`. Place milestones by date.
> - Slide 3: `status-learnings`
>
> Footer: "…". Add page numbers. Paste the speaker notes I give you into each slide.

## Code agent

> Using the slides skill, write a deck spec JSON for these slides, run `scripts/build_slides.py`, and give me the .pptx.
