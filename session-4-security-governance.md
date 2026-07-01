[← Back to Student Handbook](student-handbook.md)

---

# Session 4: Security & Governance

**Day 1 - Thursday, 2 July 2026**

**What you'll do:** Understand exactly what Claude Code can and cannot touch, set safe permissions for your own project, learn what client data is safe to use and what must never go in, and agree on team norms you can roll out across Bristlecone.

---

## Why this session matters to you

You run enterprise IT, cybersecurity, and quality management for a living.

This session is your home turf.

The other sessions taught you to use the tool. This one teaches you to govern it.

By the end you will be able to answer the question your CISO, your auditor, or your client will ask:

> "If our people start using this, what stops it from touching the wrong file or running the wrong command?"

You will know the real answer. Not a guess.

Most of this session is not technical. It is governance, controls, and norms. That is leadership work, and it is exactly what you do every day.

Let's make this concrete for Bristlecone. You handle supply chain client data. You run SAP environments. You sit under NDAs with large clients. So every example here is framed for that world.

---

## Part 1 - How Claude Code's permission system actually works

Start with the one sentence that matters most.

**Claude Code asks before it changes anything.**

It reads files. It thinks. It proposes. Then it waits for you to approve before it edits a file or runs a command.

Nothing lands on your machine without you saying yes.

This is the opposite of "autopilot." It is a fast colleague who checks with you before acting.

### What Claude asks permission for

When Claude wants to do any of these, it stops and shows you a prompt:

- Create a new file
- Edit an existing file
- Delete a file
- Run a terminal command

You see exactly what it wants to do. You read it. You approve or deny.

### Check what Claude is allowed to do

Inside a Claude session, type:

```
/permissions
```

This shows the current rules. What is allowed without asking. What still needs your approval.

Run it now in your own project. Look at what is there.

### The three permission modes

Claude Code has different modes. Each one changes how often it asks.

| Mode | What it does | When a leader uses it |
| --- | --- | --- |
| **Default (ask)** | Claude asks before every edit and every command | Your everyday setting. Safe. Use this. |
| **Plan mode** | Claude can only read and plan. It cannot edit or run anything until you approve the plan | When the task is big or touches sensitive files. Claude shows its plan first. |
| **Accept-edits** | Claude can make file edits without asking each time | Only for low-risk, repetitive work in a throwaway folder. Not for client data. |

You switch modes with the **Shift+Tab** key inside a Claude session. Press it to cycle through the modes. The mode you are in shows at the bottom of the screen.

**The rule for your cohort:** stay in **Default** mode. Use **Plan mode** for anything that touches real client material. Avoid **accept-edits** while you are learning.

### Plan mode - your safest setting

Plan mode is the one to remember.

In plan mode, Claude reads everything, understands the task, and writes out a plan.

It does not touch a single file until you read that plan and approve it.

This is "review before run" built into the tool.

For a leader rolling this out across teams, plan mode is the answer to "how do I stop people breaking things while they learn." You tell your team: for anything important, plan mode first.

Try it now. Press **Shift+Tab** until you see plan mode, then ask:

```
Plan how you would reorganize the files in this folder. Do not make any changes yet. Just show me your plan.
```

Claude shows the plan. Nothing changes. You stay in control.

### What Claude can and cannot touch

This is the part your security team will want.

**Claude works inside the folder you start it in.**

When you run `claude` from a folder, that folder is its workspace. It reads and writes there.

**What Claude cannot do without your approval:**

- It cannot edit a file without showing you the change first
- It cannot run a command without showing you the command first
- It cannot send your files anywhere without you connecting an external tool on purpose

**What you control:**

- Which folder you start it in (so keep client work in a dedicated folder, never your whole drive)
- Every edit and command, through the permission prompt
- What leaves your machine, through privacy settings

> **The trio to know:** `/permissions` controls what Claude can *do*. Plan mode controls *when* it can act. `/privacy-settings` controls what *leaves* your machine. Together, they give you full visibility.

---

## Part 2 - The allow and deny lists (settings.json)

This is where governance becomes a written rule, not a habit.

