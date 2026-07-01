[← Back to Student Handbook](student-handbook.md)

---

# Extra Handbook: Connect Claude to Your Microsoft Tools (MCP + Connectors)

**What you unlock:** Claude searches and reads your Outlook inbox, your SharePoint files, your OneDrive, and your Teams chats directly. No copy-paste. You ask in plain English, Claude pulls the live data, and it triages your inbox using your own rules.

This handbook is optional. The main bootcamp runs fully on your laptop with no outside connections. This is for when you are ready to let Claude reach into your real work tools, safely.

Everything here runs on **claude.ai** (the web and desktop app), not the terminal. If you have only used Claude Code so far, this is a different door into the same Claude.

*Current as of 1 July 2026. Claude's menus change every few months. If a button name here does not match your screen, check the live help pages linked at the bottom.*

---

## What Is MCP, and What Is a Connector? (3 min, read don't type)

So far, everything Claude knows comes from files you give it. But your real work lives in Outlook, SharePoint, Teams, and a dozen other tools. How does Claude reach those?

**MCP, Model Context Protocol,** is the answer. MCP is an open standard that lets Claude connect to outside services. Think of it as a USB port for AI: any service that speaks MCP can plug into Claude and share data.

A **connector** is the plug. On claude.ai, a connector is a ready-made MCP link to a service. You turn it on, log in once, and Claude can read that service from then on.

There are two kinds:

- **Native connectors** are built into claude.ai. One of them is **Microsoft 365**, and a single switch covers Outlook, SharePoint, OneDrive, Teams, and your calendar together. This is the easy path, and it is what most of this handbook covers.
- **Custom connectors** are ones you add yourself by pasting a web address (the MCP server URL). This is how you connect tools that are not in the built-in list. Covered in Part C.

> **Two things to know before you start.**
> 1. The Microsoft 365 connector is **read-only**. Claude can search and read your email, files, and chats. It cannot send email, change files, or delete anything. You stay in control of every action.
> 2. A connector still lets your data flow to Claude. For Bristlecone client work, follow the same rule from the Security session: no outside connection on a client project without IT and security signing off. Connect your own work tools first, learn the pattern, then decide what is safe for client data.

---

## Part A: Connect Claude to Microsoft 365 (Outlook + SharePoint)

**What you unlock:** Claude can search and read your Outlook email, your SharePoint document libraries, your OneDrive files, and your Teams chats. One connector does all four. This is the foundation for the inbox triage in Part B.

---

### Before you start: two requirements

1. **You need a Bristlecone work account.** The Microsoft 365 connector needs a Microsoft work or school account (a Microsoft Entra tenant on a Business plan). Personal accounts like `@outlook.com` or `@hotmail.com` will not connect. Your Bristlecone email is exactly what it wants.

2. **An admin has to approve it once.** Before anyone at Bristlecone can connect, a Microsoft administrator (a Global Admin) has to give consent for the whole tenant. This is a one-time step. If you try to connect and get blocked with a permissions message, that approval has not happened yet. Send your IT contact the link at the bottom of this handbook and ask them to enable it.

The connector itself works on **every Claude plan, including Free.** So once IT approves it, cost is not the blocker.

---

### Step 1: Open the Connectors page

1. Go to **claude.ai** and sign in with your Bristlecone account.
2. Click your name (bottom left), then **Customize**.
3. Open **Connectors**.

This page is your connector directory. Everything Claude can plug into shows here. You can also open the full catalogue at **claude.ai/connectors**.

---

### Step 2: Connect Microsoft 365

1. In **Customize → Connectors**, find **Microsoft 365** in the list.
2. Click **Connect**.
3. A Microsoft login window opens. Sign in with your **Bristlecone work account**.
4. Microsoft shows you exactly what Claude will be allowed to do, and it is all read-only. Read it, then **Accept**.

Back on claude.ai, Microsoft 365 should now show as **Connected**.

That one connection covers your Outlook, SharePoint, OneDrive, Teams, and calendar. You do not connect them separately.

> **Why a separate login?** You are logging into Microsoft, not Claude. Microsoft hands Claude a limited, read-only key. You can pull that key back any time by clicking **Disconnect** here, or from your Microsoft account. Claude never sees your password.

---

### Step 3: Turn the connector on inside a chat

A connector being connected does not mean Claude uses it automatically. You switch it on per conversation.

