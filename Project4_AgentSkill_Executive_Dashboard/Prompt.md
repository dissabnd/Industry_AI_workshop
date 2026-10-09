# Project 3 — Executive Dashboard (Agent + skill)

First build the skill with `_Shared_Skill_Report_Builder/Skill_Creation_Prompt.md`.

Then set up the agent: paste `Agent_Instructions.md` into Instructions, upload your `industrial-report-builder.zip` as the skill, turn on code interpreter. Do not add the CSV as knowledge.

**Attach `Monthly_Plant_Packaging_Efficiency_Data.csv` to the same message as the main prompt** (paperclip icon). Copilot only gives the file to the code interpreter in the message you attach it to.

## Main prompt (with the file attached)

```text
Use the code interpreter: load the attached file with pandas and print df.shape (expect 810 rows, 23 columns). Then, using the industrial-report-builder skill, build plant_executive_dashboard.html with 5 KPI cards and three tabs, each with at least one chart:
- Plant Director: scrap vs lost-capacity cost by line. Assess the LKR 25 mn CapEx request to overhaul the F01 sealing jaws — payback and recommendation.
- Shift Supervisor: Morning vs Afternoon vs Night. A 4-point handover checklist for the incoming morning shift.
- Maintenance Planner: fault Pareto by downtime hours, clean-run baseline shown separately. Top 3 PM actions.
Save with require=dict(tabs=3, charts=3, kpis=5).
```

## Follow-up
If the follow-up needs new calculations, attach the CSV again to that message.

```text
What is the annual prize if Line 1 matched Line 3's reject rate? Split it into scrap savings (LKR mn) and recovered packs.
```

## Debrief
Swap the CSV for another plant's data and rerun. Instructions and skill stay the same; only the data changed. The skill you built today can be reused by any other agent that needs an HTML report.
