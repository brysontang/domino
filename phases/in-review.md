# In Review (Story)

Stories here have passing tests. Do not modify unless fixing Codex issues.

```mermaid
flowchart TD
    Check{All stories in in-review?}
    Check -->|No| Wait[Wait for other stories]
    Check -->|Yes| Codex[Run: codex review --uncommitted]
    Codex --> Result{Result?}
    Result -->|Logic bug| Fix[Fix immediately] --> Codex
    Result -->|Functionality| Story[New story in backlog/] --> TDD[TDD pipeline] --> Codex
    Result -->|Clean| Human[Human review]
    Human --> Done[mv epic to done/]
```

## The Codex Gate

**Run this exact command:**
```bash
codex review --uncommitted
```

This is the `codex` CLI tool, NOT a subagent. Wait for it to complete.

## Rules
- **Do NOT move to done until Codex is clean**
- Logic bugs: fix immediately, re-run `codex review --uncommitted`
- Functionality issues: create story, ask user if ambiguous, TDD, re-run Codex
- Loop until Codex has no issues
