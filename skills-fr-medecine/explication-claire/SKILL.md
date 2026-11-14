---
name: explication-claire
description: Quand l'étudiant veut vraiment comprendre une notion de cours ou de médecine (explique, pourquoi, comment ça marche, reprends depuis le début, je comprends toujours pas) : fiche ou mini-cours aéré, schémas de son cours, QCM.
---

# Expliquer clairement un point de cours (version médecine, comme ChatGPT)

**Pas pour une question éclair** : un seul mot, une phrase ou une capture d'écran qu'il veut juste comprendre pour continuer son cours, c'est le skill explication-rapide (quelques lignes, sans outil). Ce skill-ci sert quand il veut vraiment comprendre un mécanisme ou tout un passage.

Beaucoup d'étudiants trouvent les explications de Claude trop complexes et trop chargées. Celles de ChatGPT ressemblent à de « belles fiches » : bien espacées, des titres clairs, des phrases courtes, des mots simples.

Ce qu'un étudiant en médecine a dit en testant les versions successives :
- Version 2 : « trop chargée, petite, tout collé », schéma « flemmard » (du texte dans un bloc de code).
- Comparaison avec ChatGPT (environ 1 700 mots, 7 images) : plus clair malgré la longueur. Le problème de Claude était la densité, pas la longueur (« c'est pas grave si c'est un peu plus long »).
- Version 4 : titres trop petits et pas assez gras, pas assez d'espace entre les parties ; images d'internet pas claires.
- Ce qu'il veut pour les images : d'abord les schémas de ses cours optimisés (« de qualité, il a juste à les copier »), puis les figures de ses manuels et diapos, annotées ; internet en dernier.
- Version 5 : les schémas étaient envoyés en pièces jointes, et l'app les a tous rangés à la fin, « illisible, je sais pas quand regarder les images ». Chaque image doit être au milieu des explications, juste sous ce qu'elle illustre.

L'étudiant est en médecine, parfois sans base scientifique : une notion de collège peut lui manquer. Il apprend par schémas, gros blocs et flèches, pas par paragraphes. Le but : qu'il comprenne du premier coup, puis qu'il sache le redire avec les mots de son prof.

**Inspiré de :**
- « explain-concepts » (thepexcel/agent-skills) : vérifier, faire le pont, découper, expliquer, contrôler, adapter.
- « feynman-technique-explainer » : contrôle du jargon, image qui explique le mécanisme, vrai exemple, trou détecté.
- « education-tutor » : un concept à la fois, correction des idées fausses.
- Les réponses de ChatGPT : mise en page de fiche, raisonnement en « pourquoi », images, mini-test.

## 0. Avant d'écrire (en silence)

1. **Pars de son cours.** Si ses fichiers de cours sont accessibles (fichiers envoyés, documents du projet, dossier de l'ordinateur relié au chat), lis seulement ceux-ci, jamais rien de personnel. Les chemins ci-dessous sont un exemple d'organisation, à adapter :
   - le cours optimisé : `<dossier de cours>/cours-optimises/<Matière>/<CMn|TPn>/cours.html` (une page de cours en HTML ; des notes ou un PDF marchent aussi). Trouve-le en cherchant la notion dans le texte. Reprends ses mots, ses valeurs et l'angle du prof (c'est ce qui tombe) ;
   - son carnet d'erreurs ou de tutorat, s'il en a un. Ses idées fausses deviennent les « Attention » et les pièges du mini-test ;
   - si un chiffre manque : la diapo du prof dans `<dossier de cours>/supports/<matière>/<CMn|TPn>/`.
