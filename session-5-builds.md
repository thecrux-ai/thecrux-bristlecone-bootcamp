[← Back to Student Handbook](student-handbook.md)

---

# Session 5: Build

**Day 2 - Friday, 3 July 2026**

**The flagship build.** We do this one together, step by step, the whole room at the same pace. Nobody falls behind. By the end, from a single spreadsheet, you will walk away with four things:

1. A reusable **design.md** that holds Bristlecone's branding (colours, fonts, layout rules).
2. A clean business **report** (markdown, with a PDF).
3. An interactive **dashboard** (an HTML page with charts and filters).
4. A branded **PowerPoint deck** an exec could actually stand up and present.

All four come out looking on-brand, because they all read the same design.md.

---

## Why this session matters to you

In the pre-bootcamp survey, 13 of you said data work eats your time.

Pulling numbers out of a tracker.
Reformatting them into a report.
Rebuilding the same status deck every week.
Then making it look presentable for a client or a leader.

That is hours, every week, on work a machine can do.

Today you build the machine. Once.

The first time you do this, it feels slow because you are learning. The second time, it is fifteen minutes. The tenth time, it is a habit. That is the whole point.

You are not learning to code. You are learning to **direct**. You describe what you want in plain English, Claude builds it, you look at the result, you tell it what to fix. That loop is the entire skill.

---

## What you will have by the end of this session

- One folder with a runnable build inside it.
- `design.md` - your Bristlecone branding engine.
- `project-health-report.md` and a matching **PDF**.
- `dashboard.html` - opens in your browser, with charts, a filter, and a chat you can ask questions.
- `server.js` - the local helper that powers the chat using your Claude subscription.
- A branded **.pptx** deck.

Every output uses the same blue and grey Bristlecone look, because every output reads the same design.md.

---

## A note before we start

You don't need any technical know-how today. You describe what you want in plain English, Claude does the technical part, and you approve.

Here is how today works.

- Every prompt you need is in a grey box on this page. Copy it. Paste it into Claude. Do not type from memory.
- We move as one room. After each part there is a **Checkpoint**. We all stop, check, and only then move on.
- If you fall behind, say `slow down`. We wait. Nobody gets left.
- If something breaks, raise your hand. There is also a full Troubleshooting section at the bottom of this page.

Three parts. One dataset. Four outputs. Let's go.

---

## Setup: get your build folder ready

We will save everything into a folder called `day2builds` inside your project. You don't set this up by hand. Make sure the `thecrux-bristlecone-bootcamp` folder is open in VS Code and Claude is running (start it the way you did in Session 0), then ask Claude:

```
Create a folder called day2builds in this project. Then copy both
spreadsheets from the sample-data folder into day2builds. When you're
done, list what's inside day2builds so I can confirm.
```

Claude makes the folder, copies the files, and shows you what landed. You should see `project_health.xlsx` and `resource_utilisation.xlsx` inside `day2builds`. Approve each step when it asks.

---

## About the data

Two Excel files. This is the kind of delivery data a consulting firm looks at every week.

The data is for **Ironwood Consulting**, a made-up supply chain and enterprise technology consulting firm. It looks a lot like Bristlecone: the same business units, the same kind of SAP and supply chain work, the same RAG health reporting. We invented every name and number, so there is nothing confidential here. You can use it freely.

**`project_health.xlsx`** - one row per active project. Twenty projects across five client accounts (Cascade Foods, Northwind Logistics, Meridian Auto, Apex Retail, Helios Pharma), spread across four business units (Technology, Growth Markets, Consumer, Industrial) and five service lines (SAP, Supply Chain B&E, Enterprise Platforms, Strategy & Consulting, Industrial Solutions). Columns cover project name, account, business unit, service line, region, the delivery head, delivery partner and client partner on the account, the project manager, status, dates, planned vs actual effort, percent complete, last month's RAG and this month's RAG health (Red/Amber/Green), open risks and issues, client satisfaction (CSAT), contract value, margin, billable headcount, and utilisation.

**`resource_utilisation.xlsx`** - utilisation by service line and region, month by month (Jan to Mar 2026). Billable headcount, bench, available days, billed days, utilisation percent, average bill rate, and attrition.

