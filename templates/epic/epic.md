---
systems: []           # Keep single-line for grep: systems: [auth, api]
created: YYYY-MM-DD
---

# Epic Name

## Vision
What is this epic about? What problem does it solve? One paragraph.

## Business Intent
<!-- What MUST be true when this epic ships? These are the checkable outcomes
     that the Intent Check verifies at the end. Be specific and concrete. -->
<!-- Example:
- Users can sign up with email and immediately access the dashboard
- Stripe processes payments without manual intervention
- Admin can disable accounts from the management UI
-->

## Decisions
<!-- Populated during planning. Each decision should be specific enough to generate a test. -->

## Dependency Graph
<!-- Show which stories can run in parallel and which are blocked -->
<!-- Example:
```
01-api ──────┬──► 04-frontend ──► 06-launch
02-emails ───┤
03-design ───┘   05-integration ─┘

Parallel groups:
- Group 1: 01, 02, 03 (no dependencies)
- Group 2: 04, 05 (after group 1)
- Group 3: 06 (after all)
```
-->

## Context Files
<!-- Key files in the codebase that this epic touches -->

## Notes
<!-- Anything else the agent should know -->