Claude Code reads its rules from settings files. You can write rules that say "always allow this safe command" and "never allow this risky one."

### Two files, two purposes

| File | What it is for | Goes into Git? |
| --- | --- | --- |
| `.claude/settings.json` | Team rules. Shared with everyone on the project. | Yes. This is your team standard. |
| `.claude/settings.local.json` | Your personal rules. Just for your machine. | No. This stays local. |

Both live in a folder called `.claude` inside your project.

The team file is the one a leader cares about. It is the written, shared standard. Everyone who opens the project inherits it.

### What goes inside

A settings file has an `allow` list and a `deny` list.

- **allow** - commands Claude can run without stopping to ask
- **deny** - commands Claude can never run, even if you approve in the moment

The deny list is the strong one. It is a hard stop. This is what you show an auditor.

### A real, safe example

Here is a settings file that allows safe read-only commands and blocks the dangerous ones.

Save this as `.claude/settings.json` in your project:

```json
{
  "permissions": {
    "allow": [
      "Bash(ls *)",
      "Bash(pwd)",
      "Bash(cat *)",
      "Bash(git status)",
      "Bash(git diff *)",
      "Bash(git log *)"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(rm -r *)",
      "Bash(sudo *)",
      "Bash(curl *)",
      "Bash(chmod 777 *)",
      "Bash(git push *)",
      "Read(./.env)",
      "Read(./**/secrets/**)"
    ]
  }
}
```

Read what this does.

**The allow list** lets Claude look around without bothering you. List files. Show where it is. Read a file. Check Git status. These are safe, read-only actions. No editing, no deleting.

**The deny list** is the guardrail.

- `rm -rf` and `rm -r` delete files permanently. Blocked.
- `sudo` runs as administrator. Blocked.
- `curl` downloads from the internet. Blocked, so no code arrives from outside.
- `chmod 777` opens files to everyone. A security hole. Blocked.
- `git push *` stops anything from being pushed to a remote repo by accident. Important when client code or data sits in the folder.
- `Read(./.env)` and the secrets pattern stop Claude from even reading your secret files. More on that next.

This is a starting point. Your security team will tighten it for Bristlecone's standards. But the shape is right: allow safe reads, deny destructive and outbound commands.

> **Note for Windows and Mac.** A deny rule matches the command Claude tries to run. Mac and Windows use different command names for the same action: deleting a file is `rm` on a Mac and `Remove-Item` or `del` on Windows. So a good deny list names both forms. The global setup below does exactly that, so you are covered whichever machine you are on. If a command in the list looks unfamiliar, that is fine. The point is that it is blocked.

### How to create the file

You do not have to write JSON by hand. Ask Claude to do it, in plan mode:

```
Create a .claude/settings.json file for this project. Allow only safe read-only commands like ls, pwd, cat, and git status. Deny anything destructive: rm, sudo, curl, chmod 777, and git push. Also deny reading any .env or secrets files. Show me the file before you write it.
```

Claude proposes the file. You read it. You approve. Now your rule is written down.

### A global safety net you set once

The settings file above protects this one project. There is a stronger move: a global deny list that protects **every** project on your machine.

It lives at `~/.claude/settings.json` (the `~` is your home folder). A project's `.claude/settings.json` covers that one project. The global file covers everything you ever run Claude on. Set the dangerous-command blocks here once, and they follow you into every folder, on every job, from now on.

The catch: Mac and Windows use different command names for the same destructive action. Deleting a file is `rm` on a Mac and `Remove-Item` or `del` on Windows. A list that only names the Mac commands leaves a Windows machine exposed, and the other way round. So you name both.

Ask Claude to set it up. Switch to plan mode first (**Shift+Tab**), then paste this:

```
Configure my global ~/.claude/settings.json to deny all destructive and
irreversible operations, so this protection applies in every project, not
just this one.

First check whether I'm on Windows or Mac. Then add deny rules that cover
the destructive commands on BOTH, so nothing slips through whichever shell
Claude uses:

- File deletion or overwrite
  - Mac/Linux: rm, rmdir, unlink, trash, shred, truncate, dd
  - Windows (PowerShell and Command Prompt): Remove-Item, ri, del, erase,
    rd, rmdir, Clear-Content
- Destructive git operations (the same on both): push --force, reset --hard,
  clean -f, checkout -- , restore, branch -D, stash drop
- Reading any .env file

Add all of these to the deny list. Do NOT remove or change any deny rule
that is already there - only add. If ~/.claude/settings.json does not exist
yet, create it. Show me the final file before you save it.
```

