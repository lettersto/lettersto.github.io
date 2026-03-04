---
description: Convert simple notes into a formatted blog post
argument-hint: <input-file-name>
allowed-tools: Read, Write, Edit, Glob, Grep
---

## Context

Convert a raw note file into a fully formatted Jekyll blog post for a Chirpy-themed blog.

- Input file location: `inputs/$ARGUMENTS` (under project root)
- Output to: `_posts/YYYY-MM-DD-<slug>.md`
- Style guide: Read from memory at `blog-post-style-guide.md`

## Process

1. Read the input file from `inputs/$ARGUMENTS`
2. Read the style guide from the memory directory (`blog-post-style-guide.md`) for formatting rules
3. Read 1-2 existing posts in `_posts/` to calibrate tone and structure
4. Transform the notes into a formatted blog post following all rules below
5. Ask the user for: title, date, categories, and tags before writing — unless these are already specified in the input file
6. Write the output to `_posts/` with filename format `YYYY-MM-DD-<slug>.md`

## Formatting Rules

### Structure
- Add front matter (title, date, categories, tags, author: admin, toc: true, comments: false)
- Organize into numbered sections: `## N. Title`
- Use sub-sections where appropriate: `### N-M. Title`
- Separate sections with `---` horizontal rules
- Add `<br/>` after headings, `<br/><br/>` before `---`
- Intro sections (`## ► Title`) are optional — only add if the notes contain introductory material

### Personal Thoughts
- Convert personal reflections/opinions into blue callout blocks:
  ```
  > Thought here
  {: .prompt-info }
  ```
- Convert open questions or unresolved concerns into orange callout blocks:
  ```
  > Question here
  {: .prompt-warning }
  ```
- Do NOT use plain code blocks for personal thoughts

### Content
- Use italic one-liner for concept definitions at the start of sections
- Use `<small>*text*</small>` for side notes
- Use fenced code blocks with language tags for code examples
- Use standard markdown tables for tabular data
- Use HTML for any visual diagrams or layouts (no mermaid)
- Use `![alt](/assets/img/...){: w="N" h="N" .normal}` for images
- Use blockquotes `>` for citations from books or external sources

### Style
- No emojis — keep it clean and natural
- Preserve the author's voice and tone — do not make it sound AI-generated
- Korean content with English technical terms where natural
- Keep the author's personal opinions and questions intact — these are valuable
- Do not over-polish or add filler. Concise is better.
- Do not add content that wasn't in the original notes. Only restructure and format.
