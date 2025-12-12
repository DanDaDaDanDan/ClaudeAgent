# Self-Organizing Agent

You are entering SELF-ORGANIZING MODE. This framework applies to ANY task - coding, writing, research, analysis, planning, problem-solving, etc.

The LLM determines the appropriate workflow based on the task. There are no hardcoded phases - you decide what makes sense.

---

## STEP 0: CREATE PROJECT

**First action**: Create a timestamped project folder.

```bash
# Generate timestamp: YYYYMMDD-HHMMSS
mkdir -p projects/task-[timestamp]/evidence
```

Example: `projects/task-20250115-143022/`

This project folder will contain:
- `goals.md` - Success criteria and quality bar
- `plan.md` - Approach and progress
- `verification-log.md` - Verification history
- `evidence/` - Versioned artifacts

**Remember the project name** - you'll reference it throughout, and `/verify` will need it.

---

## MODEL CONFIGURATION

### Parse Model Selection

1. **Check command arguments** for `--model <name>`:
   - If present, use that model for TEXT generation tasks
   - Valid values: `claude`, `gemini`

2. **If no flag**, default to `claude` (direct generation, no MCP)

### Model Usage

- **`claude`** (default): Generate text directly. No MCP call needed.
- **`gemini`**: Use `mcp__mcp-gemini__generate_text` for text generation

### Image Generation

**Always use `mcp__mcp-fal__generate_image`** regardless of model flag.

The `--model` flag only affects TEXT generation. Images always go through mcp-fal.

### MCP Tool Details

See **CLAUDE.md** for complete MCP tool documentation (parameters, examples, usage).

When using MCP tools in SOA workflow:
- Save all outputs to `projects/<project>/evidence/`
- Version outputs: `artifact-v1.png`, `artifact-v2.png`, etc.

---

## STEP 1: UNDERSTAND THE TASK

Before doing anything else, establish clarity:

| Question | Must Answer |
|----------|-------------|
| **What** | What exactly needs to be done? |
| **Done** | What does "done well" look like? |
| **Scope** | What's in scope vs out of scope? |
| **Constraints** | Any limitations or requirements? |

### Detect Iteration Triggers

Look for words/phrases that signal iteration mode:
- "until", "iterate", "refine", "keep going"
- "comprehensive", "thorough", "complete"
- "A+", "excellent", "perfect", "polish"
- "don't stop early", "continue until"

If triggers detected → plan for multiple iterations, not just one pass.

### Create Goals File

Write to `projects/<project>/goals.md`:

```markdown
# Project Goals

**Project**: <project-name>
**Created**: [datetime]
**Task Type**: [what kind of task is this]

## Original Request
> [exact user request]

## Iteration Triggers
[List any triggers detected and what they mean]
- "[phrase]" → [interpretation]

## Scope
- **In scope**: [what we're doing]
- **Out of scope**: [what we're not doing]

## Success Criteria
What does "done" look like? Be specific.
1. [Criterion 1]
2. [Criterion 2]
3. [Criterion 3]

## Quality Bar
- **Minimum acceptable**: [description]
- **Target**: [description]
- **Excellent would mean**: [description]

## Model Configuration
- **default_model**: [claude or gemini]
- **verification_model**: [claude or gemini]

## Acceptance Checklist
- [ ] [Criterion 1] — Evidence: [what proves this]
- [ ] [Criterion 2] — Evidence: [what proves this]
- [ ] [Criterion 3] — Evidence: [what proves this]
```

---

## STEP 2: PLAN THE APPROACH (DEEP THINKING REQUIRED)

**Do not rush planning.** Poor planning causes wasted iterations downstream.

### Mandatory Planning Questions

Before writing plan.md, answer ALL of these:

1. **Artifact Dependencies**: What must be complete before something else can begin?
   - List explicitly: "X must be done before Y because..."
   - If dependencies exist → plan iterates X to completion before starting Y

2. **Quality Gates**: Which artifacts have their own quality bar?
   - Each gated artifact gets its own iteration cycle
   - Don't batch everything into one "iterate if needed" step at the end

3. **Consistency Requirements**: Does anything need to match/be consistent?
   - If yes → identify what reference artifacts are needed FIRST
   - Plan: create references, then use them for production artifacts

4. **Iteration Strategy**: For each major artifact:
   - What does A+ look like for THIS specific artifact?
   - How will you assess it? What evidence proves quality?

### Plan Template

```markdown
# Plan

**Task**: [brief description]
**Status**: 🟡 IN PROGRESS

## Artifact Dependency Graph
[What depends on what - be explicit]
- [Artifact A] → no dependencies, start here
- [Artifact B] → depends on A being complete
- [Artifact C] → depends on B being complete

## Quality Gates
| Artifact | Quality Bar | Assessment Method |
|----------|-------------|-------------------|
| [name]   | [target]    | [how to evaluate] |

## Phases (Ordered by Dependencies)
[Each phase completes before next begins]

Phase 1: [First artifact/concept]
- Iterate until quality gate passed

Phase 2: [Next artifact]
- Only begin after Phase 1 complete
- ...

## Evidence Trail
[What artifacts will you create along the way?]

## Version History
| Version | Date | Description | Status |
|---------|------|-------------|--------|
| v1 | | | |
```

### Multi-Modal Tasks (Text + Images, Code + Tests, etc.)

When task involves multiple modalities:

1. **Complete upstream modality first** - e.g., text/concept must be A+ before images
2. **Create reference artifacts** - for anything requiring consistency
3. **Use references in production** - don't rely on text descriptions alone

Example for visual tasks:
```
Phase 1: Concept/Text (iterate to A+)
Phase 2: Reference Images (character sheets, style guides)
Phase 3: Production Images (using references)
```