**What this does, in plain words:**

- It writes the blocks into your *global* settings, so every project you open from now on inherits them.
- It blocks the things you cannot undo: deleting files, wiping or force-pushing git history, and reading your secret `.env` files.
- It names the Mac commands *and* the Windows commands, so you are covered on either machine.
- "Only add, never remove" means it leaves any rule you already have in place. It is safe to run even if you have set things up before.

Read the file Claude shows you, then approve. From now on, on any project, Claude refuses these commands outright, even if you approve them in the moment by mistake.

---

## Part 3 - Data safety: what is safe and what must never go in

This is the section to take back to your data protection and client teams.

Claude Code runs on your machine and reads your local files. That is good for privacy: your files stay on your laptop unless you deliberately connect an outside tool.

But you still decide what goes into the folder. So you set the rule for what is safe.

### Safe to use

- Internal templates, checklists, process docs
- Anonymized or synthetic data
- Your own meeting notes, drafts, plans
- Public information
- Sample datasets where names and numbers are scrubbed

### Never paste or place in the folder

- **Client PII** - names, contact details, employee records, anything that identifies a real person
- **Credentials** - passwords, API keys, SAP logins, database connection strings, tokens
- **Contracts and documents under NDA** - anything a client shared in confidence
- **Live production data** - real supply chain records, real customer orders, real financials tied to a named client
- **Anything you would not email outside the firewall**

The simple test: **if you would not put it in a normal email to someone outside Bristlecone, do not put it in a Claude folder.**

### How to keep work local and safe

Three habits. Teach these to every team.

**1. Dedicated project folders.**

Never run Claude from your whole drive or your desktop. Make a folder for the task. Put only what that task needs into it. Claude can only see what is in the folder.

In practice this is exactly what you did in Session 0: make a new folder (in File Explorer or Finder), open just that folder in VS Code, and start Claude there. One folder per task keeps each piece of client work walled off. You can even ask Claude to set one up: "Create a folder called bristlecone-supplychain-analysis for this piece of work."

**2. Use `.gitignore` so secrets never get committed.**

If your project uses Git, a `.gitignore` file tells Git which files to never track. This stops secrets from ending up in a shared repo.

Create a file called `.gitignore` with this:

```
.env
*.key
*.pem
secrets/
client-data/
*.local.json
```

Now even if a secret file sits in your folder, Git will not pick it up.

**3. Keep secrets in a `.env` file, never in your prompts or code.**

A `.env` file holds your secrets in one place: keys, passwords, connection strings.

```
SAP_PASSWORD=do-not-put-real-value-here-in-a-shared-doc
DB_CONNECTION=do-not-share
API_KEY=do-not-share
```

You keep `.env` out of Git (the `.gitignore` above does this) and out of the deny-read list in settings (Part 2 does this).

So Claude never reads it, and Git never tracks it. Two locks on the same door.

> **The one-line policy for Bristlecone:** real client data, credentials, and NDA documents stay out of Claude folders. Use internal, anonymized, or public material. When in doubt, leave it out.

---

## Part 4 - Governance for AI adoption across Bristlecone

You are not here to use the tool once. You are here to decide how hundreds of people use it safely.

Here is the governance frame. Keep it simple so it actually gets followed.

### Set team norms

Norms beat rules nobody reads. Agree on a short list everyone can remember.

- **Plan mode for anything important.** If it touches client material, see the plan before you approve.
- **Read before you approve.** Every prompt is a decision. No blind "yes."
- **Dedicated folders only.** Never run Claude from a personal drive or shared network root.
- **No client PII, credentials, or NDA documents.** Ever. No exceptions.
- **One shared settings.json per project.** The deny list is the team standard.

### When to use plan mode (make it a policy)

