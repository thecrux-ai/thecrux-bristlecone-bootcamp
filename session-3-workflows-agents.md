[← Back to Student Handbook](student-handbook.md)

---

# Session 3: Workflows and Agents

**Day 1 - Thursday, 2 July 2026**

**Skills unlocked:** Workflows, parallel subagents, structured synthesis, devil's-advocate critique, flagging assumptions, and building your own reusable agent with `/agents`

---

## The Big Idea

So far you have worked with one Claude at a time. One question, one answer. This session adds two new tools to your kit.

**Workflows.** A workflow is a recipe. Many steps, run in order, often with several agents working at the same time, ending in one clean output. You design the recipe once. Then you run it again and again. Today's research team is your first workflow: you define a team, run them in parallel, pull the findings into one synthesis, then stress-test it.

**Agents.** An agent is a specialist worker. One job, its own brief, ready when you call it. In the research workflow Claude spins up agents on the fly and throws them away when it's done. But you can also build your own agent, give it a name, and save it. Then it shows up every time you need it. Claude Code has a built-in command for this: `/agents`. You will build one before you leave.

Here is the simplest way to hold the two apart. A **workflow** is the recipe. An **agent** is a worker the recipe can call. Today you run a workflow (research), then you hire a worker of your own (an agent).

**The plan:**

- **Part A - Your Research Workflow.** A few agents work in parallel. Each owns a different angle. Together they produce one synthesis saved to a `research/` folder.
- **Part B - The Critique Pass.** A devil's advocate and a skeptic read the synthesis. Their job is to find what is weak before you put it in front of anyone.
- **Part C - Make the Workflow Reusable.** You save the team as a template. Next time you have a question, you brief the team again in two minutes.
- **Part D - Build Your Own Agent.** You use `/agents` to create a named specialist for your real work, and test it.

One thing to hold onto through Parts A to C. Secondary research gives you hypotheses, not answers. The agents read what is public on the web. They do not have Bristlecone's internal numbers. So everything they hand you is a starting point to check, not a finished truth. Part B exists for exactly this reason.

---

## Before You Start

You are on Windows. A few quick checks so nothing trips you up.

**1. You are in the right folder.**

You should already be inside your project folder from earlier sessions. If you are not sure, ask Claude:

```
What folder am I working in right now? List the files and folders here.
```

If you see your `CLAUDE.md` file in the list, you are in the right place. If not, tell your facilitator before you go further.

**2. Web access works.**

The agents search the web to find current information. If web search is off, they will still run, but they will only use what they learned in training, which stops in early 2026. For a question about the 2026 market, that is not good enough.

Test it now. Paste this:

```
Search the web for "supply chain consulting market 2026" and show me
3 results with their links.
```

**If you get three results with links:** web access works. Move on.

**If Claude says it cannot search the web:** type `/permissions` in Claude Code and add `WebSearch` and `WebFetch`. Then run the test search again. If you are stuck, raise your hand. Do not skip this. A failed web search part-way through gives you empty findings and no error message, which is hard to spot later.

---

## Part A: Your Research Workflow

This is a workflow: a recipe that runs several agents in parallel, then pulls their work into one place. Research is just the example. Once you have seen the shape, you can point the same recipe at any question.

### Two ways to use agents

Claude Code can spin up **subagents**. These are separate Claude instances. Each one handles a piece of a bigger job. There are two ways to use them, and the difference matters.

**Let Claude decide.**
You give Claude a big task. Claude splits the work however it wants. How many agents, what each does, who covers what. You do not control it. Sometimes that is fine. Often it is unfocused.

**You define the team.**
You tell Claude exactly who is in the room. "I want a Market Analyst, a Competitor Tracker, and a Risk Assessor. Here is what each one does. Go." You are the manager. Claude staffs and runs the team you designed.

For research, define the team yourself. Here is why. Research quality depends on framing. A generic "research this topic" prompt gives you generic output. But when you say "I need someone profiling the top competitors AND someone finding the whitespace nobody is serving," each agent goes deep on its lane. The final report is sharper because the inputs were sharper.

Today you are the team lead. You pick the agents. You define their jobs. Claude does the legwork.

---

### Step 1: The Research Question

For this session, the question is pre-set. It is built for the work you do at Bristlecone - supply-chain consulting and SAP-led transformation.

