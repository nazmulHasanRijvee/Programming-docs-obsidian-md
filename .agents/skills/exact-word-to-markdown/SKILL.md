---
name: exact-word-to-markdown
description: Convert supplied plain text or rough notes into Markdown while preserving the exact wording, order, punctuation, capitalization, and meaning. Use when the user explicitly asks for an exact word-for-word Markdown conversion; do not use for rewriting, polishing, summarizing, correcting, or refactoring.
---

# Exact Word-to-Markdown Conversion

Convert the user's supplied text into Markdown only. Treat the user's wording as immutable source content.

## Non-negotiable rules

- Preserve every word, phrase, line sequence, spelling, capitalization, punctuation mark, and technical identifier unless Markdown syntax itself requires a wrapper.
- Do not add explanations, examples, conclusions, transitions, facts, headings, labels, or code that are not present in the source.
- Do not correct grammar, spelling, terminology, factual claims, code, or formatting choices.
- Do not paraphrase, summarize, reorganize, refactor, expand, or remove content.
- If the source is already Markdown, preserve it and make only the smallest syntax conversion needed.
- Do not modify the user's original note unless the user explicitly asks for the note to be edited. Return the converted Markdown or write only to the explicitly requested destination.

## Formatting pattern

Apply structure without changing the source wording:

- Use `#` before standalone explanatory statements when the user's pattern marks them as explanation lines.
- Use `•` for source lines that are explicitly list items.
- Use Markdown headings for clearly labeled sections and steps, keeping the original label text.
- Put code, pseudo-code, trees, vertical workflows, and alignment-sensitive diagrams in fenced code blocks. Use a language fence only when the source clearly identifies the language; otherwise use a plain fence.
- Preserve indentation and diagram characters inside code blocks.
- Keep notes beginning with `NOTE:` as blockquotes when that matches the source pattern.
- Keep inline emphasis, inline code, wikilinks, and other Markdown markers only when they are directly supported by the source or requested by the user; never use them to rewrite wording.

## Decision rule

When unsure whether a formatting change would alter meaning or source content, leave the text unchanged and apply less formatting. The result should be a faithful Markdown transcription, not an improved document.