Tell your teams: use plan mode when any of these are true.

- The task touches real client work
- The task could delete or move many files
- The task runs commands you do not fully understand
- It is a new person still learning the tool

Plan mode costs ten seconds. It prevents most mistakes. Make it the default for anything that matters.

### Review-before-run discipline

This is the cybersecurity instinct you already have, applied to a new tool.

Every command Claude proposes, someone reads before it runs.

Train your people to ask, before approving:

> "What exactly will this do? Is it reversible?"

If they cannot answer, they deny and ask Claude to explain first.

### Approving tools

Claude Code can connect to outside tools (these are called MCP connections). This is where data could leave your machine.

**Governance rule:** no outside tool gets connected in a client project without IT and security signing off. By default, Claude runs fully local. Keep it that way for sensitive work.

### An "AI use" checklist a leader can roll out

Hand this to every team. One page. Pin it.

```
BRISTLECONE - CLAUDE CODE SAFE USE CHECKLIST

Before I start:
[ ] I am in a dedicated project folder, not my whole drive
[ ] The folder has NO client PII, credentials, or NDA documents
[ ] A shared .claude/settings.json with a deny list is in place
[ ] .gitignore covers .env, keys, and client-data folders

While I work:
[ ] I use plan mode for anything touching real client material
[ ] I read every command before I approve it
[ ] If I don't understand a command, I ask Claude to explain it first
[ ] I never approve rm -rf, sudo, or curl-from-internet commands

Before I share or commit:
[ ] No secrets in the files I'm committing
[ ] No real client data in anything leaving my machine
[ ] If connecting an outside tool, IT and security approved it first
```

That checklist is your governance, in plain language, that a non-technical person can follow.

---

## Part 5 - Safe defaults: set up your own project now

Time to apply it. Do this in your own project folder, right now.

### Step 1: Confirm where you are

Make sure the `thecrux-bristlecone-bootcamp` folder is the one open in VS Code, not your whole drive or your home folder. If you're not sure, ask Claude: "What folder are you working in right now?"

### Step 2: Ask Claude to create your settings file

Switch to plan mode first (**Shift+Tab** until you see plan mode), then:

```
Create a .claude/settings.json for this project. Allow safe read-only commands: ls, pwd, cat, git status, git diff, git log. Deny destructive and outbound commands: rm -rf, rm -r, sudo, curl, chmod 777, git push. Also deny reading .env and any secrets folder. Show me the file before writing it.
```

Read the plan. Approve it. You now have a written team standard.

### Step 3: Add a .gitignore

```
Create a .gitignore file that ignores .env, *.key, *.pem, a secrets/ folder, a client-data/ folder, and *.local.json. Show it to me first.
```

### Step 4: Check your permissions

```
/permissions
```

Confirm the allow and deny lists look right.

### Step 5: Check privacy settings

```
/privacy-settings
```

Read what is there. This controls whether your prompts and files can be used to improve the model. For sensitive work, this is the setting to check. You do not need to change anything today, but you should know where it lives.

That is your safe default. A deny list, a `.gitignore`, privacy checked. Repeat this for every real project.

---

## Quick Reference

### Permission modes

| Mode | What it does | How to reach it |
| --- | --- | --- |
| Default (ask) | Asks before every edit and command | Starting mode |
| Plan mode | Reads and plans only, no changes until approved | Shift+Tab to cycle |
| Accept-edits | Edits without asking each time | Shift+Tab (avoid for client work) |

### Key commands

| Command | What it does |
| --- | --- |
| `/permissions` | View and change what Claude can do |
| `/privacy-settings` | Control what leaves your machine |
| `Shift+Tab` | Cycle through permission modes |
| `Escape` | Stop Claude mid-response |
| `Ctrl+C` | Hard stop / exit |

### The two settings files

| File | Purpose | In Git? |
| --- | --- | --- |
| `.claude/settings.json` | Shared team rules | Yes |
| `.claude/settings.local.json` | Your personal rules | No |

### The one-line policy

```
Real client data, credentials, and NDA documents stay out of Claude folders.
Use internal, anonymized, or public material. When in doubt, leave it out.
```

