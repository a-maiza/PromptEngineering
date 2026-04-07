# How Models Actually Read Prompts

---

## Module 1 — Le fonctionnement par tokens

### Sujet du cours

Comprendre comment les LLMs traitent le langage via des tokens, et pourquoi la clarté du prompt conditionne directement la qualité de la réponse.

### Concepts clés

- **Token** : unité de base du langage pour un LLM. Un mot courant = 1 token ; un mot long ou rare = plusieurs tokens.
- **Prédiction token par token** : à chaque étape, le modèle choisit le token le plus probable parmi ~30 000 options, puis recommence.
- **Hallucination** : le modèle génère une information fausse mais présentée avec confiance, parce qu'il comble les lacunes du prompt par des prédictions incorrectes.
- **Effet people-pleaser** : si le prompt contient une prémisse fausse ou orientée, le modèle tend à la valider plutôt qu'à la corriger.

### Explications essentielles

Un LLM ne *comprend* pas le sens d'une phrase — il prédit le mot le plus probable à chaque étape, en se basant sur tout ce qui précède. Cette mécanique explique pourquoi :
- Un prompt clair et structuré → réponse cohérente et utile.
- Un prompt vague ou trompeur → réponse incohérente, hors sujet, ou inventée.

**Analogie :** le modèle est un constructeur qui travaille brique par brique. Si on lui donne des briques cassées (prompt flou), la structure sera bancale. Des briques bien formées (prompt précis) donnent un résultat solide.

### Points à retenir

- Plus le prompt est précis sur **le but, l'audience, le format et les faits à utiliser**, plus les prédictions sont pertinentes.
- Les hallucinations ne sont pas des bugs aléatoires — elles sont la conséquence directe d'un prompt insuffisamment guidé.
- Ne pas traiter le modèle comme un interlocuteur qui comprend l'intention, mais comme un **constructeur qui suit des instructions**.

---

## Module 2 — La gestion du contexte

### Sujet du cours

Comprendre ce qu'est le contexte d'un LLM, ses limites, et comment le gérer efficacement pour maintenir des réponses précises et cohérentes.

### Concepts clés

- **Contexte** : tout le texte que le modèle voit avant de générer sa réponse — prompt, historique de la conversation, instructions système.
- **Context window** : limite fixe du nombre de tokens que le modèle peut traiter en une fois. Au-delà, une partie de l'input est ignorée.
- **Chunking** : découper une tâche complexe en étapes séquentielles pour garder le modèle focalisé et précis.
- **Ordre des instructions** : ce qui vient en premier dans le prompt définit le cadre de toute la réponse qui suit.

### Explications essentielles

Les LLMs n'ont **pas de mémoire native** : à chaque échange, le système reconstitue l'historique et l'envoie comme un nouveau message complet. Plus la conversation est longue, plus les tokens consommés sont nombreux, jusqu'à atteindre la limite de la context window.

**Chunking — exemple :**

❌ Prompt surchargé :
> *"Summarize this 10,000-word report, write a marketing email about it, and suggest five social media captions."*

✅ Approche par étapes :
- **Prompt 1** : *Analyze the report and provide a summary.*
- **Prompt 2** : *Based on that summary, draft a marketing email.*
- **Prompt 3** : *Now suggest five social media captions.*

**Ordre des instructions :**
Les premiers tokens du prompt définissent le cadre d'interprétation de tout ce qui suit. Commencer par les informations les plus importantes améliore la qualité de l'ensemble de la réponse.

### Méthodes / Raisonnements

Bonnes pratiques de gestion du contexte :
1. **Limiter le contexte** : dense et précis, sans dépasser les limites.
2. **Prioriser l'ordre** : mettre les informations essentielles en premier.
3. **Une tâche à la fois** : ne pas empiler les demandes dans un seul prompt.

### Points à retenir

- Le modèle ne se souvient de rien — c'est le système qui reconstitue l'historique à chaque échange.
- Un contexte trop long ou mal ordonné dégrade la qualité des réponses.
- Le chunking est la stratégie clé pour maintenir précision et cohérence sur des tâches complexes.

---

## Module 3 — L'efficacité en prompt engineering

### Sujet du cours

Comprendre l'impact des tokens sur les ressources et les coûts, et apprendre à optimiser ses prompts pour maximiser la valeur par token.

### Concepts clés

- **Coût par token** : via l'API, on paie les tokens en entrée (prompt) + les tokens en sortie (réponse). Chaque token superflu a un coût.
- **Empreinte ressources** : chaque requête LLM consomme électricité, eau et matériel — un prompt long augmente cet impact à grande échelle.
- **Efficacité** : obtenir le maximum de valeur avec le minimum de tokens, sans sacrifier la précision.

### Explications essentielles

À l'échelle d'une entreprise traitant des milliers de requêtes par jour, la différence entre un prompt optimisé et un prompt verbeux représente des coûts significatifs — financiers et environnementaux.

**Exemple concret :** dire *"please"* et *"thank you"* à un LLM à l'échelle mondiale représente des dizaines de millions de dollars de tokens inutilisés.

### Méthodes / Raisonnements

**Optimiser ses prompts :**
- Supprimer les préambules longs et les détails inutiles.
- Éviter les instructions qui se répètent ou se chevauchent.
- Fixer des limites de longueur sur l'output (ex. : *"in 3 bullet points"*, *"in under 100 words"*).
- Demander un résumé d'abord, les détails seulement si nécessaire.

**Surveiller ses métriques :**
- Utiliser le dashboard API pour suivre la consommation de tokens et les coûts.
- Outils open-source disponibles : **PromptLayer**, **Langfuse**, **Helicone**.
- Traiter la performance d'un prompt comme une **feature testée en A/B**.

### Points à retenir

- Chaque token a un coût — financier, énergétique et environnemental.
- Un bon prompt engineering, c'est aussi **savoir quoi ne pas inclure**.
- À petite échelle, l'impact est faible ; à grande échelle (entreprise, production), l'optimisation devient critique.