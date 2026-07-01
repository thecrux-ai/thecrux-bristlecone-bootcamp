[← Back to Student Handbook](student-handbook.md)

---

# Session 2: Skills

**Day 1 - Thursday, 2 July 2026**

**Skill unlocked:** Skills - reusable `/slash-commands` that bottle a job you do over and over, so you never have to explain it to Claude twice.

---

## What this session is

In Session 1 you taught Claude who you are. Now you teach it how you work.

Think about the things you do again and again at Bristlecone.

A weekly status report in the same shape every time.
A statement of work that always has the same sections.
A governance check that always asks the same questions.
A hiring shortlist filtered the same way.

Right now, every time you want one of those, you explain it to Claude from scratch. The format. The tone. The sections. The rules. That works, but it is slow, and you say the same thing a hundred times.

A **skill** fixes that.

A skill is a small file that holds your instructions for one repeatable job. You write it once. Then you call it with a short command like `/report` or `/sow`, and Claude does the job exactly the way you taught it. Every time. No re-explaining.

By the end of this session you will have built two of your own. One that writes in your voice. One that does a core task in your role.

---

## What you will have built by the end of this session

1. Understood what a skill is and where it lives.
2. Pulled out your **writing voice** from real samples you wrote.
3. Built a **Comms Lead** skill at `.claude/skills/comms-lead/SKILL.md` that writes anything in your voice.
4. Built a **second skill** for your role: `/report`, `/sow`, `/governance-check`, or similar.
5. Tested both with a real command.
6. Seen the skills marketplace, so you know there are ready-made skills you can grab off the shelf for Day 2.

**The big idea:** a skill turns a thing you explain over and over into a thing you call with one word. The hour you spend building it today saves you that explanation every week for the rest of the year.

---

## First, how this works

You will not write these skill files by hand.

You describe what you want in plain English. Claude writes the file. You test it. If it is off, you tell Claude what to fix, and it edits the file for you.

That is the whole loop. Describe, test, correct. No code. No syntax to memorise.

To slow the pace, say `slow down` to whoever is running the room. Nobody moves to the second skill until everyone has the first one working.

---

## Getting started

You should still have the `thecrux-bristlecone-bootcamp` folder open in VS Code from Session 1. If Claude isn't running:

1. Make sure that folder is open (**File → Open Folder...** if not).
2. Open a terminal: **Terminal → New Terminal**.
3. Type `claude` and press Enter.

---

## Part 1: What a skill actually is (2 min - read, don't type)

Claude Code has a built-in **skills system**. A skill is just a small text file with instructions for one job.

The files live in a folder called `.claude/skills/`. Each skill gets its own folder, and inside it a file called `SKILL.md`. So a skill called `report` lives at:

```
.claude/skills/report/SKILL.md
```

Here is what a simple `SKILL.md` looks like inside. You do not type this. You are just seeing the shape:

```yaml
---
name: report
description: Writes my weekly delivery status report in my standard format. Use whenever I ask for a status update, weekly report, or steering note.
---

When I give you raw notes, turn them into my weekly report in this exact shape:

1. RAG status (Red / Amber / Green) for the engagement, with one line of why.
2. Top 3 risks, ranked, each with an owner and a date.
3. Milestones hit this week.
4. Milestones at risk, with the recovery action.
5. Asks of the steering committee.

Keep it tight. Use the project names and people from my CLAUDE.md.
```

Two parts matter:

- The **name** is the command. `name: report` means you call it by typing `/report`.
- The **description** tells Claude when this skill is useful. A good description means Claude can even pick the skill up on its own when you ask for a report, without you typing the slash command.

Skills can live in two places:

- **Project skills** live in this project's `.claude/skills/` folder. They work only here. Good for one client or one project.
- **Personal skills** live at `~/.claude/skills/`. They follow you into every project. Good for things you do everywhere, like writing in your voice.

