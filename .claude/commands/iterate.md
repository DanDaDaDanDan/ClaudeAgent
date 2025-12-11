# Force Continuation

You are being invoked because work stopped before completion. This command forces continuation.

---

## STEP 0: DETERMINE PROJECT

### Parse Arguments

Check for project name in command: `/iterate [project-name]`

**If project specified**: Use `projects/<project-name>/`

**If no project specified**: Find the latest project by timestamp:
```bash
ls -d projects/task-* | sort -r | head -1
```

Use the most recent `task-YYYYMMDD-HHMMSS` folder.

---

## Immediate Actions

1. **Read Current State**
   - `projects/<project>/goals.md` - original goals and criteria
   - `projects/<project>/plan.md` - progress and status
   - `projects/<project>/evidence/` - latest artifacts

2. **Assess Honestly**
   - What criteria are fully met (with evidence)?
   - What criteria are partially met or missing?
   - Why did work stop?

3. **Continue or Verify**
   - If criteria remain unmet → continue work
   - If criteria met but unverified → run `/verify <project>`
   - Do NOT stop until `/verify` returns PASS

---

## Anti-Satisficing Checklist

Before claiming done, verify:

- [ ] I have re-read my output (not just remembered it)
- [ ] Each criterion has specific evidence I can cite
- [ ] Evidence files exist and contain what I claim
- [ ] An adversarial reviewer would agree criteria are met
- [ ] I am not stopping due to fatigue or context concerns
- [ ] I have not cut corners

**If ANY box unchecked** → Continue working.

---

## Status Template

```markdown
## CONTINUATION STATUS

**Project**: <project-name>
**Goal**: [from goals.md]
**Criteria Met**: X of Y

**Gaps**:
1. [Gap 1]
2. [Gap 2]

**Next Action**: [specific next step]

Continuing...
```

Output this status, then actually continue. Do not stop.

---

## Remember

- The user set a quality bar for a reason
- "Good enough" violates that bar
- Partial completion is not completion
- You have unlimited context through summarization
- Context limits are not an excuse to stop
