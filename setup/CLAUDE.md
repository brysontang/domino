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
rm -rf domino/.git        # no nested repo — the project's git owns the vault
rm -rf domino/setup
rm -rf domino/examples
rm -f domino/README.md
rm -f domino/icon.svg
```

To update the vault later, the project's README "Update" flow fetches a fresh
clone and syncs framework files — see `setup/UPDATE.md` upstream.

## That's It

Once the import is added, Claude will automatically load the vault context when entering the project. The user can now create epics and stories just by asking.

Tell the user to restart Claude Code so the new import is loaded properly.

Delete this folder when done.
