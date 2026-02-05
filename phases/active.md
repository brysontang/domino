# Active (Story)

```mermaid
flowchart TD
    Start[Read story + epic.md] --> Tests[Write tests for acceptance criteria]
    Tests --> Red[Run tests — must fail]
    Red --> Commit1[Commit: test: story - red]
    Commit1 --> Code[Write code until tests pass]
    Code --> Green[Run full suite + linter]
    Green --> Commit2[Commit: feat: story - green]
    Commit2 --> Move[mv story to in-review/]
```

## Rules
- Tests FIRST — no code without failing tests
- Every acceptance criterion = at least one test
- If blocked: write question in `## Blocked`, set `agent_status: blocked`, STOP
