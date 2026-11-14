# Claude, explain it like ChatGPT 💡

**Two skills that make Claude explain things the way ChatGPT does: airy study sheets with big headings, one idea per line, real diagrams and a quick quiz. Plus an instant mode for "what does this word mean?".**

[English](#english) · [Français](#français)

---

## English

### Why

I'm a first-year medical student and I use Claude every day to study. Claude is great at reasoning, but its explanations are often **dense**: long paragraphs, small headings, jargon left unexplained, and "diagrams" typed as text in a code block.

Ask ChatGPT the same question and the answer usually reads like a **clean study sheet**: big headings, one sentence per line, white space, real images, a 5-question quiz at the end.

So I compared both, side by side, on real course questions. Then I wrote these skills and rewrote them five times, until Claude explained as clearly as ChatGPT, while keeping Claude's accuracy.

The main lesson: **the problem is density, not length.** A long answer is fine if it breathes.

### What's inside

| Skill | When | What you get |
|---|---|---|
| [`clear-explanation`](skills/clear-explanation/SKILL.md) | "Explain…", "why…", "start from the beginning", "I still don't get it" | A study sheet (short question) or a mini-lesson (big topic): big headings, the chain of "why", a comparison picture, real or drawn diagrams, both cases (too much / too little), key takeaways, an arrow recap, an interactive quiz |
| [`quick-explanation`](skills/quick-explanation/SKILL.md) | One word, one sentence, a screenshot | An instant answer in 40 to 120 words, **no tools**, so you get back to work right away |
| [`explication-claire`](skills-fr-medecine/explication-claire/SKILL.md) | French, for medical students | The same, tuned for medical school (course slides, textbook figures, exam traps) |
| [`explication-rapide`](skills-fr-medecine/explication-rapide/SKILL.md) | French, for medical students | The instant version, with word breakdowns (hyper- / kal- / -emia) |

### Before / after

**Before** (Claude without the skill):

> At rest, the cell is negative inside because its envelope lets almost only potassium out, so blood potassium regulates it directly. Each ion has an equilibrium value where the electric force balances the concentration difference: +67 mV for Na⁺, −95 mV for K⁺. At rest, the membrane has leak channels (K2P, Kir) open mostly for K⁺, so the marker sits near E_K…
>
> *(and a "diagram" made of aligned characters in a code block)*

**After** (with `clear-explanation`):

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
> *(here, a diagram drawn in the chat, right under the comparison)*
>
> 📌 **Key takeaway:** the more easily an ion crosses, the harder it pulls.

### What makes the difference

- **Big, separated headings**: `#` for each part of a lesson, `##` for each block of a sheet, a line between parts.
- **One sentence per line**, with a blank line in between (otherwise the chat glues them into a paragraph).
- **Images in the right place**: each diagram appears right under the sentence it explains, drawn in the chat, never sent as attachments that the app piles up at the end.
- **Your own material first**: a diagram copied from your own study pages (with [a small script](skills/clear-explanation/scripts/figure_to_chat.py)), then a slide or textbook figure redrawn and **annotated** in color, then a web image, then a diagram drawn from scratch. Never a diagram in a code block.
- **The chain of "why"**: each part answers the question the previous one raises.
- **Both cases, always**: too much and too little, side by side.
- **Words**: every technical term translated, simple verbs, a jargon check and a "would this mislead you in an exam?" check before sending.
- **Speed when you need it**: the quick version uses no tools at all.

### Images in the right place: what we found

Why Claude's images often pile up at the end, and how to make them appear right under the sentence they illustrate (tested methods, the best one, a free diagram bank): **[claude-inline-images](https://github.com/alxhe3-lab/claude-inline-images)**.

### Install

**Claude app or claude.ai:** download the `.zip` of a skill from [Releases](../../releases) (or zip its folder yourself), then go to Settings → Skills and upload it.

**Claude Code:**

```bash
git clone https://github.com/alxhe3-lab/claude-explain-like-chatgpt.git
cp -r claude-explain-like-chatgpt/skills/* ~/.claude/skills/
```

Then just ask your question. The descriptions tell Claude which skill to use: a single word or a screenshot triggers the quick one, "explain" or "why" triggers the full one.

**Works best with:** the visual (diagram) tool and image search turned on, and your course files available to Claude (uploaded, in a Project, or in a linked folder).

### Built from

- [explain-concepts](https://playbooks.com/skills/thepexcel/agent-skills/explain-concepts) (thepexcel/agent-skills): verify → bridge → chunk → explain → check → adapt.
- [Feynman Technique Explainer](https://openskillindex.com/skills/openclaw-skills-feynman-technique-explainer): jargon check, a comparison that explains the mechanism, a real example.
- [education-tutor](https://playbooks.com/skills/eddiebe147/claude-settings/education-tutor): one concept at a time, fixing misconceptions.
- Side-by-side tests against ChatGPT on real medical-school questions.

Ideas, better examples, other languages: issues and pull requests are welcome. If it helps you, a ⭐ helps others find it.

*Not affiliated with Anthropic or OpenAI.*

---

## Français

### Pourquoi

Je suis en 1re année de médecine et j'utilise Claude tous les jours pour étudier. Claude raisonne très bien, mais ses explications sont souvent **trop chargées** : longs paragraphes, petits titres, jargon pas expliqué, « schémas » tapés en texte dans un bloc de code.

ChatGPT, lui, répond comme une **belle fiche** : gros titres, une phrase par ligne, de l'espace, de vraies images, un QCM à la fin.

J'ai comparé les deux sur de vraies questions de cours, puis j'ai écrit ces skills et je les ai réécrits cinq fois, jusqu'à ce que Claude explique aussi clairement que ChatGPT, en gardant sa justesse.

Ce qu'on a appris : **le problème, c'est la densité, pas la longueur.** Une réponse longue passe très bien si elle est aérée.

### Ce qu'il y a dedans

| Skill | Quand | Ce que tu obtiens |
|---|---|---|
| [`explication-claire`](skills-fr-medecine/explication-claire/SKILL.md) | « Explique », « pourquoi », « reprends depuis le début », « je comprends toujours pas » | Une fiche (question précise) ou un mini-cours (sujet large) : gros titres, le fil des « pourquoi », une image de la vie courante, les schémas de ton cours placés juste sous ce qu'ils expliquent, l'excès et le manque, « À retenir », un récap en flèches, un QCM cliquable |
| [`explication-rapide`](skills-fr-medecine/explication-rapide/SKILL.md) | Un mot, une phrase, une capture d'écran | Une réponse éclair de 40 à 120 mots, **sans outil**, pour reprendre ton cours tout de suite |
| [`clear-explanation`](skills/clear-explanation/SKILL.md) et [`quick-explanation`](skills/quick-explanation/SKILL.md) | Les mêmes, en anglais, pour toutes les matières | |

### Les images au bon endroit

Pourquoi les images de Claude finissent souvent toutes à la fin, et comment les afficher juste sous la phrase qu'elles illustrent : **[claude-inline-images](https://github.com/alxhe3-lab/claude-inline-images)**. Banque de 425 schémas de médecine en français : [schemas-medecine](https://github.com/alxhe3-lab/schemas-medecine).

### Installer

**App Claude ou claude.ai :** télécharge le `.zip` du skill dans [Releases](../../releases) (ou compresse son dossier), puis Paramètres → Skills → importer.

**Claude Code :** copie le dossier du skill dans `~/.claude/skills/`.

Ensuite, pose simplement ta question : un mot ou une capture déclenche la version rapide, « explique » ou « pourquoi » déclenche la version complète.

Les chemins de dossiers dans la version médecine sont un exemple d'organisation : adapte-les aux tiens.

Si ça t'aide, une ⭐ aide les autres à le trouver.

*Projet indépendant, sans lien avec Anthropic ni OpenAI.*
