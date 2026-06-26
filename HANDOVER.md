# Help Me Learn — Handover Document

## What This Is
A single-page web app for students in Grades 6–10 about how to learn effectively.  
All content lives in **`index.html`** — one file, no build tools, no dependencies.

**Live site:** https://aerwin-sgcs.github.io/HelpMeLearn/  
**GitHub repo:** https://github.com/aerwin-sgcs/HelpMeLearn  
**Local path:** `/Users/aerwin/Desktop/2026 CLAUDE ACCESS/HelpMeLearn/HelpMeLearn/`  
**Push via:** GitHub Desktop, authenticated as `aerwin-sgcs`

---

## Colour Palette
| Name | Hex |
|---|---|
| Light teal | `#A8DADC` |
| Steel blue | `#457B9D` |
| Cream (background) | `#F1FAEE` |
| Yellow | `#F1C40F` |
| Teal | `#2A9D8F` |
| Dark navy (text) | `#1D3557` |
| Dark green | `#2d5a1b` |

**No gradient backgrounds** — all backgrounds use solid colours only. Gradients were removed for readability (white text was unreadable on pale gradient stops).

---

## Version Control
- `index.html` — always the current working version
- `indexv1.html` — snapshot before the Learnership page was added
- `indexv2.html` — snapshot before the interactive Learnership modals were added
- When making significant changes: save current `index.html` as `indexv[n].html` first, then edit

---

## Navigation Pages (in order)

### 1. Home (`home`)
- Hero with tagline and four quick-link cards to other sections
- Three intro cards: "It's a skill not a gift", "Work smarter not longer", "Growth is always possible"
- Highlight box and a quote

### 2. Learning Ceilings (`ceilings`)
- **Intro paragraphs at the top of the page** (added 2026-06) explaining what a ceiling is, how it happens at different ages (Year 8, Year 10, gap-year examples), and why breaking through matters
- Ceiling visual box and "Why we hit ceilings" — 6 cards (includes Cognitive Overload and Lack of Deliberate Practice)
- **5-step "smash through a ceiling" guide** (Identify, Switch strategy, Embrace struggle, Rest, Get a different perspective)
- **12 additional ceiling-smashing strategy cards** (numbered 1–12)
- **Bonus Challenge: The Learning Ceiling Ladder** — dark navy panel with inline SVG ladder illustration
- Key Mindset Shift yellow callout

### 3. Ways to Learn (`learn`)
- **Categorised into 4 sections with scrolling nav buttons at the top:**
  - ⚡ **Active Learning** — One-Minute Summary, Retrieval Brain Dump, Draw It, Sketch Notes, Question Storming, Rank and Justify, Teach Someone Else, The Feynman Technique
  - 🧠 **Brain Science** — Flashcard Recall, The Story Method, Create Analogies, Dual Coding, Make Predictions, Memory Palaces
  - 💾 **Memory** — Colour Coding, Mind Mapping, Compare and Contrast Tables, Create Acronyms and Mnemonics
  - 🎨 **Creativity** — Set It to Music, Use Gestures and Movement, Remix the Learning, Become the Concept
- Each section has a styled header: coloured icon box + uppercase category label + heading + description paragraph
- `scroll-margin-top: 90px` on each section anchor to clear the fixed nav
- The Learning Pyramid highlight box and Benjamin Franklin quote at the bottom

### 4. Try It Now (`try`)
- New page added between Ways to Learn and Ways to Study in the nav
- Students pick **up to 3 strategies** from the full 22-item Ways to Learn list
- Strategies are grouped by category (Active Learning, Brain Science, Memory, Creativity) with colour-coded selectable buttons
- Selecting a 4th strategy is blocked with an inline message; tapping a selected strategy deselects it
- Once 3 are chosen, a "Your 3 to try" section appears below with one activity card per selection — each card contains a short, immediately actionable prompt requiring only paper and a pen
- A "Start fresh" button resets all selections
- Selections persist in `localStorage` under key `try_picks` (JSON array of up to 3 strategy IDs)
- `initTry()` is called from `showPage()` when `id === 'try'`
- Activity prompts are stored in the `TRY_DATA` object in the script block

