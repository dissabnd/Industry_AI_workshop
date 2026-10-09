# Project 2: RCA Investigation (Agent)

**Time:** 40 min  
**Copilot mode:** Agent.  
**Layer you learn:** Standing instructions. The rules now persist across every question and every chat.

## Context
When a packaging line stops, two people write about it. The operator writes a shift note about what they saw ("bags slipping", "powder dusting", "adjusted seal dwell"). The maintenance technician writes a work order about what they found and fixed ("worn suction cups", "sensor drift", "loose load-cell bolts").

These two records often tell different stories. The operator sees the symptom; the technician finds the cause. If management acts only on shift notes, it fixes the wrong thing and the failure comes back.

## The problem
The log holds 381 incidents across three lines, each with telemetry, an operator note and a technician work order. Reading them all by hand is not realistic. We want an AI investigator that:
- groups incidents into failure clusters and sizes downtime and scrap,
- finds where operator notes hide the real mechanical cause,
- builds evidence-based 5-Whys and a costed corrective action (CAPA) plan,
- and follows the same rules of evidence every time, without being reminded.

## What you will learn
- How agent instructions differ from a prompt: instructions say *how to behave*; the prompt says *what to do now*.
- How a few short rules (trust the technician record, flag bad data, stop the 5-Whys where evidence stops) shape every answer.
- Why you should never put the expected answers in the instructions.

## Files
- `Shift_Incident_and_Operator_Notes.csv`: 381 incidents with telemetry, operator notes and technician work orders
- `Agent_Instructions.md`: paste into the agent's Instructions
- `Prompt.md`: the main prompt, a follow-up and the debrief

## Steps
1. In Copilot, choose **Create an agent**. Name: `Plant RCA Investigation Agent`.
2. Paste `Agent_Instructions.md` into **Instructions**.
3. Do **not** upload the CSV under Knowledge. You attach it in the chat in Step 5 (see the note below).
4. Turn on **Code interpreter**.
5. Start a chat with the agent, **attach `Shift_Incident_and_Operator_Notes.csv` to the message that asks for calculations**, and run the prompts in `Prompt.md`.

> **Why attach the CSV in chat?** A file under Knowledge is indexed for search: the agent only sees snippets, so totals come out wrong or truncated. A file attached in the chat goes to the code interpreter as a complete file, so every number can be calculated from all rows. Use Knowledge for documents you search (SOPs, manuals); attach data you calculate from. Two more things: tell the agent to *use the code interpreter* on the file (left to itself it may answer from the preview), and attach the file to the same message that asks for the calculation, because the code interpreter only gets it for that message.

## What to look for
- Are the numbers calculated from the file (does it say how)?
- Does it spot where operator notes and technician records disagree?
- Does the 5-Whys stop where the evidence stops?
- In a new chat, does the agent still follow the rules without being told?
