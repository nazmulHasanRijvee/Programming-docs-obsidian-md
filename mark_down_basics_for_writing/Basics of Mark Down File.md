First create a File_name.md file with text editor or something else. we might need to rename it to README.md.text to README.md, enable file extension in the view of file explorer. To add a readme file in GitHub

---
## Table of Contents
- [Headings in Mark Down](#Headings in Mark Down)
- [Text Styling](#Text Styling in MD)
- [Paragraph & Line Break](#Paragraph & Line Break)
- [Writing Lists](#Lists in Mark Down)
- [Links in MD](##Links in MD)
- [Images in MD](##Images in MD)
- [Code Blocks in MD](##Code Blocks in MD)
- [Blockquotes in MD](##Blockquotes in MD)
- [Tables in MD](##Tables in MD)
- [Horizontal Line in MD](##Horizontal Line in MD)
- [Emoji in MD](##Emoji in MD)
- [Collapsible Sections in MD](##Collapsible Sections in MD)
- [Centering Content in MD](##Centering Content in MD)
- [Keyboard Keys in MD](##Keyboard Keys in MD)
- [Anchor Links in Mark Down](##Anchor Links in Mark Down)

---
## **Headings in Mark Down**

We can add headings and subheadings like title, section, subsection and more using # (single hash), ## (double) , ### (triple) and more. Like this:
**# H1 - Project Title**
**## H2 - Section**
**### H3 – Subsection**
**#### H4**
**##### H5**
**###### H6**

---
## Text Styling in MD

we can make the text body bold by writing in a double star pair  **   **
Italic by writing  the text in a single star pair * *
And we can mix bold + italic by writing the text in triple start pair ***   ***
We can make the text strike through using ~~ ... ~~
And inline code using single back tics pair **`  `**
**Bold**

***Italic***

*****Bold + Italic*****

**~~Strikethrough~~**

**`Inline code`**

---
## Paragraph & Line Break

We need to ad extra enter between two lines to go to new line
**This is a paragraph**

**This is a new paragraph**
Or we can enter two spaces after the first lie to go to new line
**Line one**  # Two extra spaces
**Line two**

---
## Lists in Mark Down

We can make unordered list just using hyphen - and tab
- Item
- Item
  - Subitem
   - Sub-subitem\
For ordered list just use numbers 1., 2. ....
1. First
2. Second
3. Third
For task lists use hyphen -, third parentheses [ ] and x like this - [x]
- [x] Done
- [ ] Not done

---
## Links in MD

We can add links to words, when that word is clicked the user will be redirected to that link. We can do this by writing the word in third parentheses [ ] and link in the first parentheses ()
[GitHub](https://github.com)
Or we can add the link directly
https://github.com

---
## Images in MD

We can simply drop and drop the image in README editor. Or we can add manually using 
!-[alt text]-(image-url), remove the hyphens

![Alt text](image-url)

Image with link, when tapped will be redirected to link [ -! - [Logo](image-url)]-(https://link.com) remove the hyphens

[ ![Logo](image-url)](https://link.com)

---
## Code Blocks in MD

For in line code use single back ticks pair **`     `**
**Use `print()` to log**
For multi-line or code block (like a code snippet) use triple back tics and write the programming language name (Supported language dart, js, ts, python, java, bash, json, yaml etc.) 
```python
var = "hello"
print(var)
```

```bash
flutter pub get
```

---
## Blockquotes in MD

We can use is single right > for quote and double right arrow for nested quote >>
> This is a quote
> > Nested quote

---
## Tables in MD

We need to follow this pattern for tables
**| Feature | Status |**
**|--------|--------|**
**| Login |** **✅** **|**
**| Map |** **❌** **|**

| Feature | Status |
| ------- | ------ |
| Login   | ✅      |
| Map     | ❌      |

Alignment using colon :
**| Left | Center | Right |**
**|:---- |:------:| -----:|**
**|   L   |      C   |    R   |**

| Left | Center | Right |
|:---- |:------:| -----:|
| L      | C         | R       |
___
## Horizontal Line in MD

We can use --- , *** and __ to create lines

---
***
___

## Emoji in MD

Add emojis directly
🚀 ✨ 🔥 ✅ ❌ ⚠️ 🧠 🎯 📦

---
## Collapsible Sections in MD

Using details and summary tags 

<details>

<summary>Click to expand</summary>

Hidden content here

</details>

---
## Centering Content in MD

Using HTML’s div tag
<div align="center">
# Project Title
</div>

___
## Keyboard Keys in MD

Follow this pattern (It’ll show **Press ctr + c**):

Press <kbd>Ctrl</kbd> + <kbd>C</kbd>

---
## Highlighted Notes in MD

Use right arrow **>** and double star *…*

> **⚠**️ **Warning:** Be careful

>💡**Tip:** Useful info

---
## Anchor Links in Mark Down

For table of contents **- [install] ** **(#heading or # Subheading)**
- [Install](#install)
- [Usage](#usage)

For Heading
**## Install**