Today you build project skills. After the bootcamp you can promote the ones you love to personal skills so they follow you everywhere.

That is the whole concept. Now you build one.

---

## Part 2: Build your Comms Lead - a skill that writes in your voice

Your first skill is a writer. Not a generic AI writer. One that sounds like **you**.

This is the most useful skill most leaders build in this bootcamp. Every email, every LinkedIn post, every client note, every internal update - all of it can come out in your voice, at your best, in seconds.

### Step 1: Point Claude at your writing samples

You brought 5 to 10 things you wrote as pre-work. Emails to clients, status reports, LinkedIn posts, meeting follow-ups. If you have not put them in a folder yet, ask Claude:

```
Create a folder called writing-samples in this project.
```

Now drop your files in there. Any format works. Word docs, PDFs, plain text, or just paste the words into a text file. Name them whatever you like. Claude reads everything.

> **Did not bring samples?** Open your Outlook, Teams, or LinkedIn right now. Copy 5 to 7 messages you actually wrote into separate text files in the `writing-samples` folder. Takes 3 minutes. Use real ones you wrote, not things colleagues sent you.
>
> If you genuinely cannot pull anything of your own, paste any 3 to 5 messages you have sent recently on any topic. Real is always better than nothing.

### Step 2: Pull out your voice DNA

Paste this:

```
Read every file in the writing-samples folder. These are all written by me.

Analyse my writing voice across all of them. Tell me:

1. TONE. Am I formal, casual, or in between? Does it change by context?
2. SENTENCE STRUCTURE. Short and punchy, long and flowing, or mixed?
3. VOCABULARY. Words or phrases I lean on. Jargon I use.
4. QUIRKS. Do I use dashes, brackets, lists? Do I lead with the point
   or build up to it?
5. RHYTHM. How do I open a message? How do I close it?
6. WHAT I NEVER DO. Formal sign-offs? Over-hedging? Corporate filler?

Be specific. Quote real lines from my samples.

Save this as a voice profile to writing-samples/voice-profile.md, and
also show it to me here so we can fix anything that is off.
```

Read the output. Does it sound like you? If something is wrong, say so:

```
That is not quite right. I am actually more [describe how].
Look at [name the file] again, then update voice-profile.md.
```

Iterate once or twice until it feels true.

### Step 3: Turn the voice profile into a skill

```
Turn the voice profile at writing-samples/voice-profile.md into a Claude
Code skill called "comms-lead".

Create it at .claude/skills/comms-lead/SKILL.md

The skill should:
- Have a clear description so Claude knows to use it for any writing task
  in my voice.
- Write in my voice for any topic or brief I give it.
- Match my tone to the format. A client email sounds different from an
  internal Teams note, which sounds different from a LinkedIn post.
- NEVER use phrases or patterns I never use. List them in the skill file
  so the rule is explicit.
- When unsure, default to my most common style.
- Produce writing in my voice without me having to point at any other file.

Use proper YAML frontmatter (name, description) and a markdown body.
```

When it is done, Claude tells you the file is created.

### Step 4: Test it

You do not even need the slash command. Because the description is clear, Claude picks the skill up on its own. Just ask:

```
Write a short email to my client sponsor updating them on where my
current engagement stands, what is next, and what I need from them.
```

New skills usually load on their own. If Claude doesn't seem to know about it yet, run `/reload-skills`, or just close and reopen Claude Code.

Read it out loud. Does it sound like something you would actually send? If a phrase is off, fix it once:

```
Close, but [the thing that sounds wrong].
Update .claude/skills/comms-lead/SKILL.md so it stops doing that.
```

### Step 5: Drop a short version into CLAUDE.md as a safety net

The skill is strong, but it has two limits.

1. It lives in **this project only**. Open Claude in a different folder next week and the skill is not there.
2. It mainly fires for proper writing tasks. If you ask for "a quick one-line Teams reply" in passing, it might not load.

