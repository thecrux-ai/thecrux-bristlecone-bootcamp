---
name: slide-creator
description: >
  Generates a beautiful, self-contained HTML slideshow from any input: a free-form
  topic description, a structured outline or bullet points, an existing markdown or
  text file, or a JSON data payload. Produces a single HTML file with keyboard and
  click navigation, smooth transitions, and a theme the user picks each run.
  Invoke whenever the user wants to make slides, a presentation, a deck, a slideshow,
  or a pitch — even if they say "turn this into slides", "make me a deck about X",
  "build a presentation from this file", or just paste an outline and ask to visualize it.
---

# slide-creator

You generate a polished, self-contained HTML slideshow. No dependencies, no build step —
a single `.html` file the user can open in any browser, present with, and share.

## Step 1: Understand the input

Figure out what the user has given you. Match to one of these four cases:

**Case A — Free-form topic or description**
The user says something like "make a 10-slide deck about climate change" or "build a
presentation on how our product works". There's no pre-existing content.
→ You will generate all the content. Ask about scope in Step 2.

**Case B — Outline or bullet points (pasted inline)**
The user pastes slide titles, bullet points, or rough structure directly in the chat.
→ Parse what they gave you. No extra questions about content, only design.

**Case C — Markdown or text file**
The user points to a file path (`.md`, `.txt`, `.mdx`, etc.).
→ Read the file. Parse headings as slide titles, body text as slide content.
   Treat `---` or `***` as explicit slide breaks if present.

**Case D — JSON payload**
The user provides structured data, e.g.:
```json
[
  { "title": "Slide 1", "body": "...", "notes": "..." },
  ...
]
```
→ Use the JSON directly. Keys `title`, `heading`, `body`, `content`, `bullets`,
  `notes`, `image` are all recognized. Gracefully ignore unrecognized keys.

If the input is ambiguous, briefly state which case you're treating it as and proceed.
Don't ask for confirmation unless the input is completely unclear.

---

## Step 2: Gather missing details (only what you need)

