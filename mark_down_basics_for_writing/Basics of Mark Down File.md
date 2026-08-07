First create a File_name.md file with text editor or something else. we might need to rename it to README.md.text to README.md, enable file extension in the view of file explorer. To add a readme file in GitHub

---
### Table of Contents
- [Headings in Mark Down](#Headings_in_Markdown)
- [Text Styling](#Text_Styling_in_MD)
- [Paragraph & Line Break](#Paragraph_&_Line_Break)
- [Writing Lists](#Lists_in_Markdown)
- [Links in MD](#Links_in_MD)
- [Images in MD](#Images_in_MD)
- [Code Blocks in MD](#Code_Blocks_in_MD)
- [Blockquotes in MD](#Blockquotes_in_MD)
- [Tables in MD](##Tables_in_MD)
- [Horizontal Line in MD](#Horizontal_Line_in_MD)
- [Emoji in MD](#Emoji_in_MD)
- [Collapsible Sections in MD](#Collapsible_Sections_in_MD)
- [Centering Content in MD](#Centering_Content_in_MD)
- [Keyboard Keys in MD](#Keyboard_Keys_in_MD)
- [Anchor Links in Mark Down](#Anchor_Links_in_Markdown)

---
### **Headings_in_Markdown**

We can add headings and subheadings like title, section, subsection and more using # (single hash), ## (double) , ### (triple) and more. Like this:
**# H1 - Project Title**
**## H2 - Section**
**### H3 – Subsection**
**#### H4**
**##### H5**
**###### H6**

---
### Text_Styling_in_MD

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
### Paragraph_&_Line_Break

We need to ad extra enter between two lines to go to new line
**This is a paragraph**

**This is a new paragraph**
Or we can enter two spaces after the first lie to go to new line
**Line one**  # Two extra spaces
**Line two**

---
## Lists_in_Markdown

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
### Links_in_MD

We can add links to words, when that word is clicked the user will be redirected to that link. We can do this by writing the word in third parentheses [ ] and link in the first parentheses ()
[GitHub](https://github.com)
Or we can add the link directly
https://github.com

---
### Images_in_MD

We can simply drop and drop the image in README editor. Or we can add manually using 
!-[alt text]-(image-url), remove the hyphens

![Alt text](image-url)

Image with link, when tapped will be redirected to link [ -! - [Logo](image-url)]-(https://link.com) remove the hyphens

[ ![Logo](image-url)](https://link.com)

---
### Code_Blocks_in_MD

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
### Blockquotes_in_MD

We can use is single right > for quote and double right arrow for nested quote >>
> This is a quote
> > Nested quote

---
### Tables_in_MD

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
### Horizontal_Line_in_MD

We can use --- , *** and __ to create lines

---
***
___

### Emoji_in_MD

Add emojis directly
🚀 ✨ 🔥 ✅ ❌ ⚠️ 🧠 🎯 📦

---
### Collapsible_Sections_in_MD

Using details and summary tags 

<details>

<summary>Click to expand</summary>

Hidden content here

</details>

---
### Centering_Content_in_MD

Using HTML’s div tag
<div align="center">
# Project Title
</div>

___
### Keyboard_Keys_in_MD

Follow this pattern (It’ll show **Press ctr + c**):

Press <kbd>Ctrl</kbd> + <kbd>C</kbd>

---
### Highlighted_Notes_in_MD

Use right arrow **>** and double star *…*

> **⚠**️ **Warning:** Be careful

>💡**Tip:** Useful info

---
### Anchor_Links_in_Markdown

For table of contents **- [install] ** **(#heading or # Subheading)**
- [Install](#install)
- [Usage](#usage)

For Heading
**## Install**