You don't need to study these. Claude will read them. But it helps to know roughly what is in there, so when you read the report you can tell if the numbers feel right.

---

# PART A - Build the Bristlecone design.md (your branding engine)

**Time: about 25 minutes.**

Before we touch the data, we build the thing that makes every output look like Bristlecone and not like a generic template.

## What a design.md is, in plain words

A design.md is a short text file that holds your brand rules. Your colours. Your fonts. Where the logo goes. How a report, a proposal, and a deck are laid out at Bristlecone.

Once this file exists, you point Claude at it and say "use design.md." From then on, every report, every dashboard, every deck comes out in Bristlecone's look. No re-explaining. No fiddling with colours each time.

Think of it as a style guide that Claude actually reads and obeys.

## Why we build it first

Everything else today reads this file.

The report reads it for fonts and the header.
The dashboard reads it for the colour of the charts.
The deck reads it for the title slide and the accent colour.

Build it once now, and the look is consistent across all three. That consistency is what makes a stack of outputs feel like it came from one company instead of three different interns.

## Get a real Bristlecone file into your folder

We will not type brand rules by hand. That is slow and it guesses. Instead, you hand Claude a real Bristlecone file and let it pull the brand rules out for you.

Pick one file you already have that shows the Bristlecone look. Any of these works, best first:

- A recent Bristlecone deck (a sales or delivery PPT)
- The brand or style guideline document, if you have it
- A branded proposal or SOW
- A branded report or one-pager

One file is enough. A deck is usually the richest, because it shows colours, fonts, the logo, and layout all at once.

**Get your file into the build folder.**

The easiest way is drag and drop. In VS Code, find the file on your machine (File Explorer or Finder), and drag it onto the `day2builds` folder in the VS Code file list on the left.

If it's easier, just ask Claude to do it (change the file name and location to match yours):

```
My Bristlecone deck is in my Downloads folder, called
your-bristlecone-file.pptx. Copy it into the day2builds folder, then
confirm it's there.
```

> No branded file on your laptop right now? Two options. Borrow one: ask a colleague for the latest deck, or use any Bristlecone document you can find. The point is to extract from a real file, not to invent values.
>
> **Or use the ready-made one.** We put a finished `design.md` in your `sample-data` folder called `design-bristlecone-sample.md`. It already holds the real Bristlecone colours and fonts, pulled from a real delivery deck. Ask Claude:
>
> ```
> Copy sample-data/design-bristlecone-sample.md into day2builds and
> rename the copy to design.md.
> ```
>
> Then skip ahead to Checkpoint A. The rest of the session uses the same colour names, so everything works the same.

## Build design.md from that file

Now point Claude at your file and let it do the work. Change the file name to match yours, then paste this:

```
Read the Bristlecone file in the day2builds folder called [your-file-name].
Pull out the brand rules and write them into day2builds/design.md.

I want design.md to capture, with exact values wherever you can find them:
- Colours: pull the exact hex codes from the file. Map them onto these
  standard names so the rest of my build can use them: Brand Navy (the
  darkest, for headers and titles), Brand Blue (the main accent), Sky Blue
  (a lighter second accent), a Light Grey background, and status colours
  Green, Amber and Red. If the file is missing one, pick the closest match
  from the file and mark it.
- Fonts: the heading font and the body font, with a safe fallback.
- Logo: where the Bristlecone logo or wordmark sits, and its colour.
- Layout rules for a report, a proposal or SOW, and a deck: headers,
  section styles, table styling, and footers.

Where you cannot find a value in the file, make a sensible choice that
matches the look and clearly mark it so I can confirm it. Show me design.md
when you are done, with the hex codes in plain sight.
```

Claude reads your actual file and writes the brand rules down for you. This is the real way to build a design.md, the same way you would for any client.

## Check it and fix anything

Open the design.md Claude made and read it. Two quick checks:

- Do the colours match what you see in your file? If a hex code looks off, tell Claude the right one.
- Is anything marked as a guess? Confirm it or correct it.

To fix a value, just say what is wrong in plain English, for example:

```
In design.md, the Brand Blue should be [your hex code], not the one you used.
Update it and keep everything else the same.
```

That is it. You now have a branding engine pulled from a real Bristlecone file. Everything you build next reads it.

