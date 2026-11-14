# claude-explain-like-chatgpt

I'm a first-year med student and I use Claude every day to understand my courses. Honestly, Claude is smart, but its explanations were hard to read for me: long paragraphs, small headings, jargon nobody explained, and "diagrams" typed in a code block.

When I asked ChatGPT the same question, I got something that looked like a clean revision sheet. Big headings, one sentence per line, real pictures, a little quiz at the end. Much easier to read, even when it was longer.

So I wrote these skills to make Claude explain things that way. I rewrote them a bunch of times, comparing both answers side by side on real course questions, until Claude's answers were as easy to read as ChatGPT's.

What I learned along the way: the problem wasn't length, it was density. A long answer is fine as long as it has room to breathe.

## The skills

- [`clear-explanation`](skills/clear-explanation/SKILL.md): for when you actually want to understand something ("explain", "why", "start over"). You get a short sheet for a precise question, or a mini-lesson for a whole topic, with big headings, a comparison from everyday life, diagrams right under the text, a recap with arrows and a quick quiz.
- [`quick-explanation`](skills/quick-explanation/SKILL.md): for one word or a screenshot you don't get while studying. A few lines, no tools, so you're back to your notes in 20 seconds.
- [`explication-claire`](skills-fr-medecine/explication-claire/SKILL.md) and [`explication-rapide`](skills-fr-medecine/explication-rapide/SKILL.md): the same two, in French, tuned for medical school.

## Before and after

Before, Claude would answer something like:

> At rest, the cell is negative inside because its envelope lets almost only potassium out, so blood potassium regulates it directly. Each ion has an equilibrium value where the electric force balances the concentration difference: +67 mV for Na⁺, −95 mV for K⁺. At rest, the membrane has leak channels (K2P, Kir) open mostly for K⁺, so the marker sits near E_K…

With the skill:

> ## 💡 The idea
>
> At rest, a nerve cell is **negative inside**, mainly because potassium leaks out.
>
> ## 🪢 Picture it: a tug of war
>
> - 🟢 **Potassium (K⁺)** pulls toward −95 mV, with many players.
> - 🟠 **Sodium (Na⁺)** pulls toward +67 mV, with very few players.
> - The marker stops near the strongest team: **−70 mV**.
>
> 📌 **Key takeaway:** the more easily an ion crosses, the harder it pulls.

## What changed things the most

- Big headings and a line between parts, so you can see where a new part starts.
- One sentence per line, with an empty line in between.
- Every technical word explained the first time it shows up.
- Both cases every time: too much and too little.
- Images right under the sentence they explain, never piled up at the end. How I got that to work is in a separate repo: [claude-inline-images](https://github.com/alxhe3-lab/claude-inline-images).
- A short quiz at the end of a long explanation.

## Install

In the Claude app: grab the `.zip` of a skill in [Releases](../../releases), then Settings → Skills → upload.

With Claude Code:

```bash
git clone https://github.com/alxhe3-lab/claude-explain-like-chatgpt.git
cp -r claude-explain-like-chatgpt/skills/* ~/.claude/skills/
```

Then just ask your question. A single word or a screenshot triggers the quick one, "explain" or "why" triggers the full one.

## Credits

I didn't start from zero. These skills borrow ideas from [explain-concepts](https://playbooks.com/skills/thepexcel/agent-skills/explain-concepts), the [Feynman Technique Explainer](https://openskillindex.com/skills/openclaw-skills-feynman-technique-explainer) and [education-tutor](https://playbooks.com/skills/eddiebe147/claude-settings/education-tutor).

If it helps you study, a star is appreciated. Ideas and fixes are welcome too.

---

**En français.** Je trouvais les explications de Claude trop chargées par rapport à celles de ChatGPT, alors j'ai écrit ces skills pour qu'il explique comme une vraie fiche : gros titres, une phrase par ligne, des schémas au bon endroit, un petit QCM. Les versions françaises pour la médecine sont dans `skills-fr-medecine/`.
