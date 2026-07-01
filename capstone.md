[← Back to Student Handbook](student-handbook.md)

---

# Capstone Projects

**Day 2 - Friday, 3 July 2026**

**Skill unlocked:** You stop following steps and start building your own thing. One real piece of work, built by you, using everything you set up over the last two days.

---

## What this session is

For two days you built the parts.

A CLAUDE.md that knows who you are.
A design.md that holds Bristlecone's look and brand.
A skill or two you can reuse.
A research workflow, and your own agent, that dig into a question.
And at least one finished thing: a report, a dashboard, or a deck.

Now you put it together on a problem that actually matters to you.

On Day 2 we run this as a hackathon. You build your pick, then present it to the room.

This is the part you take back to your desk on Monday.

---

## The most important line in this whole session

**The capstone is yours to pick.**

Below are five suggested tracks. They are starter ideas, nothing more. Each one maps to something a Bristlecone team asked for, either in the survey or on the kickoff call.

You can pick one of these five.
Or you can ignore all of them and build a real problem from your own week.

If you have a report you dread every Monday, build the thing that does it for you.
If you have a proposal due next week, build the helper that drafts it.
If there is one task you wish would just disappear, that is your capstone.

The five tracks are there so nobody stares at a blank screen. They are not a menu you must order from.

Pick whatever will save you the most time on Monday. That is the only rule.

---

## Before you start

You should already have these from Day 1 and this morning's build. Reuse them. Do not rebuild them.

- **CLAUDE.md** at the root of your project folder.
- **design.md** with Bristlecone's colours, fonts, and brand rules.
- At least one **skill** you built.
- Your **research workflow** prompt.
- One finished build from earlier: a report, a dashboard, or a PPT.

Open your folder and check what you have. In VS Code, make sure the `thecrux-bristlecone-bootcamp` folder is open, then open a terminal (**Terminal → New Terminal**) and type `claude`.

Then ask Claude to take stock:

```
List what's in my project folder. Tell me which of these I have:
CLAUDE.md, design.md, any skills, a research workflow prompt, and any
reports, dashboards, or decks I built earlier. Then suggest which one
of my real work problems would make the best capstone for the time
we have, based on what's in my CLAUDE.md.
```

Read its suggestion. Use it or overrule it. You decide.

---

## How the build runs

Keep it simple. Move through these steps in order.

1. Pick your project. One of the five tracks, or your own.
2. Tell Claude the plan. Drop in your reference files and data.
3. Build. One thing, end to end. This is the bulk of your time.
4. Polish. Branding, format, a final read.
5. Prep your 3-minute share for the showcase.

Do not try to build five things. Build one thing well.

---

## The five suggested tracks

Each track has a short brief, the outcome you walk away with, and a few starter prompts. Copy a prompt, paste it into Claude, change the bits in [brackets] to match your real work.

---

### Track 1 - SOW / Proposal Accelerator

**For:** Pre-sales, consulting, go-to-market.

**The brief:** You feed Claude a couple of your past SOWs or proposals. It learns the structure and the language. Then for a new deal, it drafts a fresh, Bristlecone-branded SOW or proposal that already sounds like your best work, not a blank template.

**The outcome:** A first-draft SOW or proposal for a real or sample deal, in Bristlecone's tone, ready for you to refine instead of starting from zero.

**Starter prompts:**

```
I'm going to give you 2 or 3 of our past SOWs and proposals as
reference. Read them and tell me the common structure: the sections,
the order, the tone, and the kind of language we use. Save what you
learn as a file called sow-pattern.md so we can reuse it.
```

```
Using sow-pattern.md and my design.md for branding, draft a new SOW
for this deal: [client name], [what they need], [rough scope],
[timeline], [team size]. Keep our usual structure. Mark anything you're
guessing in {curly braces} so I can fix it.
```

```
Turn that SOW into a Bristlecone-branded PDF using the colours and
fonts in design.md. Add a cover page with the client name and date.
```

```
Read the draft back as if you were a tough client. Tell me the three
weakest sections and rewrite them sharper.
```

---

### Track 2 - Cost & Finance Report Bot

**For:** Finance, FP&A.

**The brief:** You have a report you build every month or every week from raw spreadsheets. Cost accounting, project margins, a spend summary, whatever it is. You hand Claude the raw files and tell it the format you want. It builds the report for you, branded and clean.

**The outcome:** A repeatable bot. Next month you drop in the new numbers, run one prompt, and the same report comes out. No more rebuilding it by hand.

**Starter prompts:**

