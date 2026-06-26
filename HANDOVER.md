# Breaking Through the Ceiling — Handover Document

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
- What a learning ceiling is, why we hit them (4 cards)
- **5-step "smash through a ceiling" guide** (Identify, Switch strategy, Embrace struggle, Rest, Get a different perspective)
- **12 additional ceiling-smashing strategy cards** (numbered 1–12):
  1. Learn the Opposite Way
  2. Teach an Imaginary Student
  3. Increase the Difficulty by 10%
  4. Switch Representation
  5. Hunt for Mistakes
  6. Connect It to Something Else
  7. Set a Constraint
  8. Ask Better Questions
  9. Deliberately Practise Your Weakest Skill
  10. Reflect Like a Scientist
  11. Create a Productive Struggle
  12. Change Your Learning Environment
- **Bonus Challenge: The Learning Ceiling Ladder** — dark navy panel with an inline SVG ladder illustration. 5 rungs: Notice → Experiment → Struggle → Reflect → Repeat. Closing note about changing approach rather than doing the same thing longer.
- Key Mindset Shift yellow callout

### 3. Ways to Learn (`learn`)
- 20 method cards in a grid (see full list below)
- The Learning Pyramid highlight box
- Benjamin Franklin quote

### 4. Ways to Study (`study`)
- Original 4 strategies: Pomodoro, Interleaving, Spaced Repetition, Practice Testing
- Study space tips (3 cards)
- Before-you-start ritual yellow box
- 3-step session guide
- **Physical & Movement** section (10 methods)
- **Creative & Visual** section (6 methods)
- **Social & Interactive** section (4 methods)
- **Unusual Methods** grid (10 ideas)
- Closing note: "Strongest combination is retrieval practice + movement + teaching someone else"

### 5. Practical Ideas (`practical`)
- Interactive tick-off checklist (7 items) — labelled "Start Here: Your Challenges"
- 6 quick-win cards
- Highlight box reminder to pick one strategy and stick with it

### 6. My Reflection (`reflection`)
- **Summary strip** — live counts of ticked / crossed / yet to try
- **Two range sliders** (1 = Non-Learner → 6 = Agile Learner):
  - "Where I am now" and "Where I want to be"
  - Dynamic gap message links to Learnership page
  - Slider state saved to `localStorage`
- **Methods tracker** — all 53 methods listed across 6 categories, each with ✓ and ✗ buttons
  - State persists in `localStorage` (key format: `method_<id>`)
  - Reset button with confirmation prompt

### 7. Learnership (`learnership`)
- **James Anderson's** "Learnership: The Skill of Learning" framework
- Credit and link: www.jamesanderson.com.au/learnership
- Recreated pill-row table: 6 learner types × 5 dimensions
- Every cell and row label is a **clickable button** opening a modal
- 6 explanation cards below the table (one per learner type)
- Key insight callout

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

Each of the 36 entries (30 cells + 6 row labels) opens a modal containing:
- Learner type badge + dimension badge
- Plain-English explanation
- 5 characteristics
- "How to move up" action step (or "Mastery" note for Agile Learner entries)

---

## All 53 Methods (used in My Reflection tracker)

### Ways to Learn (20)
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

### Study Strategies (4)
21. Pomodoro Technique
22. Interleaving
23. Spaced Repetition
24. Practice Testing

### Physical & Movement (10)
25. Walk and Recall
26. Corners Challenge
27. Human Timeline
28. Sticky Note Hunt
29. Basketball Revision
30. Throw-and-Answer
31. Learning Relay
32. Gesture Coding
33. Hopscotch Revision
34. Memory Walk

### Creative & Visual (5)
35. Comic Strip Learning
36. Doodle Notes
37. Build a Model
38. Create an Infographic
39. Colour-Coded Connections

### Social & Interactive (4)
40. Teach a Toy
41. Quiz Show
42. Expert Panel
43. Speed Teaching

### Unusual Methods (10)
44. Write notes in chalk outside
45. Treasure hunt revision
46. Giant floor mind map
47. Record a podcast
48. Study at a whiteboard
49. "Top 10 Things" lists
50. Playing card flashcards
51. Board game revision
52. Act out processes or events
53. Create memes

---

## Technical Notes

- **Navigation:** JS function `showPage(id)` swaps `.active` class on sections and nav buttons. Calling `showPage('reflection')` also triggers `initReflection()`.
- **Modals:** `openModal(id)` / `closeModal()` — data lives in `MODAL_DATA` object in the script block. Closes on ✕ button, backdrop click, or Escape key.
- **localStorage keys:**
  - `reflect_current` — current learner slider value (1–6)
  - `reflect_target` — target learner slider value (1–6)
  - `method_<id>` — `'tick'`, `'cross'`, or `''` for each method
- **iPad optimised:** min touch targets 44px, no hover-only interactions, horizontal scroll on Learnership table for portrait mode
- **No external dependencies** — pure HTML/CSS/JS, no frameworks or libraries
- **SVG ladder** on the Learning Ceilings page is inline (no external image file needed)

---

## Design Decisions Made
- Single `.html` file — simplest possible deployment, works offline
- Filename versioning (`indexv1.html`, `indexv2.html`) instead of branch-per-feature
- Footer text stripped back to just the app name
- Nav is full-width column layout (logo centred above buttons) so wrapping always looks intentional
- "Teach Someone Else" and "Question Storming" appear on Ways to Learn but NOT duplicated in Ways to Study; "Set It to Music" appears once in the tracker
- Reflection prompts on cards 11 and 12 of the ceiling strategies are styled in italic teal/steel-blue at the bottom of each card

---

## Possible Future Work
- Individual student profiles / login
- Teacher view to see class reflection data
- Printable versions of the Learnership table
- More content on specific subjects (e.g. how to apply these strategies to Maths vs English)
- Animations or transitions between pages
