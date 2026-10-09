# Project 3: Executive Dashboard (Agent + skill)

**Time:** 40 min (Step 1: 15 min, Step 2: 25 min)  
**Copilot mode:** Agent with a skill.  
**Layer you learn:** A reusable skill that you build yourself. The instructions say *what* to analyse; the skill handles *how the output looks*.

## Context
Every month, someone turns shift data into a performance pack for leadership. The same data must answer different questions for different people:
- the **Plant Director** wants money and decisions (where are we losing, should we approve this CapEx?),
- the **Shift Supervisor** wants shift comparisons and what to hand over,
- the **Maintenance Planner** wants the worst faults and what to fix first.

Preparing this takes an analyst days, and the format changes with whoever builds it.

## The problem
We have 90 days of shift records (810 shifts, three lines). We want an agent that calculates the KPIs correctly (weighted OEE, scrap vs lost capacity), writes for three audiences, and delivers a dashboard that looks the same, professional quality every month.

Instructions can fix the analysis, but not the look. Ask an agent for "an HTML dashboard" twice and you get two different pages. A **skill** solves this: a packaged recipe (`SKILL.md`) plus a tool (`build_report.py`) that any agent can use to produce the house style, and that refuses to save a page that is too thin.

## What you will learn
- How to create a skill from an example of good output.
- How instructions and a skill divide the work: analysis vs presentation.
- How one skill can be reused by many agents, so every report in the plant looks the same.

## Files
- `Monthly_Plant_Packaging_Efficiency_Data.csv`: 810 shift records, 90 days, Lines 1–3
- `Agent_Instructions.md`: paste into the agent's Instructions
- `Prompt.md`: the dashboard prompt, a follow-up and the debrief
- The skill: you create `industrial-report-builder.zip` in Step 1 (see `_Shared_Skill_Report_Builder`)

## Steps
**Step 1: build the skill (about 15 min).** Follow `_Shared_Skill_Report_Builder/Skill_Creation_Prompt.md`. You end up with `industrial-report-builder.zip`.

**Step 2: build and run the agent (about 25 min).**
1. In Copilot, choose **Create an agent**. Name: `Plant Executive Dashboard Agent`.
2. Paste `Agent_Instructions.md` into **Instructions**.
3. Do **not** upload the CSV under Knowledge. You attach it in the chat in Step 6 (see the note below).
4. Add the skill: upload the `industrial-report-builder.zip` you made in Step 1 (required; the agent will not build the dashboard without it).
5. Turn on **Code interpreter**.
6. Start a chat with the agent, **attach `Monthly_Plant_Packaging_Efficiency_Data.csv` to the message that asks for calculations**, and run the prompts in `Prompt.md`, then open `plant_executive_dashboard.html` in a browser.

> **Why attach the CSV in chat?** A file under Knowledge is indexed for search: the agent only sees snippets, so totals come out wrong or truncated. A file attached in the chat goes to the code interpreter as a complete file, so every number can be calculated from all rows. Use Knowledge for documents you search (SOPs, manuals); attach data you calculate from. Two more things: tell the agent to *use the code interpreter* on the file (left to itself it may answer from the preview), and attach the file to the same message that asks for the calculation, because the code interpreter only gets it for that message.

## What to look for
- Did it use the skill? The chat should show the `save()` output with tab, chart and KPI counts.
- Is OEE weighted by operating time? Are scrap and lost-capacity costs shown separately?
- Does each tab speak to its reader?
- Open `SKILL.md` inside the zip and compare it with `Agent_Instructions.md`: which file controls the analysis, and which controls the look?
