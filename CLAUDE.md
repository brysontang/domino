# Vault

This is the task vault. The file system is the instruction set.

## Philosophy

There is no orchestration daemon. No database. No custom scripts. Just `mv`, `find`, `grep`, and CLAUDE.md doing what it already does natively.

Moving a folder IS the orchestration:
- `mv epics/planning/my-epic epics/active/` → Epic is greenlit, agents can work
- `mv backlog/story.md active/` → Story is claimed, work begins
- `mv active/story.md in-review/` → Implementation done, awaiting review
- `mv epics/active/my-epic epics/done/` → Epic shipped

You walk into a folder and become the right agent for that context.

## Structure
```
domino/
├── phases/      # Canonical instructions (single source of truth)
├── templates/   # Dash/epic/story/contract templates (use @ imports)
├── epics/       # Single epics
│   ├── backlog/   — epics waiting to be planned
│   ├── planning/  — epics being specced
│   ├── active/    — epics approved for execution
│   └── done/      — shipped epics (historical reference)
└── dashes/      # Multi-epic pushes (shorter than a sprint)
    ├── backlog/   — dashes waiting to be planned
    ├── planning/  — epics specced in isolation, then woven into one graph
    ├── active/    — dashes approved for execution
    └── done/      — shipped dashes
```

A dash is a folder of epics shipped together, plus `contracts/` — frozen
interface docs that let the epics run in parallel. Cross-epic dependencies are
story-level edges in `dash.md`; every edge must cite a contract.

## Creating Work

**New epic:**
```bash
cp -r templates/epic epics/backlog/my-epic-name
# Edit epics/backlog/my-epic-name/epic.md with vision
```

**New story:**
```bash
cp templates/story.md epics/planning/my-epic/backlog/01-story-name.md
# Edit with acceptance criteria
```

**New dash:**
```bash
cp -r templates/dash dashes/backlog/my-dash-name
# Edit dash.md with vision — epics get split out during planning
```

## Navigation
- Each epic is a folder containing `epic.md` and story subfolders
- Stories live in: `backlog/`, `active/`, `in-review/`, `completed/`
- Find active stories: `find epics/active/ -path "*/active/*.md" ! -name "CLAUDE.md"`
- Find by system: `grep -rl "systems:.*jwt" epics/ dashes/`
- Find a contract's consumers: `grep -rl "contracts:.*jwt-claims" dashes/`

## Parallel Execution

When entering an active epic, check the dependency graph in `epic.md`. Stories without dependencies can run in parallel using subagents:

```
# If stories 01, 02, 03 have no dependencies:
# Spawn 3 subagents, one per story
# Wait for all to reach in-review
# Then spawn subagents for the next dependency group
```

Inside an active dash there are no waves at all — one story-level DAG spans
every epic and stories launch the moment their dependencies complete. See
`phases/dash-workspace.md`.

## Autonomy

**Never ask permission to continue.** Move to the next task, next story, next wave. Just go.

**Escalate tradeoffs, not code.** When you hit a decision point with real tradeoffs:
- Don't ask "should I use approach A or B?"
- Do explain: "A is faster but harder to test. B is cleaner but adds a dependency."
- Let the user decide based on tradeoffs, not implementation details.

## Rules
- **When moving stories, never move CLAUDE.md** — move stories by name, not by glob
- Never modify stories in `epics/done/`
- Never start work on an epic that isn't in `epics/active/`
- **If something is ambiguous, stop and escalate. Do not assume.**

Assuming is how agents drift. If a story doesn't answer a question you need, STOP. Write the question under `## Blocked`. Report it. Wait for clarification.