1. Start a **new chat** on claude.ai.
2. Click the **+** button in the lower-left of the chat box (or type **/** and choose **Connectors**).
3. Toggle **Microsoft 365** on for this chat.

This is on purpose. You decide, conversation by conversation, what Claude is allowed to touch.

---

### Step 4: Verify it works

In the chat, type:

```
Search my Outlook inbox. Show me my 5 most recent emails.
For each: who it's from, the subject, and a one-line summary.
```

If you see your real emails, the Outlook side works.

Now test SharePoint:

```
Search our SharePoint. Find the 5 documents I've opened or changed most recently.
List each one with its name, the site or library it's in, and when it changed.
```

Both working? You are ready for Part B.

> **Nothing comes back?** Open **Customize → Connectors** and check Microsoft 365 shows **Connected**. If not, click **Reconnect** and log in again. Then confirm it is toggled on inside your chat (Step 3). Almost every problem is one of those two things.

---

### What each Microsoft 365 tool can do

One connector, five tools. Everything is read-only: Claude searches, reads, and summarises. It never sends, changes, or deletes. Here is what each one gives you, with a prompt to try.

**Outlook (email)**
Claude can search and read your messages, including the sender, subject, and date, your folder structure, and shared mailboxes you have access to. Good for finding threads, summarising long ones, and spotting action items.

```
Find my email thread with the vendor about the renewal.
Summarise it and list every action item still open, and who owns each one.
```

**Microsoft Teams**
Claude can read your chat messages, channel messages, and who was in each conversation. Good for catching up on a channel and pulling out decisions.

```
Summarise the key decisions from this week's chat in our delivery channel.
Flag anything that needs a reply from me.
```

**SharePoint**
Claude can search and read documents across every site and library you have access to, using your own permissions. Good for finding specs, plans, and contracts.

```
Search SharePoint for project proposals from the last three months.
Summarise the common themes across them.
```

**OneDrive**
Claude can search and read your own files and any file you have access to. Same idea as SharePoint, for your personal storage.

```
Find the latest version of my status report in OneDrive and give me the headline in two lines.
```

**Calendar**
Claude can read your calendar events and shared calendars. Good for prepping your week.

```
What meetings do I have this week about the Q3 go-live?
For each, tell me who's attending.
```

> **The real power is combining them.** Because it is one connector, you can ask across tools in a single prompt: "Search my Outlook and our Teams channel for anything about the Q3 go-live this week, and pull the latest plan from SharePoint." Claude reads all three and answers in one go.

> **A note on what it can't do.** No tool here sends, posts, files, or edits. Claude cannot reply to an email, post in Teams, change a SharePoint file, or add a calendar invite. It reads and tells you. You do the action. That is the read-only design, and it is what makes it safe to switch on.

---

## Part B: Triage Your Inbox with Outlook

**What you unlock:** Claude reads your live Outlook inbox and sorts it the way YOU would, using your own rules. Not generic "important vs not." Your people, your priorities, your red flags.

Remember the connector is read-only. Claude reads and triages and drafts reply text for you in the chat. It does not send, move, or file anything. You do the sending from Outlook yourself.

---

### Step 1: Give Claude your triage rules

Claude triages well only if it knows what matters to you. The best place to store this on claude.ai is a **Project**.

A Project is a folder for chats that share the same background instructions. Set your rules once, and every chat inside that Project follows them.

1. On claude.ai, create a new **Project**. Call it **Inbox Triage**.
2. Open the Project's **instructions** (the custom-instructions box for the Project).
3. Paste rules like the ones below. Edit them to be true for you.

```
You are my inbox assistant. When I ask you to triage my Outlook email,
sort every message into one of four buckets:

URGENT — flag immediately:
- Anything from my manager or my direct reports (list their names).
- Anything from a named client account I own (list the accounts).
- Words like "deadline", "blocker", "escalation", "down", "urgent", "EOD".
- Anything about a release or go-live in the next 48 hours.

IMPORTANT — put in my daily summary, not on fire:
- Project updates, meeting requests, approvals I owe someone.
- Anything from my wider team.

FYI — I should know, no action:
- CC threads where I'm not the main person.
- Newsletters from tools we actually use.

IGNORE — never show me:
- Marketing, promotions, recruiter spam, social notifications.

For each email, give me: sender, subject, the bucket, and one line on why.
List URGENT first.
```

The more specific you are with real names and real client accounts, the better the triage. Vague rules give vague results.

> **Already built a CLAUDE.md or a Chief of Staff manual in the bootcamp?** Reuse it. Paste the triage section from that file straight into your Project instructions. Same rules, new tool.

---

### Step 2: Run the triage

Inside the **Inbox Triage** Project, start a chat (make sure Microsoft 365 is toggled on, Part A Step 3) and type:

```
Search my Outlook inbox for everything from the last 24 hours.
Triage every email using my rules.
Then give me a short morning brief:

TOP PRIORITY: what I must handle in the next 2 hours.
URGENT: each email, sender, subject, one line.
IMPORTANT: grouped, one line each.
FYI: a single short list.
SUGGESTED REPLIES: for the top 3, draft one or two lines I could send.
```

Read what comes back. Is the triage right? Did it catch the things that actually matter? If something is in the wrong bucket, tell it: "Move anything from Priya to URGENT." Then update your Project instructions so it remembers next time.

You copy the drafted replies into Outlook and send them yourself. Claude drafts. You decide what goes out.

---

### Step 3: Connect the dots with SharePoint

This is where it gets useful. Ask Claude to pull a related document while it triages.

```
One of my urgent emails is about the [project name] status report.
Search SharePoint for that report, read it, and tell me in three lines
where the project actually stands before I reply.
```

Now Claude is not just sorting mail. It is reading the email, finding the matching document, and giving you the context to answer. That is the difference between an inbox sorter and a real assistant.

> **Want it to look wider?** Because one connector covers all of Microsoft 365, you can ask across tools in a single prompt: "Search my Outlook and our Teams for anything about the Q3 go-live this week, and pull the latest plan from SharePoint." Claude reads all three.

---

## Part C: Connect to Other MCPs from claude.ai

Microsoft 365 is the start. claude.ai connects to many more tools, two ways.

---

### Way 1: Native connectors (the directory)

Back in **Customize → Connectors** (or the full catalogue at **claude.ai/connectors**), scroll the list. Beyond Microsoft, you will usually find connectors for tools like **Slack**, **Linear**, **Notion**, **Asana**, **Atlassian (Jira/Confluence)**, **Canva**, and more.

Each one connects the same way: click **Connect**, log in to that tool, accept, then toggle it on inside your chat with the **+** button. If your tool is in this list, you never have to touch a web address.

> The exact list depends on your plan and on what your admin has allowed. On Team and Enterprise, an owner may need to add a connector for the org first before you see it.

---

### Way 2: Custom connectors (add by URL)

If a tool is not in the directory but it offers an MCP server, you can add it yourself.

1. Go to **Customize → Connectors**.
2. Click the **+** button, then **Add custom connector**.
3. Paste the **remote MCP server URL**. This is a web address the tool's vendor gives you, starting with `https://`.
4. If the tool needs it, open **Advanced settings** to enter an OAuth Client ID and Secret.
5. Click **Add**, then **Connect**, and log in if it asks.

Once added, a custom connector behaves like a native one. It shows in your tools list and you toggle it on per chat.

A few limits to know:

- **Free** users can add **one** custom connector. Pro, Max, Team, and Enterprise can add more.
- On **Team and Enterprise**, an owner adds the connector first under **Organization settings → Connectors** (choose **Custom**, then **Web**). Members then connect it from their own **Customize → Connectors**.
- The MCP server must be **reachable on the public internet**. A server behind a VPN, a firewall, or on a private company network will not connect, even if it works from your own laptop.

> **Where do I get the URL?** From the tool or its docs. Search "[tool name] MCP server URL". If a vendor supports MCP, they publish it. If they do not have one yet, you cannot add them this way.

> **Custom connectors and client data.** This is the most powerful and the most sensitive option. You are pointing Claude at an outside server. For anything touching Bristlecone client work, this goes through IT and security first. No exceptions. Same rule as the Security session.

---

> **Checkpoint: Claude connected to your Microsoft tools**
>
> - [ ] Microsoft 365 connected on claude.ai (one connector covers Outlook, SharePoint, OneDrive, Teams, calendar)
> - [ ] Microsoft 365 toggled on inside a chat with the **+** button
> - [ ] A "Inbox Triage" Project holds your triage rules
> - [ ] Claude triages your real Outlook inbox and produces a morning brief
> - [ ] Claude can pull a matching SharePoint doc while it triages
> - [ ] You know the connector is read-only: it drafts, you send
> - [ ] You know the two ways to add more tools: directory and custom URL

---

## Troubleshooting

| Issue | Fix |
| --- | --- |
| Can't connect, get a permissions or consent error | A Microsoft Global Admin has not approved the connector for Bristlecone yet. Send IT the Microsoft 365 connector help link below and ask them to grant consent for the tenant. |
| Tried to connect with a personal account | The connector only works with a Microsoft work/school account. Use your Bristlecone email, not an `@outlook.com` or `@hotmail.com` address. |
| Connected, but Claude says it can't see my email | The connector is connected but not turned on for this chat. Click the **+** button (lower-left of the chat) and toggle Microsoft 365 on. |
| Login window closes and nothing happens | Pop-up blocker. Allow pop-ups for claude.ai and click Connect again. |
| Triage puts things in the wrong bucket | Your rules are too vague. Add real names and real client accounts to your Project instructions, then run it again. |
| Claude pulls the wrong SharePoint file | Tell it the exact file name or the library it lives in. "Look in the Delivery library for the file called X." |
| I asked Claude to send or file an email and it didn't | By design. The connector is read-only. Claude drafts reply text in the chat. You copy it into Outlook and send it yourself. |
| Custom connector won't connect | The MCP server must be reachable on the public internet. A server behind a VPN, firewall, or private network won't work. Check the URL and the OAuth details. |
| Want to cut off access fast | **Customize → Connectors → Disconnect**. Or revoke it from your Microsoft account. Access stops at once. |

---

## Official help pages (current source of truth)

If a step here does not match your screen, these are the live Anthropic pages:

- [Set up and use the Microsoft 365 connector](https://support.claude.com/en/articles/12542951-enable-and-use-the-microsoft-365-connector)
- [Microsoft 365 connector security guide](https://support.claude.com/en/articles/12684923-microsoft-365-connector-security-guide)
- [Use connectors to extend Claude's capabilities](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities)
- [Get started with custom connectors using remote MCP](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)

---

**Back to:** [Student Handbook →](student-handbook.md)
