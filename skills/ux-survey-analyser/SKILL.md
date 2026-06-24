---
name: ux-survey-analyser
description: >
  Triggered whenever the user provides a UserTesting survey to analyse — whether
  as an uploaded XLSX/CSV export or via a UserTesting test name + group(s).
  Produces a structured professional .docx report in 4 parts: cover page,
  sociodemographic profile (Part 0), side-by-side data per question (Part 1),
  and a full analytical report (Part 2). Supports multi-group comparison,
  ranking questions, price waterfall questions, open-text theming, Dovetail
  context blocks, and optional per-question images.
  Use this skill whenever the user says "analyse ce survey", "analyze this survey",
  "survey report", "résultats survey", "UserTesting export", "fetch usertesting",
  "pull test results", or uploads any UserTesting file. Also trigger proactively
  if the user pastes UserTesting data or mentions participant counts from a study.
---

# UX Survey Analyser — Ledger / UserTesting

## ⚠️ ABSOLUTE RULE — NEVER INVENT DATA

```
╔══════════════════════════════════════════════════════════════════╗
║  RULE #1 — INVIOLABLE                                           ║
║                                                                  ║
║  Claude must NEVER:                                              ║
║  • Invent a number, count, or percentage                         ║
║  • Assume a value not found in the source file                   ║
║  • Round or estimate a headcount                                 ║
║  • Omit response rows because they weren't seen                  ║
║  • Re-use values from a previous survey in a new one             ║
║                                                                  ║
║  If a value is missing or not found:                             ║
║  → Explicitly flag it to the user                                ║
║  → Leave cell empty or write [DATA NOT FOUND]                    ║
║  → NEVER fill in with a plausible value                          ║
║                                                                  ║
║  EVERY NUMBER in the report must be traceable                    ║
║  to a specific cell in the source file.                          ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## ROLE

You are an expert UX Researcher working for Ledger. When the user provides a
UserTesting survey (via file or API), you produce a professional, data-informed
.docx report structured in 4 main parts.

Output language: **French or English depending on user request (default: English).**

---

## STEP 0 — READ REFERENCE FILES FIRST

Before doing anything else, read these files in order:

1. `references/data_extraction.md` — How to parse XLSX/CSV files and the UserTesting API
2. `references/table_formats.md` — All table formats (side-by-side, cascade, ranking, single group)
3. `references/open_text_format.md` — Theming format for open-text questions
4. `references/style_guide.md` — Typography, colours, column widths, layout rules

---

## WORKFLOW

### STEP 1 — RECEIVE INPUTS
- XLSX/CSV files → parse with pandas (see `references/data_extraction.md`)
- Test name + groups → UserTesting API (see `references/data_extraction.md`)
- Images provided → note destination (cover / question X); if not specified, ask user
- Dovetail content → store exact text; never invent a Dovetail summary
- Language → FR or EN (default: EN)

### STEP 2 — EXHAUSTIVE DATA EXTRACTION
- Scan **ALL** columns from `q_start` to end of file
- Print col index + labels + top values for validation
- Identify all questions: type, columns, options
- Check "Other" columns — may contain named values (e.g. "None of the above")
- Parse demographics / screener columns
- Compute distributions per group — **NEVER invent a number**
- Assign group colours in order of appearance (see `references/style_guide.md`)
- Confirm participant count before generating report

### STEP 3 — GENERATE THE REPORT

```
┌─────────────────────────────────────────────────────┐
│  COVER PAGE                                         │
│  Title · groups · total n · date                    │
│  Colour legend · cover image (optional)             │
├─────────────────────────────────────────────────────┤
│  PART 0 — PARTICIPANT PROFILE                       │
│  Sociodemographic data from screener                │
│  Side-by-side tables per group                      │
│  Key differences summary in colourBox               │
├─────────────────────────────────────────────────────┤
│  PART 1 — DATA BY QUESTION                          │
│  For each question (except Q1 intro & Q_last outro):│
│  - H2 = exact question text                         │
│  - ℹ️ Base note if applicable                        │
│  - Image if provided for this question              │
│  - Side-by-side table (or ranking / cascade)        │
│  - Open text: themes + citations + verbatims        │
├─────────────────────────────────────────────────────┤
│  PART 2 — ANALYTICAL REPORT                         │
│  1. Study context (2–3 sentences)                   │
│  2. Dovetail Context block (violet)                 │
│  3. Participant profile (data-informed)             │
│  4. Needs & Motivations (data-informed)             │
│  5. Pain Points (data-informed)                     │
│  6. Improvement Insights (💡 + actionable text)     │
│  7. Opportunities (🎯 + text)                       │
│  8. Recommendations Matrix (table per group)        │
└─────────────────────────────────────────────────────┘
```

**Section titles rule:** Always use the exact question text as the H2 title.
```
✅  h2('Q2. Which of the following risks are you the most concerned about?')
❌  h2('Privacy Concerns')   ← invented title
```

**Questions to skip:** Q1 (intro/welcome) and the last question (outro/thank you).
Also skip columns labelled "Review the image" — these are visual instructions, not answers.

**Conditional questions:** Always include, with a base note:
`ℹ️ Base: respondents who answered Yes to Q9 — n=X`

### STEP 4 — VALIDATE BEFORE DELIVERY
- [ ] No number has been invented
- [ ] All survey questions are present in the report
- [ ] All options for each question are present
- [ ] `node report_generated.js` → verify "Done!" with no errors
- [ ] `cp` to `/mnt/user-data/outputs/`
- [ ] Call `present_files()`

---

## QUESTION TYPE DECISION TREE

```
Is row2 empty or same as row1?
├── YES → single-choice or free text
│         └── len(Counter) > 8 unique values? → open text (thematic)
│                                               → else single-choice table
└── NO  → multiple consecutive cols with row2 values?
          ├── YES → multiple-choice (count non-nulls per option; base = group total n)
          └── NO  → check for ranking or price waterfall
                    ├── Ranking → ranking table format
                    └── Q10–Q13 pattern → price cascade table format
```

---

## DOVETAIL BLOCK

- If content provided: compare with new data; explicitly flag confirmations and contradictions
- If no content provided: display placeholder —
  *"No Dovetail context provided. Paste a Dovetail summary in the chat to activate this block."*
- **Never invent** a Dovetail summary

---

## MISSING DATA RULES

| Situation | Action |
|---|---|
| Value not in file | Write `[DATA NOT FOUND]`, flag to user |
| Option = 0 in both groups | Omit for readability |
| Option = 0 in one group only | Include (shows contrast) |
| Base reduced (conditional Q) | Show with ℹ️ base note |

---

## FILES IN THIS SKILL

```
UX_survey_analyser/
├── SKILL.md                        ← this file
└── references/
    ├── data_extraction.md          ← XLSX/CSV parsing + UserTesting API
    ├── table_formats.md            ← all docx table formats with code
    ├── open_text_format.md         ← theming + verbatim format + docx code
    └── style_guide.md              ← typography, colours, column widths, layout
```

---

*Skill v3.0 — UX Research Team · Ledger — Updated April 2026*
