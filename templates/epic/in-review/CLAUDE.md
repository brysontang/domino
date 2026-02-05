# In Review

Stories here have passing tests and have been through automated review.

These are waiting for human review. Do not modify unless asked.

If the human requests changes, make them and keep the story here until approved.

When approved, move to `../completed/`.

---

## Epic Completion

When ALL stories are in `in-review/` or `completed/`, the epic enters the **review loop**:

### Review Loop

1. **Run automated review** (Codex if available, otherwise spawn a review subagent):
   ```bash
   git diff main --stat  # See scope of changes
   ```

2. **For each issue found:**
   - If ambiguous → ask human for clarification
   - If clear → create a new fix story in `backlog/`

3. **Run fix stories through the pipeline:**
   - Move to `active/`
   - TDD: write tests, implement, verify
   - Move to `in-review/`

4. **Run review again**

5. **Loop until review is clean** (no issues or only minor notes)

### Final Steps

6. **Human reviews** the full epic:
   - Check all stories in `in-review/`
   - Verify acceptance criteria met
   - Test key flows manually if needed

7. **Human moves epic to done** (from domino root):
   ```bash
   mv active/{epic-name} done/
   ```
