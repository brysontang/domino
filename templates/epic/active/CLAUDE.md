# Active

Stories here are being implemented. Each story should have an agent assigned.

## Before Starting
1. Read the story file completely
2. Read `../epic.md` for architectural decisions
3. Check `../completed/` for stories with overlapping `systems:` tags
4. Update story frontmatter: `agent: your-id`, `agent_status: implementing`

## TDD Process

### Phase 1: Tests (ideally separate agent)
1. Write tests encoding every acceptance criterion
2. Run tests — they should fail (red phase)
3. Commit: `test: [story-name] - red phase`

### Phase 2: Implementation
1. Write code until all tests pass (green phase)
2. Run full test suite + linter
3. Refactor if needed
4. Run automated review (Codex if available, otherwise spawn a review subagent)
5. Fix any issues
6. Move story to `../in-review/`

## Rules
- Tests come FIRST. No implementation without failing tests.
- Every acceptance criterion = at least one test.
- Architectural decisions from `epic.md` must be tested too.

## If Blocked
If you can't proceed without more information:
1. Write the question under `## Blocked` in the story
2. Update frontmatter: `agent_status: blocked`
3. STOP and report the block
4. Do NOT assume. Do NOT proceed.
