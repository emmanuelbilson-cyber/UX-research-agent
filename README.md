# UXR-Agent — Ledger

Assistant IA qui accompagne les PM et Product Designers de Ledger dans le cadrage de leurs recherches utilisateur. L'agent mène la conversation dans Slack, génère les documents (research plan + protocoles FR/EN) et notifie l'UX Researcher quand tout est prêt pour la session de validation.

---

## Ce que contient ce repo

```
UX-research-agent/
├── ORCHESTRATOR.md                          # Instructions de l'agent (system prompt)
└── skills/
    ├── research-ux-plan-generator/
    │   ├── SKILL.md                         # Cadrage du research plan (7 étapes)
    │   └── references/
    │       ├── research-modes.md            # Logique de sélection des méthodes
    │       ├── screener-templates.md        # Questions screener par persona
    │       └── output-formats.md            # Formats de documents par méthode
    ├── protocol-generator/
    │   └── SKILL.md                         # Rédaction des protocoles FR + EN
    ├── ledger-persona-oracle/
    │   ├── SKILL.md                         # Connaissance des personas Ledger
    │   └── references/                      # Données personas (quanti + quali)
    ├── docx/
    │   └── SKILL.md                         # Génération de livrables Word
    └── ux-survey-analyser/
        ├── SKILL.md                         # Analyse de surveys UserTesting
        └── references/                      # Templates et logique d'analyse
```

**`ORCHESTRATOR.md`** = le system prompt de l'agent. À injecter tel quel au démarrage de chaque session. Il décrit le workflow complet (5 étapes), la machine à état, les règles de comportement et les ressources (Drive, Sheet, Slack).

**`skills/`** = les compétences spécialisées invoquées par l'agent selon les étapes du workflow. Chaque skill est un fichier d'instructions autonome.

---

## Workflow (résumé)

```
PM écrit sur Slack
  └─► Étape 1 — Accueil & qualification de la demande
  └─► Étape 2 — Research Plan (skill: research-ux-plan-generator)
              → Consultation Dovetail (insights existants)
              → Google Doc créé dans Drive
              → Push Jira optionnel
  └─► Étape 3 — Protocoles (skill: protocol-generator, 1 par expérimentation)
              → .docx FR + EN par protocole
  └─► Étape 4 — Dépôt dans Google Drive (/docs)
  └─► Étape 5 — DM Slack → Emmanuel Bilson (UX Researcher)
              "Research plan prêt, caler un call de validation"
```

État de chaque demande suivi dans un **Google Sheet** (une ligne = une demande).

---

## Dépendances (à configurer côté déploiement)

| Outil | Usage | Auth requise |
|---|---|---|
| **Slack** | Interface PM ↔ agent + notification DM à l'UXR | Bot token + App token (Socket Mode recommandé) |
| **Google Drive** | Lecture/écriture des documents dans `/docs` | OAuth utilisateur (compte Emmanuel Bilson) |
| **Google Sheets** | Suivi de l'état du workflow | OAuth utilisateur (même compte) |
| **Dovetail** | Consultation des insights existants (step 2) | Token API Dovetail |
| **Atlassian (Jira/Confluence)** | Alignement OKRs (step 2) + création issue Jira (optionnel) | Token API Atlassian |

> **Important :** Google Drive et Google Sheets doivent être connectés sous le **compte utilisateur d'Emmanuel Bilson** (pas un service account) — l'agent crée les documents en son nom et les partage automatiquement avec lui.

---

## Personas Ledger référencés dans les skills

| Persona | Profil |
|---|---|
| Felix HW | Utilisateur hardware wallet, sécurité-first, transactions peu fréquentes |
| Sam HW | Hardware wallet, trader actif, fréquence élevée |
| Warren | Power user / institutionnel |
| Talia | Débutant, onboarding |
| Alex | Profil intermédiaire |

---

## Contact & ownership

**Owner du repo / product owner :** Emmanuel Bilson (UX Researcher) — `emmanuel.bilson@ledger.fr`
Toute modification du workflow ou des skills doit passer par lui.

---

## Scope v1 — ce qui N'est PAS inclus

Fonctionnalités prévues pour une version ultérieure (v2+) :

- Booking automatique de créneaux agenda (Google Calendar)
- Envoi automatique d'email avec les documents en pièces jointes
- Récupération et analyse du transcript de la réunion de validation
- Recommandations post-meeting postées au PM
- Agrégation automatique des insights dans le tableau Dovetail
