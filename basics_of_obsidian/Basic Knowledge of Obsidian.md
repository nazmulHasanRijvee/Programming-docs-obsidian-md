
---
### **Table of Contents**

- [Vault](#Vault)
- [Base in Obsidian](#Base_in_obsidian)
- [Insert Template](#Insert_Template)
- [Templates vs Bases](#Templates_vs_Bases)
- [Canvas in Obsidian](#Canvas_in_Obsidian)
- [Note Links in Obsidian](#Note_Links_in_Obsidian)
- [Tags in Obsidian](#Tags_in_Obsidian)
- [The Important Obsidian Pieces](#The_Important_Obsidian_Pieces)

---

### **Vault**

Vault in obsidian is like a knowledge base or  "A folder of Mark Down files (.md)". To create a Vault or open an existing Vault:
- Expand the file view and see the bottom left corner
- we'll see the current vaults name like "programming_docs_obsidian_md".
- Tap on it and click on manage vaults
- Here we can create new Vaults or open existing Vaults

We can create and open each of these folders as a separated Obsidian Vault. We aren't restricted to one. We have two commo approaches like

1. **One Big vault:**

``` ASCII
My Vault/
├── Flutter/
├── Python/
├── University/
├── Books/
└── Personal/
```

2. **Multiple vaults:**

``` ASCII
Programming Vault/
University Vault/
Personal Vault/
```

But it is recommended to use one vault when information is interconnected. For example , if our **Flutter** notes link to **Dart** notes, which link to programming concepts, keeping them together is useful because Obsidian's linking system can connect them to make a graph.

We can create as many as we want and can switch between them from Obsidian:

``` ASCII
Obsidian
│
├── Programming Vault
│
├── University Vault
│
├── Personal Vault
│
└── Project Vault
```


> **⚠**️ **Warning:** But **don't create a new vault for every project by default**. If we create:

```
Flutter Vault
Riverpod Vault
Python Vault
FastAPI Vault
ML Vault
```

We'll make it harder to connect related knowledge. Start with something like:

```
Knowledge Vault/
│
├── Programming/
│   ├── Flutter/
│   ├── Dart/
│   ├── Python/
│   ├── FastAPI/
│   └── ML/
│
├── University/
│
├── Projects/
│
└── Resources/
```

Then use **links, properties, tags, templates, and Bases** to organize it further. Use separate vaults we we want **strong separation** e.g. work vs personal, or completely unrelated knowledge bases.

The folders give us **physical organization**; the links give us **knowledge organization**. That's a very important distinction in Obsidian.

---

### **Base_in_Obsidian**

**Bases** aren't simply another kind of note. A Base is essentially a **database-like view of our notes**. Imagine we have:

```ASCII
Movies/
├── Interstellar.md
├── Inception.md
├── The Batman.md
└── Arrival.md
```

And inside those notes we have properties Like:

```YAML
title: Interstellar
director: Christopher Nolan
year: 2014
rating: 9
status: Watched
```

A base can take those properties and display them as something like:

| Title        | Director          | Year | Rating | Status  |
| ------------ | ----------------- | ---- | :----: | ------- |
| Interstellar | Christopher Nolan | 2014 |   9    | Watched |
| Inception    | Christopher Nolan | 2010 |   9    | Watched |
| Arrival      | Denis Villeneuve  | 2016 |   8    | Watched |
So the notes are still Mark Down files. The base is just another way of viewing and organizing those notes based on their properties. We can think of it as:

```ASCII
Markdown notes
      ↓
   Properties
      ↓
     Base
      ↓
Table / Cards / List / etc.
```

This is why it can feel somewhat like Excel or a database.

> **⚠️** **The important distinction:** A  Base doesn't replace our notes. It provides a structured view over our notes.

For example, we could have:

```ASCII
Flutter/
	Riverpod.md
	Provider.md
	Notifier.md
	AsyncNotifier.md
```

Each note could have:

```YAML
type: concept
difficulty: intermediate
status: learning
```

Then a Base could show, this where Bases become really useful for knowledge management:

```ASCII
Flutter Knowledge

Concept       Difficulty       Status
---------------------------------------
Riverpod      Intermediate     Learning
Provider      Beginner         Done
Notifier      Intermediate     Learning
AsyncNotifier Advanced         Learning
```

---

### **Insert_Template**

Templates are basically reusable note structures. Suppose whenever we learn something technical, we want our notes to have:

```Markdown
# Topic

## Definition

## How it works

## Example

## Common mistakes

## Related concepts
```

We don't want to type that every time. So, we create a template once:

```ASCII
Templates/
└── Technical Concept.md
```

Then: **Insert template → Technical Concept** and Obsidian inserts the structure into our current note. So:

```
New note
   ↓
Insert Template
   ↓
Predefined structure appears
```

Templates are especially useful for things like:
- Programming concepts
- Book notes
- Meeting notes
- Daily notes
- Project notes
- Study notes
- Bug reports
- Research notes

---

### **Templates_vs_Bases**

These are completely different things.

#### Template

Helps us **create notes consistently**.

```
Template
   ↓
New Note
   ↓
Same structure every time
```

#### Base

Helps us **organize/view existing notes**.

```
Many Notes
   ↓
Properties
   ↓
Base
   ↓
Table / List / Cards / etc.
```

So we might actually use both together. For example:

```
Template
   ↓
Creates standardized movie notes
   ↓
Each movie gets properties
   ↓
Base
   ↓
Shows all movies in a table
```


---

### **Canvas_in_Obsidian**

Canvas is more visual. Instead of:

```ASCII
Note A
   ↓
Note B
   ↓
Note C
```

We can put things visually on a board:

```ASCII
┌──────────────┐
│ Flutter      │
│ Architecture │
└──────┬───────┘
       │
       ↓
┌──────────────┐
│ Repository   │
│ Pattern      │
└──────┬───────┘
       │
       ↓
┌──────────────┐
│ API Layer    │
└──────────────┘
```

We can put notes, text, images, links, etc. onto the Canvas and connect them. It's useful for **brainstorming, planning, visualizing relationships, architecture, research, etc.**


---

### **Note_Links_in_Obsidian**

Obsidian isn't really powerful because it lets us make folders. It's powerful because we can write this using [[Basics of Mark Down File]]:

```
I'm learning [[Riverpod]].

Riverpod uses [[Provider]] and can work with
[[AsyncNotifier]].
```

Now our notes are connected and we can click to open it. So, we can have:

```
Flutter
   │
   ├── Dart
   │    └── Async/Await
   │
   ├── Riverpod
   │    ├── Provider
   │    └── AsyncNotifier
   │
   └── Architecture
        ├── MVVM
        └── Repository Pattern
```

That's where Obsidian starts becoming more than just a folder containing Markdown files.


---

### Tags_in_obsidain

We can use colorful tags only in Obsidian, like to indicate a category and by clicking on the tag we can see in which notes the tags are present
Use #.... with no spacing to specify a tag

#Center

#Coding

#Docs

___

### **The_Important_Obsidian_Pieces**

We can think of Obsidian's core features like this:

|Feature|Purpose|
|---|---|
|**Vault**|Your knowledge base / folder|
|**Folder**|Organize files physically|
|**Markdown note**|Your actual content|
|**Link**|Connect notes together|
|**Properties**|Structured metadata about a note|
|**Tags**|Categorize notes|
|**Template**|Reusable note structure|
|**Base**|Database-like view of notes|
|**Canvas**|Visual workspace|
|**Graph View**|Visualize connections between notes|
|**Plugins**|Add functionality|
|**Commands**|Perform actions quickly|
