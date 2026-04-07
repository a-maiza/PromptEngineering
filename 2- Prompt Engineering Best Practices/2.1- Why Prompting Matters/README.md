# Getting More Done with Better Prompts

---

## Module 1 — Pourquoi le prompting est une compétence clé

### Sujet du cours

Comprendre pourquoi la qualité d'un prompt détermine directement la qualité de la réponse IA, et pourquoi le prompt engineering est devenu une compétence incontournable.

### Concepts clés

- **Un bon prompt est un multiplicateur** : une seule requête bien formulée remplace plusieurs échanges inefficaces.
- **La différence ne vient pas du modèle, mais du prompt** : le même outil peut produire un résultat médiocre ou excellent selon la façon dont on lui parle.

### Explications essentielles

Les LLM (Large Language Models) performent en fonction de ce qu'on leur demande. Une formulation vague produit une réponse générique ; une formulation précise et contextualisée produit une réponse utile, personnalisée et actionnable.

### Exemples importants

| Domaine          | Prompt faible                         | Prompt efficace                                                                                                                         |
|------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Storytelling** | *Write a story.*                      | *Write a 200-word bedtime story about a cat astronaut traveling to Mars, in the style of J.K. Rowling.*                                 |
| **Design**       | *Make me a logo for my coffee shop.*  | *A simple modern logo for a coffee shop called Moonbrew with a crescent moon as the cup handle.*                                        |
| **Code**         | *Write Python code for a calculator.* | *Write Python code for a command-line calculator that supports add, subtract, multiply, and divide with clear comments for a beginner.* |

**Analogie clé :** un prompt vague, c'est comme entrer dans un restaurant et dire *"Food!"* — on obtient quelque chose, mais rarement ce qu'on voulait. Un bon prompt, c'est commander précisément : le chef sait exactement quoi préparer.

### Points à retenir

- Un bon prompt **économise du temps** et **élargit ce qu'on est capable de produire**.
- Le prompt engineering s'applique partout : travail, code, créativité, vie quotidienne.

---

## Module 2 — Quand les prompts échouent : les 3 pièges à éviter

### Sujet du cours

Identifier les trois erreurs de prompting les plus courantes qui produisent des réponses inutiles, fausses ou superficielles.

### Concepts clés

- **Piège 1 — Vagueness (vague)** : un prompt trop large pousse le modèle à tout couvrir sans rien approfondir.
- **Piège 2 — Bias (biais)** : les modèles sont *people pleasers* — une question orientée obtient une réponse orientée, même fausse.
- **Piège 3 — Overload (surcharge)** : trop de tâches en un seul prompt produit des réponses superficielles sur chaque point.

### Explications essentielles

**Vagueness :**
*"Explain quantum computing"* → réponse dense, technique, générique. Sans contexte ni contrainte, le modèle essaie de tout couvrir et finit par ne rien dire d'utile.

**Bias :**
Si on pose une question orientée comme *"Remind me why Edison invented the internet?"*, le modèle peut confirmer une information fausse avec assurance. Les modèles s'améliorent, mais le risque reste présent sur des sujets spécifiques ou subjectifs.

**Overload :**
*"Plan a business, create its marketing strategy, and write the website copy"* → le modèle produit trois listes courtes, aucune exploitable. Plus on empile les tâches, moins chaque réponse est détaillée.

### Points à retenir

- **Prompt vague** → réponse confuse.
- **Prompt biaisé** → réponse trompeuse.
- **Prompt surchargé** → réponses trop superficielles.
- Identifier ces pièges permet d'éviter les allers-retours inutiles et d'obtenir des réponses directement utilisables.

---

## Module 3 — Le superpouvoir caché : diriger l'IA comme un expert

### Sujet du cours

Dépasser l'usage basique de l'IA (moteur de recherche) pour la diriger comme un collaborateur expert, capable de produire des livrables concrets dans n'importe quel domaine.

### Concepts clés

- **Diriger, pas chercher** : avec un bon prompt, on contrôle le ton, le style, le format et les règles d'interaction.
- **Fournir du contexte externe** : quand le modèle ne connaît pas une librairie, une donnée ou un document, on peut lui fournir directement.

### Méthodes / Raisonnements

**3 façons de fournir du contexte au modèle :**
1. **Upload manuel** : copier-coller le texte ou uploader un fichier directement dans le chat.
2. **Navigateur IA** : outils comme ChatGPT Atlas qui récupère automatiquement le contenu d'une page web.
3. **Agents autonomes** : agents capables de rechercher eux-mêmes les informations nécessaires.

### Exemples importants

**Demo 1 — Mode développeur :**
> Contexte : le modèle ne connaît pas forcément la version la plus récente de la librairie pandas.
> Solution : fournir la documentation directement (URL ou copier-coller), puis demander : *"Using this documentation, write Python code that loads a CSV file and calculates the average of one column."*
> Résultat : code fonctionnel basé sur les docs fournies, sans hallucination.

**Demo 2 — Mode analyste financier :**
> Contexte : rapports de revenus d'Apple et Tesla uploadés directement.
> Prompt : *"Using the reports provided, summarize the key revenue trends for Apple and compare them with Tesla."*
> Résultat : analyse comparative en langage clair, sans dépendre de données obsolètes.

**Demo 3 — Mode product manager :**
> Contexte : navigation sur producthunt.com via ChatGPT Atlas.
> Prompt : *"From this list, summarize the main product categories, highlight common features, and suggest three trends worth watching."*
> Résultat : clustering des produits, analyse des tendances, en quelques secondes.

### Points à retenir

- L'IA ne se limite pas à ce qu'elle sait déjà — **on peut lui apporter le contexte dont elle a besoin**.
- Avec un bon prompt, un seul développeur, rédacteur ou designer peut produire plus vite qu'une équipe entière.
- Le prompt engineering permet de **passer directement de l'idée à l'exécution**, en compressant les étapes intermédiaires (recherche, planification, prototypage).