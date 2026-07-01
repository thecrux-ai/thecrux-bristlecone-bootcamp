# Bristlecone × theCRUX.ai - Claude Code Bootcamp

Welcome. Over two days you will go from AI user to AI builder.

You will not become a developer. You will learn to make Claude do real Bristlecone work: build your own context file, build skills that work in your voice, run workflows and build your own agents, and turn a spreadsheet into a branded report, dashboard and deck.

This handbook is your map. Each session has its own file. Open one session at a time. Every prompt you need is inside the session files.

---

## What You Will Walk Away With

| What | Where it ends up |
| --- | --- |
| CLAUDE.md - your role, projects, priorities, preferences | Project root |
| Comms Lead skill - writes in your voice | `.claude/skills/comms-lead/` |
| A workflow skill for your role - `/report`, `/sow`, `/governance-check` | `.claude/skills/` |
| Safe-defaults governance setup | `.claude/settings.json` |
| A research workflow - parallel agents, structured synthesis | `research/` |
| Your own agent - a named specialist you build with `/agents` | `.claude/agents/` |
| `design.md` - your Bristlecone branding engine | `day2builds/` |
| A branded report, dashboard, chat and PPT from one dataset | `day2builds/` |
| A capstone you choose | Your project folder |

---

## Day 1 - Thursday, 2 July 2026 (10 am to 5 pm)

1. [Session 0: VS Code setup + Hello Claude](session-0-hello-claude.md)
2. [Session 1: CLAUDE.md - Your Work DNA](session-1-claude-md.md)
3. [Session 2: Skills](session-2-skills.md)
4. [Session 3: Workflows and Agents](session-3-workflows-agents.md)
5. [Session 4: Security & Governance](session-4-security-governance.md)
6. Build your own game + talk about the hackathon _(we run this live)_

## Day 2 - Friday, 3 July 2026 (9 am to 4 pm)

1. [Build - design.md, Report, Dashboard, Chat, PPT](session-5-builds.md)
2. Working lunch + hackathon _(live - [project ideas](capstone.md))_
3. Hackathon presentations _(live)_
4. [Possibilities (e.g. MCP)](mcp-handbook.md), [Feedback + Close](closing.md)

---

## Sessions At A Glance

| # | Session | What you leave with |
| - | --- | --- |
| 0 | [Hello Claude](session-0-hello-claude.md) | Claude Code installed and running |
| 1 | [Your Work DNA](session-1-claude-md.md) | A rich CLAUDE.md |
| 2 | [Skills](session-2-skills.md) | Comms Lead + one workflow skill live |
| 3 | [Workflows and Agents](session-3-workflows-agents.md) | A research workflow, a critiqued synthesis, and your own agent |
| 4 | [Security & Governance](session-4-security-governance.md) | Safe defaults set, governance you can roll out |
| 5 | [Build](session-5-builds.md) | design.md + branded report, dashboard, chat, PPT |
| - | [Capstone](capstone.md) | A build you choose |
| - | [Closing](closing.md) | Your plan for after the bootcamp |

**Stuck?** Open the [Appendix](appendix.md). Each session also has its own troubleshooting at the bottom.

---

## Your Project Folder

Everything you build lives in one folder: `thecrux-bristlecone-bootcamp`. Starting Claude is four clicks in VS Code:

1. Open **Visual Studio Code**.
2. **File → Open Folder...** and pick `thecrux-bristlecone-bootcamp`.
3. **Terminal → New Terminal** (a panel opens at the bottom).
4. Type `claude` and press Enter.

Session 0 walks you through making this folder and pulling in the materials the first time. After that, this is all you do to start each session.

That is it. One folder. One word. Let's build.
