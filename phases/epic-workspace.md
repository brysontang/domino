# Epic Workspace

Read `epic.md` first for vision, decisions, and dependency graph.

```mermaid
flowchart TD
    Start[Read epic.md] --> Branch[Create branch: epic/name]
    Branch --> Spawn[Spawn subagents for independent stories]
    Spawn --> Wait[Wait for all to reach in-review/]
    Wait --> More{More stories?}
    More -->|Yes| Spawn
    More -->|No| Codex[MANDATORY: Run codex review]
    Codex --> Issues{Issues?}
    Issues -->|Logic bug| Fix[Subagent fix] --> Codex
    Issues -->|Functionality| Story[New story + ask user] --> Spawn
    Issues -->|None| Done[mv to done/]
```

## Rules
- You are the **orchestrator**, not the implementer
- Spawn 3-4 subagents in parallel per wave
- Do NOT implement stories yourself (unless only one remains)
- **MANDATORY: When all stories reach in-review, run `codex review --uncommitted`. This is the final gate. Do NOT skip it. Do NOT move to done without Codex approval.**
- Loop until Codex approves — no early exit