### 5. Ways to Study (`study`)
- **Categorised into 6 sections with scrolling nav buttons at the top:**
  - 🔑 **Secret Weapons** — The Pomodoro Technique, Interleaving, Spaced Repetition, Practice Testing, Elaboration, Dual Coding
  - 🏠 **Your Study Space** — Phone Away, The Music Question, Change Your Location + Before-You-Start Ritual yellow box + 3-step session guide
  - 🤸 **Physical & Movement** — 10 movement-based methods
  - 🎨 **Creative & Visual** — 6 methods
  - 👥 **Social & Interactive** — 4 methods
  - 💡 **Outside the Box** — 10 unusual methods in unusual-grid layout
- "The Strongest Combination" yellow box at the bottom
- Note: section was previously called "Study Strategies" — renamed to "Secret Weapons" as "strategies" is too complex for Grade 6

### 6. Let's Begin (`practical`)
- Interactive tick-off checklist (7 items) — labelled "Start Here: Your Challenges"
- 6 quick-win cards
- Highlight box reminder to pick one strategy and stick with it

### 7. Learnership (`learnership`)
- **James Anderson's** "Learnership: The Skill of Learning" framework
- Credit and link: www.jamesanderson.com.au/learnership
- Recreated pill-row table: 6 learner types × 5 dimensions
- Every cell and row label is a **clickable button** opening a modal
- 6 explanation cards below the table (one per learner type)
- Key insight callout

### 8. My Reflection (`reflection`)
- **Summary strip** — live counts of ticked / crossed / yet to try
- **Progress celebration panel** (`#reflect-progress`) — appears once the student has ticked 1+ strategy:
  - Benchmark message: "You've tried [n] strategies — most students try 3 or fewer"
  - Own-progress message: compares current tick count to the count at the start of the previous session ("Last visit you'd tried X — now Y. That's Z more.")
  - Milestone messages at 5, 10, 15, 20 strategies ticked
  - Session tracking uses `sessionStorage` key `reflect_session_started`; at the start of each new session, current tick count is saved to `localStorage` key `reflect_prev_count`
- **Learnership nudge** (`#learnership-nudge`) — teal callout, hidden by default; appears dynamically when the student has ticked ✓ on 10 or more Ways to Learn strategies; contains a link to the Learnership page
- **Two range sliders** (1 = Non-Learner → 6 = Agile Learner)
- **Methods tracker** — all 56 methods listed across 6 categories, each with ✓ and ✗ buttons
  - State persists in `localStorage` (key format: `method_<id>`)
  - Reset button with confirmation prompt

---

## Learnership Table — Full Content

| | Challenge | Habits of Mind | Mistakes | Feedback | Time & Energy |
|---|---|---|---|---|---|
| **Agile Learner** | Embraces | Cultivates | Designs | Tailors | Growing |
| **Independent Learner** | Targets | Develops | Uses | Requests | Striving |
| **Directed Learner** | Attempts | Extends | Corrects | Responds | Producing |
| **Performance Learner** | Limits | Applies | Avoids | Selects | Performing |
| **Beginner Learner** | Reduces | Describes | Recognises | Acknowledges | Doing |
| **Non-Learner** | Avoids | Ignorant | Ignores | Disregards | Wastes |

Row colours: dark→light green (Agile→Directed), medium→dark blue (Performance→Non-Learner)  
Column header colours: green / blue / orange / pink / purple

---

## All 56 Methods (used in My Reflection tracker)

