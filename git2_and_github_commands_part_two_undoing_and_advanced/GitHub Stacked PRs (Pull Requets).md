Stacked Pull Requests are two or more Pull Requests in the same repository, where the first (bottom) PR targets the trunk usually `main` and each subsequent PR targets the branch of the PR below it.

> **In One Sentence:** A Stack is a chain of PRs where each one builds on the previous one, so we never have to wait for one to merge before starting the next

Like we opened a PR called **"Added Auth"** with our current `feature/auth` branch by comparing it with `main` and wanting to merge the PR (**Added Auth**) with `main`. But we can't open another PR from `feature/auth` branch unless the previous one has to be reviewed and merged, wasting valuable time. This is where Stacked PRs comes in

---
### The Problem it Solves

Imagine we're building the Local Event Finder app and we have 3 things to do that depend on each other:

```ASCII
1. Set up database models       (everything depends on this)
2. Build the API endpoints      (depends on models being done)
3. Build the Flutter map screen (depends on API being done)
```

##### The Solution:
**Without stacks**, we write all 3 in one giant PR. One PR = one massive diff. Reviewer gives up. Nobody reviews it properly. It goes stale. We merge it hoping for the best.

**With stacks**, 3 small PRs, each reviewable on its own. We don't wait for PR 1 to merge before starting PR 2. We keep building.

> **The key principle:** if code in one layer depends on code in another, the dependency must be in the same branch or a lower one.

Otherwise, create a new branch when we start a different concern like when you switch from backend to frontend work, move from core logic to tests, or when the current branch is already large enough to review.

---
### Mental_Model

Remember, Foundational changes like shared types and database schema go in lower branches, and code that depends on them like API routes and UI components go in higher branches

```ASCII
main (trunk)
  │
  └── feat/db-schema         → PR #1  ← BOTTOM (targets main)
        │
        └── feat/api-routes  → PR #2  (targets feat/db-schema)
              │
              └── feat/map-ui → PR #3  ← TOP (targets feat/api-routes)

```

Here, each PR's diff shows ONLY its own changes:
- **PR #1 diff:** just the db model files
- **PR #2 diff:** just the API files (not the db stuff again)
- **PR #3 diff:** just the Flutter UI files (not API or db stuff)
Reviewer reads 200 lines per PR, not 600 lines all at once.

---
## The Tool or CLI (`gh stack`) to Manage Stacks

The `gh stack` extension in **GitHub CLI** handles the local development workflow. We can:
- Create and track branches in the correct dependency order
- Keep branches rebased, push branches
- Create and link pull requests, and navigate between layers.

The biggest pain with manual stacking is rebasing. If **PR #1** changes after review, branches like **feat/api-routes** and **feat/map-ui** above it,(see [Mental Model](#Mental_Model) above) all need to be rebased. Rebasing is the trickiest part of working with stacks, and **GitHub** handles it automatically.
So, we can trigger a server-side cascading rebase from the pull request, or run a local cascading rebase with `gh stack`

---
### Installation

Step-1, Make sure GitHub CLI is installed and authenticated

```bash
gh auth login
```

Step-2, Install the `gh-stack` extension

```bash
gh extension install github/gh-stack
```

Step-3, Optional butcreate a short alias so we type less. Like **`gs push`** works instead of **`gh stack push`**

```bash
gh stack alias
```

---
### Core CLI Commands

The Full Workflow:

#### 1. Setting up a stack:
We’re on **main** branch. Start a new stack by running the below command. This initializes our Stack with **feat/db-schema** as the first layer and the Trunk is set to **main** branch automatically
 
```bash
gh stack init feat/db-schema
```

Now write our database models. Stage and commit. Then when we're ready for the next concern. Just run the below command to add a new layer on top the current branch.

```bash
gh stack add feat/api-routes
```

Or stage all changes, commit, and add the new branch in one step by combining **-A** = stage all and **-m** = commit message flags together

```bash
gh stack add -Am "Add event db models" feat/api-routes
```

 Finally add the third layer the same way:

```bash
gh stack add -Am "Add API endpionts" feat/map-ui 
```

Now check what our local stack looks like using this command

```bash
gh stack view
```

Output:

```ASCII
feat/map-ui ← top (we are here)
feat/api-routes
feat/db-schema ← bottom
main ← trunk
```

#### 2. Pushing and Creating PRs:
The below command pushes branches to the remote repo and creates a Pull Request for every branch in the Stack. After creating Pull Requests, **`gh stack`** **submit** automatically creates a stack on **GitHub** to link the pull requests together.

