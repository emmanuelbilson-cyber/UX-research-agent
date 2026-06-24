# Table Formats Reference

## Group Colours

```javascript
const GROUP_COLORS = {
  0: { color: "2E75B6", hFill: "D6E4F0" },  // Blue  — group 1
  1: { color: "E67E22", hFill: "FDEBD0" },  // Orange — group 2
  2: { color: "27AE60", hFill: "D5F5E3" },  // Green  — group 3
  3: { color: "8E44AD", hFill: "E8DAEF" },  // Purple — group 4
  4: { color: "E74C3C", hFill: "FADBD8" },  // Red    — group 5
  5: { color: "16A085", hFill: "D1F2EB" },  // Teal   — group 6
};
```

Each group keeps its colour consistently throughout the entire report.
The colour legend appears on the cover page.

---

## Format 1 — Standard Side-by-Side (default multi-group)

One row per answer option. Both groups on the same row for direct comparison.
Use for all multi-group tables unless the question type requires a special format.

```
┌─────────────────────┬──────────────────┬──────────┬──────────────────┬──────────┐
│ Answer              │ 🔵 Group 1 bar   │ n / %    │ 🟠 Group 2 bar   │ n / %    │
├─────────────────────┼──────────────────┼──────────┼──────────────────┼──────────┤
│ Option A            │ ████████         │ 37/61    │ ██████           │ 50/121   │
│                     │                  │ 61%      │                  │ 41%      │
├─────────────────────┼──────────────────┼──────────┼──────────────────┼──────────┤
│ Option B            │ ███              │ 18/61    │ ████████         │ 66/121   │
│                     │                  │ 30%      │                  │ 55%      │
└─────────────────────┴──────────────────┴──────────┴──────────────────┴──────────┘
```

**Sort order:** by combined total (sum of both groups) descending.

**n/% column format — always show:**
```javascript
// ✅ Correct
makeCell(`${cnt}/${group.n}  ${pct}%`, ...)
// ❌ Wrong — missing denominator
makeCell(`${cnt} / ${pct}%`, ...)
```
Where `group.n` = total participants in the group, not the question base if reduced.
If base is reduced, add an ℹ️ base note row above the table.

**Column widths (A4, 1000 DXA margins):**
```javascript
const aW = 2900;  // answer
const bW = 2213;  // bar per group
const cW = 850;   // count per group
// Total: 2900 + (2213 + 850) × 2 = 9026 ✓
```

---

## Format 2 — Price Waterfall (Q10→Q11→Q12→Q13)

Use when questions form a pricing cascade: each is asked only to participants
who declined the previous tier.

```
┌────────────────────┬──────────┬──────────┬──────────┬──────────┬──────────┬───────────────────────┐
│ Fee tier           │ G1 base  │ G1 Yes   │ G1 %     │ G2 base  │ G2 Yes   │ Note                  │
├────────────────────┼──────────┼──────────┼──────────┼──────────┼──────────┼───────────────────────┤
│ 1.2% ($12)         │ 61       │ 39/61    │ 64%      │ 121      │ 81/121   │ Initial — all asked   │
│ 0.8% ($8)          │ 22       │ 2/22     │ 9%       │ 40       │ 9/40     │ Re-asked: declined 1.2│
│ 0.5% ($5)          │ 20       │ 4/20     │ 20%      │ 31       │ 11/31    │ Re-asked: declined 0.8│
│ 0.2% ($2)          │ 16       │ 14/16    │ 88%      │ 20       │ 9/20     │ Re-asked: declined 0.5│
├────────────────────┼──────────┼──────────┼──────────┼──────────┼──────────┼───────────────────────┤
│ TOTAL cumulative   │ —        │ 59/61    │ 97%      │ —        │ 110/121  │ Across all 4 tiers    │
└────────────────────┴──────────┴──────────┴──────────┴──────────┴──────────┴───────────────────────┘
```

⚠️ The "base" column must reflect the real number of participants asked at that tier —
never the group total. % is calculated on the tier base. The cumulative TOTAL row
uses the group total as denominator.

**Column widths:**
```javascript
// [tier, g1_base, g1_yes, g1_pct, g2_base, g2_yes, g2_pct, note]
const cols = [1500, 820, 700, 800, 820, 700, 800, 860]; // ≈ 8000; adjust to 9026
```

---

## Format 3 — Ranking

Use for "Rank your top N reasons" type questions.
Show top 3 responses per rank position, per group.

```
┌─────────────────────┬──────────┬──────────────────────────────┬────────────┐
│ Group               │ Rank     │ Top reason selected           │ n          │
├─────────────────────┼──────────┼──────────────────────────────┼────────────┤
│ Group 1 (n=61)      │ 1st      │ Protection against volatility │ 47         │
│                     │ 1st      │ Low cost to transfer          │ 38         │
│                     │ 1st      │ Earn interest/yield           │ 35         │
│                     ├──────────┼──────────────────────────────┼────────────┤
│                     │ 2nd      │ Stay liquid (no tax event)    │ 48         │
│ Group 2 (n=121)     │ …        │ …                             │ …          │
└─────────────────────┴──────────┴──────────────────────────────┴────────────┘
```

---

## Format 4 — Single Group

For questions asked to one group only (e.g. Q17 Non-Ledger only).

```javascript
const oW = 3500;  // answer
const bW = 3800;  // bar
const cW = 1726;  // count
// Total: 3500 + 3800 + 1726 = 9026 ✓
```
