---
title: markdown showcase (macro)
date: 2026-01-15
---

This page shows what longer **macro** posts can do: headings, sidenotes, tables, code, color swatches, and more.

# first section

Regular paragraphs support _italic_, **bold**, and [links](https://example.com).

A sidenote sits in the margin on wide screens^[On narrow screens, hover or tap the number to read the note. Sidenotes use `^[like this]` in markdown.].

> Blockquotes work for pull quotes or asides. They stay readable against the main column.

## nested lists

- Top level
  - Nested item
  - Another nested item
- Back to top level

1. Ordered lists
2. Work too
3. For steps or rankings

### a small table

| Feature   | Syntax                   |
| --------- | ------------------------ |
| Images    | `![[img/photo.jpg]]`     |
| Cover     | `cover:` in front matter |
| Sidenotes | `^[note text]`           |

# second section

Inline `code` and fenced blocks:

```markdown
---
title: my post
date: 2026-06-01
cover: img/thumbnail.jpg
---
```

Footnotes also work in the classic style.[^demo]

[^demo]: This is a footnote at the bottom of the post.

![[img/inspo-handdrawn.png|480]]

# third section

Use multiple `#` headings in the body to build the table of contents in the left gutter on wide screens.
