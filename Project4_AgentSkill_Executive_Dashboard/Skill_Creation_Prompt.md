# Build the industrial-report-builder skill (about 15 min)

You create the skill yourself; the aim is a working skill, not a perfect one.

**Where:** a **new** Copilot Chat with **Code interpreter** on (an old chat may hand back an earlier file).  
**Attach:** `example_report_style.html` (the example report, charts replaced by placeholders).

## Prompt (send once)

```text
Attached is an example report that plant leadership liked. Create a reusable skill called industrial-report-builder so any agent can produce HTML reports in this style.

1. Create build_report.py (pandas and matplotlib only, matplotlib.use("Agg"), no internet) with this API:

   r = Report(title, subtitle, footer="")
   r.banner(text)                      # data caveat, shown under the header
   r.kpis([dict(label=, value=, sub=)])  # KPI cards in a grid that fits any number of cards
   t = r.tab(name)                     # tabs using inline JavaScript; first tab open, active tab highlighted
   t.text(text)
   t.bullets([items])
   t.chart(fig, title, caption)        # card with title, chart image and a two-sentence caption
   t.table(df)                         # styled table: thousands separators, max 2 decimals, text HTML-escaped
   r.save(path, require=dict(tabs=3, charts=3, kpis=5))

   Chart helpers that return a matplotlib figure: bar_chart(labels, values, ylabel), stacked_bar(labels, {series: values}, ylabel), hbar(labels, values, xlabel). Use the example's colours, axis labels, value labels on bars, a legend when there are 2+ series, dpi=150.
   Formatters: fmt_kg (1,250 kg), fmt_lkr_mn (LKR 1.33 mn), fmt_pct (91.0%), fmt_hrs (57.1 hrs).

   Rules:
   - Match the example's colours, fonts, header, card and table styles. Do not copy its content.
   - Everything added (banners, text, bullets, charts, tables) must appear in the saved HTML.
   - Count a chart only when t.chart() places it on the page.
   - save() prints the counts. If any is below require, raise an error saying what is short (e.g. "FAILED RUN: charts need 3, have 1") and do not write the file. Write the file as UTF-8.

2. Create SKILL.md. It must start with:
   ---
   name: industrial-report-builder
   description: <one line saying when to use this skill>
   ---
   Then explain: how to import build_report.py, the workflow (calculate every number first, build the page, save with require), a short code example, and "Do not rewrite the module or hand-write HTML."

3. Test before handing over: from small made-up data, build a demo with a banner, 5 KPI cards, 3 tabs, 3 charts (one of each type) and a table. Save with require=dict(tabs=3, charts=3, kpis=5). Confirm the banner text and the table appear in the HTML. Then show that require=dict(charts=4) fails.

Give me the demo HTML and industrial-report-builder.zip with SKILL.md and build_report.py at the top level of the zip.
```

## Before you move on (2 min)
1. Open the demo HTML. Does it look like the example? Do the tabs switch?
2. Did Copilot show the `FAILED RUN` test?
3. The zip contains `SKILL.md` (starting with the name/description block) and `build_report.py`.
4. Open `build_report.py`: you should see `def banner`, `def tab`, `def chart` and `def save`. If not, Copilot ignored the spec; start a new chat and resend.

If one thing is missing, ask Copilot to fix just that one thing. Do not polish further; move on to Project 3, Step 2, and upload the zip to your agent.
