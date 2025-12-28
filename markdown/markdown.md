# MARKDOWN

## Basic Syntax

This section covers the essential Markdown syntax for writing readable and structured documents.

### Headings

Use `#` for headings. The number of `#` indicates the level:

```markdown
# H1 Heading
## H2 Heading
### H3 Heading
#### H4 Heading
##### H5 Heading
###### H6 Heading
```

### Paragraphs and Line Breaks

- Paragraphs are separated by blank lines.
- For a line break within a paragraph, end the line with two spaces or use `<br>`.

### Emphasis

- **Bold**: `**text**` or `__text__`
- *Italic*: `*text*` or `_text_`
- ~~Strikethrough~~: `~~text~~`

### Lists

#### Unordered Lists

Use `-`, `*`, or `+`:

```markdown
- Item 1
- Item 2
  - Subitem
```

#### Ordered Lists

Use numbers followed by a period:

```markdown
1. First item
2. Second item
   1. Subitem
```

### Links

- `[Link text](URL)`: [Example](https://example.com)
- Reference-style: `[Link text][ref]` with `[ref]: URL` at the bottom.

### Images

- `![Alt text](image-url)`: ![Alt](https://via.placeholder.com/150)
- Reference-style similar to links.

### Code

- Inline: `` `code` ``
- Block: Triple backticks with optional language:

```javascript
console.log('Hello, world!');
```

### Blockquotes

Use `>`:

> This is a blockquote.

### Tables

```
| Header 1 | Header 2 |
|----------|----------|
| Cell 1   | Cell 2   |
```

### Task Lists

- [ ] Unchecked item
- [x] Checked item

### Horizontal Rule

Use `---` or `***`:

---

## Advanced Tips

- Escape special characters with `\`.
- Use HTML for complex formatting if needed.
- Preview in a Markdown viewer to check rendering.