CLAUDE.md covers both gaps. It loads in every session, in every project where it lives. So we put a short version of your voice in there too.

```
Add a section to my CLAUDE.md called "## My Writing Voice" with a short
summary of my voice. The 5 or 6 patterns that matter most.

Keep it tight. It should be enough for any future Claude session to write
roughly in my voice even without the full comms-lead skill.
```

Now the skill does the heavy, careful writing. CLAUDE.md carries your voice everywhere else, including the reporting bot you build later today, which runs Claude in the background and cannot type a slash command.

---

## Part 3: Build a skill for your role

Your Comms Lead handles voice. Your second skill handles **a job you actually do**.

Pick the one option below that fits your role at Bristlecone. Read the others if you like, but build one. Get it working before you start a second.

Each one follows the same pattern. You describe the exact shape you want, the rules it must follow, and the things it must never do. Claude writes the file.

### Option A - `/report` (delivery, SAP CoE, PMO)

For anyone who sends a weekly status or steering note.

```
Build a skill called "report" at .claude/skills/report/SKILL.md

It takes my raw notes (typed in, or a file path) and turns them into my
weekly engagement report in this exact shape:

1. RAG STATUS. Red, Amber, or Green for the engagement, with one line of why.
2. TOP 3 RISKS. Ranked. Each one in a single sentence, with an owner and a
   target date.
3. MILESTONES HIT this week.
4. MILESTONES AT RISK, each with the recovery action and a date.
5. ASKS of the steering committee. What I need, from whom, by when.

Rules the skill must enforce:
- Every risk and every milestone has a date. "Soon" is not a date.
- Never invent a number, a date, or a status. If something is missing
  from my notes, flag it in {curly braces} so I can fill it in.
- Use the project names and people from my CLAUDE.md.
- No filler, no restating my notes back to me. Just the report.

Use proper YAML frontmatter (name, description) and a markdown body.
```

### Option B - `/sow` (pre-sales, GTM, delivery leads)

For anyone who writes statements of work or proposal sections.

```
Build a skill called "sow" at .claude/skills/sow/SKILL.md

It takes a short brief from me (client, scope, the problem they have) and
drafts a statement of work section in Bristlecone's standard shape:

1. BACKGROUND. The client's situation in 3 to 4 lines.
2. OBJECTIVES. What this engagement delivers, as bullet outcomes.
3. SCOPE. In scope and, just as important, out of scope.
4. APPROACH. The phases, with a one-line description each.
5. DELIVERABLES. A clear list, each one named.
6. ASSUMPTIONS AND DEPENDENCIES. What must be true for this to work.

Rules the skill must enforce:
- Always include an "out of scope" list. Most disputes come from a missing
  one.
- Never invent commercials, timelines, or headcount. If I have not given a
  number, flag it in {curly braces}.
- Tone: professional, plain, confident. No marketing fluff.
- Use Bristlecone's positioning where it fits: supply-chain consulting and
  SAP-led transformation.

Use proper YAML frontmatter (name, description) and a markdown body.
```

### Option C - `/governance-check` (governance, delivery excellence, quality)

For anyone who runs audits, gate reviews, or compliance checks.

```
Build a skill called "governance-check" at
.claude/skills/governance-check/SKILL.md

It takes details of a project or engagement and runs it through my standard
governance checklist. For each item it gives a clear PASS, GAP, or NEEDS
INFO, with one line of evidence or what is missing.

Check these areas:
1. Scope and change control. Is scope baselined? Is there a change log?
2. Risk and issue management. Is there a live risk register with owners?
3. Status reporting. Is reporting current and going to the right people?
4. Resourcing. Are key roles filled? Any single points of failure?
5. Financials. Is the engagement tracking to budget?
6. Stakeholder sign-off. Are the right approvals in place?

Rules the skill must enforce:
- End with a SUMMARY: count of PASS, GAP, and NEEDS INFO, plus the top 3
  things to fix first, ranked by risk.
- Never assume a control exists. If I have not confirmed it, mark it
  NEEDS INFO, not PASS.
- Plain language. This gets read by a steering committee, not auditors.

Use proper YAML frontmatter (name, description) and a markdown body.
```

