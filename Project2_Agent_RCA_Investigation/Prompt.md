# Project 2 — RCA Investigation (Agent)

Set up the agent: paste `Agent_Instructions.md` into Instructions, turn on code interpreter. Do not add the CSV as knowledge.

**Attach `Shift_Incident_and_Operator_Notes.csv` to the same message as the main prompt** (paperclip icon). Copilot only gives the file to the code interpreter in the message you attach it to.

## Main prompt (with the file attached)


Use the code interpreter: load the attached file with pandas and print df.shape (expect 381 rows, 20 columns). Then investigate the incidents in the log:

1. Group them into failure clusters. Table: incidents, downtime hours, scrap kg.
2. Find the two clusters where operators described a symptom but technicians found a different mechanical cause. Show 2–3 examples side by side.
3. Build a 5-Whys for each of those two clusters.
4. Propose a CAPA plan (containment, corrective, preventive) with owner and estimated annual saving, valuing scrap at LKR 1,500/kg.


## Follow-up
If the follow-up needs new calculations, attach the CSV again to that message.


The CI manager can fund one project this quarter:

A) Optical-sensor air purges on the can line — LKR 4.0 mn

B) Dual-RTD sealing-jaw heaters on Line 1 — LKR 6.0 mn

Using scrap (LKR 1,500/kg) and downtime (LKR 50,000/hr) from the log, which has the better 12-month return? Show the calculation.