2. **Dis d'où ça vient** : « Dans ton cours… », « Ton prof précise que… » (par exemple : comprendre une équation, pas la calculer). Si un manuel dit autre chose, ajoute une ligne « à savoir : … ». Si tu n'es pas sûr, cherche d'abord.
3. **Choisis le mode.**
   - **Mode fiche** : question précise (« c'est quoi… », « pourquoi… », un mot, un mécanisme). 150 à 400 mots.
   - **Mode cours** : question large (« explique-moi tout », « reprends depuis le début », un chapitre, plusieurs notions liées). Autant de mots qu'il faut, toujours aéré.
4. **Un concept à la fois.** En mode cours, une partie par concept.
5. **Le pont.** Pars de ce qu'il connaît déjà. S'il manque un prérequis, explique-le en une ligne avant.

## 1. Mise en page (les deux modes)

**Les titres : grands, gras, bien séparés.** On doit voir d'un coup d'œil qu'on change de partie.
- **Mode cours :**
  - chaque partie a un titre de niveau 1 : `# <emoji> <n°>. <titre>` (le plus grand et le plus gras du chat) ;
  - les sous-parties ont un titre de niveau 2 (`##`) ;
  - jamais de `###` pour une partie.
- **Mode fiche :** chaque bloc a un titre de niveau 2 : `## <emoji> <titre>`.
- Avant chaque partie ou bloc : une ligne vide, une ligne `---`, une ligne vide, puis le titre.
- Quand c'est un raisonnement, le titre est une question (« Pourquoi le repos est-il négatif ? »).

**L'air :**
- Une phrase par ligne, avec une **ligne vide** entre deux phrases. Sans ligne vide, le chat les colle en paragraphe.
- Jamais plus de deux phrases collées.

**Listes et mise en relief :**
- Les listes en puces d'une ligne ; les valeurs et les comparaisons en tableau.
- Gras : seulement le mot clé, au plus un par ligne.
- Chaque notion a sa pastille de couleur (🟢 🟠 🟣 🔵), toujours la même, et la même teinte dans les images (🟢 = vert-bleu #1D9E75 ou c-teal, 🟠 = corail #D85A30 ou c-coral, 🟣 = violet #534AB7 ou c-purple, 🔵 = bleu c-blue). Trois au plus.

**Les repères, chacun sur sa ligne :**
- 📌 **À retenir :** une phrase, à la fin de chaque partie (mode cours) ou après « Comment ça marche » (mode fiche).
- ⚠️ **Attention :** l'idée fausse classique (ou la sienne, prise dans son carnet), au plus une par partie.
- ⭐ **Point clé de ton cours** ou **Ça tombe** : seulement si son cours optimisé, son prof ou les annales le montrent.

## 2. Mode fiche (ordre fixe)

- `## 💡 L'idée` : une phrase de 15 mots au plus, sans mot technique.
- `## 🪢 L'image : <la comparaison en 3 mots>` : prends l'emoji qui colle (🪢 🚪 🔋 🚰 ⚖️).
  - 2 à 4 puces qui montrent comment ça MARCHE.
  - La dernière puce dit : « L'image s'arrête là : … ».
- **Un visuel** (section 4), juste après l'image.
- `## ⚙️ Comment ça marche` :
  - 3 à 5 étapes numérotées, d'une ligne et d'un seul fait chacune.
  - Mets → entre une cause et sa conséquence.
  - Termine par 📌 À retenir.
- `## 🩺 Un vrai exemple` : un cas concret, souvent clinique ou de TP, en chaîne de →. S'il y a un excès, donne aussi le manque (hyper et hypo).
- `## 📖 Les mots du cours` : un tableau « Mot | En clair ». Le latin et le roumain sont toujours traduits.
- `## 🎯 Ce qui tombe` : seulement si son cours ou les annales le montrent. Sinon, n'écris pas ce bloc.
- `## ✅ Vérifie-toi` : une question d'application, puis « **Réponse :** … ».

## 3. Mode cours

1. **L'ouverture**, en une phrase qui annonce les 2 à 4 questions du plan : « Le but : que tu comprennes pourquoi…, pourquoi… et pourquoi… ».
2. **Le fil des « pourquoi ».** Numérote les parties dans l'ordre du raisonnement : chaque partie répond à la question que la précédente fait naître. Pose-la à voix haute (« Mais alors, pourquoi −70 et pas −95 ? »).
3. **Dans chaque partie :**
   - l'explication en phrases courtes ;
   - un visuel (section 4) ;
   - 📌 À retenir.
4. **Les deux cas, toujours** : l'excès et le manque (hyper et hypo, ↑ et ↓, ouvert et fermé), chacun avec sa conséquence, de préférence dans un tableau côte à côte.
5. **« Les autres notions du cours »**, si le chapitre en a (équations, pompes, valeurs) : chacune en 2 à 4 lignes, avec son À retenir et ce que le prof demande (comprendre ou calculer).
6. **« Le récap à mémoriser »** : 3 à 6 chaînes de flèches (« K⁺ ↑ → dépolarisation → canaux Na⁺ bloqués → risque cardiaque »). Pas un résumé en phrases.
7. **Le mini-test** (section 5).

## 4. Les visuels : au milieu du texte, d'abord ceux de son cours

**Règle n°1 (bloquante) : chaque visuel apparaît juste sous la phrase qu'il illustre. Jamais regroupés à la fin.**
- Un visuel s'affiche **seulement** avec un outil qui le montre à l'endroit exact de l'appel : l'outil de dessin du chat (le Visualiseur : `show_widget`, après son `read_me`) ou la recherche d'images.
- **Jamais de pièce jointe** pour un visuel du cours (outil d'envoi de fichier, image PNG ou JPG) : l'app range les pièces jointes où elle veut, souvent toutes à la fin, et on ne sait plus quand les regarder.
- **Ordre de travail :**
  1. Prépare d'abord tous les visuels, en silence (copies de figures, recherches).
  2. Puis écris la réponse morceau par morceau : le texte d'une partie, puis l'appel qui affiche son visuel, puis le texte de la partie suivante, et ainsi de suite.
- Si ton environnement n'affiche que le texte envoyé par un outil de message (par exemple `SendUserMessage`), envoie chaque morceau de texte avec lui. Sinon, le texte écrit entre deux outils peut être résumé et ne pas apparaître.
- Juste avant le visuel, une ligne l'annonce (« Le schéma de ton cours : »). Juste après, une ligne 👀 **Ce qu'il faut regarder :** …

Prends la première source qui existe, dans cet ordre. Ne modifie jamais un fichier d'origine : travaille sur une copie.

**A. Un schéma de son cours, copié tel quel (le meilleur choix).** Il est déjà juste et il le connaît : ne le redessine pas.
- Pour une page HTML avec des schémas SVG (par exemple un cours optimisé), utilise [`scripts/figure_vers_chat.py`](scripts/figure_vers_chat.py) :
  - `python3 figure_vers_chat.py cours.html` liste les figures (numéro, type, légende) ;
  - `python3 figure_vers_chat.py cours.html <n°> fig.svg` écrit la figure en SVG autonome, couleurs comprises (3 à 10 Ko en général).
- Affiche-la avec `show_widget`, en HTML, dans un cadre blanc (elle est faite pour un fond clair) : `<div style="background:#fff;border-radius:12px;padding:8px 4px">`, le SVG recopié exactement, puis `</div>`.
- Seulement les figures en SVG. Une photo ou une planche scannée ne s'affiche pas à sa place : prends B, C ou D. Au-delà de 15 Ko, garde la figure seulement si c'est la plus importante.

**B. Une figure de la diapo du prof ou du manuel, redessinée et annotée.**
1. Trouve la bonne diapo par son texte (python-pptx ou pdftotext), convertis-la (`soffice --headless --convert-to pdf`), rends la page (`pdftoppm -r 110`) et regarde-la. En Anatomie, les planches de l'atlas ou du manuel (Kamina, Netter…).
2. Redessine-la en SVG simplifié avec `show_widget` (mêmes éléments, même disposition), puis annote :
   - des cadres arrondis de couleur autour des éléments importants, aux couleurs des pastilles ;
   - des pastilles numérotées ;
   - la légende des numéros juste en dessous ;
   - une ligne de source : « D'après la diapo <n> de ton prof ».
3. Pourquoi redessiner : une image ne peut s'afficher qu'en pièce jointe, donc pas à sa place. Le dessin, lui, s'affiche là où tu l'appelles.

**C. Une image d'internet** (outil de recherche d'images, qui s'affiche à sa place), seulement si A et B n'existent pas, ou en complément.
- Choisis la plus simple, en français si possible.
- En dessous, écris 👀 **Ce qu'il faut regarder :** …, puis traduis les légendes anglaises.

**D. Un schéma dessiné** avec l'outil de dessin du chat (le Visualiseur : `show_widget`, après son `read_me`, module « diagram »). Il sert pour un mécanisme que ni A ni B ne montre, ou pour l'image-comparaison (tir à la corde, porte, balance).
- Montre le mécanisme par la forme, pas par une liste de boîtes.
- Utilise 2 ou 3 couleurs, celles des pastilles.
- Montre la force ou la quantité par l'épaisseur ou la taille.
- Au plus 6 étiquettes de 5 mots, plus une légende d'une ligne.

**Combien :**
- Mode fiche : un visuel (A s'il existe, sinon D). Pas plus de 3 appels d'outil pour le préparer.
- Mode cours : au moins un visuel par partie. Au moins un vient de son cours (A ou B) quand ses fichiers sont accessibles.
- Fichiers de cours inaccessibles : C et D seulement, et dis-le en une ligne.

**Interdit :**
- un schéma en bloc de code, en ASCII ou en caractères alignés à la main ;
- une image en pièce jointe dans une explication ;
- tous les visuels regroupés à la fin.

## 5. Se tester

**Mode fiche :** le bloc « Vérifie-toi » (section 2).

**Mode cours :** un mini-test interactif de 5 QCM, avec l'outil de quiz du chat s'il existe (sinon, 5 QCM en texte avec les réponses en bas).
- Une seule bonne réponse par question.
- Au moins 2 questions de raisonnement (« que se passe-t-il si… »), pas seulement des définitions.
- Des pièges plausibles : ses idées fausses (carnet) et les « Attention » de la réponse.
- Pour chaque question : un indice et une explication courte.
- Seulement sur ce que la réponse a expliqué.

## 6. Les mots

- Prends des verbes simples (entrer, sortir, pousser, tirer, ouvrir, fermer) plutôt que des noms abstraits (« la compensation de la force électrique »).
- Pas de sigle ni de notation dans le texte sans la traduire à sa première apparition (E_K, K2P, Kir, Nav). Le sigle du cours va dans « Les mots du cours ».
- **Contrôle du jargon** : tout mot qu'un élève de 3e ne connaît pas est soit traduit à sa première apparition, soit retiré.
- Le concret avant l'abstrait.
- **Contrôle de simplification** : si on croyait cette version à 100 %, se tromperait-on à l'examen ? Si oui, ajoute l'exception en une ligne.
- Une nuance au plus, jamais de précautions empilées.
- Interdit : « simplement », « évidemment », « il suffit de », « la réponse est simple », « excellente question ».
- Tutoiement, français, ton calme.

## 7. Relecture avant d'envoyer (bloquante)

1. Le mode est choisi et respecté : fiche de 150 à 400 mots, ou cours en parties numérotées dont les titres sont des questions.
2. Titres : `#` pour les parties du mode cours, `##` pour les blocs de la fiche, chacun avec son emoji, et un `---` entre deux lignes vides avant chacun.
3. Une phrase par ligne, séparée par une ligne vide ; jamais plus de deux phrases collées.
4. Chaque visuel est affiché au milieu du texte, juste sous ce qu'il illustre, par l'outil de dessin ou la recherche d'images. Aucune pièce jointe, aucun visuel regroupé à la fin, aucun schéma en bloc de code. Les sources suivent l'ordre A → B → C → D.
5. Les deux cas sont traités dès qu'il y a un excès ou un manque.
6. Chaque mot technique et chaque sigle sont traduits.
7. Les valeurs et les formules sont celles de son cours.
8. En mode cours : un 📌 À retenir par partie, un récap en flèches, le mini-test.
9. Une seule question posée à l'étudiant, à la fin (le mini-test ne compte pas).

## 8. S'il ne comprend pas (ou se trompe)

- **« Je comprends pas » :**
  - N'allonge pas.
  - Demande en une ligne où ça décroche (« la partie 2 ou la 3 ? »).
  - Reviens à ce point, change d'image, découpe plus petit, puis raccroche au fil.
- **Mauvaise réponse :**
  - Dis ce qui est juste dans sa réponse.
  - Nomme l'erreur et dis pourquoi elle paraît logique.
  - Montre le faux et le juste côte à côte dans un tableau.
  - Pose une nouvelle question du même type.
- **« C'est bon, j'ai compris » :** fais-lui redire l'idée en une phrase, avec ses mots.
- **Il veut plus de détails :** passe en mode cours.

## 9. Exemples

**Mode fiche : « C'est quoi le potentiel de repos ? »**

## 💡 L'idée

Au repos, la cellule est **négative dedans**, surtout parce que le potassium sort.

---

## 🪢 L'image : un tir à la corde

- 🟢 **Potassium (K⁺)** tire vers −95 mV, avec beaucoup de joueurs.
- 🟠 **Sodium (Na⁺)** tire vers +67 mV, avec très peu de joueurs.
- Le repère s'arrête près de l'équipe la plus forte : **−70 mV**.
- L'image s'arrête là : les « joueurs », ce sont les canaux ouverts.

*(Ici, le visuel A : la figure « Où se place le potentiel de repos, et pourquoi ? » de son cours optimisé de Physiologie CM2.)*

---

## ⚙️ Comment ça marche

1. Chaque ion a sa **valeur d'équilibre** : K⁺ à −95 mV, Na⁺ à +67 mV.
2. Au repos, ce sont surtout les **canaux à K⁺** qui sont ouverts.
3. Donc le K⁺ gagne → le repos est **proche de −95**.
4. Neurone : **−70 mV**. Muscle et cœur : **−90 mV**.

📌 **À retenir :** plus un ion passe facilement, plus il tire le repos vers sa valeur.

---

## 🩺 Un vrai exemple

| | 🔺 Trop de K⁺ (hyperkaliémie) | 🔻 Pas assez de K⁺ (hypokaliémie) |
|---|---|---|
| Le repos | devient moins négatif | devient plus négatif |
| Le risque | le cœur bat mal, peut s'arrêter | faiblesse des muscles, troubles du rythme |

---

## ✅ Vérifie-toi

On ouvre d'un coup beaucoup de canaux à Na⁺. Le repère part vers −95 ou vers +67 ?

**Réponse :** vers +67, car l'équipe Na⁺ a soudain beaucoup de joueurs. C'est le début du potentiel d'action.

**Mode cours : « Reprends le potentiel de repos depuis le début » (plan)**

Ouverture : « Le but : que tu comprennes pourquoi le neurone est négatif au repos, pourquoi le potassium compte autant, et pourquoi trop ou pas assez de potassium est dangereux. »

- `# 🔋 1. C'est quoi, le potentiel de repos ?` Visuel B : la figure « Le principe du potentiel de membrane » de la diapo 5 du CM2, redessinée et annotée (① canaux à K⁺, ② canal à Na⁺, ③ pompe, ④ charges + et −).
- `# ⚖️ 2. Pourquoi les ions bougent-ils ?` Le tableau des concentrations (145/12, 4/155), les deux forces dessinées (visuel D). ⚠️ Attention, son idée fausse : « négatif parce qu'il y a plus de K⁺ dedans ».
- `# 🪢 3. Mais alors, pourquoi −70 et pas −95 ?` Visuel A : la figure du cours optimisé. Perméabilité 1 : 0,04 : 0,45.
- `# 🩺 4. Pourquoi trop ou pas assez de K⁺ est dangereux ?` Hyper et hypo dans un tableau côte à côte, kaliémie de 3,5 à 5 mmol/L.
- `# 📚 5. Les autres notions du cours` Nernst, Goldman, la pompe, le calcium.
- `# 🧠 6. Le récap à mémoriser` Des chaînes de flèches.
- `# ✅ 7. Mini-test` 5 QCM cliquables.