### Ways to Learn (22)
1. The Feynman Technique
2. Mind Mapping
3. Flashcard Recall
4. Teach Someone Else
5. Set It to Music
6. The Story Method
7. Sketch Notes
8. Question Storming
9. Draw It
10. One-Minute Summary
11. Create Analogies
12. Use Gestures and Movement
13. Dual Coding
14. Retrieval Brain Dump
15. Colour Coding
16. Memory Palaces
17. Create Acronyms & Mnemonics
18. Compare and Contrast Tables
19. Rank and Justify
20. Make Predictions
21. Remix the Learning
22. Become the Concept

### Ways to Study (6)
23. Pomodoro Technique
24. Interleaving
25. Spaced Repetition
26. Practice Testing
27. Elaboration
28. Dual Coding

### Physical & Movement (10)
29. Walk and Recall
30. Corners Challenge
31. Human Timeline
32. Sticky Note Hunt
33. Basketball Revision
34. Throw-and-Answer
35. Learning Relay
36. Gesture Coding
37. Hopscotch Revision
38. Memory Walk

### Creative & Visual (5)
39. Comic Strip Learning
40. Doodle Notes
41. Build a Model
42. Create an Infographic
43. Colour-Coded Connections

### Social & Interactive (4)
44. Teach a Toy
45. Quiz Show
46. Expert Panel
47. Speed Teaching

### Unusual Methods (10)
48. Write notes in chalk outside
49. Treasure hunt revision
50. Giant floor mind map
51. Record a podcast
52. Study at a whiteboard
53. "Top 10 Things" lists
54. Playing card flashcards
55. Board game revision
56. Act out processes or events
57. Create memes

---

## Technical Notes

- **Navigation:** JS function `showPage(id)` swaps `.active` class on sections and nav buttons. Calling `showPage('reflection')` also triggers `initReflection()`.
- **Modals:** `openModal(id)` / `closeModal()` — data lives in `MODAL_DATA` object in the script block. Closes on ✕ button, backdrop click, or Escape key.
- **localStorage keys:**
  - `reflect_current` — current learner slider value (1–6)
  - `reflect_target` — target learner slider value (1–6)
  - `method_<id>` — `'tick'`, `'cross'`, or `''` for each method
- **Back-to-top button** — fixed, bottom-right corner, `id="back-to-top"`. Hidden (opacity 0) until 300px scroll depth, then fades in. Scrolls to `top: 0` with smooth behaviour. CSS in the stylesheet; JS scroll listener inline in the script block.
- **Section nav buttons** — Ways to Learn and Ways to Study both have a row of pill-shaped buttons at the top that `scrollIntoView({behavior:'smooth'})` to section anchors. Each anchor has `scroll-margin-top: 90px` to clear the fixed nav bar.
- **iPad optimised:** min touch targets 44px, no hover-only interactions, horizontal scroll on Learnership table for portrait mode
- **No external dependencies** — pure HTML/CSS/JS, no frameworks or libraries
- **SVG ladder** on the Learning Ceilings page is inline (no external image file needed)
- **Em dashes** — removed site-wide and replaced with commas, semicolons, colons, or parentheses. Three remain intentionally in quote citations (Henry Ford, Benjamin Franklin, Dr. Seuss).

---

## Design Decisions Made
- Single `.html` file — simplest possible deployment, works offline
- Filename versioning (`indexv1.html`, `indexv2.html`) instead of branch-per-feature
- No gradient backgrounds — replaced with solid colours for text readability
- Nav is full-width column layout (logo centred above buttons) so wrapping always looks intentional
- "Secret Weapons" used instead of "Study Strategies" for the first Ways to Study section — "strategies" is too complex for Grade 6
- My Reflection tracker categories mirror page names exactly: "Ways to Learn" and "Ways to Study"
- Footer reads "Help Me Learn" (app title)

---

## Possible Future Work
- Individual student profiles / login
- Teacher view to see class reflection data
- Printable versions of the Learnership table
- More content on specific subjects (e.g. how to apply these strategies to Maths vs English)
- Animations or transitions between pages
