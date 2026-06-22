---
name: protocol-generator
description: >
  Rédige des protocoles de recherche utilisateur pour les équipes Ledger, de manière itérative avec le demandeur (PM ou Product Designer).
  Couvre tous les types d'expérimentations UXR : usability test modéré/non modéré (distanciel via UserTesting ou présentiel), interview exploratoire,
  survey quantitatif, card sorting, focus group, ateliers de co-conception (Crazy 8, 6-to-1).
  Produit une version finale bilingue FR + EN, structurée comme un livrable interne professionnel.

  Déclencher ce skill dès que le demandeur mentionne : "protocole", "guide de test", "plan de test", "session utilisateur",
  "usability test", "interview utilisateur", "test modéré", "test non modéré", "screener", "guide d'entretien",
  "protocole de recherche", "research protocol", "test guide", "moderator guide", ou demande à préparer une expérimentation UX/UXR.
---

# Protocol Generator — Ledger UXR

Ce skill génère des protocoles de recherche utilisateur structurés, alignés sur la pratique UXR de Ledger et l'approche Atomic Research.
Un protocole est un livrable interne formel qui cadre une expérimentation : il définit les participants cibles, les hypothèses à tester,
le déroulé de la session, et la grille d'observation.

---

## Philosophie de référence

L'approche s'inscrit dans la logique **Atomic Research** :
- Chaque expérimentation produit des **faits atomiques** (observations granulaires)
- Ces faits alimentent des **insights** (patterns récurrents)
- Les insights révèlent des **opportunités** (problèmes à résoudre)
- Les opportunités guident des **recommandations** actionables

Le protocole est donc l'outil qui garantit que les données collectées seront assez précises et bien structurées pour alimenter ce pipeline.

---

## Étape 1 — Qualification de l'expérimentation

Avant de rédiger quoi que ce soit, pose ces questions au demandeur. Adapte la conversation au contexte (certaines informations peuvent déjà être disponibles depuis le research plan).

### Questions obligatoires

