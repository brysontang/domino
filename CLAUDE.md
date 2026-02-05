# Vault

This is the task vault. The file system is the instruction set.

## Philosophy

There is no orchestration daemon. No database. No custom scripts. Just `mv`, `find`, `grep`, and CLAUDE.md doing what it already does natively.

Moving a folder IS the orchestration:
- `mv planning/my-epic active/` → Epic is greenlit, agents can work
- `mv backlog/story.md active/` → Story is claimed, work begins
- `mv active/story.md in-review/` → Implementation done, awaiting review
- `mv active/my-epic done/` → Epic shipped

You walk into a folder and become the right agent for that context.

## Structure
- `backlog/` — epics waiting to be planned
- `planning/` — epics being specced (stories written, assumptions resolved)
- `active/` — epics approved for execution. Agents work here.
- `done/` — shipped epics. Historical reference only.

## Creating Work

**New epic:**
```bash
cp -r templates/epic backlog/my-epic-name
# Edit backlog/my-epic-name/epic.md with vision
```

**New story:**
```bash
cp templates/story.md planning/my-epic/backlog/01-story-name.md
# Edit with acceptance criteria
```

## Navigation
- Each epic is a folder containing `epic.md` and story subfolders
- Stories live in: `backlog/`, `active/`, `in-review/`, `completed/`
- Find active stories: `find active/ -path "*/active/*.md" ! -name "CLAUDE.md"`
- Find by system: `grep -rl "systems:.*jwt" .`

## Parallel Execution

When entering an active epic, check the dependency graph in `epic.md`. Stories without dependencies can run in parallel using subagents:

```
# If stories 01, 02, 03 have no dependencies:
# Spawn 3 subagents, one per story
# Wait for all to reach in-review
# Then spawn subagents for the next dependency group
```

## Autonomy

**Never ask permission to continue.** Move to the next task, next story, next wave. Just go.

**Escalate tradeoffs, not code.** When you hit a decision point with real tradeoffs:
- Don't ask "should I use approach A or B?"
- Do explain: "A is faster but harder to test. B is cleaner but adds a dependency."
- Let the user decide based on tradeoffs, not implementation details.

## Rules
- **When moving stories, never move CLAUDE.md** — move stories by name, not by glob
- Never modify stories in `done/` epics
- Never start work on an epic that isn't in `active/`
- **If something is ambiguous, stop and escalate. Do not assume.**

Assuming is how agents drift. If a story doesn't answer a question you need, STOP. Write the question under `## Blocked`. Report it. Wait for clarification.
