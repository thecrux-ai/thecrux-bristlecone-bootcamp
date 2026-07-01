[← Back to Student Handbook](student-handbook.md)

---

# Session 0: VS Code setup + Hello Claude

**Day 1 - Thursday, 2 July 2026**

**What you'll do:** Make your bootcamp folder, open it in Visual Studio Code, start Claude, let Claude pull in the bootcamp materials, and then try your first prompts. By the end you're working inside the right folder with Claude ready to go.

---

## Before we start - read this

This is simpler than it looks.

Visual Studio Code and Claude were already set up for you in the pre-work. Today you point a few clicks in the right direction and then talk to Claude in plain English.

Here's how today works. You click a few menus. You type **one** word to start Claude: `claude`. After that, everything is plain English. Claude reads plain English, so once it's open, you talk to it like you'd talk to a sharp junior on your team.

Three rules for today:

1. **Copy and paste the prompts. Don't type from memory.** Every prompt you need is in a grey box on this page.
2. **If something looks off, just ask.** Someone from the team is right there to help.
3. **Go one step at a time.** Finish one box before moving to the next.

That's it. Let's go.

---

## The two tools you'll use

- **Visual Studio Code** (we'll call it **VS Code**) - a free app where you'll do all your work for two days. Think of it as the room you work in.
- **Claude Code** - the AI. You start it by typing `claude` once inside VS Code, then you talk to it in plain English.

That's the whole setup. One room, one assistant.

---

## Step 1: Make your bootcamp folder

First you make an empty folder to keep everything in. You do this the normal way, by clicking, not by typing.

### Windows - using File Explorer

1. Open **File Explorer** (the folder icon on your taskbar).
2. Go to **Documents** (or anywhere you like to keep your files).
3. Right-click an empty space, then choose **New → Folder**.
4. Name the folder `thecrux-bootcamp` and press **Enter**.

### Mac - using Finder

1. Open **Finder**.
2. Go to **Documents** (or anywhere you like).
3. From the top menu choose **File → New Folder** (or right-click and choose **New Folder**).
4. Name the folder `thecrux-bootcamp` and press **Enter**.

That empty folder is your home base for the two days.

---

## Step 2: Open the folder in VS Code

1. Open **Visual Studio Code**.
2. From the top menu, choose **File → Open Folder...**
3. Find and select the `thecrux-bootcamp` folder you just made, then click **Open**.
4. If VS Code asks *"Do you trust the authors of the files in this folder?"*, click **Yes, I trust the authors**.

You'll now see `THECRUX-BOOTCAMP` in the left panel (the **Explorer**). It's empty for now. We're about to fill it.

---

## Step 3: Open a terminal and start Claude

A **terminal** is a small panel at the bottom of VS Code where you type short commands. You'll only type a handful of things into it all day.

1. From the top menu, choose **Terminal → New Terminal**. A panel opens along the bottom of VS Code.
2. Click inside that panel. You'll see a blinking cursor waiting for input.
3. Type the word below and press **Enter**:

```
claude
```

Claude Code starts up. You'll see something like a `>` prompt on a new line — that's Claude waiting for your message.

> **This is the only thing you ever type into the terminal to start Claude: `claude`.** Everything from here on is plain English typed at the `>` prompt, or menu clicks in VS Code.

If `claude` doesn't start, or it asks you to log in again and you get stuck, raise your hand. Someone from the team will sort it in under a minute.

---

## Step 4: Ask Claude to pull in the bootcamp materials

All the sessions, prompts, and sample data live in one place online. You don't download anything by hand. You just ask Claude to fetch it.

Type this into Claude (at the `>` prompt) and press **Enter**:

```
Clone the repository https://github.com/thecrux-ai/thecrux-bristlecone-bootcamp into this folder.
```

Claude will tell you what it's about to do and ask your permission before it runs anything. Read the short summary, then click **Yes** (or press **Enter** to allow).

**Wait for it to finish.** It takes about 15–30 seconds.

---

## Step 5: Confirm the files are there

Look at the left panel in VS Code (the **Explorer**). You should now see a new folder inside `THECRUX-BOOTCAMP`:

```
THECRUX-BOOTCAMP
└── thecrux-bristlecone-bootcamp
    ├── session-0-hello-claude.md   ← this file
    ├── session-1-claude-md.md
    ├── session-2-skills.md
    └── ...
```

Click the arrow next to `thecrux-bristlecone-bootcamp` to expand it. You should see all the session files. That's everything for the two days sitting on your machine.

> If the folder didn't appear, tell Claude: `The clone didn't seem to work — what do I check?` Claude will diagnose it. If you're still stuck, raise your hand.

---

## Step 6: Exit Claude, move into the new folder, and reopen Claude

This is the most important step of the setup. Right now Claude is running inside the empty `thecrux-bootcamp` folder. You want it working **inside** the `thecrux-bristlecone-bootcamp` folder so it can see and work with the session files.

**Step 6a - Exit Claude.** Type this at the Claude prompt and press **Enter**:

```
/exit
```

Claude closes. You're back in the terminal (you'll see the usual terminal prompt, not the `>` Claude prompt).

**Step 6b - Move into the new folder.** In the terminal, type this and press **Enter**:

```
cd thecrux-bristlecone-bootcamp
```

`cd` means "change directory" — it moves you into a folder. This is one of only two terminal commands you'll use today (`cd` and `claude`).

> **Mac note:** your prompt might show a `%` or `$` at the end — that's normal. Just type the command after it.
>
> **Windows note:** your prompt might show `PS` at the start — that's PowerShell, and it's fine. The command is the same.

**Step 6c - Start Claude again.** Type this and press **Enter**:

```
claude
```

Claude starts back up. This time it's running inside `thecrux-bristlecone-bootcamp`. It can now see and work with all the session files.

> **How to tell it worked:** ask Claude `What folder are you in right now?` It should say the `thecrux-bristlecone-bootcamp` folder. If it says `thecrux-bootcamp`, you're still in the wrong folder — type `/exit`, then try step 6b again.

---

## Step 7: Your first prompt - a tiny win

Now Claude is in the right place, let's put it to work.

Type this into Claude and press **Enter**:

```
Who are you and what can you help me with? Keep it to five lines.
```

Claude introduces itself. First conversation done.

Now make it do something real:

```
What's inside this folder, and what is this bootcamp about? Explain it in plain English.
```

Claude reads your folder and tells you, in normal words, what's there and what the two days hold. You didn't need to know anything technical. You asked, it acted.

---

## Step 8: Watch Claude ask permission

Here's the most important habit of the day. Before Claude creates, changes, or deletes anything, it **asks you first.** You approve or deny. Always.

Let's see it. Type this:

```
Create a file called hello.txt in this folder with one line inside it that says: My first day with Claude Code at Bristlecone.
```

Claude doesn't just do it. It shows you exactly what it wants to write, then asks your permission. You'll see options like:

- **Yes** (allow this once)
- **Yes, and don't ask again this session**
- **No** (deny)

Choose **Yes** to allow it once. Read what it's proposing before you approve. That five-second habit keeps you in control.

Then check it worked:

```
Read hello.txt back to me.
```

Claude reads the file and shows you the line. You just created your first file with AI, and you approved it before it landed.

> **The permission model in one sentence:** Claude proposes, you approve. This is not autopilot. It's a very fast colleague who checks with you before acting.

---

## Step 9: The Claude commands you'll use every day

Inside Claude Code, anything starting with `/` is a **command** to the tool itself. Type `/` and the full list pops up.

Here are the ones worth knowing today. Try a couple now.

| Command | What it does | When you'll use it |
| --- | --- | --- |
| `/help` | Shows all commands and quick help | When you forget a command |
| `/permissions` | Shows and changes what Claude can do without asking each time | To stop approving the same safe action over and over |
| `/model` | Shows which Claude model you're on, and lets you switch | When you want the most powerful model for hard work |
| `/usage` | Shows how much of your plan you've used | To keep an eye on your limits |
| `/context` | Shows how full Claude's memory of this chat is | When a long chat starts to feel sluggish |
| `/compact` | Summarises the chat so far to free up space, and keeps going | When `/context` shows you're getting full |
| `/clear` | Wipes the conversation and starts fresh | When you switch to a brand new task |
| `/exit` | Closes Claude | When you're done or need to move folders |

Try these now:

```
/context
```

```
/model
```

`/context` shows a bar of how much of Claude's working memory this conversation is using. Early in a chat it's nearly empty. When it fills up on a long task, use `/compact` to summarise and keep going, or `/clear` for a completely fresh start.

> **Important:** `/clear` and `/compact` only affect the **conversation**, never your files. Your `hello.txt`, every file on disk — all safe. Clearing the chat is like starting a new email thread, not deleting your documents.

---

## Step 10: A taste of real work

A small taste before we wrap. Type this into Claude:

```
I work in supply chain consulting. Draft a short, neutral status update I could send to a delivery lead about a SAP rollout that has slipped by two weeks. Keep it to four lines. No blame, just facts and the next step.
```

Claude drafts it. Now correct it without starting over — just nudge it:

```
Make it a bit warmer and add one line reassuring them the timeline is recoverable.
```

Claude builds on what it already wrote. You didn't repeat the brief. You nudged it. This is how you'll work for two days: a conversation, not a one-shot.

> **Learning point:** When Claude gives you something 80% right, don't rewrite your whole prompt. Just say "change this part." Treat it like a colleague who handed you a draft.

---

## What you just did

In this session, you:

- Made your `thecrux-bootcamp` folder and opened it in VS Code
- Started Claude with a single word: `claude`
- Asked Claude to clone the bootcamp repo, and approved it
- Confirmed the files appeared in the VS Code Explorer panel
- Exited Claude, `cd`'d into the new folder, and reopened Claude inside it
- Ran your first prompts and watched the permission model in action
- Tried `/context` and `/model`, and know when to use `/clear` and `/compact`
- Made Claude draft real work and corrected it in one line

That's the whole rhythm of the bootcamp. You've already got it.

---

## Where today and tomorrow are going

| Session | What you'll build |
| --- | --- |
| **CLAUDE.md** (next) | A context file that tells Claude who you are and how you work |
| **Skills** | Your own `/` commands that bottle a repeated task, in your voice |
| **Workflows and Agents** | A research workflow with structured synthesis, plus your own agent |
| **Security & Governance** | Safe defaults and an AI governance playbook you can roll out |
| **Build** (Day 2) | A branded report, dashboard and deck from one spreadsheet |

---

## Quick reference - keep this open

### Starting Claude each time

1. Open VS Code with the `thecrux-bristlecone-bootcamp` folder (**File → Open Folder...**).
2. Open a terminal (**Terminal → New Terminal**).
3. Type `claude` and press Enter.

OR, if you're continuing from where you left off:

1. Open a terminal in VS Code.
2. `cd thecrux-bristlecone-bootcamp` (if you're not already there).
3. `claude`.

### Claude commands (type `/` to see them all)

| Command | What it does |
| --- | --- |
| `/help` | List all commands |
| `/permissions` | Control what Claude can do without asking |
| `/model` | See or switch the Claude model |
| `/usage` | See your plan usage |
| `/context` | See how full the chat's memory is |
| `/compact` | Summarise the chat to free up space |
| `/clear` | Start a fresh conversation (files stay safe) |
| `/exit` | Leave Claude Code |

### Keyboard controls inside Claude

| Key | What it does |
| --- | --- |
| `Escape` | Stop Claude mid-response |
| `Ctrl + C` (twice) | Exit Claude |
| Up arrow | Bring back your last typed line |

---

## Checkpoint: Session 0 complete

> - [ ] `thecrux-bootcamp` folder made and opened in VS Code
> - [ ] Claude started by typing `claude` in the terminal
> - [ ] Asked Claude to clone the bootcamp repo, and approved it
> - [ ] Confirmed the folder `thecrux-bristlecone-bootcamp` appeared in the VS Code Explorer
> - [ ] Typed `/exit`, then `cd thecrux-bristlecone-bootcamp`, then `claude` to reopen in the right folder
> - [ ] First prompt run, first file created with permission, first draft corrected
> - [ ] Tried `/context` and `/model`, and know what `/clear` and `/compact` do

---

## Troubleshooting - Session 0

Quick fixes, all of them. If anything here doesn't clear up in a couple of minutes, ask the team.

| Issue | What's happening | Fix |
| --- | --- | --- |
| Typing `claude` says "command not found" | The pre-work install didn't finish, or it's an odd terminal window | Close the terminal panel, open a new one (**Terminal → New Terminal**), type `claude` again. If still failing, raise your hand. |
| Claude asks me to log in again | First-run login hiccup | Press `Ctrl + C`, type `claude` again. If the browser won't open, raise your hand. |
| The clone didn't work | Network or permission hiccup | Copy the red error text and paste it to Claude with "this didn't work, what's the fix?" If still stuck, raise your hand. |
| After `cd`, it says "No such file or directory" | The folder name was typed wrong, or the clone didn't finish | Check the exact folder name in VS Code Explorer — it must be `thecrux-bristlecone-bootcamp`. Copy-paste it to be safe. |
| Claude says it can't see the session files | Claude is still in `thecrux-bootcamp`, not inside the cloned folder | Type `/exit`, then `cd thecrux-bristlecone-bootcamp`, then `claude`. |
| I don't see the session files in VS Code Explorer | You're looking at the wrong folder | Use **File → Open Folder...** and open the `thecrux-bristlecone-bootcamp` folder. The session files live there. |
| VS Code asks if I trust the authors | Normal safety prompt | Click **Yes, I trust the authors**. These are your own course files. |
| Claude seems stuck or confused | It happens | Press `Escape` to stop it. If it's still odd, `/clear` for a fresh conversation. |
| The chat feels slow after a long task | The conversation has grown large | Run `/context` to check, then `/compact` to summarise, or `/clear` to start fresh. |
| Not sure what to do next | Easy to lose your place | Take it one grey box at a time. Ask the team any time. |

---

**Next:** [Session 1: Your Work DNA →](session-1-claude-md.md)
