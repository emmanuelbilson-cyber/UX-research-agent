# Style Guide Reference

## Typography

| Element          | Font  | Size | Style        | Colour  |
|------------------|-------|------|--------------|---------|
| H1               | Arial | 32pt | Bold         | #1F5C99 + blue underline |
| H2               | Arial | 26pt | Bold         | #2E75B6 |
| H3               | Arial | 22pt | Bold         | #1A1A2E |
| Body             | Arial | 20pt | Normal       | Black   |
| Verbatim         | Arial | 18pt | Italic       | #555555, quotes, level 1 |
| Open text label  | Arial | 20pt | Bold blue + bold grey count + normal body | — |
| Base note        | Arial | 18pt | Italic       | #888888 |

---

## Colour Palette

### Fixed colours

| Use                  | Hex      |
|----------------------|----------|
| Cover background     | #D6E4F0  |
| Insights box         | #E8F4FD  |
| Pain points box      | #FFF3E0  |
| Dovetail box         | #F3E5F5  |
| Dovetail header text | #6A1B9A  |
| Table header         | #D6E4F0  |
| Alternating rows     | #F5F5F5  |
| Base note text       | #888888  |

### Group colours

| Group | Bar colour | Header fill |
|-------|-----------|-------------|
| 1     | #2E75B6   | #D6E4F0     |
| 2     | #E67E22   | #FDEBD0     |
| 3     | #27AE60   | #D5F5E3     |
| 4     | #8E44AD   | #E8DAEF     |
| 5     | #E74C3C   | #FADBD8     |
| 6     | #16A085   | #D1F2EB     |

Each group keeps its colour consistently throughout the entire report.
Colour legend appears on the cover page.

---

## Column Widths (DXA units)

All tables must total **9026 DXA** to fit A4 with 1000 DXA margins.

### Multi-group side-by-side

```javascript
const aW = 2900;  // Answer column
const bW = 2213;  // Bar per group
const cW = 850;   // Count per group
// 2900 + (2213 + 850) × 2 = 9026 ✓
```

### Single group

```javascript
const oW = 3500;  // Answer
const bW = 3800;  // Bar
const cW = 1726;  // Count
// 3500 + 3800 + 1726 = 9026 ✓
```

### Price cascade

```javascript
// [tier, g1_base, g1_yes, g1_pct, g2_base, g2_yes, g2_pct, note]
const cols = [1500, 820, 700, 800, 820, 700, 800, 860];
// Sum ≈ 8000; scale proportionally to reach 9026
```

---

## Page Layout

| Setting       | Value                    |
|---------------|--------------------------|
| Format        | A4 (11906 × 16838 DXA)   |
| Margins       | 1000 DXA all sides       |
| Page breaks   | Before Part 0, Part 1, Part 2 |

---

## Images

- Supported formats: PNG, JPG, JPEG, GIF, WEBP
- Max width in document: 500px, centred
- If placement not specified by user → ask before inserting

**Display order when an image is associated with a question:**
1. H2 question title
2. Full question text in italic
3. Base note (if applicable)
4. IMAGE centred
5. Answer table

---

## Dovetail Block

```javascript
const DOVETAIL_BG = "F3E5F5";  // very light violet

// Header: "📚  DOVETAIL CONTEXT" in dark violet #6A1B9A
// Body: italic text, max 150 words / ~10 lines
// Footer: "Source: [name]" in grey #888888
```
