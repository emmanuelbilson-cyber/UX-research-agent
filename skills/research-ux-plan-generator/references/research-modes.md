# Research Modes — Method Selection Logic

## Mode Detection Summary

| Signal | Weight | → Mode |
|---|---|---|
| Prototype / Figma link mentioned | Strong | VERIFICATION |
| UX objective = "évaluer" or "vérifier" | Strong | VERIFICATION |
| UX objective = "découvrir" or "identifier" | Strong | EXPLORATION |
| UX objective = "mesurer" | Medium | VERIFICATION or MIXED |
| No prototype + no existing data | Strong | EXPLORATION |
| Strong Dovetail data exists on topic | Medium | Reinforce VERIFICATION |
| User says "I don't know what users think yet" | Strong | EXPLORATION |

If signals conflict → ask: *"Avez-vous déjà un prototype ou un parcours défini à tester,
ou êtes-vous encore en phase de compréhension du problème ?"*

---

## EXPLORATION Mode

**When to use:** User has little or no knowledge about the topic. No prototype.
Goal is to understand before building.

**Recommended plan:** Quali pillar + Quanti pillar

### Quali Methods (5–10 participants)

| Method | Best for | Modality | Duration |
|---|---|---|---|
| Entretiens utilisateurs | Comprendre motivations, comportements, contexte | On-site ou Remote | 3 semaines |
| Focus groupe | Explorer des perceptions collectives, faire émerger des tensions | On-site | 3 semaines |
| Atelier de co-création | Générer des idées avec les utilisateurs, tester des concepts | On-site | 3 semaines |
| Guerrilla test | Feedback rapide sur un concept ou une idée | On-site (interne ou salon) | 1 semaine |
| Diary study | Comprendre des comportements sur la durée | Remote | 4-6 semaines |

**Method selection by Morville dimension:**
- Utilité / Contexte → Entretiens ou Diary study
- Désirabilité / Valeur → Focus groupe ou Atelier co-création
- Trouvabilité / Utilisabilité (concept) → Guerrilla test
- Crédibilité → Entretiens approfondis

### Quanti Methods (20+ participants)

| Method | Best for | Modality | Duration |
|---|---|---|---|
| Sondage quantitatif | Dimensionner un phénomène, mesurer des perceptions | Remote (UserTesting / Typeform) | 1-2 semaines |
| Analyse de données existantes | Valider des hypothèses sur base de données internes | — | 1 semaine |
| Usability non-modéré (20+) | Mesurer des taux de réussite à grande échelle | Remote (UserTesting) | 1-2 semaines |
| AB test | Comparer deux versions | Remote (produit live) | Variable |

> ⚠️ RÈGLE ABSOLUE : Les sondages sont UNIQUEMENT remote (UserTesting ou Typeform).
> Ne jamais proposer un sondage en présentiel.

**Method selection by Morville dimension:**
- Utilité / Valeur → Sondage
- Utilisabilité (scale) → Usability non-modéré
- Contexte → Analyse données existantes + Sondage
- Désirabilité → Sondage avec questions de willingness-to-pay

---

## VERIFICATION Mode

**When to use:** User has a prototype, a defined flow, or a solution to test.
UX objective = vérifier, évaluer, mesurer.

**Recommended plan:** Usability test (primary) ± Quanti (support)

### Primary Methods (5–8 participants)

| Method | Best for | Modality | Duration |
|---|---|---|---|
| Usability test modéré | Comprendre les comportements ET les raisons | On-site ou Remote | 3 semaines (on-site) / 1-2 sem (remote) |
| Usability test non-modéré | Mesurer les taux de réussite rapidement | Remote (UserTesting) | 1-2 semaines |
| Test 5 secondes | Évaluer la compréhension immédiate d'une interface | Remote | 1 semaine |

### Support Methods (optional, for quantifying findings)

- Sondage post-usability (5-10 questions max)
- Analyse des données analytics existantes
- Benchmark contre un concurrent ou une baseline

---

## Hypothesis Assignment Logic

When assigning hypotheses to experiments, apply these rules:

**Group together:**
- Hypotheses that explore the same user context or scenario
- Hypotheses about the same feature or flow
- Hypotheses that can be tested in the same session without overloading the participant

**Assign as standalone (dedicated experiment):**
- Hypotheses that require a very specific participant profile not shared by others
- Hypotheses about an isolated edge case or niche flow
- Hypotheses that need a specific stimulus (separate prototype version, specific data setup)
- Hypotheses that test mutually exclusive designs (→ AB test)

**Assign to quanti pillar:**
- Hypotheses that need statistical validation (% of users, frequency, ranking)
- Hypotheses about prevalence ("combien d'utilisateurs font X")
- Hypotheses about willingness-to-pay or price sensitivity

**Assign to quali pillar:**
- Hypotheses about motivations, mental models, emotions
- Hypotheses about "why" rather than "how many"
- Hypotheses about context and environment

---

## Confidence Weight Framework

Used in Step 7 (cross-analysis). Each insight gets a confidence weight based on validation sources.

| Sources | Weight | Label |
|---|---|---|
| 0 sources (hypothesis only) | — | ⬜ Non testée |
| 1 quali source (N<10) | Low | 🟡 Faible |
| 1 quanti source (N<50) | Medium-low | 🟠 Modérée |
| 1 quanti source (N≥50) | Medium | 🟠 Modérée-haute |
| 1 quali + 1 quanti | High | 🟢 Élevée |
| 2+ quali sources | Medium-high | 🟢 Élevée |
| 2+ sources (quali + quanti ≥50) | Very high | 🟢🟢 Très élevée |

Insights with conflicting signals across sources must be flagged explicitly in the cross-analysis.
