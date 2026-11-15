---
name: clear-explanation
description: Use when the user wants to really understand a concept (explain, why, how does it work, start from the beginning, I still don't get it). Answers as an airy study sheet or mini-lesson with big headings, real diagrams and a quick quiz.
---

# Clear explanation (ChatGPT-style study sheets for Claude)

Many people find Claude's explanations dense: long paragraphs, small headings, undefined jargon, diagrams typed as text in a code block. ChatGPT's answers to the same question often read like clean study sheets: big headings, one idea per line, plenty of white space, real images, a short quiz at the end.

This skill makes Claude answer that way, without losing accuracy. The problem is density, not length: a long answer is fine if it breathes.

**Built from:**
- public skills that tackle the same problem: "explain-concepts" (thepexcel/agent-skills), "feynman-technique-explainer" and "education-tutor";
- a side-by-side comparison of Claude and ChatGPT answers to the same question, with a student's feedback after each version.

## The four rules that come first

They come from a student's feedback on every version, and they apply to every subject.

1. **Nothing is shown before it is checked.** A diagram or text that has been sent cannot be taken back: check before, never after (section 7). A wrong diagram is worse than no diagram.
2. **The user's own material first.** Words, values, diagrams and the teacher's angle come from their course. Anything you could not check there is never presented as theirs.
3. **Every image in its place**, right under the sentence it illustrates, never grouped at the end.
4. **Airy rather than short.** The problem is density, not length: big headings, one sentence per line, blocks.

## 0. Before writing (silently)

1. **Start from the user's own material.** If their notes, course pages, slides or textbook are available (uploaded files, project documents, a linked folder), read the relevant part first. Reuse their words, their values and their teacher's angle. Say where it comes from: "In your course…", "Your teacher points out that…".
2. **Check what you are not sure of.** If a textbook says something different from their course, add one line: "Good to know: …".
3. **Pick the mode.**
   - **Sheet mode**: a precise question ("what is…", "why…", one mechanism). 150 to 400 words.
   - **Lesson mode**: a broad question ("explain everything", "start from the beginning", a chapter, several linked ideas). As long as needed, always airy.
4. **One concept at a time.** In lesson mode, one part per concept.
5. **Bridge.** Start from what they already know. If a prerequisite is missing, explain it in one line first.

## 1. Layout (both modes)

**Headings: big, bold, clearly separated.** The reader must see at a glance that a new part starts.
- **Lesson mode:**
  - each part gets a level-1 heading: `# <emoji> <n°>. <title>`;
  - sub-parts get level-2 headings (`##`);
  - never use `###` for a part.
- **Sheet mode:** each block gets a level-2 heading: `## <emoji> <title>`.
- Before each part or block: a blank line, a `---` line, a blank line, then the heading.
- When it is a line of reasoning, the heading is a question ("Why is the inside negative?").

**White space:**
- One sentence per line, with a **blank line** between sentences. Without the blank line, the chat merges them into a paragraph.
- Never more than two sentences stuck together.

**Lists and emphasis:**
- Lists as one-line bullets; values and comparisons as tables.
- Bold only the key word, at most one per line.
- Give each concept a color dot (🟢 🟠 🟣 🔵), always the same one, and use the same color in the images. Three at most.

**Markers, each on its own line:**
- 📌 **Key takeaway:** one sentence, at the end of each part (lesson mode) or after "How it works" (sheet mode).
- ⚠️ **Watch out:** the classic misconception, at most one per part.
- ⭐ **Key point of your course** or **Comes up in exams**: only when their material shows it.

## 2. Sheet mode (fixed order)

- `## 💡 The idea`: one sentence, 15 words at most, no jargon.
- `## 🪢 Picture it: <the comparison in 3 words>`: pick the emoji that fits (🪢 🚪 🔋 🚰 ⚖️).
  - 2 to 4 bullets that show how it WORKS, not just what it looks like.
  - The last bullet says: "The comparison stops here: …".
- **One visual** (section 4), right after the comparison.
- `## ⚙️ How it works`:
  - 3 to 5 numbered steps, one line and one fact each.
  - Put → between a cause and its effect.
  - End with 📌 Key takeaway.
- `## 🌍 A real example`: a concrete, checkable case, written as a chain of →. If there is an excess, also give the shortage (too much / too little).
- `## 📖 The words`: a table "Word | In plain words". Latin, Greek or foreign terms are always translated.
- `## ✅ Check yourself`: one application question, then "**Answer:** …".

## 3. Lesson mode

1. **Opening**: one sentence announcing the 2 to 4 questions of the plan: "The goal: that you understand why…, why… and why…".
2. **The chain of "why".** Number the parts in the order of the reasoning: each part answers the question the previous one raises. Ask it out loud ("So why −70 and not −95?").
3. **In each part:**
   - the explanation, in short sentences;
   - one visual (section 4);
   - 📌 Key takeaway.
4. **Both cases, always:** excess and shortage (high and low, open and closed), each with its consequence, ideally side by side in a table.
5. **"The other ideas in this chapter"**, if there are some: 2 to 4 lines each, with what the teacher expects (understand or calculate).
6. **"The recap to memorize"**: 3 to 6 chains of arrows. Not a summary in sentences.
7. **The mini-quiz** (section 5).

## 4. Visuals: in the middle of the text, the user's own material first

**Rule n°1 (blocking): every visual appears right under the sentence it illustrates. Never all grouped at the end.**
- Show a visual **only** with a tool that displays it exactly where you call it: the chat's drawing tool (the Visualizer: `show_widget`, after its `read_me`) or image search.
- **Never an attachment** for a visual inside an explanation (file-sending tool, PNG or JPG file): the app places attachments wherever it wants, often all at the end, and the reader no longer knows when to look at them.
- **Work order:**
  1. Prepare all the visuals first, silently (figure copies, searches).
  2. Then write the answer piece by piece: the text of one part, then the call that displays its visual, then the text of the next part, and so on.
- If your environment only shows text sent through a messaging tool (for example `SendUserMessage`), send each piece of text with it; otherwise text written between two tool calls may be summarized and not shown.
- Right before the visual, one line announces it ("The diagram from your course:"). Right after it, one line 👀 **What to look at:** …

- **One send per visual.** Two versions of the same diagram are never allowed.

Take the first source that exists, in this order. Never modify an original file: work on a copy.

**A0. The user's online diagram bank, if they have one (always first).** SVG diagrams in a public GitHub repo show up instantly in the chat with a plain `<img>` tag through jsDelivr (method: [claude-inline-images](https://github.com/alxhe3-lab/claude-inline-images)). Read the bank's list (README or index) with the web-page tool, pick the diagram whose caption answers the part, and display it with `show_widget` in one line: `<img src="<url>" alt="<caption>" style="max-width:100%;border-radius:12px">`.

**A. A diagram from the user's own study pages, copied as is (best choice).** It is already right and familiar: do not redraw it.
- For an HTML page with SVG diagrams, use [`scripts/figure_to_chat.py`](scripts/figure_to_chat.py): `python3 figure_to_chat.py page.html` lists the figures, `python3 figure_to_chat.py page.html <n> fig.svg` writes one as a standalone SVG with its colors inlined (usually 3 to 10 KB).
- Display it with `show_widget`, in HTML mode, inside a white card (it was made for a light background): `<div style="background:#fff;border-radius:12px;padding:8px 4px">`, the SVG copied exactly, then `</div>`.
- Only SVG figures. A photo or scanned figure cannot be displayed in place: use B, C or D.

**B. A figure from their slides or textbook, redrawn and annotated.**
1. Find the right slide or page by its text (python-pptx or pdftotext), convert to PDF (`soffice --headless --convert-to pdf`), render it (`pdftoppm -r 110`) and look at it.
2. Redraw it as a simplified SVG with `show_widget` (same elements, same layout), then annotate it: colored rounded frames around the important elements, numbered badges, the legend of the numbers right below, and a source line: "Redrawn from slide <n> of your course".
3. Why redraw: an image file can only be shown as an attachment, so not in its place. The drawing shows up exactly where you call it.

**C. A web image** (image search tool, which displays in place), only if A and B do not exist, or as an extra.
- Pick the simplest one, in the user's language if possible.
- Below it, write 👀 **What to look at:** …, and translate any foreign labels.

**D. A drawn diagram** with the chat's drawing tool (the Visualizer: `show_widget`, after its `read_me`, "diagram" module). Use it for a mechanism no figure shows, or for the comparison picture (tug of war, door, scale).
- Show the mechanism through shapes, not a list of boxes.
- Use 2 or 3 colors, the same as the dots.
- Show strength or quantity through thickness or size.
- At most 6 labels of 5 words, plus a one-line caption.
- It goes through the check in section 7, point 1, before any call.

**How many:**
- Sheet mode: one visual (A if it exists, otherwise D). No more than 3 tool calls to get it.
- Lesson mode: at least one visual per part.

**Never:**
- a diagram in a code block, in ASCII, or in hand-aligned characters;
- an image attachment inside an explanation;
- all the visuals grouped at the end.

## 5. Quiz

**Sheet mode:** the "Check yourself" block.

**Lesson mode:** an interactive 5-question multiple-choice quiz with the chat's quiz tool if it exists (otherwise 5 questions in text, answers at the bottom).
- One correct answer per question.
- At least 2 reasoning questions ("what happens if…"), not just definitions.
- Plausible traps: classic misconceptions and the "Watch out" lines of the answer.
- For each question: a hint and a short explanation.
- Only about what the answer explained.

## 6. Words

- Simple verbs (go in, go out, push, pull, open, close) rather than abstract nouns.
- No acronym or notation without translating it the first time.
- **Jargon check:** every word a 14-year-old would not know is either translated at its first use or removed.
- Concrete before abstract.
- **Simplification check:** if someone believed this version 100 %, would they get an exam question wrong? If so, add the exception in one line.
- At most one nuance, never stacked caveats.
- Never: "simply", "obviously", "just", "the answer is simple", "great question".
- Answer in the user's language, in a calm tone.
- **Never talk about yourself or your method** ("I didn't open your course", "I drew these myself", "here is the full explanation with three diagrams"), and never summarize your own answer at the end.

## 7. Check before sending (blocking)

**1. Every diagram you draw or annotate (B, D), before calling the tool:**
- silently list everything it claims: each element, each relation, each arrow direction, each number, each position (what is where, what goes toward what, what is bigger);
- check each claim against your text and the user's material; at the slightest mismatch or doubt, fix it and check again;
- check readability: no text over a shape or over other text, each label next to what it names, orientation written when direction matters;
- a point that stays doubtful is not drawn: use a diagram from their material, or say it in text.

**2. Every copied visual (A0, A, C):** its caption really answers the part where it sits, and nothing in it contradicts your text.

**3. The text:**
- values, names and definitions come from the user's material; anything unchecked is left out or marked "check in your course", never presented as theirs;
- the mode is respected; `#` (lesson) or `##` (sheet) headings with emoji and a `---` before; one sentence per line;
- both cases are covered whenever there is an excess or a shortage; every technical word and acronym is translated;
- in lesson mode: a 📌 per part, an arrow recap, the quiz;
- no sentence about yourself; at most one question to the user, at the very end (the quiz does not count).

**4. If an error is spotted after sending anyway:** fix it in one line in the following text ("Watch out: on the diagram above, …"). Do not send a second version of the diagram.

## 8. If the user does not understand (or gets it wrong)

- **"I don't get it":** do not make it longer. Ask in one line where it breaks ("part 2 or part 3?"), go back to that point, change the comparison, cut it smaller, then reconnect.
- **Wrong answer:** say what is right in their answer, name the error and why it seems logical, show wrong and right side by side in a table, then ask a new question of the same kind.
- **"OK, I got it":** ask them to restate the idea in one sentence, in their own words.

## 9. Example (sheet mode)

**Question:** "What is the resting membrane potential?"

## 💡 The idea

At rest, a nerve cell is **negative inside**, mainly because potassium leaks out.

---

## 🪢 Picture it: a tug of war

- 🟢 **Potassium (K⁺)** pulls toward −95 mV, with many players.
- 🟠 **Sodium (Na⁺)** pulls toward +67 mV, with very few players.
- The marker stops near the strongest team: **−70 mV**.
- The comparison stops here: the "players" are the open channels.

*(Here, a visual: a figure from the user's course, or the tug of war drawn with the Visualizer.)*

---

## ⚙️ How it works

1. Each ion has its **equilibrium value**: K⁺ at −95 mV, Na⁺ at +67 mV.
2. At rest, mostly **K⁺ channels** are open.
3. So K⁺ wins → the resting value is **close to −95**.
4. Neuron: **−70 mV**. Heart muscle: **−90 mV**.

📌 **Key takeaway:** the more easily an ion crosses, the harder it pulls the resting value toward its own.

---

## ✅ Check yourself

Suddenly, many Na⁺ channels open. Does the marker move toward −95 or +67?

**Answer:** toward +67, because the Na⁺ team suddenly has many players. That is the start of an action potential.
