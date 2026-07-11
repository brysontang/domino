# Domino Update

You're updating an existing Domino install to the latest version. You were
launched from a fresh clone (e.g. `/tmp/domino-latest`); the installed vault
is the `domino/` folder inside the user's project.

## The One Rule

**Framework files get updated. Work never gets touched.**

- Framework: `phases/`, `templates/`, the vault's root `CLAUDE.md`, the
  lifecycle-folder `CLAUDE.md` pointers (`epics/*/CLAUDE.md`, `dashes/*/CLAUDE.md`)
- Work: everything the user put INSIDE the lifecycle folders — epic folders,
  dash folders, stories, contracts. Never modify, move, or delete these.

## What to Do

### 1. Detect local customizations

The installed vault may have been customized (e.g. Codex swapped for a review
subagent) or drifted (folders moved). Before overwriting anything:

```bash
diff -rq <fresh-clone>/phases/ domino/phases/
diff <fresh-clone>/CLAUDE.md domino/CLAUDE.md
```

For each framework file that differs, check whether the difference is an
upstream change (apply it) or a local customization (preserve it — merge the
upstream change around it). If you can't tell, show the user the diff and ask.

### 2. Sync framework files

- Copy new phase files and templates in; update changed ones (respecting step 1)
- Create any new top-level structure that doesn't exist yet (e.g. `dashes/`
  with its lifecycle folders) — copy the folders WITH their `CLAUDE.md`
  pointers, but never overwrite lifecycle folders that already contain work

### 3. Clean up

```bash
rm -rf domino/setup domino/examples
rm -f domino/README.md domino/icon.svg
rm -rf <fresh-clone>
```

### 4. Report

Tell the user what changed (new capabilities, updated phases), what local
customizations were preserved, and to restart Claude Code so imports reload.

## Rules

- **Never touch work artifacts** — if a framework change seems to require
  restructuring the user's epics or dashes, STOP and ask
- Local customizations win over upstream on conflict — ask when ambiguous
- Do NOT re-add the `@domino/CLAUDE.md` import if it already exists
