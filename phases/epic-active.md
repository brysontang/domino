# Active (Epic)

Epics here are greenlit. Enter the epic folder and follow its `CLAUDE.md`.

```mermaid
flowchart TD
    Start[Enter epic/] --> Read[Read epic.md + CLAUDE.md]
    Read --> Graph[Check dependency graph]
    Graph --> Spawn[Spawn subagents for independent stories]
    Spawn --> Wait[Wait for in-review/]
    Wait --> More{More stories?}
    More -->|Yes| Spawn
    More -->|No| Gate[Codex gate in in-review/]
```

## Rules
- Follow dependency graph — don't skip ahead
- Blocked stories > wrong implementations
- Use parallel mode (subagents) for speed
