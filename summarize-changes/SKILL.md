---
name: summarize-changes
description: Summarize all changes on the current branch compared to main in plain language, one bullet per change. Use for PR descriptions, handoffs, or quick recaps.
---

# Summarize Changes

Generate a plain-language summary of all changes on the current branch compared to main. 

## Arguments

- `$ARGUMENTS` - (optional) Base branch to compare against. Defaults to `origin/main`.

## Instructions

### Step 1: Gather the diff

1. Determine the base branch: use `$ARGUMENTS` if provided, otherwise `origin/main`
2. Run `git diff <base>...HEAD --stat` to get the list of changed files
3. Run `git diff <base>...HEAD` to get the full diff
4. Run `git log <base>...HEAD --oneline` to see commit messages for context

### Step 2: Analyze the changes

For each changed file or logical group of changes:

1. Identify **what** changed (the code)
2. Identify **why** it changed (the intent — bug fix, new feature, refactor, etc.)
3. Identify **impact** (what behavior is different for users or developers)

Group related changes together (e.g. a service change + its spec = one bullet).

### Step 3: Write the summary

Output a markdown list where each item is:

```
- **Short title** — One sentence explaining the change in plain language
```

Rules:
- One bullet per logical change, not per file
- Use plain language a non-engineer could understand
- Lead with what changed, not how
- Don't mention file paths or method names
- Group a code change with its tests into a single bullet
- Order by importance, not alphabetically
- Keep each bullet to one sentence

### Step 4: Output

Return only the markdown list. Actually markdown. Don't render the markdown. It should be code block. No preamble, no closing remarks.