**For Case A only:** ask the user:
- How many slides? (default: 10 if they don't say — treat any number they give as a hard cap, not a suggestion)
- Audience and purpose? (e.g. "investors", "internal team", "conference talk")

**For all cases:** ask about **visual theme** — show these 4 options:

```
A) Clean minimal     — white background, subtle type, lots of whitespace
B) Dark / developer  — dark bg (#0f1117), monospace accents, code-friendly
C) Bold & editorial  — strong typography, accent color block, high contrast
D) Warm startup      — off-white, earthy tones, friendly and approachable
```

Also ask: do they want a **title slide** prepended if the content doesn't have one?
(default: yes if Case A, no otherwise — just confirm or skip based on context)

Combine these into a single AskUserQuestion if you need to ask at all. For Cases B/C/D
where content is clear, only the theme question is needed.

---

## Step 3: Plan the slides

**First, establish the slide budget:**
- If the user specified a count ("10 slides", "6 max", "keep it to 5"), that number is a hard cap. Do not exceed it.
- For Case A with no count given: default budget is 10.
- For Cases B/C/D (structured input): budget = number of top-level sections + 1 (for title). A 4-section outline → 5 slides. Do not expand each section into multiple slides unless the user asked for that.

Output a brief numbered slide plan:
```
Slide budget: N  ← state this explicitly
1. [Title slide] Topic — Author / Date
2. [Agenda] What we'll cover
3. [Slide title] Key point summary
...
N. [Closer] Call to action
```

Keep it to 2–3 words per slide so the user can scan it fast. **Count your plan.** If the total exceeds the budget, merge or cut slides before proceeding — don't ask, just fix it. A "10-slide deck" means 10 slides, not 12 because you had great ideas. Cut the weakest slides. The constraint is what makes a tight deck useful.

For Case A content generation: write slides that are substantive and specific. Avoid
platitudes, generic bullet lists, and filler. Real data > vague claims. Short punchy
bullets > long paragraphs. Each slide should have ONE main idea.

---

## Step 4: Generate the HTML slideshow

**Before writing: verify your slide plan matches the budget.** If you planned N slides and the budget is M, and N > M, go back and cut. Writing HTML for more slides than the budget is the most common failure mode. Do not rationalize overrun with "but each section needed its own slide."

Write a single self-contained HTML file. Save it to:
`/tmp/slideshow-<slug>-<YYYYMMDD>.html`
where `<slug>` is a 2–3 word kebab-case name derived from the topic.

### Required structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Presentation Title]</title>
  <style>
    /* All CSS inline — no external stylesheets */
  </style>
</head>
<body>
  <!-- Slide deck container -->
  <div id="deck">
    <div class="slide active" data-index="0"> ... </div>
    <div class="slide" data-index="1"> ... </div>
    <!-- ... -->
  </div>
  <!-- Navigation controls -->
  <div id="controls"> ... </div>
  <!-- Slide counter -->
  <div id="counter">1 / N</div>
  <script>
    /* All JS inline */
  </script>
</body>
</html>
```

### Navigation (implement exactly this)

```js
let current = 0;
const slides = document.querySelectorAll('.slide');
const counter = document.getElementById('counter');

function goTo(n) {
  slides[current].classList.remove('active');
  current = Math.max(0, Math.min(n, slides.length - 1));
  slides[current].classList.add('active');
  counter.textContent = `${current + 1} / ${slides.length}`;
}

document.addEventListener('keydown', e => {
  if (e.key === 'ArrowRight' || e.key === 'ArrowDown' || e.key === ' ') goTo(current + 1);
  if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') goTo(current - 1);
  if (e.key === 'Home') goTo(0);
  if (e.key === 'End') goTo(slides.length - 1);
});

// Click left/right halves of the screen to navigate
document.getElementById('deck').addEventListener('click', e => {
  const mid = window.innerWidth / 2;
  if (e.clientX > mid) goTo(current + 1);
  else goTo(current - 1);
});
```

### CSS transitions (smooth, not flashy)

```css
.slide {
  display: none;
  animation: fadein 0.25s ease;
}
.slide.active {
  display: flex; /* or grid, depending on layout */
}
@keyframes fadein {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

### Theme tokens

Apply the chosen theme via CSS custom properties at `:root`. Use these as the
canonical tokens for each theme:

**A — Clean minimal**
```css
:root {
  --bg: #ffffff; --bg2: #f8f8f8; --fg: #111111; --fg2: #555555;
  --accent: #2563eb; --font-body: 'Inter', system-ui, sans-serif;
  --font-heading: 'Inter', system-ui, sans-serif; --mono: 'JetBrains Mono', monospace;
}
```

**B — Dark / developer**
```css
:root {
  --bg: #0f1117; --bg2: #1a1d27; --fg: #e8eaf0; --fg2: #8892a4;
  --accent: #7c3aed; --font-body: 'JetBrains Mono', monospace;
  --font-heading: 'JetBrains Mono', monospace; --mono: 'JetBrains Mono', monospace;
}
```

**C — Bold & editorial**
```css
:root {
  --bg: #ffffff; --bg2: #111111; --fg: #111111; --fg2: #444444;
  --accent: #ef4444; --font-body: 'DM Sans', system-ui, sans-serif;
  --font-heading: 'DM Serif Display', Georgia, serif; --mono: 'JetBrains Mono', monospace;
}
```

**D — Warm startup**
```css
:root {
  --bg: #faf8f5; --bg2: #f0ebe3; --fg: #2d2a26; --fg2: #6b6560;
  --accent: #d97706; --font-body: 'Plus Jakarta Sans', system-ui, sans-serif;
  --font-heading: 'Plus Jakarta Sans', system-ui, sans-serif; --mono: 'JetBrains Mono', monospace;
}
```

Load fonts via Google Fonts `<link>` tags in `<head>`.

### Slide layout rules

Design each slide around ONE of these layout types, chosen to fit its content:

| Layout | When to use |
|--------|-------------|
| **Title** | Opening slide, section dividers |
| **Hero + body** | Key statement + supporting text |
| **Bullets** | 3–6 items (max), never more |
| **Two-column** | Side-by-side comparison or image + text |
| **Quote** | Standout quote, large type, attributed |
| **Code** | Code snippet, monospace block |
| **Stat** | Big number / key metric front and center |
| **Blank canvas** | Content-free breather or section end |

Use a `data-layout` attribute on each slide div. Apply distinct CSS grid/flex rules
per layout. Don't default every slide to "bullets".

The title slide always gets special treatment: large type, centered, full-bleed
background color (use `--bg2` or `--accent` depending on theme).

### Content rules

- Bullet points: 6 words max per bullet. Period. Not sentences.
- Slide body text: never more than 40 words total.
- Headings: punchy, not descriptive. "Revenue doubled" not "Revenue increased significantly".
- Code slides: use `<pre><code>` with a `<span class="comment">` for inline annotation.
- Never use lorem ipsum. If content is absent, make something realistic up or leave
  the slide visually structured but note it for the user.

### Slide counter and controls UI

```html
<div id="counter">1 / 12</div>
<div id="nav">
  <button onclick="goTo(current-1)">&#8592;</button>
  <button onclick="goTo(current+1)">&#8594;</button>
</div>
```

Position counter bottom-right, nav buttons bottom-center. These should be visible but
not intrusive — small, low-opacity until hover.

### Accessibility

- Each slide has `role="region"` and `aria-label="Slide N of M"`.
- The deck root has `aria-live="polite"` so screen readers announce navigation.
- Color contrast meets WCAG AA for body text against background.
- The active slide has `aria-current="true"`.

---

## Step 5: Open and preview

```bash
open /tmp/slideshow-<slug>-<YYYYMMDD>.html
```

Tell the user:
- Path to the file
- Total number of slides
- Navigation: arrow keys, space bar, or click left/right halves

---

## Step 6: Refinement loop

Ask: "How does it look? Anything to adjust — content, layout, theme, specific slides?"

Apply changes with surgical edits (Edit tool, not full rewrite). After each change,
briefly say what was updated (1 sentence). Re-open if the user seems to be reviewing
in a different window.

Exit when the user says "done", "looks good", "ship it", or similar.

---

## Important rules

- **One HTML file, zero dependencies.** No CDN JS, no external CSS. Google Fonts via
  `<link>` is the only allowed external resource.
- **Real content over placeholders.** Generate specific, substantive slide content.
  Vague fillers destroy trust in the output.
- **Layout variety.** A deck where every slide is "heading + bullets" is boring. Mix
  layouts deliberately.
- **Don't over-animate.** Subtle fade is enough. No flying elements, no parallax,
  no dramatic 3D transitions. The content is the show.
- **Surgical edits in refinement.** Never regenerate the full file to fix one slide.
