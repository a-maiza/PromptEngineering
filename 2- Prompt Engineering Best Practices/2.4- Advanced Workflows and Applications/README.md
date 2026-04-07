# Advanced Workflows and Applications

---

## Module 1 — Workflows créatifs : génération d'images et vidéos

### Sujet du cours

Appliquer le prompt engineering à la génération d'images et de vidéos avec les outils spécialisés (MidJourney, Stable Diffusion, Sora, Veo), en utilisant des formules, des paramètres et des techniques d'itération.

### Concepts clés

- **Formule image** : `Sujet + Style + Environnement + Paramètres`
- **Paramètres techniques** : contrôlent la mécanique (ex. `--ar` pour le ratio d'aspect, `--seed` pour la reproductibilité).
- **Paramètres créatifs** : contrôlent la direction artistique (ex. `--stylize`, `--chaos`).
- **Negative prompts** : indiquer ce que le modèle doit *éviter* pour affiner le résultat.
- **Reverse image prompting** : uploader une image pour générer le prompt qui l'aurait créée.

### Méthodes / Raisonnements

**Bonnes pratiques pour la génération d'images :**
1. **Utiliser la formule** : sujet + style + contraintes + paramètres → ne jamais oublier un composant essentiel.
2. **Ajouter les paramètres en dernier**, dans le bon format selon l'outil utilisé.
3. **Générer plusieurs variations** (ex. 4 images dans MidJourney), puis upscaler la meilleure — économise du temps et des ressources.
4. **Utiliser le style calling** : référencer des artistes, médiums ou genres pour orienter le style (*"in the style of Studio Ghibli"*).
5. **Prompt chaining pour les prompts complexes** : utiliser un LLM pour rédiger le prompt image, puis l'injecter dans le générateur.

**Outils de découverte de prompts :**
- **Lexica** : galerie d'images avec leurs prompts exacts — permet d'étudier comment les autres structurent leurs prompts.
- **Reverse prompting** : uploader une image pour obtenir un template réutilisable.

**Pour la vidéo (Sora, Veo, Firefly) :**
La même formule s'applique avec un composant supplémentaire : le **mouvement**.
> *Ex. : "A drone shot over snowy mountains at sunrise, cinematic, 16:9."*

### Exemples importants

| Prompt faible | Prompt structuré                                                                                                      |
|---------------|-----------------------------------------------------------------------------------------------------------------------|
| *A lion*      | *A lion, 16:9 aspect ratio, shot with a 35mm lens, golden hour lighting, savanna environment --ar 16:9 --stylize 750* |

### Points à retenir

- En génération d'images, la qualité du prompt compte encore plus qu'en génération de texte.
- Dans les LLMs conversationnels sans syntaxe paramétrique, utiliser le langage naturel pour décrire les paramètres (*"ultra-wide 6:9 aspect ratio, high chaos"*).
- Itérer sur des variantes basse qualité avant de dépenser des ressources sur le rendu final.

---

## Module 2 — ReAct : l'architecture des agents IA

### Sujet du cours

Comprendre ReAct comme l'architecture fondamentale des agents IA et comme pratique avancée de prompt engineering pour orchestrer des workflows autonomes.

### Concepts clés

- **Agent IA** : un LLM dont le prompt lui impose d'itérer en boucle entre planification, action et observation.
- **Boucle ReAct** : `Thought → Action → Observation → (répétition) → Final Answer`
- **System prompt rigide** : template non-négociable qui force le modèle à suivre la boucle ReAct.

### Méthodes / Raisonnements

**Template de system prompt ReAct :**

```
You must strictly follow these steps:
1. THOUGHT: Analyze the question. State what external information is required.
2. ACTION: Select the single best tool (search, calculation, etc.).
3. OBSERVATION: Wait for the tool's result. Evaluate success.
→ Repeat steps 1–3 until the answer is confirmed.
FINAL ANSWER: Summarize all observations into a complete response.
```

**Bénéfices de ce template :**
- **Outputs mesurables** : syntaxe prédéfinie → facile à parser automatiquement.
- **Réduction des hallucinations** : le modèle est forcé d'agir (chercher, citer) plutôt qu'inventer.
- **Contexte dynamique** : chaque observation enrichit le contexte en temps réel avec des données fraîches et factuelles.

### Points à retenir

- ReAct transforme un LLM en agent actif capable de gérer des workflows complexes multi-étapes.
- Derrière tout outil moderne avec navigation web ou exécution de code, un prompt structuré ReAct orchestre la séquence en coulisses.

---

## Module 3 — Assistants de code

### Sujet du cours

Bonnes pratiques de prompt engineering pour les agents de développement (Copilot, Cursor) afin de maximiser l'efficacité, économiser des tokens et maîtriser les risques.

### Concepts clés

- **Instruction set complet** : traiter le prompt comme un jeu d'instructions exhaustif, pas comme une conversation humaine.
- **Gestion du contexte** : toujours fournir les fichiers pertinents directement dans le prompt pour éviter que l'agent ne les cherche (coût en tokens inutile).
- **Version control (Git)** : filet de sécurité indispensable quand un agent modifie des dizaines de fichiers simultanément.

### Méthodes / Raisonnements

**Bonnes pratiques :**

| Pratique                                                          | Pourquoi                                                                                                       |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Fournir les fichiers pertinents dans le prompt                    | Évite la recherche de contexte → économise des tokens et du temps.                                             |
| Fournir des images pour les UI/UX                                 | Le contexte visuel est plus précis que la description textuelle.                                               |
| Utiliser des prompt files pour les tâches complexes réutilisables | Stocke les instructions multi-étapes, évite de les réécrire.                                                   |
| Utiliser Git en permanence                                        | Permet de revenir en arrière rapidement et d'explorer des solutions en branches.                               |
| Toujours relire le code généré                                    | L'agent est un partenaire, pas un remplaçant du QA — vérifier les erreurs logiques et les failles de sécurité. |
| Demander à l'agent d'exécuter le build                            | Permet de voir les erreurs exactes de compilation → corrections immédiates.                                    |
| Ne pas gaspiller les requêtes premium                             | Pour des questions simples (une ligne, un fichier), utiliser un outil gratuit.                                 |
| Changer de modèle si bloqué                                       | GPT, Claude, Gemini ont des forces différentes selon les tâches — ne pas être loyal à une marque.              |

### Points à retenir

- La différence entre un utilisateur amateur et un ingénieur professionnel : la rigueur du prompt et la gestion du contexte.
- L'agent est un partenaire puissant, pas un développeur autonome — la revue humaine reste indispensable.

---

## Module 4 — API et usage en entreprise

### Sujet du cours

Appliquer le prompt engineering aux contraintes de déploiement en production : efficacité des tokens, outputs structurés, sécurité, et gouvernance à l'échelle.

### Concepts clés

- **Token efficiency** : chaque token en entrée et en sortie a un coût financier et une latence — les minimiser est une priorité.
- **Model routing** : utiliser le modèle le plus petit capable d'accomplir la tâche ; réserver les modèles puissants aux tâches complexes.
- **Structured output** : forcer des formats (JSON, XML) pour garantir la compatibilité avec les systèmes en aval.
- **Prompt versioning** : versionner les prompts comme du code (Git, staging avant production).

### Méthodes / Raisonnements

**Efficacité des tokens :**
- Être **brutalement concis** dans les instructions : bullet points et abréviations plutôt que paragraphes verbeux.
- Contrôler la longueur de l'output : `max_tokens` en paramètre API + instructions textuelles (*"Respond in under 50 words"*).
- **Model routing** : ne pas utiliser GPT-4 pour une tâche qu'un modèle plus petit peut accomplir.

**Outputs structurés :**
- Demander explicitement le format : *"Generate output only as a valid JSON object"*.
- Utiliser des **few-shot examples** pour imposer un template précis (ex. format de dates, structure d'objet).

**Gouvernance et sécurité :**

| Pratique                              | Objectif                                                                                               |
|---------------------------------------|--------------------------------------------------------------------------------------------------------|
| **Caching**                           | Réutiliser les réponses pour les requêtes identiques → économies directes.                             |
| **Température basse + seed fixe**     | Outputs déterministes → même input = même output pour tous les utilisateurs.                           |
| **Prompt versioning (Git)**           | Tracer les évolutions, tester en staging avant production.                                             |
| **Telemetry (Langfuse, PromptLayer)** | Monitorer coût, latence et taux d'erreur en production.                                                |
| **Anonymisation des données**         | Ne jamais envoyer de données sensibles dans les prompts — conformité RGPD et réglementations internes. |

### Points à retenir

- En entreprise, la qualité de l'output n'est qu'une dimension — l'efficacité, la robustesse et la sécurité sont tout aussi critiques.
- Versionner, monitorer et tester les prompts comme du code : c'est la norme en production.
- La confidentialité des données est non-négociable : anonymiser avant d'envoyer au modèle.