---

> **Checkpoint A - design.md is ready**
>
> - [ ] `day2builds/design.md` exists
> - [ ] It has sections for colours (with hex codes), fonts, logo, and report/proposal/deck layout
> - [ ] You read it and it makes sense
>
> If yours isn't ready, say `slow down`. We wait for the whole room before Part B.

---

# PART B - Excel to Report to Dashboard

**Time: about 80 minutes.**

Now the satisfying part. We take the data, clean it, write a real business report, and build an interactive dashboard. All branded by design.md.

## Step B1: Let Claude read and check the data

First, have Claude look at the data and tell us what's in it. This is also a quick quality check.

```
Read both Excel files in the day2builds folder:
day2builds/project_health.xlsx and day2builds/resource_utilisation.xlsx.
Give me a short summary of each: how many rows, what the columns are,
and one line on what the data is about.

Then check for problems: missing values, dates that look wrong, numbers
that look impossible (like utilisation over 100, or actual effort far
above planned). List anything you'd want to clean before reporting on it.
```

Read the summary. Notice that a few projects have actual effort above planned and a couple of Red projects. That is normal. That is the story the report will tell.

## Step B2: Clean the data

```
Clean the data so it's ready for reporting. Specifically:
- Make sure every date is a proper date.
- Make sure percent and money columns are numbers, not text.
- Flag any project where Actual Effort is more than Planned Effort as an
  effort overrun.
- Flag any project with Health = Red as at-risk.
- Save the cleaned project data as day2builds/project_health_clean.csv.

Tell me what you changed and what you flagged.
```

Claude writes a clean file and tells you what it fixed. If a number still looks off, just ask: "Where did that figure come from? Show me the row."

## Step B3: Write the business report

This is the report a delivery leader would actually send up the chain. We tell Claude to use design.md so it comes out branded.

```
Write a business report called day2builds/project-health-report.md from
day2builds/project_health_clean.csv and day2builds/resource_utilisation.xlsx.
This is for a Bristlecone delivery leadership review.

Use the branding rules in day2builds/design.md (colours, fonts, header,
footer, table style). The report should read like a Bristlecone document.

Structure it like this:

1. Executive summary - 4 to 5 bullets. The headline: total portfolio
   value, how many projects are Green vs Amber vs Red, the average
   margin, the average utilisation, and the single biggest risk.

2. Portfolio health - a table of all projects with Account, Project,
   Health, Percent Complete, Margin, and CSAT. Sort by Health worst-first
   (Red, then Amber, then Green).

3. At-risk projects - call out every Red project by name. For each one,
   say what the data shows: effort overrun, low CSAT, open risks and
   issues, thin margin. One short paragraph each.

4. Margin and value - which accounts carry the most contract value, and
   where margin is thin. A short table by account.

5. Resource utilisation - utilisation by service line over Jan to Mar.
   Which service lines are running hot, which have bench sitting idle.
   Note any attrition worth watching.

6. Recommendations - 3 to 5 concrete next steps a leader could action
   this week. Each with a clear owner-type (e.g. "PM", "account lead",
   "resourcing").

Keep it crisp. Lead with the point. No fluff. Use real numbers from the
data, never invented ones. Show me the report when it's done.
```

Read it. This is the moment most people sit up. The report names real projects, real numbers, and real risks. It reads like something a person on your team wrote.

If a section feels thin or wrong, fix it in plain English:

```
The at-risk section is too soft. For each Red project, give me the
specific numbers: the exact effort overrun in person-days, the CSAT
score, and the count of open risks and issues. Be blunt.
```

## Step B4: Make a PDF of the report

Leaders want a PDF they can forward. Let's make one.

```
Turn day2builds/project-health-report.md into a clean PDF called
day2builds/project-health-report.pdf. Apply the day2builds/design.md
branding: the Bristlecone wordmark top-left, the report title and today's
date top-right, a thin Brand Blue rule under the header, Navy section
headings, and the table style from day2builds/design.md. Footer:
"Bristlecone | Confidential" left, page number right.

Use the pdf skill in the project root.
```

Type `/pdf` in Claude to invoke the pdf skill. It will handle the conversion using Python's reportlab library — no heavy installs needed.

