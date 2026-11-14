# Showing images in the middle of Claude's answers

**Problem:** when Claude explains something with several images, they often end up all grouped at the end of the answer. You read the text, then scroll through a pile of pictures without knowing which one goes with which paragraph.

**Why:** images sent as **file attachments** are placed by the app wherever it wants, usually at the end. Only things drawn by Claude's **visual tool** (the Visualizer, `show_widget`) and **image search** results appear exactly where Claude calls them.

## What we tested (Claude app, November 2026)

| Method | Shows in place? | Cost | Verdict |
|---|---|---|---|
| Image sent as a file attachment | ❌ grouped at the end | low | avoid inside explanations |
| Diagram redrawn by Claude in the Visualizer | ✅ | slow: Claude writes the whole drawing | fine for new diagrams |
| Your own SVG copied into the Visualizer ([script](../skills/clear-explanation/scripts/figure_to_chat.py)) | ✅ | 3–10 KB per diagram, 20–40 s | works, no redraw |
| Image embedded as `data:` (base64) in the Visualizer | ✅ | very heavy for real figures | only for tiny images |
| `<img>` in the Visualizer pointing to **jsDelivr** (`cdn.jsdelivr.net/gh/<user>/<repo>@main/<file>`) | ✅ | one line, instant | **best solution** |
| Image search | ✅ | instant | good extra, but not your own material |

## The best solution, step by step

1. Put your diagrams (SVG or PNG) in a **public** GitHub repo. jsDelivr serves files from public repos only, and it is one of the few image hosts the Visualizer accepts.
2. Give each file a name that contains a short hash of its content (`fig06-6ba08680.svg`): if a diagram changes, it gets a new name, so the CDN never shows an old version.
3. Keep an index (`index.json` or one `README.md` per chapter) with each diagram's caption and URL, so Claude picks the right one.
4. In the answer, Claude writes the text of a part, then calls the Visualizer with a single line:
   ```html
   <img src="https://cdn.jsdelivr.net/gh/<user>/<repo>@main/<path>/fig06-6ba08680.svg" style="max-width:100%;border-radius:12px">
   ```
   then writes the next part.
5. Give SVGs a white background inside the file: the chat may be in dark mode.

Example bank built this way: [schemas-medecine](https://github.com/alxhe3-lab/schemas-medecine) (425 diagrams, French, CC BY 4.0).

**Limit:** the repo must be public. Copyrighted figures (textbooks, teachers' slides) must not go there: redraw them instead.

---

# Afficher les images au milieu des réponses de Claude (résumé en français)

- Les **pièces jointes** finissent toutes à la fin : à éviter dans une explication.
- Ce qui s'affiche **à sa place** : l'outil de dessin du chat (Visualiseur) et la recherche d'images.
- **La meilleure solution** : mettre ses schémas dans un dépôt GitHub **public**, puis faire afficher par le Visualiseur une seule ligne `<img src="https://cdn.jsdelivr.net/gh/...">`. Instantané, au bon endroit, sans rien redessiner.
- Noms de fichiers avec une empreinte du contenu, fond blanc dans le SVG, un index avec les légendes.
- Jamais de figures sous droits d'auteur (manuels, diapos du prof) dans un dépôt public : on les redessine.
