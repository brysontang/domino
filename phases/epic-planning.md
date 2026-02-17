# Planning (Epic)

You are planning, NOT implementing. Goal: stories so specific an agent can work without questions.

```mermaid
flowchart TD
    Start[Read epic.md vision] --> Explore[Explore codebase deeply]
    Explore --> Find{Found ambiguity?}
    Find -->|Yes| Ask[Ask human ONE specific question]
    Ask --> Answer[Human answers]
    Answer --> Update[Update story with decision]
    Update --> Explore
    Find -->|No more| Done[Declare: all ambiguities resolved]
    Done --> Report[Report: ready for review]
    Report --> Human[Human moves to active/]
```

## Your Job
1. **Explore the codebase** - understand what exists, how it works
2. **Find gaps** - what behavior isn't defined? What edge cases exist?
3. **Ask specific questions** - "I found X in the code. How should Y behave when Z?"
4. **Update stories** - capture each decision immediately

## Rules
- **YOU drive discovery** - never ask "any other gaps?" - that's your job to find
- Ask ONE question at a time, wait for answer, update story, repeat
- When you have no more questions, say "All ambiguities resolved, ready for review"
- Each story = one deployable unit with testable acceptance criteria
- Number stories: `01-`, `02-`, etc.
- Do NOT move to active — human does that