```
Where is the next wave of demand heading in supply-chain consulting
and SAP S/4HANA transformation services through 2026 to 2028, which
competitors are winning that work and how, and where is the whitespace
a mid-size specialist firm could credibly own?
```

This is a real question. It is the kind of thing a strategy or practice lead would spend two or three days on. It needs a market view, a competitor view, a client-demand view, and a hard look at the risks. Perfect for a team.

> **Want to use your own question instead?** That is fine, and often better. Good options for your world:
>
> - A competitor scan: "How are Accenture, Deloitte, and the SAP-focused boutiques positioning their supply-chain transformation offers in 2026, and where do they differ?"
> - An opportunity assessment: "What is the demand outlook for supply-chain control-tower and planning work in [a sector you know], and what does a buyer actually want?"
> - A client-account brief: "What is going on at [a real or named target account] right now - their supply-chain priorities, recent moves, and likely pain points?"
> - A capability or whitespace scan: "Where in the SAP services market is demand growing faster than supply, and what capability would a firm need to win there?"
> - **For EP-Kinaxis**: "What is the demand outlook for Kinaxis Rapid Response and supply-chain planning implementations through 2027, which system integrators are winning these engagements and why, and where is the whitespace for a specialist consulting firm?"
>
> Pick something you would actually research at work. Specific enough to act on. Broad enough to need more than one angle. Replace the question wherever it appears in the prompts below.

---

### Step 2: Define Your Research Team

Four agents. Each owns a distinct angle. No overlap.

For the pre-set question, this is a strong team:

| Agent | Focuses on |
| --- | --- |
| **Market Analyst** | Size and growth of the supply-chain consulting and SAP S/4HANA services market through 2028. Which segments are growing fastest. The 2027 SAP ECC support deadline and what it means for demand. Named numbers and named sources wherever possible. |
| **Competitor Tracker** | Who is winning this work and how. The big firms (Accenture, Deloitte, IBM, Capgemini, Infosys, TCS, Wipro) and the SAP-focused specialists. Their positioning, their named offers, where each is strong and where each is thin. |
| **Client Demand Researcher** | What buyers actually want. Which industries are spending. The real pain points behind the spend (resilience, planning, cost, ESG reporting). What makes a buyer pick a specialist over a Big Four firm. |
| **Whitespace and Risk Assessor** | Where demand is outrunning supply - the gaps a mid-size firm could own. AND the risks: where the market could soften, where the big firms could crush a smaller player, what could go wrong with the whitespace bet. |

> **You can change this team.** Swap an agent. Add one. If your question is a single-account brief, you might want a "Recent News and Signals" agent and a "Stakeholder and Org" agent instead. The rule stays the same: each agent has a clear, non-overlapping job that serves your question.

Write your team down before you launch. If you are using your own question, fill these in:

- Agent 1: __________ - focuses on __________
- Agent 2: __________ - focuses on __________
- Agent 3: __________ - focuses on __________
- Agent 4: __________ - focuses on __________

---

### Step 3: Quick Share

Take 30 seconds. Say your research question out loud to the person next to you. Just one sentence.

Hearing someone else's question sharpens your own. You will often notice yours is too broad, or too vague, the moment you have to say it out loud.

---

### Step 4: Launch Your Research Workflow

This is the main build. One prompt. Copy it, fill in your name where shown, and paste it into Claude Code.

If you are using your own question, replace the question and the four agent descriptions with yours.