When the PDF is made, ask Claude to open it:

```
Open day2builds/project-health-report.pdf so I can see it.
```

If the branding looks off (wrong colour, no header), tell Claude exactly what's wrong: "The header has no Bristlecone wordmark and the headings are black, not navy. Fix it to match design.md."

---

> **Checkpoint B1 - report and PDF are ready**
>
> - [ ] `project-health-report.md` exists and reads like a real report
> - [ ] It names the Red projects and uses real numbers
> - [ ] `project-health-report.pdf` opens and looks branded (wordmark, navy headings, blue rule)
>
> Stop here. Make sure your PDF opens before we build the dashboard.

---

## Step B5: Build the interactive dashboard

A dashboard is an HTML page you open in your browser. Charts. Numbers. A filter so you can slice by account.

```
Build an interactive HTML dashboard called day2builds/dashboard.html from
day2builds/project_health_clean.csv and day2builds/resource_utilisation.xlsx.
It must be a single HTML file I can open in my browser by double-clicking.
No server needed. Load chart libraries from a CDN (Chart.js is fine).

Apply the day2builds/design.md branding throughout: Brand Navy header, Bristlecone
wordmark top-left, Brand Blue and Sky Blue as the chart colours, the
Light Grey page background, the table style from design.md. Red/Amber/
Green status uses the exact status colours from design.md.

Layout:

TOP - four summary cards: Total Portfolio Value (sum of contract value),
Projects At Risk (count of Red), Average Margin, Average Utilisation.

A FILTER at the top: a dropdown to filter the whole dashboard by Account
(All, Cascade Foods, Northwind Logistics, Meridian Auto, Apex Retail,
Helios Pharma). Changing it updates the cards and charts.

CHARTS:
1. Project health - a doughnut chart of Green / Amber / Red counts.
2. Contract value by account - a bar chart.
3. Margin percent by account - a bar chart.
4. Utilisation by service line over Jan to Mar - a line chart, one line
   per service line.
5. Effort: planned vs actual by project - a grouped bar chart, so
   overruns are obvious.

A TABLE at the bottom: all projects with Account, Project, Health (shown
as a coloured dot or pill), Percent Complete, Margin, CSAT. The Red rows
should stand out.

Make it clean and professional. It should look like a Bristlecone
internal tool. Show me when it's ready.
```

When Claude is done, ask it to open the dashboard:

```
Open day2builds/dashboard.html in my browser.
```

Play with the filter. Pick "Cascade Foods." Watch the cards and charts update. That moment, where a spreadsheet becomes a tool you can click through, is the whole reason we're here.

## Step B6: Polish the dashboard

The first version is never quite right. Here are the fixes people usually need. Use the ones you need, in plain English.

```
The charts are too small. Make them bigger and put them two per row on a
wide screen, one per row on a narrow screen.
```

```
Add a second filter for Region (All, North America, EMEA, APAC) that
works together with the Account filter.
```

```
The summary cards should show the number big and the label small
underneath, in the design.md card style. Add a thin Brand Blue top border
on each card.
```

```
On the effort chart, colour any bar where actual is above planned in
Alert Red so overruns jump out.
```

Stop when it looks good. Don't chase perfect. Good and branded beats perfect and late.

---

> **Checkpoint B2 - dashboard is ready**
>
> - [ ] `dashboard.html` opens in your browser by double-clicking
> - [ ] Four summary cards at the top show real numbers
> - [ ] The Account filter changes the cards and charts
> - [ ] Charts use the Bristlecone blue/grey look from design.md
> - [ ] The project table at the bottom shows Red projects clearly
>
> This is the halfway high point. Everyone should have a working dashboard before the break. Say `slow down` if you don't.

---

## Step B7: Add a chat to the dashboard

**Time: about 20 minutes.**

A dashboard shows the numbers. A chat lets a leader ask. "Which Red projects are over budget?" "What's our margin by account?" You type the question, you get the answer from your own data, in seconds.

This runs on your machine and uses your team's Claude subscription. No API key. The same Claude login you already use, just wired into the dashboard.

### How it works, in one line

A small helper (a Node.js server) sits behind the dashboard. It reads your data files, serves the page, and when someone asks a question it passes the question and the data to Claude using `claude -p` (the same Claude you are logged into), then shows the answer in the chat panel.