1. **Sujet / Feature** : Sur quelle feature ou problématique porte cette recherche ?
2. **Objectif principal** : Qu'est-ce qu'on cherche à apprendre ou valider ?
3. **Type de recherche** :
   - Qualitative (comprendre le "pourquoi", émotions, comportements, contexte — 5 à 10 participants)
   - Quantitative (mesurer la taille d'un phénomène — 100+ réponses)
4. **Méthode** : voir la taxonomie complète ci-dessous
5. **Modalité** : distanciel (UserTesting) ou présentiel (bureau Ledger)
6. **Personas cibles** : Felix HW, Sam HW, Warren, Talia, Alex — ou combinaison
7. **Hypothèses** : quelles sont les hypothèses à tester ? (peuvent venir du research plan)
8. **Prototype / Matériel** : lien Figma, maquette, ou autre support disponible ?

### Questions selon la méthode

- **Usability test modéré** → durée estimée de la session, nombre de tâches, langue(s) de passation
- **Usability test non modéré** → plateforme (UserTesting), instructions écrites nécessaires
- **Interview** → guide ouvert ou semi-directif, thèmes principaux
- **Survey** → nombre de questions envisagé, outil de diffusion, taille d'échantillon cible
- **Présentiel** → logistique (lieu, matériel, nombre de sessions sur place, contraintes calendaires)
- **Focus group / Co-conception** → nombre de participants par session, facilitateurs prévus

---

## Étape 2 — Taxonomie des méthodes

### Recherche qualitative (distanciel — UserTesting)
| Méthode | Description | Participants typiques |
|---|---|---|
| Usability test modéré | Session avec animateur, pensée à voix haute, prototype Figma | 5 à 8 |
| Usability test non modéré | Le participant réalise seul les tâches sur la plateforme | 8 à 15 |
| Interview exploratoire | Entretien semi-directif, compréhension du contexte utilisateur | 6 à 10 |
| Card sorting non modéré | Tri de cartes pour évaluer l'architecture de l'information | 15 à 30 |

### Recherche quantitative (distanciel — UserTesting / autre)
| Méthode | Description | Participants typiques |
|---|---|---|
| Survey | Questionnaire structuré, données chiffrées | 100 à 500+ |

### Recherche qualitative (présentiel — bureaux Ledger)
| Méthode | Description | Logistique |
|---|---|---|
| Usability test modéré | Même protocole qu'à distance + accueil physique | Salle équipée, recrutement, déplacements |
| Interview | Entretien en face à face | Salle calme, enregistrement audio/vidéo |

### Approche UX (complément, hors UXR stricte)
| Méthode | Description |
|---|---|
| Focus group | Discussion collective sur un sujet, 6 à 8 participants |
| Atelier Crazy 8 | 8 sketches en 8 minutes, idéation rapide |
| Atelier 6-to-1 | Convergence collective sur 1 solution parmi 6 |

---

## Étape 3 — Structure du protocole

Génère le protocole en suivant **exactement cette structure**, dans cet ordre.
Adapte le contenu et la profondeur de chaque section selon la méthode retenue.

### Header table
Tableau de présentation en début de document :

| Champ | Valeur |
|---|---|
| Lead Researcher | À compléter |
| Product Designer | À compléter |
| Method | [Méthode retenue] |
| Estimated duration | [Durée en minutes] |
| Participants | [Nombre et profil] |
| Target personas | [Personas Ledger] |
| Prototype / Material | [Lien Figma ou description du matériel] |

### Section 1 — Introduction
Contexte de la session : feature concernée, stade du projet (discovery / validation / post-lancement), objectif global de la recherche.
Écrit à la 3ème personne, style livrable interne.

### Section 2 — Objectives
Liste numérotée d'objectifs mesurables, formulés de manière actionable.
Ex : "Measure whether users spontaneously discover the [feature] entry point (H1)"
Chaque objectif doit pouvoir être relié à une hypothèse.

### Section 3 — Screeners
Critères de sélection des participants, sous forme de questions avec logique Accept/Reject.

**Format par question :**
- Numéro + intitulé de la question
- Tableau des réponses possibles avec [Accept] / [Reject] par persona si nécessaire
- Indication du persona visé si plusieurs cibles

**Personas de référence Ledger :**
- **Felix HW** : utilisateur hardware wallet, motivé par l'indépendance financière et la sécurité, transactions peu fréquentes, méfiant envers les systèmes centralisés
- **Sam HW** : hardware wallet, trader plus actif, capitalise sur la volatilité des marchés, fréquence d'utilisation élevée
- **Warren** : profil institutionnel ou power user, à adapter selon le contexte
- **Talia** : profil débutant ou utilisateur en onboarding, à adapter selon le contexte
- **Alex** : profil intermédiaire, à adapter selon le contexte

Inclure systématiquement une **Trap Answer** sur au moins une question pour filtrer les réponses peu fiables (à signaler avec ⚠️).

### Section 4 — Hypotheses
Tableau des hypothèses, numérotées H1, H2, H3...

| # | Hypothèse |
|---|---|
| H1 | [Les utilisateurs ne trouveront pas spontanément le point d'entrée de la feature] |
| H2 | [Les utilisateurs ne comprennent pas le concept de...] |

Chaque hypothèse doit être liée à au moins une tâche dans le Test Guide.

### Section 5 — Test Guide
Corps principal du protocole. Organisé en **phases numérotées**, chaque phase contenant une ou plusieurs tâches.

**Structure d'une phase :**
```
PHASE [N] — [Nom de la phase] | [Durée estimée] | Hypothèses testées : H[x], H[y]

Objectif de la phase : [description courte]

[Si applicable : instruction de mise en place du prototype ou contexte à donner au participant]

TÂCHE [N] — [Nom de la tâche]
| Scenario    | [Mise en situation réaliste, à lire au participant en italique] |
| Instruction | [Consigne exacte à formuler à voix haute] |
| Observe     | [Ce que le chercheur doit observer et noter] |
| Follow-up   | [Questions de relance après la tâche] |
```

**Phases types pour un usability test modéré :**
- Phase 0 — Opening (2 min) : accueil, présentation, consentement
- Phase 1 — User Profile (5 min) : contexte crypto, usage Ledger
- Phase 2 à N — Tâches (10-20 min chacune selon complexité)
- Phase finale — Debrief & Overall Reactions (5 min)
- Wrap-up (2-3 min) : remerciements

**Opening script** (à adapter) :
> *"Hello! My name is [NAME] and I work at Ledger. Thank you so much for joining us today. We are working on improving [feature] and your feedback is incredibly valuable. A few things to know: we are testing the product, not you — there are no right or wrong answers. Please think out loud as much as possible. The session is recorded for our internal team only. You can stop at any time. Any questions before we begin?"*

### Section 6 — Observation Grid
Tableau de suivi par participant, à imprimer ou dupliquer pour chaque session.

```
Participant # ___    Persona: [Felix ☐  Sam ☐  Autre ☐]    Date / Time: _______    Duration: _______

| Tâche | Hypothèse | Fail | Hesitant | Success |
|---|---|---|---|---|
| T1 — [Nom] | H1 | ☐ | ☐ | ☐ |
| T2 — [Nom] | H2 | ☐ | ☐ | ☐ |

General observations:

Unexpected insights:
```

---

## Étape 4 — Règles éditoriales

- **Langue** : générer systématiquement deux versions complètes — une en français, une en anglais. L'anglais est la version de référence pour UserTesting.
- **Ton** : formel et structuré, style livrable interne professionnel. Pas de familiarités.
- **Emojis** : uniquement pour illustrer des sections ou signaler une information clé (⚠️, ✅). Jamais pour donner du ton à un propos.
- **Hypothèses** : toujours formulées à la négative (ce qui pourrait dysfonctionner), pour orienter l'observation vers les zones de friction.
- **Tâches** : formulées du point de vue de l'utilisateur, jamais du point de vue du produit. Ex : "Imagine que vous souhaitez emprunter des USDC..." et non "Testez le flow de borrow".
- **Screeners** : toujours inclure une Trap Answer, signalée explicitement avec ⚠️.
- **Observation Grid** : toujours alignée sur les hypothèses — pas d'observation sans hypothèse associée.

---

## Étape 5 — Itération et validation

Après avoir généré une première version :

1. Présente un résumé structuré au demandeur :
   - Méthode retenue et justification
   - Nombre de phases et de tâches
   - Personas ciblés
   - Hypothèses couvertes
   - Points ouverts ou à confirmer

2. Demande des retours section par section si nécessaire.

3. Iterate jusqu'à validation explicite du demandeur.

4. Une fois validé, annonce que le document est prêt à être généré en .docx FR + EN pour dépôt dans Google Drive. L'orchestrateur se chargera ensuite d'envoyer une notification Slack à l'UX Researcher (Emmanuel Bilson) pour caler la session de validation.

---

## Notes sur les méthodes non modérées et surveys

Pour les **tests non modérés** (UserTesting) :
- Les instructions aux participants doivent être entièrement autonomes (pas d'animateur)
- Rédiger des consignes ultra-claires, sans ambiguïté
- Prévoir un script de démarrage écrit, pas oral
- Les follow-up questions sont intégrées dans la plateforme, pas posées en direct

Pour les **surveys** :
- Remplacer le Test Guide par un plan de questionnaire (sections, logique de saut, types de questions)
- L'Observation Grid est remplacée par un plan d'analyse statistique (métriques cibles, seuils de significativité)
- Préciser la durée estimée de complétion

Pour les **ateliers de co-conception** (Crazy 8, 6-to-1) :
- Remplacer les tâches par un agenda de session avec timing
- Inclure les consignes de facilitation
- Prévoir le matériel nécessaire (post-its, timer, templates)
