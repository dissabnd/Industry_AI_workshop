# Project 4 — Monthly Performance Pack (Agent + skill)

First build the skill with `Skill_Creation_Prompt.md` (this folder).

Then set up the agent: paste `Agent_Instructions.md` into Instructions, add your `SKILL.md` under **Configure → Skills**, turn on code interpreter. Do not add the CSV as knowledge.

Attach the CSV only in **Step A** below (paperclip icon). Copilot gives the file to the code interpreter only in the message you attach it to, so all calculations happen in Step A. Steps B–D work from the tables Step A puts in the chat.

## Check the skill is there

```text
Which skills do you have?
```
You should see `monthly-performance-pack` alongside the built-in DOCX and Slides skills.

## Build the pack in four short steps (same chat)

**Step A: the numbers** 

Use the code interpreter: load the attached file with pandas and print df.shape (expect 810 rows, 23 columns). Then, following the monthly-performance-pack skill, calculate the June–August summary tables, one per report section:
1. Headline KPIs (plant OEE weighted by operating time, reject rate, good packs, scrap cost, lost-capacity cost, total loss, annualised loss)
2. By line: OEE, reject rate, scrap cost, lost-capacity cost, unplanned downtime hours
3. By shift: OEE, reject rate, unplanned downtime hours
4. Fault ranking by downtime hours and total loss, with the NONE-Clean Run baseline as a separate row
5. CapEx: the LKR 25 mn request to overhaul the F01 sealing jaws (annualised F01 loss, payback, recommendation)
Show the tables only.
```

**Step B: the report text**  


Following the monthly-performance-pack skill, write the full Word report here in the chat: all 8 sections in order, with real text and tables, using only numbers from the summary tables above. Do not reload the CSV.

**Step C: the Word file**

Use the DOCX skill to create Monthly_Performance_Report.docx containing exactly the report text above, with its tables. Make the three charts with the code interpreter from the numbers in the summary tables above (do not reload the CSV) and insert them as images.
Then reopen the file and print: the section headings, the number of tables and images, and the word count. If any section is empty or missing, fix it and rebuild.


**Step D: the PowerPoint file**

Following the monthly-performance-pack skill, write the 6 slides here in the chat (title and up to 4 bullets each), using only numbers from the summary tables above. Do not reload the CSV.
Then use the Slides skill to create Leadership_Brief.pptx with exactly that content.
Reopen the file and print each slide's title and bullet count. If any slide is empty, fix it and rebuild.

## Final check


Audit the report and the deck against the skill: list any missing section or slide, and any number that differs between the two or from the summary tables. Fix and re-issue if needed.


## Debrief
Open both files. Then compare with someone who did Project 3: same agent, same data, same numbers, different skill, different output.