### Build it

Paste this into Claude:

```
Add a chat panel to day2builds/dashboard.html so a leader can ask
questions about the project data. Build a small Node.js server
(day2builds/server.js) using Express:

1. On startup, read day2builds/project_health.xlsx and
   day2builds/resource_utilisation.xlsx using the xlsx npm package.
2. Serve day2builds/dashboard.html at http://localhost:3030.
3. A POST /ask endpoint takes a question. It runs "claude -p" as a
   subprocess (child_process.execFile), sending the question plus the
   data, and returns Claude's answer as JSON. Use my Claude subscription
   via "claude -p" - no API key.
4. Keep answers short and factual. If a table helps, return one.

Add a chat panel to dashboard.html, bottom-right, styled with design.md
(Brand Navy header, Brand Blue send button, Light Grey panel):
- A text box and a send button.
- Suggestion chips: "Which Red projects are over budget?",
  "Average margin by account?", "Which service line has the most idle
  bench?", "Which accounts are all Amber or Red?", "Biggest delivery risk
  right now?".
- A "thinking..." indicator while it waits.
- Show the answer text and any table inline. Make the panel minimisable.

Once the server is built, install whatever it needs and start it for me.
Then tell me the exact web address to open in my browser.
```

### Run it

You don't type any setup commands. Claude installs what the server needs and starts it for you. It will ask permission before each step, so read and approve.

When it's running, Claude shows you a line like:

```
Dashboard + chat running at http://localhost:3030
```

Open that address in your browser. The dashboard loads with a chat panel at the bottom-right.

> Keep the server running while you use the chat. If you ever need to start it again, just ask Claude: "start the dashboard server again."

### Try it

Click a chip, or type your own:

- "Which Red projects are over budget?"
- "What's the average margin by account?"
- "Which service line has the most idle bench?"
- "Give me the three biggest risks in the portfolio."

Each answer takes a few seconds. Claude reads your data and answers in plain English. Spot-check one answer against the dashboard so you trust it.

### A word on safety

This sends your question and the data to Claude, exactly like any prompt you type in Claude Code. It runs locally on your laptop, on your team's subscription. Keep to internal, anonymised, or sample data here, the same rule from the governance session. No real client PII in the chat.

### Make it better

- "Keep answers to three sentences unless a table is clearer."
- "Add my last five questions as clickable history."
- "When the answer names projects, colour the Red ones in Alert Red."

---

> **Checkpoint B3 - the dashboard answers questions**
>
> - [ ] Claude started the server and printed the localhost address
> - [ ] The dashboard opens at http://localhost:3030 with a chat panel
> - [ ] The suggestion chips return answers from your data
> - [ ] You spot-checked one answer against the dashboard numbers
> - [ ] The chat panel uses the Bristlecone look from design.md

---


# PART C - Report data to a branded PowerPoint

**Time: about 35 minutes.**

You have a report and a dashboard. Now the deck. The thing a leader stands up and presents in a review. Same data. Same branding. A few clicks.

## Why a deck, when we have a report

A report is for reading. A deck is for the room.

Leaders present from slides. A branded exec deck, built in two minutes from the same data, means you never again rebuild the status pack by hand the night before a review.

## Step C1: Generate the branded deck

We build a real PowerPoint file (a `.pptx`) that opens in PowerPoint. It uses the colours and fonts from design.md.

```
Create a branded PowerPoint deck called day2builds/project-health-review.pptx
from day2builds/project-health-report.md and the data in day2builds/.
Apply the day2builds/design.md branding to every slide.

Slides:

1. Title slide - Brand Navy background, white title "Project Health
   Review", subtitle "Bristlecone Delivery Leadership", today's date, a
   Brand Blue accent bar.

2. Executive summary - the 4-5 headline bullets from the report (total
   value, Green/Amber/Red counts, average margin, average utilisation,
   biggest risk).

3. Portfolio at a glance - a simple chart or coloured table showing the
   Green/Amber/Red split.

4. At-risk projects - the Red projects in a table, with the key numbers
   (effort overrun, CSAT, open risks/issues). Use the Alert Red colour
   for emphasis.

5. Value and margin by account - a bar chart or table.

6. Resource utilisation - utilisation by service line, the hot ones and
   the idle bench, in a chart or short table.

7. Recommendations - the 3-5 next steps, as clean bullets.

Every content slide: white background, Navy title, a thin Brand Blue
underline under the title, footer with the Bristlecone wordmark and slide
number. Use real numbers from the data. Show me when it's built.

Use the pptx skill in the project root.
```

