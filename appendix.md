# Appendix - Troubleshooting

Most problems on Day 1 are small. Here are the common ones and the fix. You won't need the terminal for any of this. Each session file also has its own troubleshooting at the bottom.

## Starting Claude

Remember the three steps from Session 0: open the `thecrux-bristlecone-bootcamp` folder in VS Code (**File → Open Folder...**), open a terminal (**Terminal → New Terminal**), and type `claude`.

**Typing `claude` says "not recognized"**
- Close the terminal panel and open a fresh one (**Terminal → New Terminal**), then type `claude` again.
- Still failing? This is a setup issue, not something you did. Raise your hand and a facilitator will sort it.

**Nothing happens after `claude`**
- Wait a few seconds on first run. It is loading.
- If it asks you to log in, follow the link and sign in with your Claude account.

**I can't find my project folder**
- Use **File → Open Folder...** in VS Code and pick `thecrux-bristlecone-bootcamp` (it's inside the `thecrux-bootcamp` folder you made in Session 0).

**A build needs something installed (Day 2)**
- You don't install anything by hand. If a build needs a tool, ask Claude to set it up: paste any error and say "fix this." If it can't, raise your hand.

## During a session

**Claude keeps asking permission for everything**
- That is normal and safe. Press `Shift + Tab` to switch to accept-edits mode once you trust what it is doing. See Session 4.

**Claude edited the wrong file**
- Tell it plainly: "Undo that last change." It will fix it.
- This is why we keep everything in one folder and use plan mode for big tasks.

**I lost my work / the conversation got messy**
- Your files are saved on disk, not in the chat. They are safe.
- Type `/clear` to start a clean conversation. Your CLAUDE.md and skills stay.

**A build won't run (Day 2)**
- Read the error out loud to Claude. Paste it in. Say: "Fix this." It usually can.
- If a chart or PDF library is missing, ask Claude to install it for you.

## Golden rules when stuck

1. Read the error to Claude. Paste it. Ask it to fix it.
2. If confused, switch to plan mode (`Shift + Tab`) and ask Claude to explain its plan first.
3. Scope down. A smaller version that works beats a big one that does not.
4. Raise your hand. A facilitator will come to you.

You cannot break anything that matters. Keep going.
