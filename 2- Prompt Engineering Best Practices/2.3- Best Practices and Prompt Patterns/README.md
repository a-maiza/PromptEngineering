# Best Practices and Prompt Patterns

---

## Module 1 — Stratégies de prompting

### Sujet du cours

Maîtriser des techniques réutilisables pour formuler des prompts plus efficaces et cohérents : le Act as Hack, la formule universelle, le raffinement itératif et le prompt chaining.

### Concepts clés

- **Act as Hack** : demander au modèle d'adopter un rôle précis pour obtenir des réponses plus ciblées et pertinentes.
- **Formule réutilisable** : structure universelle `[ROLE] + [TÂCHE] + [STYLE] + [CONTRAINTES]`.
- **Raffinement itératif** : affiner la réponse étape par étape plutôt que d'attendre la perfection du premier coup.
- **Prompt chaining** : utiliser la sortie d'un modèle comme entrée pour un autre modèle ou outil spécialisé.

### Méthodes / Raisonnements

**La formule universelle :**
> *"From the perspective of [ROLE], do [TASK] in [STYLE] with [CONSTRAINTS]."*

| Composant       | Description                               | Exemple                                                   |
|-----------------|-------------------------------------------|-----------------------------------------------------------|
| **Role**        | Perspective que le modèle doit adopter    | *personal trainer, local guide, graduate student*         |
| **Task**        | Ce qu'on veut obtenir                     | *design a workout, plan a trip, write research questions* |
| **Style**       | Ton ou format souhaité                    | *bullet points, casual style, academic tone*              |
| **Constraints** | Limites : budget, durée, format, longueur | *no leg training, under $500, 4 days*                     |

**Raffinement itératif — bonnes pratiques :**
- Un seul ajustement à la fois (longueur, ton, format, niveau de détail).
- Réutiliser les réponses précédentes comme matière première.
- Savoir quand ouvrir un nouveau chat : continuer si l'historique est utile, repartir à zéro s'il devient trompeur.

**Prompt chaining — exemple :**
1. Demander à ChatGPT de rédiger un prompt détaillé pour un générateur d'images (Gemini).
2. Injecter ce prompt directement dans Gemini pour produire l'image.
   → Un modèle joue le rôle de prompt engineer, l'autre livre le résultat final.

### Exemples importants

| Prompt faible     | Prompt avec formule                                                                                          |
|-------------------|--------------------------------------------------------------------------------------------------------------|
| *Make a workout.* | *Act as a personal trainer, design a 4-day gym workout, use bullet points, no leg training.*                 |
| *Plan a trip.*    | *From the perspective of a local guide, plan a 3-day Tokyo trip, in casual style, with a budget under $500.* |

### Points à retenir

- La formule `Role + Task + Style + Constraints` est universelle et réutilisable dans tous les contextes.
- L'itération n'est pas un échec — c'est la méthode normale pour atteindre un résultat de qualité.
- Le prompt chaining permet de combiner plusieurs outils IA pour des tâches complexes multi-étapes.

---

## Module 2 — Prévenir les hallucinations

### Sujet du cours

Techniques concrètes pour réduire les hallucinations et éviter d'être induit en erreur par des réponses confiantes mais inexactes.

### Concepts clés

- **Hallucination** : le modèle génère une information fausse présentée avec assurance.
- **Sycophancy** : le modèle approuve une affirmation erronée pour paraître utile et agréable.

### Méthodes / Raisonnements

4 techniques anti-hallucination :

1. **Demander l'honnêteté** : ajouter *"If you are not sure, say so"* pour que le modèle signale ses incertitudes.
2. **Fournir des références** : uploader un document et préciser *"Use only this material"* pour ancrer la réponse dans des faits réels.
3. **Demander des citations** : forcer le modèle à sourcer ses affirmations ralentit les inventions.
4. **Restreindre le périmètre** : questions larges → dérive ; questions ciblées → résultats fiables.

### Points à retenir

- Ces techniques s'appliquent surtout aux tâches importantes : recherche, reporting, code.
- Les modèles récents réduisent les hallucinations, mais le risque reste présent sur des sujets spécifiques ou subjectifs.

---

## Module 3 — Déboguer ses prompts

### Sujet du cours

Approche systématique pour corriger un prompt qui ne donne pas le résultat attendu, sans tout réécrire de zéro.

### Concepts clés

