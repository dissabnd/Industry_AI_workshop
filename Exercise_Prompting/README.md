# Prompting Exercise: Fix This Prompt (before Project 1)


## Context
Every week someone is asked to "write a report on our downtime". Give that request to a new graduate engineer and they will come back with questions: Which lines? Which week? Planned stops too? Who is the report for? What should it look like? AI has the same problem, except it doesn't ask; it guesses.

## The problem
`Line_Downtime_Log_Week35.csv` holds one week of stops on three packaging lines (30 records): date, shift, line, product, planned or unplanned, minutes, fault area and the operator's note. A vague prompt gets a vague report. Can you write a prompt that gets a report the plant manager could act on?

## Steps
1. Open Copilot Chat and attach `Line_Downtime_Log_Week35.csv`.
2. Send the weak prompt: *"Write a report on our downtime."*
3. Rewrite it so the answer is right the first time, and send your version.
4. Compare: which answer could you act on? What did your version add?

## What to look for
- Did it separate planned stops (changeover, CIP) from unplanned breakdowns?
- Did it find which line and fault lost the most time, and on which shift?
- Did it notice the stop with no time recorded?
- Is the output in a form someone could use: a short summary, a table, actions?