Type `/pptx` in Claude to invoke the pptx skill. It builds a real `.pptx` file — no manual installs needed.

When it's ready, ask Claude to open the deck:

```
Open day2builds/project-health-review.pptx so I can see it.
```

## Step C2: Fix the deck

Decks always need a tweak or two. Plain English again.

```
The title slide text is hard to read. Make the title bigger and pure
white, and move the date to the bottom-left in Sky Blue.
```

```
On the at-risk slide, the table is cramped. Give it more room, bigger
font, and put the Red status in the Alert Red colour from design.md.
```

```
Add a closing slide: Brand Navy background, white text "Questions?", the
Bristlecone wordmark centred below.
```

When it looks like something you'd present, you're done.

---

> **Checkpoint C - branded deck is ready**
>
> - [ ] `project-health-review.pptx` opens in PowerPoint
> - [ ] The title slide is Navy with white text and a blue accent
> - [ ] Content slides have Navy titles and a blue underline
> - [ ] The at-risk slide shows the Red projects with real numbers
> - [ ] It looks like Bristlecone, not a default template

---

## You did it - what you're holding now

From one spreadsheet, in one sitting, you built:

- **design.md** - your reusable branding engine. Use it on every future build.
- **project-health-report.md** + **.pdf** - a branded business report.
- **dashboard.html** + **server.js** - an interactive tool you can click, filter, and ask questions, powered by your Claude subscription.
- **project-health-review.pptx** - a deck ready for a leadership review.

And here is the real win. Next month, when the numbers change, you don't rebuild any of this. You drop in the new Excel file and say:

```
Read the new day2builds/project_health.xlsx. Regenerate the report, the
dashboard, and the deck using day2builds/design.md, exactly like before.
```

The hours you used to spend become one prompt.

---

## If you finish early

Push it further. Try any of these.

**Anomaly report.** 

```
Look across all the data and flag anything unusual: an account where every
project is Amber or Red, a service line with high bench and low
utilisation, a Red project with high contract value. Give me a one-page
red-flag note, branded with day2builds/design.md, and save it to day2builds/.
```

**Email-ready summary.**

```
Write a short email body I could paste into Outlook, summarising the
portfolio health for my manager. Three short paragraphs, the top risk
first, branded subject line. No attachment needed, just the text.
```

**Reuse design.md.** Open it and notice you can now use this same file for a proposal, an SOW, or any future report. That is the asset you keep.

---

## Tips for the whole session

- **One thing at a time.** Build, look, fix, then move on. Don't ask for everything in one giant prompt.
- **Be specific when you fix.** "Make it better" gives you nothing. "Make the charts bigger and the Red rows stand out" gives you exactly that.
- **Check the numbers.** If a figure looks wrong, ask "show me the row that came from." Claude shows its working.
- **Save as you go.** Each output is a file in your folder. They don't vanish.
- **Branding comes from design.md.** If something looks off-brand, the fix is almost always "use the colours and fonts in design.md."

---

## Troubleshooting - Session 5

Work top to bottom. Most problems are one of these.

### Getting around and files

| Problem | Fix |
|---|---|
| Claude can't see the project files | Make sure the `thecrux-bristlecone-bootcamp` folder is the one open in VS Code (**File → Open Folder...**), then start Claude there the way you did in Session 0. |
| The Excel files aren't in day2builds | Ask Claude: "Find project_health.xlsx and resource_utilisation.xlsx on my machine and copy them into the day2builds folder." |
| I'm not sure what's in my build folder | Ask Claude: "List everything in the day2builds folder." Or open `day2builds` in the VS Code file list on the left. |

### The server and the chat