```
Here's what I need you to do. Read this entire prompt before acting.

## My Research Question
Where is the next wave of demand heading in supply-chain consulting
and SAP S/4HANA transformation services through 2026 to 2028, which
competitors are winning that work and how, and where is the whitespace
a mid-size specialist firm could credibly own?

## My Research Team
Create and run a team of four research agents with these roles:

- **Market Analyst**: Size and growth of the supply-chain consulting
  and SAP S/4HANA services market through 2028. Find named market-size
  numbers, growth rates, and which segments are growing fastest. Cover
  the 2027 SAP ECC mainstream support deadline and what it does to
  demand. Always note the source and the year of any number you use.

- **Competitor Tracker**: Profile who is winning this work and how.
  Cover the large firms (Accenture, Deloitte, IBM, Capgemini, Infosys,
  TCS, Wipro) and the SAP-focused specialists. For each, find their
  named offers, their positioning, where they are strong, and where
  they are thin. Flag any recent partnerships or acquisitions that
  change the picture.

- **Client Demand Researcher**: Find what buyers actually want. Which
  industries are spending on supply-chain transformation. The real pain
  points behind the spend (resilience, planning accuracy, cost, ESG
  reporting). What makes a buyer choose a specialist firm over a Big
  Four firm.

- **Whitespace and Risk Assessor**: Find where demand is outrunning
  supply, the gaps a mid-size specialist could credibly own. Then do
  the opposite job too: name the risks. Where could the market soften?
  Where could a large firm out-muscle a smaller player? What would have
  to be true for a whitespace bet to fail?

## Context
Read my CLAUDE.md before launching, especially my role and what I work
on. Weight all findings for a senior leader at Bristlecone, a supply-chain
consulting and SAP-led transformation firm, not a generic audience.
If a second-brain/ folder exists with relevant files, skim it and pass
that context to each agent.

## Instructions

1. Create a research/ directory in this project.
2. Create a role file for each agent:
   research/[agent-name]-role.md - their name, focus, and the specific
   questions they should answer.
3. Run ALL four agents in parallel as subagents. Each agent should:
   - Research their area thoroughly using web search.
   - Write their findings to research/[agent-name]-findings.md.
   - Include specific data points, named firms, named offers, and the
     source and year for every number.
   - Mark each finding as one of: SOURCED (a specific source backs it),
     INFERRED (a reasonable read, but no direct source), or UNCERTAIN
     (a guess or a gap). Be honest. Most secondary research is INFERRED.
   - Flag any surprising insights or contradictions.
4. After ALL agents finish, create research/synthesis.md:
   - A 3 to 5 sentence executive summary answering the core question.
   - One section per agent with their key findings as bullets.
   - A "Key Insights" section with the most important findings across
     all agents.
   - An "Assumptions and Gaps" section listing every claim that is
     INFERRED or UNCERTAIN, and what would confirm or correct it.
   - A "Recommended Next Steps" section, specific enough to act on.

Go.
```

**Fill in the blanks and paste it.** Then watch.

You will see Claude create the `research/` folder, write the four role files, then launch the agents. They run at the same time. You will see them working side by side. That is the parallel subagents pattern in action, and it is the heart of the workflow.

**While the agents work:** open one of the role files Claude created in the `research/` folder. Is it what you expected? This is your chance to see how Claude read your team design. If an agent's focus looks too broad, you can tighten it and re-run that one later.

---

### Step 5: Read the Synthesis

The agents are done. You have a `research/` folder full of findings and a `synthesis.md`. Read the summary first.

```
Read research/synthesis.md. What is the single most important thing
I should take away from this, given who I am and what I work on at
Bristlecone?
```

Now push on the most interesting finding. Pick one and go deeper.

```
The finding about [paste the specific thing] is interesting. Go deeper
on it. What does it mean for a firm like Bristlecone specifically?
Reference my CLAUDE.md.
```

---

> **Checkpoint: Part A complete**
>
> - [ ] `research/` folder with four agent findings files
> - [ ] `research/synthesis.md` exists and you have read it
> - [ ] You know the single most important takeaway
> - [ ] You have pushed deeper on at least one finding

---

### Troubleshooting - Part A

| Issue | Fix |
| --- | --- |
| Agents run one at a time, not together | Still fine. Same output, just slower. Parallel is for speed, not correctness. |
| The synthesis feels thin or generic | Tell Claude: "The synthesis is too surface-level. Go back to each findings file and pull the most specific data points: named firms, named offers, real numbers with sources. Rewrite synthesis.md." |
| Numbers with no source | This is the big one for research. Tell Claude: "Every number in the synthesis must show its source and year, or be marked INFERRED. Go back and fix any number that is just floating there." |
| Agents found different answers | Good. That is real. Do not ask Claude to smooth it over. Tell it: "Surface that contradiction clearly in the synthesis. Do not pick a side." A clean contradiction is more useful than a fake agreement. |
| Web search returned nothing | Check `/permissions` has `WebSearch` and `WebFetch`. Re-run the test search from "Before You Start." Then re-run the agent. |

---

## Part B: The Critique Pass

You have a synthesis. It looks clean. That is exactly when it is most dangerous.

Remember the rule. This is secondary research. The agents read what is public. They did not see Bristlecone's pipeline, your win rates, or what a real buyer told you last week. So the synthesis is a set of hypotheses dressed up as findings. Before it goes anywhere near a deck or a client conversation, someone needs to attack it.

