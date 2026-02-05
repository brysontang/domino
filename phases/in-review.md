# In Review

Stories here have passing tests and are awaiting review.

Do not modify stories here unless fixing issues from Codex.

---

## The Codex Gate

**When ALL stories in the epic are in `in-review/`, run Codex.**

This is the gate. The epic does not proceed until Codex is happy.

### Run Codex

```bash
codex review  # Reviews full branch diff against main
```

**Wait.** Codex takes time. This is the holding pattern. Don't burn tokens while it runs.

### Handle Feedback

**Logic Bug** (typo, null check, off-by-one, lint issue, simple oversight)
→ Spawn a subagent to fix immediately
→ Run Codex again

**Functionality Issue** (missing feature, wrong behavior, architectural concern)
→ Create a new story in `../backlog/`
→ If the solution is ambiguous, **ask the user** before proceeding
→ Run story through TDD pipeline
→ Run Codex again

### The Loop

```
Codex review → issues found?
  → Logic bug: subagent fix → Codex review
  → Functionality: new story → TDD → Codex review
  → No issues: proceed to human review
```

**Do not skip Codex. Do not exit early. Loop until Codex approves.**

---

## Human Review

Once Codex is happy:

1. Human reviews all stories in `in-review/`
2. Human verifies acceptance criteria are met
3. Human moves epic to done:
   ```bash
   mv active/{epic-name} done/
   ```