| Problem | Fix |
|---|---|
| The server won't start | Paste the error to Claude: "the server didn't start, here's the error: [paste it]. Fix it and start it again." It handles the install and setup for you. |
| The server says "port already in use" | Ask Claude to "use a different port like 3050 and start the server again." |
| The server starts but the page won't load | Open the exact address Claude printed, usually `http://localhost:3030`. Type it into your browser exactly. |
| The chat says "failed to connect" | The server has stopped. Ask Claude: "start the dashboard server again," and keep it running while you use the chat. |
| The chat won't answer | Claude Code must be running and you logged in. Tell Claude "the dashboard chat isn't answering" and let it check the server. |
| Chat answers take 10-15 seconds | Normal. Claude reads the data on each question. Ask Claude to "send only the columns needed to answer" to speed it up. |
| The chat panel looks off-brand | "Style the chat panel using design.md: Brand Navy header, Brand Blue send button, Light Grey panel." |

### The PowerPoint deck

| Problem | Fix |
|---|---|
| The deck didn't build | Paste any error to Claude: "the deck build failed, here's the error: [paste it]. Fix it and rebuild." It installs whatever it needs itself. |
| The .pptx file won't open | It may not have finished building. Ask Claude "did the deck build without errors? Rebuild it and tell me if anything failed." Then open it again. |
| The deck opens but has no branding | Tell Claude exactly what's wrong: "The slides are the default white template, not the Navy and Blue from design.md. Apply the design.md colours." |
| Charts in the deck look broken or empty | Ask Claude to "rebuild the charts in the deck using the actual numbers from the data, and check they render." |

### PDF export

| Problem | Fix |
|---|---|
| The PDF method asks me to install something heavy | Tell Claude: "Use a lighter method. Render the report to HTML, then to PDF, without installing big tools." |
| The PDF has no colours or branding | "The PDF is plain black and white. Apply the design.md header, navy headings, and blue rule." |
| The PDF is missing the header or footer | "Add the Bristlecone wordmark and date to the header, and the Confidential footer with page numbers, per design.md." |
| `start file.pdf` does nothing on Windows | Open the folder in File Explorer and double-click the PDF instead. Or run `Invoke-Item project-health-report.pdf`. |

### Charts and the dashboard

| Problem | Fix |
|---|---|
| The dashboard opens but charts are blank | The chart library may not have loaded. Ask Claude: "The charts are blank. Make sure Chart.js loads from the CDN and the data is passed in correctly." Check you have internet, the CDN needs it. |
| Charts show the wrong numbers | "These chart numbers don't match the data. Recalculate them from project_health_clean.csv and show me your working." |
| The filter doesn't change anything | "The Account filter isn't updating the cards or charts. Wire it up so changing the dropdown re-filters everything." |
| Colours are generic, not Bristlecone | "Use the exact chart colours from design.md: Brand Blue and Sky Blue. Status uses the Green/Amber/Red from design.md." |
| The page looks cramped on my screen | "Make it responsive: two charts per row on wide screens, one per row on narrow. Add more spacing." |

### Claude itself

| Problem | Fix |
|---|---|
| Claude did too much at once and it's a mess | Undo in your head, not the file. Say: "That's too much. Let's go back to just the report. Ignore the rest for now." Then rebuild one piece at a time. |
| Claude says it can't find design.md | Make sure `day2builds/design.md` exists. Run `dir day2builds` (Windows) or `ls day2builds` (Mac) to check. If it's missing, redo Part A. |
| The output ignores my branding | Always name the file: "Use the branding in design.md." If it still ignores it, say "Read design.md out loud first, then apply every colour and font to this output." |
| Claude crashed or my laptop slept | Start Claude again with `claude`. Your files are saved. Re-paste the last prompt you were on. |
| I'm completely lost | Raise your hand. Say `slow down` to the room. Nobody moves to the next part until you're caught up. |

---

> **Final checkpoint - the full stack**
>
> - [ ] `design.md` - your branding engine
> - [ ] `project-health-report.md` and `project-health-report.pdf` - branded report
> - [ ] `dashboard.html` + `server.js` - interactive, filterable, branded, and answers questions
> - [ ] `project-health-review.pptx` - a deck you could present
>
> One dataset. One design.md. A report, a dashboard you can ask, and a deck. That is the build.

---

**Next:** Working lunch + hackathon - [pick your project →](capstone.md)
