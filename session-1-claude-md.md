[← Back to Student Handbook](student-handbook.md)

---

# Session 1: Your CLAUDE.md

**Day 1 - Thursday, 2 July 2026**

**Skill unlocked:** CLAUDE.md - the one file that tells Claude who you are, so every single thing you build for the rest of the bootcamp comes out sharper.

---

## What this session is

Right now Claude knows nothing about you.

It does not know you work at Bristlecone.
It does not know you run an SAP Centre of Excellence, or a delivery practice, or a pre-sales desk, or an FP&A function.
It does not know your projects, your people, or how you like your work done.

So when you ask it for anything, it guesses. The output is generic. It could be for anyone.

CLAUDE.md fixes that.

It is a plain text file that sits in your project folder. Claude reads it automatically every time you start. No special command. You build it once, and from then on every answer feels like it came from someone who has sat next to you for a year.

This is the foundation. Everything else in this bootcamp reads this file.

---

## What you will have built by the end of this session

1. Seen what Claude does **without** context (the "before").
2. A personal **CLAUDE.md** in your project folder, built one of two ways: `/work-brain`, which reads your pre-work files and drafts most of it for you, or `/interview-me`, where Claude asks you questions and writes the file from scratch.
3. Seen the **difference** context makes (the "after"). Same question, completely different answer.
4. A file rich enough that every agent you build today already knows your role, your projects, your people, your formats, and what you want automated.
5. Understood why this file makes every later session work better.

**The big idea:** every minute you spend here saves you an hour later. A thin CLAUDE.md gives thin output across everything. A rich one means the reporting bot you build this afternoon already knows your formats, and the proposal helper already knows Bristlecone's tone.

---

## First, how this works

You will not write CLAUDE.md by hand. You will not type code. You run one command, then you talk to Claude in plain English, and it writes the file for you.

If you ever want to slow the pace, two things help:

- Say `slow down` to whoever is running the room. We will wait.
- Inside either command, you can always say `slow down` to get one question at a time, `back` to redo your last answer, or `skip` to come back to a field later.

You are a senior leader at Bristlecone. You know your work cold. That is the only expertise this session needs. The typing is the easy part, and Claude does most of it.

---

## Pick one identity for the whole bootcamp

Before you start, decide one thing: **pick one professional identity and stick with it for the whole bootcamp.**

Many of you wear several hats. You might run a delivery practice and also sit on a governance council. You might lead a competency and also help with pre-sales. Pick the one hat you want your AI team built around.

If you lead SAP CoE delivery, build for that.
If you run an S4 HANA programme, build for that.
If you lead a Kinaxis practice, build for that.
If you head Data & Analytics delivery, build for that.
If you run the Resource Management Office, build for that — your week is headcount planning, utilisation, and supply-demand matching.
If you run FP&A, build for that.
If you head talent supply chain, build for that.

Everything you make today - your CLAUDE.md, your bots, your research, your writing voice - should serve the same identity. That consistency is what makes every agent stronger.

You can always build a second one after the bootcamp. Today, pick one.

---

## Getting started

You set this up in Session 0. If Claude isn't already running in your bootcamp folder, start it the same way:

1. In VS Code, make sure the `thecrux-bristlecone-bootcamp` folder is open (**File → Open Folder...** if it isn't).
2. Open a terminal: **Terminal → New Terminal**.
3. Type `claude` and press Enter.

If you can't find the folder, it's inside the `thecrux-bootcamp` folder you made in Session 0. Use **File → Open Folder...** to locate it.

---

## Before you start: drop in your pre-work files

In the pre-work (thecrux.ai/pre-work-simple) you gathered two folders on your laptop:

- `work-files/` - 8 to 10 plain text or markdown files of real work: meeting notes, email threads, project documents, reports, strategy docs.
- `writing-samples/` - 5 to 10 things you wrote: LinkedIn posts, emails, status updates, messages.

Your bootcamp folder ships with both of these as **empty** folders. Copy your pre-work files into them now. This is what lets Claude draft your CLAUDE.md from real material instead of asking you everything from scratch.

**The easy way is drag and drop.** In VS Code you can see the `work-files/` and `writing-samples/` folders in the file list down the left. Open File Explorer (Windows) or Finder (Mac), find your pre-work files, and drag them straight onto those folders in VS Code. They copy in.

**Prefer not to drag?** Just ask Claude:

```
I have my pre-work files in my Downloads folder. Copy the work files
into work-files/ and the writing samples into writing-samples/.
```

Claude will do it and ask your permission first.

**Check what landed:** open `work-files/` in the VS Code file list, or ask Claude "list the files in work-files/." If `work-files/` is empty or has only one file, that is fine - you will use `/interview-me` instead (see the next section).

A note on `writing-samples/`: today Claude uses these **lightly**, just to catch a few phrases you use and words you avoid for your voice section. The deep voice work, building a skill that writes like you, happens in Session 2. So if you only managed the work files and not the writing samples, you lose nothing major today.

---

## Pick your path (30 seconds)

Two commands. Pick the one that matches what is in your folder.

| Command | When to run it | Time |
|---|---|---|
| `/work-brain` | You dropped 2 or more files into `work-files/`. Claude reads them, drafts the facts (your role, projects, people, what you automate), and asks you the rest. | ~15 min |
| `/interview-me` | Your `work-files/` folder is empty or thin, OR you would rather talk through all seven sections by question. | ~30 min |

Both produce the **same CLAUDE.md**. Same seven sections. Same test at the end. Same save behaviour. The only difference is the on-ramp.

If you run `/work-brain` and it says "not enough files, run `/interview-me` instead", just switch commands. No drama.

---

## Part 1: The "Before" - see Claude with no context

Before we build anything, let's see what Claude does when it knows nothing about you.

Paste this into Claude Code:

```
Write me one short paragraph on what I should focus on this week
and what risks I should watch out for.
```

Read the answer. Notice how vague it is. It is guessing. It does not know you work at Bristlecone, what you run, or what is on your plate.

Keep this answer in mind. You will ask the **exact same question** again in about thirty minutes. The difference is the whole point of this session.

---

## Part 2: Build your CLAUDE.md

However you build it, your CLAUDE.md has the **same seven sections**. This is the shape both commands fill in.

| # | Section | What it captures |
|---|---|---|
| 1 | Who I Am | Your name, role, function, experience, what you own |
| 2 | What I Do All Week | Your priorities, what eats your time, what you'd hand off |
| 3 | Current Projects | Your active programmes, milestones, what's stuck |
| 4 | Key People | Your manager, your team, key contacts and sensitivities |
| 5 | How I Want Work Done | Your formats, length, what to always and never include |
| 6 | My Voice | How you sound when you write |
| 7 | What I Want To Automate | The repetitive work you want off your plate |

The two paths below build these seven sections differently. Read the one you are on. Both meet again at **The test before you save**.

---

### Path A: `/work-brain` - draft from your files

Run this if you dropped 2 or more files into `work-files/`.

Type this and press Enter:

```
/work-brain
```

Claude takes over. Here is what happens.

**1. It shows you what it found.** Claude lists your work files and tells you what it will do. There is nothing to pick - it just gets going:

```
Inventoried work-files/:
  found  weekly-status.md       (320 words)
  found  governance-notes.md    (210 words)
  found  client-email-thread.txt (180 words)
  ... etc ...

I found 6 usable work files. I'll draft the sections they cover and
ask you about anything that's missing, plus how you want work done
and your voice. Section 6 (My Voice) I'll seed lightly from your
writing samples if you have them.
```

That is the whole deal: it drafts what your files carry, then asks you about the rest. No modes, no settings.

**2. It checks your identity.** If your files show more than one hat, Claude asks which one to build for. This is the "pick one identity" rule in action.

**3. It drafts each section from your files.** For sections 1 to 4 and 7, Claude reads your files and shows you a draft, with a note on which file it came from:

```
DRAFT from weekly-status.md and governance-notes.md:
  Top priorities: "..."
  What eats my time: "..."
Source: work-files/weekly-status.md lines 3 to 11.

Confirm? (yes / edit / re-extract)
```

Three ways to respond:

- `yes` - capture and move on.
- `edit` - tell Claude what to change.
- `re-extract` - Claude re-reads the file looking for what it missed.

If your files don't cover one of those sections - say your current projects live only in your head, not in any document - Claude just asks you about it instead. It never leaves a section blank or makes one up.

Sections 5 (How I Want Work Done) and 6 (My Voice) are about your preferences, not in your files, so Claude asks you those by question. For Section 6, if you added writing samples, it pulls a few real phrases from them for you to confirm.

**4. A word on privacy.** Your work files have real client and colleague names in them. Claude **does not** copy those straight into your CLAUDE.md. It swaps them for roles or initials and flags each one, so the file is safe to share. You will see things like `{a consumer-goods client}` instead of the real name. That is deliberate. We cover data handling properly in Session 4.

Once Section 7 is confirmed, jump to **The test before you save** below.

---

### Path B: `/interview-me` - talk it through

Run this if your `work-files/` folder is empty or thin, or you would rather answer questions.

Type this and press Enter:

```
/interview-me
```

That is it. Claude takes over from here. It will:

1. Tell you what you are building and ask if you are ready.
2. Start with **who you are**, then show you a one-line "persona snapshot" so you can confirm it understood you.
3. Walk you through the seven sections, two or three questions at a time, in the language of your function.
4. Run the test at the end and save the file.

Spend about **fifteen minutes** answering. Answer with **real specifics from your actual work.** The more real you are, the better everything else performs today.

**Stuck on what to say?** Think about last Tuesday. What did you do? What took too long? What status report did you have to pull together? Who pinged you for an update? That is your raw material.

#### How to give good answers

The interview is only as sharp as what you tell it. Two rules.

**Use real names and real numbers.**

Weak: "I run delivery for some accounts."
Sharp: "I run delivery excellence across 6 active SAP transformation programmes, the biggest being a consumer goods client mid-rollout, with a governance review due the last week of every month."

**Be concrete about the work you want off your plate.**

Weak: "Reporting takes time."
Sharp: "Every Monday I spend two hours pulling a status deck from six project trackers. I want that done for me."

The more specific you are, the more Claude can actually do for you this afternoon without you re-explaining.

#### Shortcuts you can use mid-interview

You can say any of these at any time:

| Say | What it does |
|---|---|
| `back` | Go back to your last answer and change it. |
| `skip` | Leave a question for later. Claude marks it as a TODO. |
| `example` | Ask Claude to show you one example answer for the current question. |
| `draft it` | Have Claude take a guess based on what you've said so far, with its guesses marked clearly so you can correct them. |
| `slow down` | Claude will ask one question at a time instead of two or three. |
| `stop` | End the interview. Claude saves what you have so far, with TODOs for the rest. |

Once you have confirmed all seven sections, continue to **The test before you save** below.

---

### The test before you save (both paths)

Before it saves anything, Claude runs one quick test. Same drill on both paths.

Using only what is now in your file, Claude drafts a short note to your manager on this week's top risk on your biggest project, in your format and your voice. Then it asks:

> "Score it 1 to 5. 1 = generic, could be any consultant. 5 = I could send this Monday. What would you tighten?"

If you score it **3 or below**, Claude asks which section to fix. It is almost always Section 5 (How I Want Work Done), Section 3 (Current Projects), or Section 6 (My Voice). You edit, Claude re-runs the test. Two tries. A 3 is workable for Day 1.

If you score it **4 or 5**, that is the bar. Claude shows you the full file and asks to save. Say `yes`, and your CLAUDE.md is written.

---

## Part 3: The "After" - see the difference

Your CLAUDE.md is written. Now see what changed.

Start a fresh session so the file loads cleanly. Type `/quit`, then type `claude` again to restart it.

CLAUDE.md loads automatically. You do not have to do anything.

Now ask the **exact same question** from Part 1:

```
Write me one short paragraph on what I should focus on this week
and what risks I should watch out for.
```

Compare it to the answer you got in Part 1.

Same question. Completely different answer. The second one names your projects, your deadlines, your actual risks. It reads like it came from someone on your team.

**That is the power of context.** Claude did not get smarter. You gave it your brain.

---

## A worked example - what a rich CLAUDE.md looks like

Here is a finished CLAUDE.md for a made-up Bristlecone leader. She is not real. Use her as a shape to aim for, not a script to copy. Yours should be about your actual work.

```markdown
# CLAUDE.md - Priya Deshpande

## Who I Am
- Name: Priya Deshpande
- Role: Head of Delivery Excellence, Bristlecone (Mahindra Group)
- Function: Delivery Excellence / Governance
- 22 years in supply chain and SAP consulting. 7 of them at Bristlecone.
- I own delivery quality and governance across our active SAP-led
  supply chain transformation programmes.

## What I Do All Week
- Keep delivery quality high across every live programme.
- Run the monthly governance review with programme managers and account leads.
- Step in when a programme slips - re-plan, re-staff, reset the client.
- Coach programme managers. A lot of my value is in the room, not the deck.

The work that eats my time: pulling status across six trackers, prepping
governance decks, and chasing updates. I'd hand all of that off tomorrow.

## Current Projects
- Consumer goods client, SAP S/4 rollout. Mid-build. UAT starts end of
  June. This is my biggest risk right now - timeline is tight.
- Auto components client, supply chain planning module. Going well. Steady.
- Internal: rebuilding our delivery governance checklist so every
  programme runs to the same standard. Stuck on getting PMs to adopt it.

## Key People
- Rajesh Nair - my VP. Wants early warning on slippage, not surprises.
  Likes a one-page risk summary, no padding.
- My six programme managers - they come to me when a plan breaks or a
  client gets tense. I unblock and coach.
- Client delivery head at the consumer goods account - anxious about the
  UAT date. Needs steady, confident communication.

## How I Want Work Done
- Tables for status. Bullets for everything else. Rarely long paragraphs.
- Crisp. One page beats five. Lead with the recommendation.
- Always include: owners, dates, the top three risks, a clear next step.
- Never: fluff, hedging, "it depends" without a view, long preambles.
- Tone: client-ready and calm for external, fast and blunt for internal.

## My Voice
- Direct and calm. I do not soften bad news, I frame it with a next step.
- Phrases I use: "early warning", "one-pager", "what's the ask", "next step".
- Words I never use: "synergy", "leverage" as a verb, "circle back", filler.

## What I Want To Automate
- Weekly status roll-up across six programme trackers into one deck.
  Takes me ~2 hours every Monday.
- Monthly governance pack prep. Half a day, every month.
- First-draft risk summaries for Rajesh before each review.
```

Notice what makes it good. Real names. Real numbers. A clear view on what she wants and refuses. A stranger reading this could brief her team for her. That is the bar.

---

## Part 4: Why this matters for the rest of the bootcamp

Read your finished file back, and ask Claude how it changes the work:

```
Read my CLAUDE.md back to me. Then tell me: based on this, how would you
help me if I asked you to draft a status report? A client proposal? A
governance summary? What would you do differently for me versus a
generic user?
```

This is the frame for everything that follows.

Every agent and skill you build in this bootcamp reads this file. When your reporting skill uses your exact format, it is because of CLAUDE.md. When your proposal helper sounds like Bristlecone and not a textbook, it is because of CLAUDE.md. When your governance summary leads with the risk, like you do, it is because of CLAUDE.md.

**The better this file, the better your whole AI team.**

---

## What makes a great CLAUDE.md

A vague file gives vague output. A specific one gives output that feels like a colleague who knows your world.

| Level | What it looks like | What Claude does with it |
|---|---|---|
| **Weak** | "I work in delivery at Bristlecone." | Generic delivery advice. Could be anyone. |
| **Better** | "I run delivery excellence across our SAP transformation programmes." | Tailored to your function and industry. |
| **Great** | Same, plus: real project names, real deadlines, your manager and what he wants, your formats, what you refuse to see. | Output that reads like it came from your own team. |

---

## If you finish early

Push the file further. Try any of these.

### Stress-test it with a real task

```
Using only what's in my CLAUDE.md, draft a short note to my manager on
this week's top risk on my biggest project. Mark anything you're
guessing in {curly braces}.
```

If it sounds generic, the section it pulled from is too thin. Fix that section, run it again.

### Have Claude critique its own work

```
Read my CLAUDE.md. Tell me three things that are still too vague, and
three places where I gave you good detail that'll make later builds
sharper. Be honest.
```

### Add "What I Offer" for the personal-brand work later

```
Add a "What I Offer" section to my CLAUDE.md. Ask me what people at
Bristlecone come to me for, the experience I bring that's hard to find,
and the problems I solve that others struggle with. Then update the file.
```

### Compare with a neighbour

Share your CLAUDE.md with the person next to you. What did they put in that you didn't? Steal the good ideas.

---

> **Checkpoint: your CLAUDE.md is ready**
>
> - [ ] CLAUDE.md saved at the root of your project folder
> - [ ] It has: who you are, your role at Bristlecone, projects, key people, how you want work done, your voice, what you want to automate
> - [ ] You ran the before/after test and saw the difference
> - [ ] You read the whole file and it sounds like you, not a brochure
> - [ ] You understand every later build reads this file

---

## Troubleshooting - Session 1

| Issue | Fix |
|---|---|
| `/work-brain` says "not enough files" | Your `work-files/` folder has fewer than 2 usable files. Either drop more pre-work files in, or run `/interview-me` instead. Same destination, ~30 min. |
| `/work-brain` or `/interview-me` not recognised | Make sure the `thecrux-bristlecone-bootcamp` folder is the one open in VS Code, then start Claude in a terminal there. The commands live in `.claude/commands/`. If it still does not work, use the manual fallback at the bottom of this page. |
| `/work-brain` drafted the wrong facts | Type `re-extract` to make it re-read the file, or `edit` and tell it what to change. If the file just is not carrying enough, it will switch to asking you questions for that section. |
| It kept the real client name in my file | It should mask them. If you see a real name you want hidden, say "mask {that name} as a role". By default it generalises client and employee names. |
| I can't find my project folder | In VS Code use **File → Open Folder...** and pick `thecrux-bristlecone-bootcamp` (it's inside the `thecrux-bootcamp` folder you made in Session 0). |
| `claude` does nothing or "not recognised" | Close the terminal panel, open a new one (**Terminal → New Terminal**), and type `claude` once more. If still nothing, raise your hand. |
| The before/after test shows no real difference | Your CLAUDE.md is probably too vague. Add real project names, real deadlines, real people. Specifics are what make the difference show up. |
| Claude is asking too many questions at once | Type `slow down` or `one at a time`. It will go field by field. |
| The example answer doesn't fit my role | Ignore it. Answer in your own words. The example is just a hint at the shape. |
| Claude wrote the wrong function for me | Correct it plainly: "I run FP&A, not delivery. Rewrite that part." It will fix it. |
| CLAUDE.md came out too short | Run the "critique its own work" prompt from "If you finish early", then answer its questions. |
| The session crashed or my laptop slept midway | Start Claude again and re-run the same command. It finds your `CLAUDE.draft.md` and offers to resume where you left off. |

