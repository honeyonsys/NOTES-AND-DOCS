# Markdown Cheat Sheet

This guide provides a quick reference for common Markdown syntax and how it appears in most Markdown previews.

## 1. Headers
Markdown supports six levels of headers.

| Syntax | Preview |
| :--- | :--- |
| `# Header 1` | # Header 1 |
| `## Header 2` | ## Header 2 |
| `### Header 3` | ### Header 3 |
| `#### Header 4` | #### Header 4 |
| `##### Header 5` | ##### Header 5 |
| `###### Header 6` | ###### Header 6 |

---

## 2. Emphasis
You can make text bold, italic, or both.

| Syntax | Preview |
| :--- | :--- |
| `*Italic*` or `_Italic_` | *Italic* |
| `**Bold**` or `__Bold__` | **Bold** |
| `***Bold & Italic***` | ***Bold & Italic*** |
| `~~Strikethrough~~` | ~~Strikethrough~~ |

---

## 3. Lists
Markdown supports ordered and unordered lists.

### Unordered List
`* Item 1`  
`* Item 2`  
`  * Sub-item`

**Preview:**
* Item 1
* Item 2
  * Sub-item

### Ordered List
`1. First item`  
`2. Second item`  
`3. Third item`

**Preview:**
1. First item
2. Second item
3. Third item

---

## 4. Links and Images

| Type | Syntax | Preview |
| :--- | :--- | :--- |
| **Link** | `[Google](https://www.google.com)` | [Google](https://www.google.com) |
| **Image** | `![Alt Text](https://via.placeholder.com/150)` | ![Alt Text](https://via.placeholder.com/150) |

---

## 5. Blockquotes
For quoting text or sections.

`> This is a blockquote.`

**Preview:**
> This is a blockquote.

---

## 6. Code
Inline code and code blocks.

### Inline Code
Use backticks around text: `` `Code here` ``.
**Preview:** `Code here`

### Code Block
Use triple backticks (```) with an optional language name.

\```javascript
function hello() {
  console.log("Hello, World!");
}
\```

**Preview:**
```javascript
function hello() {
  console.log("Hello, World!");
}
```

---

## 7. Tables
Create tables using pipes `|` and hyphens `-`.

`| Header 1 | Header 2 |`  
`| :--- | :--- |`  
`| Row 1 Col 1 | Row 1 Col 2 |`  

**Preview:**
| Header 1 | Header 2 |
| :--- | :--- |
| Row 1 Col 1 | Row 1 Col 2 |

---

## 8. Horizontal Rule
Use three or more asterisks, hyphens, or underscores.

`---` or `***` or `___`

**Preview:**
---

## 9. Task Lists
`- [x] Task Completed`  
`- [ ] Task Pending`

**Preview:**
- [x] Task Completed
- [ ] Task Pending
