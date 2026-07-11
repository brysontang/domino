# Active (Dash)

Dashes here are greenlit. Enter the dash folder and follow its `CLAUDE.md`.

```mermaid
flowchart TD
    Start[Enter dash/] --> Read[Read dash.md + contracts/]
    Read --> Graph[Compile ONE story DAG across all epics]
    Graph --> Orchestrate[Launch stories as their deps complete]
    Orchestrate --> Gate[Per-story Codex review, merge as ready]
    Gate --> Final[Final dash gate when all epics done]
```

## Rules
- Contracts are FROZEN — a wrong contract is an escalation, not an edit
- Follow the DAG — cross-epic edges in dash.md, in-epic edges in each epic.md
- Blocked stories > wrong implementations
- No waves — a story starts the moment its dependencies are completed