---

## Manual fallback - if neither command is available

If the commands do not run for any reason, you can do the same thing by pasting this prompt into Claude Code:

```
I want to create my personal CLAUDE.md file. Save it at the root of this
project. It will tell you who I am so every future conversation is about me,
not a generic user.

I work at Bristlecone, a supply-chain consulting and technology firm, part of
the Mahindra Group. Interview me to build my CLAUDE.md. Ask me 2 to 3
questions at a time, in plain language, and wait for my answers before the
next batch. Cover these seven sections, then write the file and show it to me:

1. WHO I AM - name, role/title, function I run, years of experience, what
   I'm responsible for.
2. WHAT I DO ALL WEEK - top 2 to 3 priorities, what eats my time, what I
   wish was off my plate.
3. CURRENT PROJECTS - active programmes by name, stage and next milestone,
   what's going well and what's stuck.
4. KEY PEOPLE - my manager and what they want, my team, key client contacts
   and sensitivities.
5. HOW I WANT WORK DONE - bullets/tables/paragraphs, length, what to always
   include (owners, dates, risks, a recommendation), what to never include.
6. MY VOICE - how I sound, words I use, words I never use.
7. WHAT I WANT TO AUTOMATE - the repetitive tasks, how long each takes, the
   one that would save me the most time.

I am a senior leader but new to tools like this, so keep it plain.
```

---

**Next:** [Session 2: Skills →](session-2-skills.md)