```
I'm giving you a raw spreadsheet of [cost data / project spend /
margins]. Read it and tell me what's in it: the columns, the totals,
anything that looks off. Don't summarise yet, just show me you
understand the data.
```

```
Build me a monthly [cost / finance] report from this data. I want:
a one-line headline, a summary table, the top 3 things that moved,
and a short note on anything that needs attention. Use my CLAUDE.md
format rules. Brand it with design.md.
```

```
Save the exact steps you just did as a skill called finance-report so
next month I can drop in new numbers and run it again. Write the skill
so a non-technical person can use it.
```

```
Now turn the report into a Bristlecone-branded PDF I could send to
my manager.
```

---

### Track 3 - Process & Governance Assistant

**For:** Delivery, Quality, PMO.

**The brief:** You build an assistant that checks whether a project is following the process it should. Think SDLC adherence, a delivery-excellence review, an audit checklist. You give it your standard and a project's status, and it tells you where the gaps are.

**The outcome:** A governance checker you can point at any project. It runs the review, flags what is missing, and gives you a clean summary for your monthly governance pack.

**Starter prompts:**

```
Here is our standard process / checklist for [SDLC / delivery
governance / quality review]. Read it and turn it into a clear list of
checks: what each project must have, and how I'd know it's been done.
Save it as governance-checklist.md.
```

```
Here is the status of a project: [paste status, or point to a file].
Run it against governance-checklist.md. Tell me which checks pass,
which fail, and which I can't tell from this data. Put it in a table
with a red / amber / green column.
```

```
Write a one-page governance summary from that review. Lead with the
top 3 risks, name owners and dates where you can, and end with a clear
recommendation. Use my CLAUDE.md format rules.
```

```
Save this whole review as a skill called governance-check so I can run
it on any project next month.
```

---

### Track 4 - Branded Deck & Doc Studio

**For:** Marketing ops, Competency, Pre-sales.

**The brief:** You take raw content, rough notes, a capability write-up, a case study, and turn it into a polished, Bristlecone-branded PDF or deck. Then you make it reusable: a template you can fill again next time.

**The outcome:** One branded deliverable now, plus a reusable Bristlecone PPT or doc template you can reuse for the next ten.

**Starter prompts:**

```
Here's some raw content: [paste notes / capability write-up / case
study]. Shape it into a clean structure for a [PDF / deck]: a strong
title, clear sections, and a takeaway at the end. Don't design it yet,
just get the content right.
```

```
Now build it as a Bristlecone-branded [PDF / PPT] using the colours and
fonts in design.md. Add a cover and a closing slide. Keep it clean and
senior, not busy.
```

```
Turn this into a reusable Bristlecone template. Leave clear
placeholders like [TITLE], [SECTION], [KEY POINT] so I can drop new
content in next time. Save it so I can find it again.
```

```
Make me a second version of the cover in a different layout so I can
pick the one I like.
```

---

### Track 5 - Hiring / Talent Accelerator

**For:** HR, Talent Acquisition.

**The brief:** You speed up the slowest part of hiring. You give Claude a job description and a stack of CVs. It scores each CV against the role, ranks them, and tells you who to talk to first and why. Or it builds a role-based learning path for a new joiner.

**The outcome:** A CV-to-JD matcher that turns an afternoon of screening into a few minutes, with a clear, defensible reason for each ranking. Or a ready learning journey for a role.

**Starter prompts:**

```
Here is a job description: [paste JD]. Pull out the must-haves and the
nice-to-haves as a clear list. I'll use this to score CVs against.
Save it as jd-criteria.md.
```

```
Here are [number] CVs. Score each one against jd-criteria.md from 1 to
10. Give me a ranked table: name, score, the top reason for the score,
and one gap or flag. Be honest, don't inflate scores.
```

```
For my top 3 candidates, draft three interview questions each that
probe their biggest gap. Keep them fair and specific to the role.
```

```
Alternative: build a 90-day role-based learning journey for a new
[role] joining my team. Break it into weeks, with what they learn and
who they meet. Use my CLAUDE.md context.
```

---

### Track 6 - SAP Delivery Accelerator

**For:** SAP delivery, S4 HANA programme leads, implementation managers.

**The brief:** Pick the SAP delivery task that eats the most time in your week. Three strong options:

- **Cutover tracker**: Feed Claude your cutover task list (a spreadsheet or pasted table). It outputs a RAG-colour-coded open-items table, surfaces the critical-path blockers, and writes the cutover status paragraph for your daily call.

- **Change request classifier**: Paste a CR description. Claude outputs estimated impact (High/Medium/Low), effort band, and a draft recommendation for your CCB pack.