That someone is your critique panel. Their job is not to be helpful. Their job is to find what is wrong. The critique pass is part of the workflow, not an extra.

---

### Step 1: Flag the Assumptions First

Before the critics argue strategy, get the synthesis to be honest about what it actually knows.

```
Read research/synthesis.md and all the findings files in research/.

You are a fact-checker preparing this for a senior leadership review at
Bristlecone. Go through every substantive claim in the synthesis and
label each one:

- VERIFIED - backed by a specific, named source with a year.
- ESTIMATED - a reasonable read from the data, but not directly sourced.
- ASSUMPTION - stated as fact, but really a guess or a leap.
- FLAGGED - likely out of date, contested, or true for one market but
  stretched across the whole picture.

For every ASSUMPTION or FLAGGED item, write one sentence on what evidence
would confirm or correct it.

Save the full report to research/assumptions-report.md.
Then update research/synthesis.md to add a marker, VERIFIED, ESTIMATED,
ASSUMPTION, or FLAGGED, next to each key claim.
```

Open `research/assumptions-report.md`. Look for two things.

First, how many ASSUMPTION or FLAGGED claims are there? If it is more than a handful, the research did not go deep enough, or your question was too broad. That is useful to know now, not after you have built a deck on it.

Second, are the gaps clustered in one agent's area? If most of the holes are in, say, the market-size section, that agent's brief was too vague. You can re-run just that one.

You do not need to fix everything. You need to know the shape of what is solid and what is not.

---

### Step 2: Run the Critique Panel

Now three reviewers read the synthesis. Each comes with a different agenda. Their disagreement is the signal.

```
Read research/synthesis.md, including the VERIFIED / ESTIMATED /
ASSUMPTION / FLAGGED markers.

You are three senior reviewers critiquing this research. Each of you
has a different agenda. Be specific. Quote the synthesis where it helps.
3 to 5 bullet points each.

CRITIC 1 - THE PRACTICE LEAD:
You want to use this to back a real investment decision in front of
Bristlecone leadership. Ask: Is the whitespace clear enough to act on,
or is it still at the level of "explore opportunities"? Which 2 to 3
plays would you actually back first? What is still missing before you
would take this upstairs?

CRITIC 2 - THE COMPETITOR'S STRATEGIST:
You run strategy at a large rival firm. You have just read this. Ask:
What has this team got wrong or underweighted? Which assumptions would
a well-briefed competitor laugh at? What market move or capability does
this synthesis miss that you already have in motion? Where would a big
firm simply out-spend a mid-size player?

CRITIC 3 - THE DEVIL'S ADVOCATE:
Your job is to argue the opposite. Ask: What if the whole framing is
wrong? What if the "next wave" of SAP and supply-chain demand is smaller,
later, or already locked up by the incumbents? What is the strongest case
that the recommended whitespace bet fails? What would have to be true for
this entire synthesis to be misleading?

The three of you must disagree on at least one real point. Do not be
polite. Find the cracks.
```

If the three critics line up too neatly, push back:

```
The three critics are too aligned. The Devil's Advocate should find a
credible reason the whole framing could be wrong. The Competitor's
Strategist should name a specific market dynamic we got wrong. Make them
actually disagree.
```

---

### Step 3: Get the Fix List

The critics have had their say. Now make them agree on what actually has to change, and in what order.

```
The three critics have finished. Now have them produce one prioritised
fix list.

P0 - must fix before this goes into any brief, deck, or client
     conversation. Something a leader or a client would immediately
     challenge or find misleading.
P1 - important gaps. Fix before the next version goes out, but they do
     not block use today.
P2 - polish. Nice to have. The output is solid without them.

Rules:
- The critics can disagree on priority. Not every item needs consensus.
- Each item must name the exact section and the specific change, not
  just the problem.
- Keep P0 short. If everything is P0, nothing is P0.

Save the list to research/fix-list.md and show it to me here.
```

Read `research/fix-list.md`. The P0 list is what you act on now.

---

### Step 4: Apply the P0 Fixes

```
Read research/fix-list.md. Apply all P0 fixes to research/synthesis.md.
For each fix, show me the before and after before you save.
```

Once the P0s are done, the synthesis is ready to put in front of someone. P1s go on your backlog. P2s are optional.

