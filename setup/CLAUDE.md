# Domino Setup

You're in the setup folder. This runs once to integrate Domino into a project.

## What to Do

### 1. Add Import to Project CLAUDE.md

The project's root CLAUDE.md needs to import domino. Add this line:

```
@domino/CLAUDE.md
```

If the project doesn't have a CLAUDE.md yet, create one with:
```markdown
# Project Name

@domino/CLAUDE.md
```

### 2. Clean Up

Remove repo files that aren't needed after integration:
```bash
rm -rf domino/setup
rm -f domino/README.md
rm -f domino/icon.svg
```

## That's It

Once the import is added, Claude will automatically load the vault context when entering the project. The user can now create epics and stories just by asking.

Delete this folder when done.
