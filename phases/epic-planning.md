# Planning (Epic)

You are planning, NOT implementing. Goal: stories so specific an agent can work without questions.

```mermaid
flowchart TD
    Start[Read epic.md vision] --> Explore[Explore codebase]
    Explore --> Ask{Ambiguities?}
    Ask -->|Yes| Clarify[Ask human] --> Ask
    Ask -->|No| Write[Write stories in backlog/]
    Write --> Graph[Build dependency graph in epic.md]
    Graph --> Report[Report: ready for review]
    Report --> Human[Human moves to active/]
```

## Rules
- Ask questions FIRST — planning is where ambiguity gets resolved
- Each story = one deployable unit with testable acceptance criteria
- Number stories: `01-`, `02-`, etc.
- Do NOT move to active — human does that