---

> **Checkpoint: Part B complete**
>
> - [ ] `research/assumptions-report.md` exists - claims labelled, gaps named
> - [ ] `research/synthesis.md` has inline markers
> - [ ] Critique panel ran - all three critics gave specific, distinct feedback
> - [ ] `research/fix-list.md` exists with P0 / P1 / P2
> - [ ] P0 fixes applied to the synthesis

---

### Troubleshooting - Part B

| Issue | Fix |
| --- | --- |
| Everything comes back VERIFIED | The check was too soft. Tell Claude: "Be stricter. Any number without a named source is ESTIMATED at best. Any claim about the whole market based on one example is FLAGGED." |
| Too many ASSUMPTION items | Your findings files are thin. Tell Claude: "The findings for [agent name] are too thin. Run that agent again with a tighter focus on specific data and named sources." |
| Critics are vague | Tell Claude: "Each critic must quote the exact line they are challenging. General feedback is useless here." |
| Devil's Advocate just agrees | Tell Claude: "The Devil's Advocate must argue the opposite seriously. What is the strongest possible case that the whole framing is wrong?" |
| Everything lands in P0 | Tell Claude: "P0 means it blocks the output from going anywhere. Downgrade anything important but not blocking to P1." |

---

## Part C: Make the Workflow Reusable

You have run the workflow once. Now save it so you never start from scratch again.

```
Create a file called research/team-template.md that captures:
1. My team configuration today - the four agent names, their roles, and
   focus areas.
2. The launch prompt as a reusable template, with [RESEARCH QUESTION]
   and the agent descriptions as placeholders I can swap out.
3. Short instructions for adapting the team to different question types
   (a competitor scan, a single-account brief, a whitespace scan).
4. A note that this is secondary research, so the assumptions pass and
   the critique panel in Parts B and C are not optional.

Then update my CLAUDE.md to add a short section saying I have a reusable
research workflow at research/team-template.md and how to run it.
```

**The frame to take away:** your research workflow is built. Any question, any topic, any time. You do not start a blank document and stare at it anymore. You brief your team. They deliver a structured analysis. Then you stress-test it before you trust it.

The workflow is not a one-off. It is a recipe you reuse. Next time a partner asks "what do we know about this market?" on a Monday, you know exactly what to do.

---

## Part D: Build Your Own Agent

In Part A the workflow created agents on the fly and threw them away. That is fine for a one-off team. But some workers you want around all the time. The status-report writer. The RFP requirement reader. The meeting-notes summariser. The agent that always checks a SOW against your governance rules.

For those, you build a real agent and save it. Claude Code has a command for exactly this: `/agents`. An agent you make this way gets a name, its own brief, and lives in your project. You call it by name, or Claude calls it for you when the job fits. It works across every chat and every workflow from now on.

A workflow is the recipe. An agent is a worker. Here you hire a worker of your own.

---

### Step 1: Open the agents manager

In Claude Code, type:

```
/agents
```

This opens the agent manager. You will see any agents that already exist, and an option to create a new one. Choose to create a new agent. When it asks where to save it, choose the **project** option so the agent lives in this folder (`.claude/agents/`) and travels with your work.

If you would rather not use the menu, you can just ask in plain English:

```
Create a new project agent for me using /agents. Walk me through it
one step at a time.
```

---

### Step 2: Pick the worker you actually need

Do not invent something clever. Pick a small, real job you repeat most weeks. Some good Bristlecone-shaped agents:

| Agent idea | What it does |
| --- | --- |
| **Status Report Writer** | Takes your rough notes on a programme and turns them into a clean RAG status update in your house format. |
| **RFP Requirement Extractor** | Reads an RFP or client brief and pulls out every requirement, deadline, and evaluation criterion into a checklist. |
| **Meeting Notes Summariser** | Turns a messy transcript or your scribbles into decisions, owners, and next actions. |
| **SOW Governance Checker** | Reads a statement of work and flags anything that breaks your safe-data or scope rules from Session 4. |
| **Deck Outline Builder** | Takes a topic and audience and returns a slide-by-slide outline before you build the deck. |

Pick one. Write its job in a single sentence before you create it. A clear one-line job makes a sharp agent.

---

### Step 3: Create the agent

When `/agents` asks you to describe it, you have two routes. The easy one: describe the agent in plain English and let Claude write the brief and pick the tools. Tell it something like:

