# Project 1: SOP Compliance (Copilot Chat)


## Context
Every deviation on the plant floor (a seal temperature drop, high powder moisture, a failed metal-detector check) is logged by the shift team. QA must then check each one against the plant SOPs: Was it classified at the right severity? Was the right amount of product quarantined? Did the right person sign off the release?

This audit is done by hand, under time pressure, and errors are costly. An under-classified deviation can let unsafe product leave the site; a wrong sign-off is a governance breach an external auditor will find.

## The problem
The log contains 60 deviations from five plant areas, checked against four SOPs (sanitation, quality, HACCP, packaging). Some incidents are logged with a severity lower than the measured value justifies, and some releases were signed off by the wrong role. Can AI find these reliably, cite its evidence, and refuse to make up rules that are not in the SOP?

## What you will learn
- How to write a prompt that sets a role, limits the AI to your files and asks for evidence.
- How to check the AI's work: citations, arithmetic, and whether it admits what it does not know.
- Why chat alone is not enough: the rules disappear when you open a new chat.

## Files
- `Plant_Manufacturing_SOP_Quality_Guidelines.pdf`: the plant standard
- `Quality_Deviation_Incidents_Log.csv`: 60 deviation records
- `Prompt.md`: the opening prompt, follow-ups and debrief

## Steps
1. Open a new Copilot Chat.
2. Attach the PDF and the CSV.
3. Send the opening prompt from `Prompt.md`, then the follow-ups.
4. Do the debrief exercise at the end of `Prompt.md`.

## What to look for
- Does every finding cite an SOP clause and an Incident ID?
- Did it catch the incidents where the logged severity understates the measured value?
- Is the quarantine arithmetic shown and correct?
- Does it decline the FDA question instead of inventing an answer?
