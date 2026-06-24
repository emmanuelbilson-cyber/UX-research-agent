# Open Text Format Reference

Never produce a bar chart for open-text questions.
Identify themes, count citations, then illustrate with verbatims.

---

## Required Structure

```
[h3] Group X (n=Y)

• Theme 1 — Theme name (N citations) — Short one-sentence description.
    › "Representative verbatim example 1."
    › "Representative verbatim example 2."

• Theme 2 — Theme name (N citations) — Short one-sentence description.
    › "Representative verbatim example."

[…]
```

---

## Rules

- Themes sorted by frequency descending (most cited first)
- Citation count = honest estimate based on reading all responses
- Maximum **2 verbatims** per theme
- Verbatims are indented (level 1 list) below the theme
- **Never invent** a theme or verbatim — everything must come from the file
- For very small bases (n < 5): list all responses directly instead

---

## docx-js Code

```javascript
// Theme with citation count
const themePara = (label, count, body) => new Paragraph({
  numbering: { reference: 'bullets', level: 0 },
  spacing: { before: 80, after: 40 },
  children: [
    new TextRun({ text: `${label} `, bold: true, size: 20, font: 'Arial', color: MID_BLUE }),
    new TextRun({ text: `(${count} citations) — `, bold: true, size: 20, font: 'Arial', color: '888888' }),
    new TextRun({ text: body, size: 20, font: 'Arial' }),
  ]
});

// Verbatim indented (level 1)
const verbatim = t => new Paragraph({
  numbering: { reference: 'bullets', level: 1 },
  spacing: { before: 40, after: 40 },
  children: [new TextRun({ text: `"${t}"`, size: 18, font: 'Arial', italics: true, color: '555555' })]
});
```

## Numbering Config (2 levels required)

```javascript
numbering: {
  config: [{
    reference: 'bullets',
    levels: [
      {
        level: 0,
        format: LevelFormat.BULLET,
        text: '•',
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 720, hanging: 360 } } }
      },
      {
        level: 1,
        format: LevelFormat.BULLET,
        text: '›',
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 1080, hanging: 360 } } }
      },
    ]
  }]
}
```