---

## Troubleshooting / FAQ - Session 4

| Issue / Question | Answer |
| --- | --- |
| "Where do I put the settings.json file?" | Inside a folder called `.claude` in your project. The path is `.claude/settings.json`. Ask Claude to create the folder and file for you. |
| "I'm on Windows and the .claude folder is hidden." | Hidden folders starting with a dot are normal. In File Explorer, turn on "Hidden items" under the View tab to see it. Or just let Claude create and edit it. |
| "Can Claude read files outside my project folder?" | It works in the folder you start it in. Keep client work in a dedicated folder and that is its whole world. Run `pwd` to confirm where you are. |
| "Does my data get sent to Anthropic?" | Claude Code runs locally and reads local files. Check `/privacy-settings` to see and control what, if anything, can be used to improve the model. For sensitive work, review this setting. |
| "I approved something I shouldn't have." | Tell Claude: "Undo the last change you made." For file edits, you can also use `/rewind` to go back and undo. |
| "Claude proposed a command I don't understand." | Deny it. Then ask: "What exactly will this command do? Is it reversible?" Approve only after you understand it. |
| "What if a teammate removes the deny list?" | Keep `settings.json` in Git so changes are tracked and reviewed, like any other config. A removed deny rule shows up in the diff. |
| "Can I use real SAP or client data if I'm careful?" | No. Use anonymized or synthetic versions. The rule is simple so nobody has to make a judgment call under pressure. |
| "Plan mode feels slow." | It is meant to. The ten seconds you spend reading a plan saves you from the mistake you can't undo. Use it for anything that matters. |
| "How do I roll this out to my team?" | Share the safe-use checklist in Part 4 and a standard `settings.json`. Make plan mode and the no-client-data rule the two norms everyone remembers. |
| "Settings file has a typo / won't load." | JSON is fussy about commas and brackets. Ask Claude: "Check my .claude/settings.json for syntax errors and fix them." |

---

> **Checkpoint: Session 4 complete**
>
> - [ ] I understand Claude asks before editing or running anything
> - [ ] I know the three permission modes and when to use plan mode
> - [ ] I created a `.claude/settings.json` with an allow and deny list
> - [ ] I added a `.gitignore` and know to keep secrets in `.env`
> - [ ] I know what client data is safe and what must never go in
> - [ ] I have the safe-use checklist to roll out to my team

---

## Day 1 Close - what you built and what's next

Step back. Look at what you have today.

### What you built on Day 1

- **Your CLAUDE.md** - your work DNA. The document every Claude session reads first. It knows who you are, what you do at Bristlecone, and how you want to work.
- **Skills** - reusable instructions Claude follows on demand. You taught it to do specific tasks your way, once, so it repeats them every time.
- **Workflows and agents** - a research workflow that runs a team of agents in parallel and hands you a checked, critiqued synthesis. And your own named agent, saved with `/agents`, ready to reuse.
- **Governance you can own** - a deny list, safe data rules, team norms, and a checklist you can roll out across teams.

Look at what you just did. You ran a team of agents and pulled a clear answer out of the noise. You set up access controls, a deny list, and a data policy.

That is not coding. That is judgement and governance. It is the thing you already do better than anyone in the room.

### Last thing today - build a game, then the hackathon

To close Day 1, you will build a small browser game with Claude. No data, no rules, just for fun. It proves the point: if you can build a game from a sentence, you can build a tool for your work.

Then we will brief the Day 2 hackathon. You will pick a real Bristlecone problem and build something for it overnight in your head, ready to start in the morning.

We will run both of these live, so just follow along.

### What's coming on Day 2

Day 2 is where it gets real for your work.

- You will point Claude at the kind of problems Bristlecone actually solves: supply chain analysis, SAP-related workflows, consulting deliverables
- You will turn a spreadsheet into a branded report, dashboard and deck in one guided build
- You will build your hackathon project on a real problem from your own week, then present it
- You will leave with workflows you can use on Monday, not someday

Day 1 gave you the controls, the safety, workflows and agents. Day 2 gives you the speed.

---

**Next:** [Session 5: Build →](session-5-builds.md)
