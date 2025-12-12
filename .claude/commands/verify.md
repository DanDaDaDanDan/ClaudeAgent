# Independent Verification

You are initiating VERIFICATION MODE. This launches an independent review of work against stated criteria.

**REMINDER**: This command MUST be run before presenting work as complete to the user. If you're seeing this because you ran `/verify`, good. If SOA tried to skip verification and ask the user if they're satisfied, that violates Hard Rule 4.

---

## STEP 0: DETERMINE PROJECT

### Parse Arguments

Check for project name in command: `/verify [project-name]`

**If project specified**: Use `projects/<project-name>/`

**If no project specified**: Find the latest project by timestamp:
```bash
ls -d projects/task-* | sort -r | head -1
```

Use the most recent `task-YYYYMMDD-HHMMSS` folder.

---

## MODEL CONFIGURATION

### Parse Model Selection

1. **Check command arguments** for `--model <name>`:
   - If present, use that model for verification
   - Valid values: `claude`, `gemini`

2. **If no flag**, check `projects/<project>/goals.md` for model config:
   ```markdown
   ## Model Configuration
   - **verification_model**: gemini
   ```

3. **If no config**, default to `claude` (Task tool with separate agent)

### Why Cross-Model Verification?

Using a different model provides:
- True independence (different training, different biases)
- Fresh perspective on the work
- Reduced risk of self-confirmation

---

## PRE-VERIFICATION CHECKLIST

Before proceeding, confirm ALL of these:

- [ ] `projects/<project>/goals.md` exists with success criteria
- [ ] `projects/<project>/plan.md` exists
- [ ] Evidence files exist in `projects/<project>/evidence/`
- [ ] You genuinely believe all criteria are met (not "close enough")

**If any box unchecked** → Do not verify yet. Complete prerequisites first.

---

## VERIFICATION PROCEDURE

### Step 1: Gather Context

Read and collect:
1. **Goals**: Read `projects/<project>/goals.md` completely
2. **Criteria**: Extract all success criteria and acceptance checklist
3. **Evidence**: List all files in `projects/<project>/evidence/`
4. **Claim**: Summarize what you're claiming is complete

### Step 2: Create Verification Request

Write to `projects/<project>/verification-request.md`:

```markdown
# Verification Request

**Project**: <project-name>
**Timestamp**: [datetime]
**Attempt Number**: [1, 2, or 3]
**Verification Model**: [claude or gemini]

## Original Goal
[From goals.md]

## Quality Bar
[From goals.md - what "done well" means]

## Success Criteria
1. [Criterion 1] — Evidence: [file/location]
2. [Criterion 2] — Evidence: [file/location]
3. [Criterion 3] — Evidence: [file/location]

## Evidence Files Submitted
- `evidence/[file1]` - [description]
- `evidence/[file2]` - [description]

## Completion Claim
[What you are claiming is done and how]

## Self-Assessment
[Honest assessment - where might this be weak?]
```

### Step 3: Launch Verification

**Determine which model to use** (see MODEL CONFIGURATION above).

#### Option A: Claude Verification (Default)

Use the Task tool to spawn an independent verification agent:

```
Use Task tool with:
- subagent_type: "general-purpose"
- prompt: [The verification prompt below]
```

**Verification Prompt:**

```
You are an INDEPENDENT VERIFIER. Your job is to objectively assess whether submitted work meets stated criteria.

## YOUR CONSTRAINTS
- You CANNOT give benefit of the doubt
- You CANNOT pass partial completion
- You MUST cite specific evidence for each criterion
- Missing evidence = automatic FAIL
- "Good enough" when bar was "excellent" = FAIL

## FILES TO READ
1. `projects/<project>/goals.md` - Success criteria and quality bar
2. `projects/<project>/plan.md` - What was planned
3. `projects/<project>/verification-request.md` - What's being claimed
4. ALL files in `projects/<project>/evidence/` - The actual evidence

## YOUR PROCESS
1. Read goals.md completely - understand what was supposed to happen
2. Read each evidence file completely - don't skim
3. For EACH success criterion:
   a. Find specific evidence that proves it
   b. Evaluate if evidence actually proves the criterion
   c. Note any gaps or weaknesses
4. Make your verdict

## YOUR OUTPUT FORMAT

---
## VERIFICATION RESULT

**Verdict**: PASS | FAIL

**Criteria Assessment**:
| Criterion | Verdict | Evidence | Notes |
|-----------|---------|----------|-------|
| [Criterion 1] | PASS/FAIL | [file or "MISSING"] | [note] |
| [Criterion 2] | PASS/FAIL | [file or "MISSING"] | [note] |

**Quality Assessment**:
- Completeness: [1-10] - [reason]
- Meets Stated Bar: YES/NO - [reason]

**Gaps Identified** (if FAIL):
1. [Specific gap]
2. [Specific gap]

**Required Actions** (if FAIL):
1. [Concrete action to fix gap 1]
2. [Concrete action to fix gap 2]

**Summary**:
[2-3 sentences on where this work stands relative to the goal]
---

Be thorough. Be skeptical. Find real problems.
```

#### Option B: Gemini Verification (Cross-Model)

Use the MCP tool for independent verification:

```
Use MCP tool: generate_text

Parameters:
- system_prompt: "You are an independent verifier. Assess whether work meets stated criteria. Be rigorous - do not give benefit of the doubt. Missing evidence = FAIL. Partial completion = FAIL."
- thinking_level: "high"
- temperature: 0.2 (low for consistent evaluation)
- prompt: |
    # Verification Task

    ## Original Goal
    [From goals.md]

    ## Quality Bar
    [From goals.md]

    ## Success Criteria
    [List all criteria]

    ## Evidence Submitted
    [Include relevant evidence content]

    ## Completion Claim
    [What is being claimed]

    ## Your Task
    Evaluate whether this work meets ALL criteria and the stated quality bar.

    Provide: Verdict (PASS/FAIL), criteria assessment table, gaps if any, required actions if FAIL.
```

### Step 4: Process Result

**If PASS**:
1. Update `projects/<project>/plan.md` status to ✅ COMPLETE
2. Log in `projects/<project>/verification-log.md`
3. Deliver final output to user

**If FAIL**:
1. Log in `projects/<project>/verification-log.md`
2. Update plan.md with gaps to address
3. Return to iteration - address each gap
4. Re-verify when gaps addressed

---

## VERIFICATION LIMITS

- **Maximum 3 verification attempts** per task
- After attempt 3, if still FAIL:
  - Present honest status to user
  - List remaining gaps
  - Ask user how to proceed

---

## ANTI-GAMING RULES

Do NOT:
- Cherry-pick which criteria to verify
- Soften criteria before verification
- Skip verification because "it's obviously done"
- Argue with verifier instead of fixing gaps

The verifier catches self-deception. Trust the process.
