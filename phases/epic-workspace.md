# Epic Workspace

Read `epic.md` first for vision, decisions, and dependency graph.

```mermaid
flowchart TD
    Start[Read epic.md] --> Branch[Create branch: epic/name]
    Branch --> Spawn[Spawn subagents for independent stories]
    Spawn --> Wait[Wait for all to reach in-review/]
    Wait --> More{More stories?}
    More -->|Yes| Spawn
    More -->|No| Codex[Run Codex review]
    Codex --> Issues{Issues?}
    Issues -->|Logic bug| Fix[Subagent fix] --> Codex
    Issues -->|Functionality| Story[New story + ask user] --> Spawn
    Issues -->|None| Human[Human review]
    Human --> Done[mv to done/]
```

## Rules
- You are the **orchestrator**, not the implementer
- Spawn 3-4 subagents in parallel per wave
- Do NOT implement stories yourself (unless only one remains)
- Loop until Codex approves — no early exit
