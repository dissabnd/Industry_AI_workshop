# Build the monthly-performance-pack skill (about 10 min)

This skill is a recipe only: no code. It tells the agent what Fonterra's monthly pack must contain and look like. The agent's built-in Word (DOCX) and PowerPoint (Slides) skills make the files.

**Where:** a new Copilot Chat.

## Prompt (send once)

```text
Write a SKILL.md file for a skill called monthly-performance-pack. It is instructions only, no code. It will be used by an agent that analyses plant packaging data and must produce a monthly Word report and a PowerPoint leadership deck.

Start the file with:
---
name: monthly-performance-pack
description: Use when asked for a monthly plant performance report or leadership deck. Produces a Word report and a matching PowerPoint deck.
---

Then write these sections, short and specific:

1. Workflow: in the message where the data file is attached, load it with the code interpreter (pandas) and calculate all numbers from the full file, never from a preview; show them in chat as a set of summary tables, one per report section (headline KPIs, by line, by shift, fault ranking with the clean-run baseline as a separate row, CapEx). Later steps use these tables and do not reload the file. Then write the report text and the slide text in the chat first, and only then build the Word report with the DOCX skill and the deck with the Slides skill from that text. After building each file, reopen it and confirm it is not empty (print the headings or slide titles).

2. Word report, sections in this order:
   Executive summary (5 lines: what happened, the biggest loss, the decision needed)
   Headline KPIs (table)
   Where the money goes (scrap vs lost capacity by line, with a chart)
   Shift performance (Morning, Afternoon, Night, with a chart)
   Top faults and maintenance priorities (ranked by downtime hours, with a chart; clean-run baseline shown separately)
   CapEx assessment (payback, recommendation)
   Actions (owner, by when)
   Data notes (source file, period, definitions, annualisation basis)

3. PowerPoint deck, exactly 6 slides:
   1 Title  2 Headline KPIs  3 Where the money goes  4 Shift performance  5 Top faults and actions  6 Decisions needed
   One message per slide, written as the slide title. No more than 4 bullets per slide. Plain white background.

4. House rules:
   - Lead with the decision, then the evidence.
   - Numbers: LKR mn to 2 decimals, percentages to 1 decimal, hours to 1 decimal, thousands separators.
   - Every number must come from the summary tables. Report and deck must show the same numbers. Action owners are roles, not numbers.
   - Every chart has a title, labelled axes with units, and one sentence saying what it means.
   - If something cannot be calculated from the data, say so in Data notes. Do not estimate.

5. Before handing over, check: all 8 report sections present, exactly 6 slides, numbers match between report and deck.

Give me the SKILL.md as a downloadable file.
```

## Before you move on (1 min)
1. `SKILL.md` starts with the `name` / `description` block.
2. It lists the 8 report sections and the 6 slides.
3. Save it. You will upload it to your agent in Step 2.
