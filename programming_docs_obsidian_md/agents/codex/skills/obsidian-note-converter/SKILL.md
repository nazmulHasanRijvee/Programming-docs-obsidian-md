---
name: obsidian-note-converter
description: "Convert DOCX-style technical notes into Obsidian Markdown while preserving the source wording. Use for pasted notes with Word formatting, encoded characters, and code examples."
---

# Obsidian Note Converter

Convert the supplied note into an Obsidian-ready `.md` file. Preserve every source word, spelling, capitalization, punctuation, and code token. Do not correct typos, add explanations, or complete partial code. Formatting changes are allowed only to make the Markdown usable.

## Source cleanup

- Decode HTML numeric entities such as `&#x20;`, `&#xA0;`, and `&#x61;` into their intended characters.
- Remove Word-exported leading `#` markers from ordinary lines. Treat them as headings only when the surrounding structure clearly identifies a real section title.
- Convert source formatting that bolds every code line into Markdown code formatting; do not retain the blanket bold styling.

## Obsidian format

- Write genuine section titles as `##` headings. Replace spaces inside subtitle names with underscores and remove a trailing colon. For example, `Mental Model:` becomes `## Mental_Model`.
- Separate each pair of `##` sections with a horizontal rule. Leave one blank line after the preceding section content, place `---` on its own line, then place the next `##` heading immediately on the following line. Do not insert a blank line between `---` and a subtitle.
- Keep simple labels and transition lines as ordinary text. Do not promote lines such as “To fix this”, “Correct code”, or “In the UI” to `#####` headings.
- Use `#####` only for explicit numbered subpoints beneath a subtitle when they are actual source subpoints. Keep ordinary bullet items as Markdown bullets and ordinary numbered items as Markdown numbered lists when that is the clearer source structure.
- Render note/warning content as a blockquote, for example `> **NOTE:** ...`.

## Technical styling

- Use inline code for identifiers, API calls, filenames, types, methods, properties, expressions, and short code snippets.
- Bold concepts, frameworks, libraries, and package names. When a term is both a concept and code identifier, use bold inline code, for example `**\`AsyncNotifier\`**`.
- Put consecutive source code lines in fenced code blocks. Use `dart` for Dart/Flutter code and `text` for diagrams, API request examples, or non-executable output.
- Preserve code exactly in meaning and token content; normalize indentation only as needed for a readable fenced block.

## Verification

Before delivering, check that the output has no leftover HTML entities or Word-exported leading `#` markers, every code fence is closed, and every `##` subtitle follows the separator rule.