```bash
gh stack submit
```

In an interactive terminal, **`gh stack submit`** opens a full-screen editor where we can draft the “title” and “description” for each PR, and choose whether the pull request opens ready for review or as a draft. By using these commands:
- Skip the editor and auto-generate titles (as a draft):
```bash
gh stack submit --auto
```

- Skip the editor and open as read-for-review (not draft):
```bash
gh stack submit --auto --open
```

#### 3. Navigating between Layers:
Without these we'd be doing **`git checkout <branch-name>`** and constantly forgetting names. To:

| Operation or Instruction                    | The Command           |
| ------------------------------------------- | --------------------- |
| Move up one layer (away from trunk or main) | **`gh stack up`**     |
| Move down one layer (toward trunk)          | **`gh stack down`**   |
| Jump up 2 layers                            | **`gh stack up2`**    |
| Jump to topmost branch                      | **`gh stack top`**    |
| Jump to bottom branch                       | **`gh stack bottom`** |
| Jump to **main**                            | **`gh stack trunk`**  |
| Choose a layer using interactive picker     | **`gh stack switch`** |

#### 4. Keeping the Stack in Sync:
This command is our daily driver:

```bash
gh stack sync
```

It:
- Fetches the latest changes from origin
- Reconciles the remote stack locally
- Fast-forwards the trunk branch
- Cascades a rebase across all stack branches
- Pushes all branches, syncs Pull Request state from **GitHub**, and links the Stack's open Pull Requests.

For syncing and deleting branches for merged PRs automatically pair it with **--prune** flag

```bash
gh stack sync --prune
```

#### 5. When Changes are Requested on PR #1:
We go down to the bottom, fix it, commit, then run the below command. **gh stack rebase** does cascading rebase, fixes all branches above automatically and **gh stack push** pushes all updated branches:

```bash
gh stack rebase
gh stack push
```

If a rebase conflict occurs, the operation pauses and prints conflicted files. Resolve the conflicts, stage them with **git add**, then continue with **--continue**. To undo the entire, rebase, use **--abort**.
- After resolving conflicts:
```bash
gh stack rebase --continue
```

- If we changed our mind:
```bash
gh stack rebase --abort
```

---
## Merging With Stacked PRs

This is the Stack state before merging:

```ASCII
main ← PR #1 (db-schema) ← PR #2 (api-routes) ← PR #3 (map-ui)
```

#### Option-A, Merge the Entire Stack at Once:
Merge **PR #3** (the top). Everything below (**PR #2**, **PR#1**) comes with it. All 3 merge into **main**. For interactive picks what to merge:

```bash
gh stack merge
```

For no prompts, squash commits

```bash
gh stack merge --yes --squash
```

#### Option-B, Merge only PR #1 (partial merge form bottom):
 Like if we only merge PR #1 then:
 
```ASCII
Before: main ← PR#1 ← PR#2 ← PR#3
After:  main ← PR#2 ← PR#3
                ↑
         PR#2 now targets main directly (auto-retargeted)
```

**PR #2** and **#3** stay open. **GitHub** automatically re-targets **PR #2** to point at **`main`**

#### Option-C, Merge a Mid-Stack PR#2:
The hard rule, PRs must always merge from the bottom up. We can never merge **PR #2** without **PR #1** going first.

```ASCII
Before: main ← PR #1 ← PR #2 ← PR #3

After merge of PR #2:

  → PR #1 and PR #2 merge into main

  → PR #3 stays open, auto-retargets to main
```

---
## Common Mistakes

- ##### Mistake-1, Using Stack of Independent Changes:
 Stacks are for dependent changes. If our map UI doesn’t actually use the API code, they shouldn’t be in the same Stack. Independent work = separated PRs, not a Stack

- ##### Mistake-2, Committing to The Wrong Layer:
If we're on **`feat/map-ui`** (top) and we need to fix something in **`feat/db-schema`** (bottom). We fix it on the top layer. Now our stack is logically broken because UI layer has **`db`** code in it.
Fix, **`gh stack down`** to the right layer, fix it there, then **`gh stack rebase`** back up.

- ##### Mistake-3, Not Syncing Before Adding a New Layer:
We add a new branch while **`main`** has moved forward. Our Stack is now behind. Always **`gh stack sync`** before adding new work.

- ##### Mistake-4, Manually Rebasing Branches in a Stack:
Don't **`git rebase`** individual branches in a Stack manually. We'll break the chain. That's exactly what **`gh stack rebase`** is for, it does the cascading rebase in the right order.

---