- **Debugging de prompt** : processus en 3 étapes — *isoler*, *ajuster*, *auto-corriger*.
- **Température** : paramètre qui contrôle la créativité vs la précision du modèle (0 = factuel, 1 = créatif).
- **Metaprompting** : guider le modèle pour qu'il évalue ou gouverne son propre processus de réponse — utilisé quand le paramètre température n'est pas accessible.

### Méthodes / Raisonnements

**Étape 1 — Isoler le problème :**
Retirer toutes les instructions sauf la plus importante. Si le modèle réussit cette tâche seule → le problème est la surcharge ou les conflits d'instructions. Sinon → problème de contexte ou de compréhension.

**Étape 2 — Ajuster les paramètres :**

| Problème                       | Solution                                                                                                  |
|--------------------------------|-----------------------------------------------------------------------------------------------------------|
| Réponse inexacte ou hallucinée | Baisser la température ou ajouter *"Your response must be entirely factual, no speculation."*             |
| Réponse ennuyeuse ou générique | Augmenter la température ou ajouter *"Be imaginative, take risks, generate three varied options."*        |
| Context window dépassée        | Résumer ou découper le contexte (chunking) pour que les données critiques restent dans la fenêtre active. |

**Étape 3 — Auto-correction par metaprompting :**
- *Demander le plan d'abord* : *"Before generating the report, list the three steps you will take and identify the most critical data you need."*
- *Challenger la réponse* : *"Your last response was incorrect because it ignored the date constraint. Analyze your previous answer, explain where you went wrong, and regenerate the correct response."*

### Points à retenir

- Ne pas tout réécrire quand un prompt échoue — isoler d'abord le problème.
- Le metaprompting remplace le réglage direct de la température dans les interfaces sans accès aux paramètres.
- Maîtriser le debugging transforme un utilisateur en véritable prompt engineer.

---

## Module 4 — Chain of Thought vs. ReAct

### Sujet du cours

Comprendre deux stratégies de raisonnement avancées pour guider le modèle sur des tâches complexes : le Chain of Thought (CoT) et le ReAct.

### Concepts clés

- **Chain of Thought (CoT)** : forcer le modèle à décomposer un problème en étapes visibles avant de donner sa réponse.
- **ReAct (Reasoning + Acting)** : le modèle alterne entre raisonnement et actions concrètes (recherche web, lecture de document, exécution de code) pour résoudre des tâches nécessitant des données externes.

### Explications essentielles

**Chain of Thought :**
En demandant *"Think step-by-step"* (ou en sélectionnant un mode raisonnement dans l'interface), le modèle expose son cheminement logique plutôt que de sauter directement à une conclusion.
- Utile pour : problèmes mathématiques, puzzles logiques, tâches multi-étapes abstraites.
- Inutile pour : questions factuelles simples où les étapes n'ajoutent pas de valeur.

**ReAct :**
Le modèle alterne entre deux types de mouvements :
1. **Reasoning** : *"I need to find Apple's Q2 report."*
2. **Acting** : recherche web, lecture d'un fichier, exécution de code.

Ce cycle se répète jusqu'à résolution de la tâche.

### Exemples importants

**Comparaison CoT vs ReAct — question financière :**

> *"What was Apple's Q2 2025 revenue, and how does it compare to Q1?"*

| Approche     | Ce qui se passe                                                                                                                                  |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **CoT seul** | Le modèle raisonne par étapes mais se base sur ses données d'entraînement, potentiellement obsolètes → risque d'hallucination.                   |
| **ReAct**    | Le modèle raisonne → cherche le rapport Q2 → compare avec Q1 → exécute une analyse financière → donne une réponse basée sur des données réelles. |

### Méthodes / Raisonnements

| Méthode              | Quand l'utiliser                                                                            |
|----------------------|---------------------------------------------------------------------------------------------|
| **Chain of Thought** | Problèmes complexes nécessitant un raisonnement soigneux, étape par étape.                  |
| **ReAct**            | Tâches nécessitant des données externes, des actions concrètes ou un workflow multi-étapes. |

### Points à retenir

- CoT améliore la **qualité du raisonnement** ; ReAct améliore la **précision factuelle** en combinant raisonnement et action.
- ReAct est indispensable quand le modèle seul ne dispose pas des informations nécessaires (données récentes, fichiers externes).
- CoT sans données fraîches peut toujours halluciner — ReAct résout ce problème en allant chercher l'information manquante.