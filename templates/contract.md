---
systems: []           # Keep single-line for grep: systems: [auth, api]
status: draft         # draft | frozen — freeze when the dash moves to active/
owner:                # The ONE story that implements this: auth/02-jwt-claims
consumers: []         # Stories that build against it: [billing/04-invoice-email]
created: YYYY-MM-DD
---

# Contract Name

## Interface
<!-- The exact shape. Schemas, function signatures, event payloads, routes,
     table columns. Specific enough that owner and consumers can build in
     parallel without talking to each other. -->

## Guarantees
<!-- Behavior consumers may rely on. Invariants, error cases, ordering. -->

## Open Questions
<!-- Must be EMPTY before freeze. A frozen contract with open questions is a
     planning failure. -->