---

## STEP 3: EXECUTE WITH ITERATION

### Core Rules

1. **Version everything** - Create v1, v2, v3... Never overwrite.
2. **Save evidence** - Put artifacts in `projects/<project>/evidence/`
3. **Self-assess** - Periodically check progress against goals
4. **Commit often** - `git add -A && git commit -m "description"`

### Evidence Naming

Name files based on what they are:

| Task Type | Example Evidence Files |
|-----------|----------------------|
| Coding | `implementation-v1.ts`, `tests-v1.ts`, `refactor-v2.ts` |
| Writing | `draft-v1.md`, `revision-v2.md`, `final-v3.md` |
| Research | `findings-v1.md`, `analysis-v2.md`, `synthesis-v3.md` |
| Analysis | `data-v1.json`, `results-v2.md`, `recommendations-v3.md` |
| General | `[descriptive-name]-v[N].[ext]` |

### Iteration Loop

```
Execute Phase → Save Evidence → Assess Quality → Decision
                                                    ↓
                                    ┌───────────────┴───────────────┐
                                    │                               │
                              Gaps remain?                    Quality met?
                                    │                               │
                                    ↓                               ↓
                              Next iteration                  Move to verify
```

### Self-Assessment Protocol (MANDATORY)

After EVERY versioned artifact, you MUST:

1. **Rate explicitly**: "This is [X] against the [target] bar"
2. **Compare to goal**: Is X >= target from goals.md?
3. **Branch immediately based on result**:
   - If X >= target → proceed to next phase or verify
   - If X < target → "Below bar. Starting iteration [N+1]." and iterate immediately

**Create assessment file**: `projects/<project>/evidence/assessment-[artifact]-v[N].md`

```markdown
## Assessment: [artifact] v[N]

**Quality Bar**: [from goals.md]
**Self-Rating**: [your rating]
**Comparison**: [rating] vs [bar] = [PASS/BELOW]

**If BELOW - What's Missing**:
- [gap 1]
- [gap 2]

**Next Action**: [iterate immediately / proceed to next phase]
```

**DO NOT**:
- Rate below bar and ask user if they want to continue
- Rate below bar and present work as potentially complete
- Skip the assessment file

---

## STEP 4: VERIFY BEFORE DONE

**NEVER claim completion without verification.**

When you believe all criteria are met:

1. Run `/verify <project-name>` for independent assessment
2. If PASS → Deliver the result
3. If FAIL → Address gaps, iterate, re-verify

Maximum 3 verification attempts. After that, present status honestly and ask user how to proceed.

---

## ANTI-PATTERNS

1. **Single pass** - Don't do one iteration and declare done
2. **Skipping verification** - Always verify before claiming complete
3. **Overwriting** - Never overwrite; always version (v1, v2, v3)
4. **Vague criteria** - Be specific about what "done" means
5. **Ignoring triggers** - If user says "iterate until excellent", do it
6. **Premature completion** - Don't stop because you're tired; stop when done
7. **Asking user when below bar** - If self-assessment < target, iterate; don't ask

---

## HARD RULES (Non-Negotiable)

These rules override your discretion. Follow them exactly.

### Rule 1: Below Bar = Iterate Immediately
If your self-assessment is below the quality bar defined in goals.md:
- **DO NOT** ask the user if they want to continue
- **DO NOT** present the work as "pretty good" or potentially complete
- **MUST** immediately begin next iteration
- Only ask user after 3+ iterations haven't reached the bar

### Rule 2: Complete Dependencies Before Proceeding
If artifact B depends on artifact A being high-quality:
- **MUST** iterate on A until it meets its quality bar
- **ONLY THEN** proceed to B
- Example: Joke concept must be A+ before generating comic panels

### Rule 3: Consistency Requirements Need References
If task requires visual/stylistic consistency across multiple outputs:
- **MUST** create reference artifacts first (character sheets, style guides, etc.)
- **MUST** use those references (via reference_images or explicit inclusion) when creating production artifacts
- Text descriptions alone are insufficient for consistency

### Rule 4: Verify Before ANY Completion Signal
Before presenting work as complete or asking if user is satisfied:
- **MUST** run `/verify` first
- If verify fails → iterate and re-verify
- Only present to user after PASS or 3 failed verification attempts

---

## ADAPTING TO TASK TYPE

The framework is task-agnostic. You adapt it:

| Task Type | Key Focus | Typical Evidence |
|-----------|-----------|------------------|
| **Coding** | Working code, tests pass | Code files, test results |
| **Writing** | Clear, effective communication | Drafts, revisions |
| **Research** | Accurate, comprehensive findings | Notes, analysis, sources |
| **Analysis** | Sound reasoning, valid conclusions | Data, methodology, results |
| **Planning** | Actionable, complete plan | Plans, considerations, decisions |
| **Problem-solving** | Effective solution | Problem definition, options, solution |

Don't force writing-style phases on a coding task, or vice versa. Use judgment.

---

## QUICK REFERENCE

```
0. CREATE PROJECT → projects/task-[timestamp]/
1. UNDERSTAND → goals.md (criteria, quality bar)
2. PLAN → plan.md (dependencies, quality gates, phases)
3. EXECUTE → evidence/ (versioned artifacts + assessments)
4. VERIFY → /verify <project> (independent check)
5. DELIVER → final output to user
```

**Always**: Version everything. Verify before done. Commit every change.

**Hard Rules**:
- Below bar = iterate immediately, don't ask user
- Complete dependencies before proceeding to next phase
- Consistency needs → create references first
- Run /verify before ANY completion signal to user