- **Weekly project status**: Point Claude at your project_health.xlsx (or a real file). It filters to your SAP accounts, writes the status narrative for each, and flags any accounts that moved RAG colour this week.

**The outcome:** One of these running end-to-end on a real project file. You walk out with a tool, not a demo.

**Starter prompts:**

```
Here is my cutover task list: [paste or attach file].
Read it and give me:
1. A table with every task, owner, due date, status (RAG), and a
   one-line risk note for anything that is Amber or Red.
2. The top 3 critical-path blockers in plain language.
3. A two-paragraph cutover status update I can read out on the
   morning call. Keep it factual, name the risks, do not sugarcoat.
Use my CLAUDE.md context for tone and format. Apply Bristlecone
branding using design.md.
```

```
Here is a change request: [paste CR description].
Classify it:
- Impact: High / Medium / Low — with one sentence justifying the rating.
- Effort: High / Medium / Low — your estimate, flag assumptions.
- Recommendation: Approve / Reject / Defer — with a plain-English reason.
Format this as a CCB submission table I can paste into our pack.
```

```
Here is my project data: [attach project_health.xlsx or paste rows].
Filter to the SAP service line only.
For each project:
- Write a two-sentence status narrative (what is going well, what is the risk).
- Flag any project where RAG moved from last month to this month.
- Give me a one-line summary I can use as the opener for my weekly
  delivery review.
Save the output as a Bristlecone-branded report using design.md.
```

---

## Building your own instead

If none of the five fit, build your real problem. The shape is always the same.

```
I want to build a tool for a real problem I have. Here it is:
[describe the task you do over and over].

Today it takes me [how long] and I do it [how often].

I have these to reuse: my CLAUDE.md, my design.md, and [any skills or
reports I built].

Walk me through building this step by step. Ask me what data or
reference files you need from me first. Then build it one piece at a
time so I can follow.
```

Let Claude lead. Feed it your real files. Build one thing end to end.

---

## If you get stuck: scope it down

Seventy-five minutes is short. If you're running behind, shrink the goal.

Big idea stuck? Cut it in half. Then in half again.

| If this is happening | Scope it down to this |
|---|---|
| You wanted a full bot, you're running out of time | Just build it working once, by hand, on one example. The reusable skill can wait for next week. |
| You have ten CVs and it's slow | Do three. Prove it works on three, then run the rest at home. |
| The branded PDF won't come out right | Ship it as a plain clean document first. Add branding only if time is left. |
| The data is messy and Claude is confused | Give it just one clean sample row or file. Get the output right on the small version first. |
| You can't pick a track | Pick Track 4. Almost everyone has raw content that needs to become a branded doc. It's the easiest win. |
| Claude did something you didn't ask for | Tell it plainly: "That's not what I wanted. I want [X]. Try again." It will. |

The win is **one real thing that works.** Not a perfect thing. A real thing.

If you are truly stuck, raise your hand. Someone will pair with you.

---

## How to present in 3 minutes

Near the end of the build, get ready to share. We move into feedback and testimonials right after this, so this is your moment.

You get three minutes. Keep it human and simple. Use these four lines:

1. **The problem.** "Every [week/month] I have to [the painful task]. It takes me [how long]."
2. **What I built.** "I built a [report bot / proposal helper / CV matcher / branded deck] that does it for me."
3. **Show it.** Open the actual output. The PDF, the dashboard, the ranked table. Let them see it, don't just describe it.
4. **What it saves me.** "This turns [2 hours] into [10 minutes]. I'll use it [when] starting Monday."

That's it. No slides about your slides. Show the real thing you made.

If you want a script, ask Claude:

```
Help me prep a 3-minute share of what I built today. Ask me what the
problem was, what I built, and what it saves me. Then write me four
short talking points I can read out. Keep it plain and confident.
```

---

## Checkpoint: your capstone is ready

> - [ ] You picked one project: a track or your own real problem.
> - [ ] You reused your CLAUDE.md and design.md, not started from scratch.
> - [ ] You built one thing, end to end, that actually works.
> - [ ] The output is branded or clean enough to show.
> - [ ] You have your four talking points for the 3-minute share.
> - [ ] You can name the one task this saves you, starting Monday.

---

## What you just did

You didn't finish a course this afternoon.

You built a tool for your own job. With your context, your brand, your data. On a problem that was yours.

The five tracks were just doors. You walked through one and built something real on the other side.

Monday, the task you dreaded has a helper now. Use it once. See what breaks. Fix that one thing. That's how this compounds.

---

**Next:** [Closing →](closing.md)
