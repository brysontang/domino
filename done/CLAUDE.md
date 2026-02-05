# Done

Epics here are shipped. Historical reference only.

## What This Folder Is
The archive. Completed epics live here so you can reference past decisions, patterns, and implementations.

## What You Can Do
- Read epics and stories for context
- Find patterns: "How did we implement X last time?"
- Reference decisions: "What did we decide about Y?"

## What You Cannot Do
- **Do NOT modify anything in this folder**
- Do NOT move stories or epics
- Do NOT "fix" old code through these files

## Using Done for Context
When working on a new story, check if a completed epic touched similar systems:

```bash
# Find epics that touched the auth system
grep -rl "systems:.*auth" done/

# Read a completed story for patterns
cat done/old-epic/completed/relevant-story.md
```

The `systems:` tags in frontmatter help you find related work.

## If Something Needs Fixing
If you find a bug in shipped code:
1. Do NOT edit the done epic
2. Create a new epic in `backlog/` or `planning/`
3. Reference the old epic: "Fixes issue from done/old-epic"
