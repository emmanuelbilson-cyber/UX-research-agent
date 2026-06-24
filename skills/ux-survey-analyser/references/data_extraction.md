# Data Extraction Reference

## Option A — XLSX / CSV Files (manual export)

The user uploads one or more files exported from UserTesting.
Each file corresponds to one group (e.g. Ledger, Non-Ledger, US, EU…).

### File structure

| Row | Content |
|-----|---------|
| 0   | Section headers ("Questions", "Demographics", "Screener"…) |
| 1   | Question labels ("Q2. Which of the following…") |
| 2   | Answer options for multiple-choice questions |
| 3+  | Participant responses |

### Initial parsing

```python
import pandas as pd
from collections import Counter

df = pd.read_excel('file.xlsx', header=None)
n_participants = df.shape[0] - 3  # rows minus 3 header rows

row0 = df.iloc[0, :]

# Find question start
q_start = None
for i, v in enumerate(row0):
    if pd.notna(v) and 'Questions' in str(v):
        q_start = i
        break

# Find demographics start
demo_start = None
for i, v in enumerate(row0):
    if pd.notna(v) and ('Demographics' in str(v) or 'Screener' in str(v)):
        demo_start = i
        break
```

### EXHAUSTIVE column scan

⚠️ Always scan ALL columns from `q_start` to end of file.
Never assume a question ends at a given column.

```python
for c in range(q_start, df.shape[1]):
    r1 = str(df.iloc[1, c])
    r2 = str(df.iloc[2, c])
    vals = [str(v) for v in df.iloc[3:, c]
            if pd.notna(v) and str(v) not in ['nan', '—']]
    n_valid = len(vals)
    if n_valid > 0:
        top3 = dict(Counter(vals).most_common(3))
        print(f'Col {c} | R1: {r1[:50]} | R2: {r2[:40]} | n={n_valid} | {top3}')
```

### Common pitfalls

1. **"Other" columns with named values** — a column with row2 = "Other" may actually
   contain responses like "None of the above". Example found in practice: col 93 labelled
   "Other" but containing `{'None of the above': 16}` → treat as option "None of the above".

2. **Conditional questions (reduced base)** — never skip. Include with a base note:
   `ℹ️ Base: respondents who answered Yes to Q9 — n=X`

3. **Ranking questions** — use the ranking table format (see `table_formats.md`).

4. **Price waterfall (Q10–Q13)** — each question is asked only to participants who
   declined the previous tier. The base n decreases at each tier. Use the cascade format.

5. **Options at 0** — include if present in the official questionnaire and non-zero
   in at least one group. Omit only if 0 in both groups.

### Distinguishing question types

- **Multiple-choice:** several consecutive columns with a value in row2
  → count non-nulls per option; base = group total n
- **Single-choice or free text:** row2 empty or same as row1
  → Counter on values; if len(Counter) > 8 → open text (thematic treatment)
- **Ranking:** columns labelled with rank positions
- **Price waterfall:** Q10/Q11/Q12/Q13 pattern with decreasing base

### Sociodemographic columns

Look in columns before `q_start`:

```python
demo_cols = {}
for i in range(demo_start or 0, q_start):
    col_name = str(df.iloc[2, i])
    if col_name in ['nan', '—']:
        col_name = str(df.iloc[1, i])
    if col_name in ['nan', '—']:
        continue
    vals = [str(v) for v in df.iloc[3:, i]
            if pd.notna(v) and str(v) not in ['—', 'nan']]
    if vals and 2 <= len(set(vals)) <= 20:
        demo_cols[col_name] = dict(Counter(vals).most_common(10))
```

Categories to display if present: Age, Gender, Employment, Household income,
Job level, Job department, Investment goal, Crypto experience, Country/Region,
Parental status, Device, OS.

---

## Option B — UserTesting API (no manual export needed)

```
Base URL : https://api.usertesting.com/api/v2
Header   : Authorization: Bearer {USERTESTING_API_TOKEN}
```

### Workflow

1. `GET /studies` → find test ID by name
2. `GET /studies/{id}/groups` → list groups
3. `GET /studies/{id}/groups/{group_id}/responses` → paginate if necessary
4. `GET /studies/{id}/questions` → get labels and types
5. Parse using the same structure as XLSX files above

### Error handling

| Code | Action |
|------|--------|
| 401  | Ask user for token |
| 404  | List available tests |
| 429  | Wait 2s and retry |

Always confirm the retrieved n with the user before generating the report.
> 500 responses → paginate and notify the user.
Store the token in session memory; never log it.
