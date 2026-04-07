# Prompt Engineering Simply Explained

---

## Module 1 — Introduction au Prompt Engineering

### Sujet du cours

Introduction au *prompt engineering* : l'art de formuler des instructions efficaces pour obtenir de meilleures réponses des outils d'IA générative (ChatGPT, Copilot, Gemini, Claude, etc.).

### Concepts clés

- **Prompt engineering** : conception de requêtes ou d'instructions précises pour guider les réponses d'un modèle d'IA.
- **Qualité de l'input = qualité de l'output** : plus la question est précise et contextualisée, meilleure est la réponse.
- **Applicabilité universelle** : le prompt engineering fonctionne avec tous les outils d'IA et tous les cas d'usage.

### Explications essentielles

Les outils d'IA générative répondent en fonction des informations qu'on leur fournit. Une question vague produit une réponse générique ; une question détaillée et contextualisée produit une réponse pertinente et utile.

### Exemples importants

| Prompt vague                       | Prompt amélioré                                                                          |
|------------------------------------|------------------------------------------------------------------------------------------|
| *What's a good gift for a friend?* | *Suggest a $50 gift for a friend who loves cooking and just moved into a new apartment.* |

Le second prompt inclut un budget, un centre d'intérêt et un contexte — ce qui oriente l'IA vers des suggestions réellement utilisables.

### Points à retenir

- Fournir **contexte, contraintes et détails** dans chaque prompt améliore significativement les résultats.
- Le prompt engineering s'applique à tous les outils IA et tous les domaines (code, images, rédaction, études…).

---

## Module 2 — How Generative AI Works

### Sujet du cours

Comprendre le fonctionnement des modèles d'IA générative pour mieux saisir pourquoi la qualité du prompt influence la qualité de la réponse.

### Concepts clés

- **Entraînement sur de vastes données** : les modèles apprennent à partir d'articles, livres, documentation, pages web, etc.
- **Prédiction du mot suivant** : le moteur fondamental de ces modèles est la prédiction statistique du prochain token (mot).
- **Contexte et détail** : plus le contexte fourni est riche, plus la prédiction est précise.

### Explications essentielles

Un modèle d'IA n'est pas « intelligent » au sens humain : il ne pense pas, il prédit. Il s'appuie sur l'ensemble des données d'entraînement pour estimer quel mot (ou suite de mots) a le plus de chances de suivre l'entrée reçue.

Tout comme un être humain complète facilement *"Once upon a…"* par *"time"* grâce à une exposition répétée à cette formule, l'IA fait de même avec les patterns statistiques de son corpus d'entraînement.

### Méthodes / Raisonnements

**Analogie pédagogique — complétion de phrases :**

| Phrase incomplète      | Complétion attendue                        | Raison                                    |
|------------------------|--------------------------------------------|-------------------------------------------|
| *Once upon a…*         | *time*                                     | Expression figée très fréquente           |
| *The cat sat on the…*  | *mat*                                      | Rime et fréquence dans le corpus          |
| *I need to buy some…*  | *milk* (si contexte = petit-déjeuner)      | Le contexte oriente la prédiction         |
| *He looked up at the…* | *ceiling* (si contexte = salle de réunion) | Le contexte réduit l'espace des possibles |

### Points à retenir

- Les modèles d'IA **prédisent**, ils ne comprennent pas.
- Fournir **du contexte supplémentaire** réduit l'ambiguïté et améliore la précision des réponses.
- La qualité de l'output est directement proportionnelle à la richesse et à la précision de l'input.

---

## Module 3 — Side-by-Side Prompt Comparisons

### Sujet du cours

Mise en pratique du prompt engineering à travers des comparaisons directes entre prompts vagues et prompts améliorés, couvrant différents cas d'usage professionnels.

### Concepts clés

- **Prompt vague** : manque de contexte, d'audience, de contraintes → réponse générique.
- **Prompt enrichi** : inclut l'objectif, le format souhaité, l'audience, les détails techniques → réponse ciblée et actionnable.
- **Itération** : les outils d'IA modernes peuvent demander des précisions si le prompt est insuffisant ; il est toutefois plus efficace de fournir le maximum d'informations dès le départ.

### Méthodes / Raisonnements

Pour améliorer un prompt, se poser ces questions :
1. **Quel est l'objectif précis ?** (expliquer, résumer, générer, corriger…)
2. **Pour qui ?** (débutant, collègue non-tech, client…)
3. **Quelles contraintes ?** (longueur, format, ton, langue…)
4. **Quel contexte manque-t-il ?** (sujet exact, erreur précise, contenu de l'email…)

### Exemples importants

| Prompt vague                       | Prompt amélioré                                                                               |
|------------------------------------|-----------------------------------------------------------------------------------------------|
| *Explain APIs*                     | *Explain what an API is in one paragraph, using a real-world analogy for non-tech coworkers.* |
| *Write API documentation*          | *Write API endpoint documentation for [route], including methods, parameters, and examples.*  |
| *Help me with this bug*            | *Suggest possible causes for [JavaScript error] occurring when [context].*                    |
| *Summarize this meeting*           | *Summarize the key decisions from [meeting topic].*                                           |
| *Give me ideas for a presentation* | *Give me 5 title ideas for a 15-minute presentation on [topic] for [audience].*               |
| *Improve this email*               | *Rewrite this email to sound more confident and concise. Purpose: [context].*                 |

**Exercices pratiques :**

- **Vague :** *Make this email sound better.*
  **Amélioré :** *Rewrite the following email to sound more confident and persuasive when asking a colleague to join a cross-functional product review meeting.*

- **Vague :** *Teach me Python.*
  **Amélioré :** *Create a beginner-friendly lesson to help me understand Python lists. Include a definition, examples, and one small coding exercise.*

### Points à retenir

- Toujours **ajouter contexte, format, audience et contraintes** à un prompt.
- En cas de doute, **itérer** avec l'IA est possible, mais anticiper les détails dès le départ est plus efficace.
- Les outils d'IA récents peuvent **demander des clarifications** automatiquement si le prompt est trop vague.