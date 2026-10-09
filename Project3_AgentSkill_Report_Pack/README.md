# Project 4: Monthly Performance Pack (Agent + skill)

**Time:** 40 min (Step 1: 10 min, Step 2: 30 min)  
**Copilot mode:** Agent with a skill.  
**Choose this or Project 3.** Project 3 produces an interactive HTML dashboard; Project 4 produces a Word report and a PowerPoint deck.  
**Layer you learn:** A recipe-only skill that teaches the agent your company's standard, and reuses the Word and PowerPoint skills the agent already has.

## Context
Every month someone turns shift data into a written report for the plant leadership team and a short deck for the review meeting. It takes days, the structure changes with whoever writes it, and the numbers in the report and the deck do not always agree.

## The problem
We have 90 days of shift records (810 shifts, three lines). We want an agent that calculates the KPIs correctly and produces both documents in a standard format, with the same numbers in each, every month.

Copilot already knows *how* to make Word and PowerPoint files: it has built-in DOCX and Slides skills. What it does not know is *what our pack should contain*: which sections, which slides, how to format numbers, what to lead with. A **skill** captures that once. Unlike Project 3, this skill has no code; it is a recipe that tells the agent how to use the tools it already has.

## What you will learn
- How to write a skill as instructions only (`SKILL.md`).
- How a custom skill can build on built-in skills: yours sets the standard, theirs makes the file.
- How the same agent and data give a different deliverable when you change the skill.

## Files
- `Monthly_Plant_Packaging_Efficiency_Data.csv`: 810 shift records, 90 days, Lines 1–3 (same data as Project 3)
- `Agent_Instructions.md`: paste into the agent's Instructions (same as Project 3, except the Output section)
- `Skill_Creation_Prompt.md`: the prompt that creates your `SKILL.md`
- `Prompt.md`: the main prompt, a check and the debrief

## Steps
**Step 1: build the skill (about 10 min).** Follow `Skill_Creation_Prompt.md`. You end up with `SKILL.md`.

**Step 2: build and run the agent (about 30 min).**
1. In Copilot, choose **Create an agent**. Name: `Plant Monthly Pack Agent`.
2. Paste `Agent_Instructions.md` into **Instructions**.
3. Do **not** upload the CSV under Knowledge. You attach it in the chat in Step 6 (see the note below).
4. Under **Configure → Skills → Add**, upload your `SKILL.md`.
5. Turn on **Code interpreter**.
6. Start a chat with the agent, **attach `Monthly_Plant_Packaging_Efficiency_Data.csv` to the message that asks for calculations**, and run the prompts in `Prompt.md`, then open both files.

> **Why attach the CSV in chat?** A file under Knowledge is indexed for search: the agent only sees snippets, so totals come out wrong or truncated. A file attached in the chat goes to the code interpreter as a complete file, so every number can be calculated from all rows. Use Knowledge for documents you search (SOPs, manuals); attach data you calculate from. Two more things: tell the agent to *use the code interpreter* on the file (left to itself it may answer from the preview), and attach the file to the same message that asks for the calculation, because the code interpreter only gets it for that message.

## What to look for
- Does the report have all 8 sections in order, and the deck exactly 6 slides?
- Do the numbers match between the report, the deck and the summary tables?
- Is OEE weighted by operating time? Are scrap and lost-capacity costs shown separately?
- Which file decided the content (`SKILL.md`) and which made the file (the built-in DOCX and Slides skills)?