```
Build a "Status Report Writer" agent.

Its job: take my rough notes about a programme and produce a clean
weekly status update.

It should:
- Use my house format: Overall RAG, then Scope, Schedule, Risks, Asks.
- Read my CLAUDE.md so the tone matches how I write.
- Keep it tight. No filler. Flag anything red at the top.
- Never invent a status I did not give it. If something is missing,
  list it as an open question instead of guessing.

Save it as a project agent.
```

Claude will draft the agent: a name, a description of when to use it, the tools it is allowed to touch, and its full brief. Read the draft. Two things to check:

- **The description.** This is how Claude decides when to call the agent on its own. Make it specific: "Use when the user wants a weekly programme status update from rough notes."
- **The tools.** Give it only what the job needs. A writer needs to read and write files. It does not need to run commands. Less access, less risk. That is the Session 4 lesson showing up early.

Save it. It now lives in `.claude/agents/` in your project.

---

### Step 4: Test it

An agent you have not tested is just a hope. Give it a real run.

```
Use my Status Report Writer agent. Here are my notes for this week:
[paste three or four messy lines about a real or sample programme -
what's on track, what slipped, one risk, one thing you need from
someone]
```

Watch what comes back. Then judge it like a manager judging a new hire:

- Did it follow your format?
- Did it sound like you, or like generic AI?
- Did it invent anything you did not tell it?

If it missed, fix the brief, not just this one answer. Open `/agents` again, edit the agent, and tighten the part it got wrong. An agent gets better the same way a team member does: clear feedback, written down once.

```
My Status Report Writer put the risks in the wrong place and the tone
was too formal. Open /agents, edit it so risks always come right after
the overall RAG, and tell it to match the plain, direct tone in my
CLAUDE.md. Save it.
```

---

> **Checkpoint: Part D complete**
>
> - [ ] You opened `/agents` and created a new project agent
> - [ ] The agent has a clear one-line job and only the tools it needs
> - [ ] You ran it on real input and read the output like a manager
> - [ ] You edited the brief at least once to make it sharper

---

### Troubleshooting - Part D

| Issue | Fix |
| --- | --- |
| `/agents` does nothing or isn't recognised | Make sure you are inside Claude Code (you typed `claude` in your project folder), not a plain terminal. Type `/` and look for `agents` in the list. |
| Claude won't call my agent on its own | Its description is too vague. Edit the agent and make the description say exactly when to use it: "Use when the user wants X from Y." |
| The agent ignores my house format | The format wasn't specific enough in the brief. Edit the agent and spell the format out as a numbered list. Tell it to read CLAUDE.md too. |
| The agent makes things up | Add a hard rule to the brief: "Never invent details. If something is missing, list it as an open question." Save and re-test. |
| I want this agent in every project, not just this one | When creating it, choose the personal/user option instead of project. Project agents live with one folder; personal agents follow you everywhere. |

---

### If You Finish Early

**Run a completely different research question.** Try a single-account brief.

```
I have a new research question: [name a real or sample target account
and what you want to know about them]. Adapt my research workflow for
this. Swap agents if needed. Run the full process again and save it in
research/account-brief/.
```

**Build a second agent.** Pick another job from the table in Part D and create it. Two good agents beat ten half-built ones.

**Turn the synthesis into something you would actually send.**

```
Take research/synthesis.md and produce three outputs:
1. A one-page brief I could send to a practice leader.
2. A comparison table of the main competitors and their positioning.
3. A "what to do next" action plan with concrete steps.
Save them in research/outputs/.
```

**Go meta.** Ask what a better team would look like next time.

```
Based on the research you just did, what would the ideal set of agents
be if I wanted to research this BETTER next time? What role did I miss?
What focus area would you change?
```

---

> **Checkpoint: Session 3 complete**
>
> - [ ] `research/` folder with four agent findings files and `synthesis.md`
> - [ ] `research/assumptions-report.md` with claims labelled
> - [ ] `research/fix-list.md` with P0 / P1 / P2 from the critique panel
> - [ ] P0 fixes applied to the synthesis
> - [ ] `research/team-template.md` saved for reuse
> - [ ] CLAUDE.md updated with your research workflow
> - [ ] Your own agent built with `/agents`, tested, and tuned

---

**Next:** [Session 4: Security & Governance →](session-4-security-governance.md)