### Option D - `/summarise` (HR, finance, anyone drowning in long documents)

For anyone who reads long reports, transcripts, or policy docs and needs the gist fast.

```
Build a skill called "summarise" at .claude/skills/summarise/SKILL.md

It takes any long input (a file path or pasted text) and produces:

1. THE GIST. 3 to 4 lines. What this document is and why it matters to me.
2. KEY POINTS. The 5 to 7 things I must know, as bullets.
3. DECISIONS AND ACTIONS. Anything that needs a decision or an action,
   with who owns it if the document says.
4. WHAT TO WATCH. Risks, red flags, or anything that needs follow-up.

Rules the skill must enforce:
- Never add information that is not in the source. If I need to know
  something the document does not say, note it under "What to watch".
- Keep the whole thing under one page.
- Plain language. Assume I am skimming this between meetings.

Use proper YAML frontmatter (name, description) and a markdown body.
```

### Test your skill with something real

Whichever you built, test it now with real, messy input. For example, for `/report`:

```
/report on this:

SAP S/4 rollout for the client, week 9. UAT started Monday, 40 of 60
test scripts passed. Two integration defects open on the order-to-cash
flow, one of them severe. Cutover is still pencilled for end of July but
the data migration dry run slipped a week. The client wants a go/no-go
call by Friday.
```

Read the output. Does it match the shape you asked for? Every risk dated? Anything missing flagged in `{curly braces}` instead of invented? If something is off, push back once and have Claude tighten the `SKILL.md`:

```
You invented a date I did not give you. The skill says flag missing
items in curly braces. Fix the output, and make that rule harder to
miss in SKILL.md.
```

That correction loop is the real skill you are learning. Build, test, correct. The file gets a little smarter every time.

### Another way to build a skill: `/skill-creator`

So far you have built skills by typing out the full instruction yourself. There is a second way, and it is even easier. Claude Code comes with a built-in skill called **`/skill-creator`** whose only job is to help you build other skills.

Instead of writing the whole prompt, you just start it and talk:

```
/skill-creator
```

Then tell it, in plain English, what you want. For example:

```
/skill-creator

I want a skill called "report" that turns my rough notes into my weekly
engagement report. It should have RAG status, top 3 risks with owners and
dates, milestones hit, milestones at risk, and asks of the steering
committee. It must never invent a date, and it should flag anything
missing in curly braces.
```

`/skill-creator` then does the work with you. It asks a few questions to get the shape right, writes the `SKILL.md` file for you, and can even help you test it and tighten it. It is the same build, test, correct loop, just guided.

This works for any of the four options above. Pick the one that fits your role, type `/skill-creator`, and describe it the same way the prompt does. Both ways end with a working skill in `.claude/skills/`. Use whichever feels more natural to you.

> **New to the skill not showing up?** `/skill-creator` saves the file for you, and new skills usually load on their own. If Claude doesn't seem to know about it yet, run `/reload-skills`, or just close and reopen Claude Code.

---

## Part 4: See the skills marketplace

You just built two skills from scratch. You can also grab ready-made ones off the shelf.

