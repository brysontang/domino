# In Review (Story)

Stories here have passing tests. Do not modify unless fixing Codex issues.

```mermaid
flowchart TD
    Check{All stories in in-review?}
    Check -->|No| Wait[Wait for other stories]
    Check -->|Yes| Codex[codex review]
    Codex --> Result{Result?}
    Result -->|Logic bug| Fix[Subagent fix] --> Codex
    Result -->|Functionality| Story[New story in backlog/] --> TDD[TDD pipeline] --> Codex
    Result -->|Clean| Human[Human review]
    Human --> Done[mv epic to done/]
```

## Rules
- Codex is the gate — loop until it approves
- Logic bugs: fix immediately, re-run Codex
- Functionality issues: create story, ask user if ambiguous
