# Active

Epics here are greenlit for execution. This is where work happens.

## Your Role: Executor & Orchestrator

You can implement. You can spawn subagents. You run the pipeline.

## Process

### 1. Pick an Epic
If multiple epics are active, the human will direct you. Otherwise, pick one.

### 2. Read the Epic
Enter `{epic}/` and read:
- `epic.md` — vision, decisions, dependency graph
- `CLAUDE.md` — execution instructions
- `backlog/` — stories waiting to be worked

### 3. Execute Stories

**Single story mode:**
1. Move lowest-numbered story from `backlog/` to `active/`
2. Claim it: update `agent:` and `agent_status:` in frontmatter
3. TDD: write tests, implement, move to `in-review/`
4. Repeat

**Parallel mode (recommended for speed):**
1. Read dependency graph in `epic.md`
2. Identify stories with no blockers
3. Spawn one subagent per independent story
4. Wait for all to complete
5. Spawn next wave based on dependency graph
6. Repeat until all stories in `in-review/`

### 4. Handle Blocks
If a story is ambiguous:
- Write question under `## Blocked`
- Update `agent_status: blocked`
- Report the block
- Move to next story or wait for clarification

### 5. Epic Completion
When all stories are in `in-review/` or `completed/`:
1. Run Codex review
2. Fix issues (create fix stories, run through pipeline)
3. Report: "Epic [name] ready for human review"
4. Human reviews and moves to `done/`

## Rules
- Only work on epics in THIS folder
- Follow the dependency graph — don't skip ahead
- Blocked stories are better than wrong implementations
- Commit often, test always

## Quick Commands
```bash
# See all stories needing work
find . -path "*/backlog/*.md" ! -name "CLAUDE.md"

# See what's in progress
find . -path "*/active/*.md" ! -name "CLAUDE.md"

# See what's waiting for review
find . -path "*/in-review/*.md" ! -name "CLAUDE.md"
```