- **`/plugin`** opens the official Anthropic marketplace inside Claude Code. Bundles like `document-skills` (Word, PowerPoint, PDF, Excel, and `frontend-design`) install in one command. You will want some of these tomorrow when you build things that produce a deck or a Word doc.
- **`/skills`** shows what you already have available, any time.
- **[skills.sh](https://skills.sh/)** is a community directory with install counts and a leaderboard. You install from there with `npx skills add <owner/repo@skill>`. It is a third-party tool. It works well, but it is not officially part of Claude Code.

**Install the design skill now, ready for Day 2.** Tomorrow you build a real web page. The `frontend-design` skill gives Claude strong design sense. Install it now so it is ready:

```
/plugin marketplace add anthropics/claude-code
/plugin install frontend-design@anthropics-claude-code
/reload-plugins
```

Your instructor will demo the `/plugin` menu live. Follow along.

**The frame:** some skills you build yourself, some you grab off the shelf. Every skill you add makes Claude more useful for the specific work you do at Bristlecone.

---

## Bonus: if you finish early

Build a third skill. Pick a job you did this past week that you will do again.

- HR: a `/shortlist` skill that scores CVs against a role you define.
- Finance: a `/variance` skill that explains budget-versus-actual in plain language.
- Consulting: a `/discovery` skill that turns a kick-off call into a structured findings note.
- Anyone: a `/email` skill that drafts replies in your voice with a subject line.

Same loop every time:

```
Build a skill called "[name]" at .claude/skills/[name]/SKILL.md

It should [what it does], in this exact shape: [the sections you want].

Rules it must enforce: [your non-negotiables].
Things it must never do: [your hard nos].

Use proper YAML frontmatter (name, description) and a markdown body.
```

Some leaders end the day with four or five skills. A voice, a report, an SOW, a summary, a checklist. That is a small AI team that does your repeatable work the way you do it.

---

> **Checkpoint: your skills folder grows**
>
> - [ ] Writing samples in the `writing-samples` folder
> - [ ] Voice DNA pulled out to `writing-samples/voice-profile.md`, and it sounds like you
> - [ ] Comms Lead skill at `.claude/skills/comms-lead/SKILL.md`
> - [ ] Comms Lead output sounds like you, you could send it with light edits
> - [ ] "My Writing Voice" section added to CLAUDE.md
> - [ ] A second skill built for your role (`/report`, `/sow`, `/governance-check`, or `/summarise`)
> - [ ] The second skill tested on real input, produces the shape you asked for, no invented numbers
> - [ ] Skills marketplace browsed, `frontend-design` installed for Day 2
> - [ ] At least one working custom skill in `.claude/skills/`

---

## Troubleshooting - Session 2

| Issue | Fix |
| --- | --- |
| No writing samples | Open Outlook, Teams, or LinkedIn. Copy 5 to 7 messages you wrote into text files in the `writing-samples` folder. Takes 3 minutes. |
| Voice profile does not sound like you | Tell Claude: "That is not quite right. I am actually more [describe]. Look at [name the file] again, then update voice-profile.md." |
| Claude does not seem to pick up the skill on its own | Open `.claude/skills/[name]/SKILL.md` and check it has a clear `description:` line. The description is how Claude knows when to use the skill. |
| `/skill-name` does not load the skill | Check the YAML frontmatter at the top. The `name` field must exactly match the folder name. Then run `/reload-plugins`, or close and reopen Claude Code. |
| I cannot see the `.claude` folder on Windows | It is a hidden folder. Ask Claude: "List the files in my .claude/skills folder so I can see what is there." You do not need to open it in File Explorer. |
| Output is too generic | Your skill or your CLAUDE.md is too vague. Add real examples and real rules. "Like this: [paste a real example]" works far better than abstract instructions. |
| The skill invents numbers or dates | Tell Claude: "You added a number I did not give you. The skill says flag missing items in curly braces. Fix the output, and strengthen that rule in SKILL.md." |
| The skill skipped one of my rules | Tell Claude: "You ignored [the rule]. Re-do the output, and rewrite that rule in SKILL.md so it is harder to miss." |
| I built the wrong skill for my role | No harm done. Just build the right one. Old skill files do nothing until you call them. |
| Everything feels too fast | Say `slow down` to the room. We wait for everyone to get one skill working before moving on. |

---

**Next:** [Session 3: Workflows and Agents →](session-3-workflows-agents.md)
