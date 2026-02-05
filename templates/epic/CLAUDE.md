# Epic Workspace

You are inside an epic. Read `epic.md` first — it contains:
- Vision: what this epic achieves
- Decisions: architectural choices (each should be testable)
- Dependency graph: which stories can run in parallel
- Context files: key codebase files this epic touches

## Story Lifecycle
```
backlog/ → active/ → in-review/ → completed/
   │          │           │            │
   │          │           │            └─ Merged, reference only
   │          │           └─ Tests pass, awaiting human review
   │          └─ Being implemented (agent assigned)
   └─ Defined but not started
```

## Execution Model

### Single Story
1. Move story from `backlog/` to `active/`
2. Update frontmatter: `agent: your-id`, `agent_status: implementing`
3. Read story for acceptance criteria
4. Check `completed/` for stories with overlapping `systems:` tags
5. TDD: write tests → implement → move to `in-review/`

### Parallel Execution (Multiple Stories)
Read the dependency graph in `epic.md`. For independent stories:

1. Identify stories with no blockers (usually the first group)
2. Spawn one subagent per story
3. Each subagent: claim story, implement, move to `in-review/`
4. Wait for all subagents to complete
5. Spawn next group of subagents
6. Repeat until all stories are in `in-review/`

```
# Example from epic.md dependency graph:
# 01, 02, 03 can run parallel (no deps)
# 04, 05 can run parallel (after group 1)
# 06 runs last (after all)

# Spawn: agent-01, agent-02, agent-03
# Wait for completion
# Spawn: agent-04, agent-05
# Wait for completion
# Spawn: agent-06
```

## Escalation

**If a story doesn't answer something you need to implement: STOP.**

1. Write the question under `## Blocked` in the story file
2. Update frontmatter: `agent_status: blocked`
3. Report: "Story [name] blocked. Question: [question]"
4. Do NOT proceed. Do NOT assume.

Assuming is how agents drift. A blocked story waiting for clarification is better than a "completed" story that built the wrong thing.

## Epic Completion
When all stories reach `in-review/` or `completed/`:

1. Run automated review (Codex if available, otherwise spawn a review subagent)
2. Fix any issues (create fix stories, run through pipeline)
3. Human reviews all `in-review/` stories
4. Human moves epic to `done/` (from domino root): `mv active/{epic} done/`
