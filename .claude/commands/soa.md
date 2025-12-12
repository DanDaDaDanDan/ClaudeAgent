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
   - If present, use that model for generation tasks
   - Valid values: `claude`, `gemini`

2. **If no flag**, default to `claude` (direct generation, no MCP)

### Model Usage

- **`claude`** (default): Generate directly. No MCP call needed.
- **`gemini`**: Use MCP tools from the `mcp-gemini` server:
  - `generate_text` - Text generation with Gemini 3 Pro (thinking enabled)
  - `generate_image` - Image generation with Nano Banana / Nano Banana Pro

When using an external model:
1. Construct a complete prompt with ALL necessary context
2. Call the MCP tool with appropriate parameters
3. Parse the response and save to evidence files

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

## STEP 2: PLAN THE APPROACH

Create `projects/<project>/plan.md` with a structure appropriate to THIS task.

The plan structure depends on what you're doing:

**For coding tasks:**
```markdown
## Phases
1. Understand existing code
2. Design approach
3. Implement
4. Test
5. Refine
```

**For research tasks:**
```markdown
## Phases
1. Define questions
2. Gather information
3. Analyze findings
4. Synthesize conclusions
```

**For writing tasks:**
```markdown
## Phases
1. Outline
2. Draft
3. Revise
4. Polish
```

**For problem-solving:**
```markdown
## Phases
1. Understand problem
2. Explore solutions
3. Evaluate options
4. Implement chosen approach
5. Validate
```

You decide what phases make sense. Don't force a structure that doesn't fit.

### Plan Template

```markdown
# Plan

**Task**: [brief description]
**Status**: 🟡 IN PROGRESS

## Approach
[How you'll tackle this task]

## Phases
[Task-appropriate phases]

## Checkpoints
[When will you pause to assess progress?]

## Evidence Trail
[What artifacts will you create along the way?]

## Version History
| Version | Date | Description | Status |
|---------|------|-------------|--------|
| v1 | | | |
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

### Self-Assessment Checkpoints

At appropriate points (you decide when), ask:
- Does this meet the success criteria?
- What's working well?
- What needs improvement?
- Am I ready for verification, or do I need another iteration?

Document assessments in `projects/<project>/evidence/assessment-v[N].md`.

### Using Gemini MCP Tools

When model is `gemini`, use the MCP tools from the `mcp-gemini` server.

#### generate_text

Text generation with Gemini 3 Pro (thinking enabled). Supports multimodal input.

```
Use MCP tool: generate_text

Parameters:
- prompt: [Task with full context] (required)
- system_prompt: [Role-appropriate instructions]
- thinking_level: "high" (default) or "low" for faster responses
- max_tokens: 65536 (default, max for Gemini 3 Pro)
- temperature: 0.7 (default) - lower for analytical, higher for creative
- images: [array of file paths] - for multimodal input (jpg, png, gif, webp, heic)
```

**Example - text generation:**
```
Use MCP tool: generate_text
- prompt: "Analyze this code architecture and suggest improvements..."
- system_prompt: "You are a senior software architect."
- thinking_level: "high"
- temperature: 0.3
```

**Example - multimodal (image analysis):**
```
Use MCP tool: generate_text
- prompt: "Describe what's in this screenshot and identify any UI issues"
- images: ["projects/<project>/evidence/screenshot-v1.png"]
```

#### generate_image

Image generation with Nano Banana (fast) or Nano Banana Pro (high-quality).

```
Use MCP tool: generate_image

Parameters:
- prompt: [Image description] (required)
- output_path: [Where to save the image] (required)
- model: "nano-banana" (default, fast) or "nano-banana-pro" (high-fidelity)
- reference_images: [array of base64 images] - for editing/composition
- aspect_ratio: "1:1", "16:9", "9:16", "4:3", "3:4", etc.
```

**Max reference images:** 3 for nano-banana, 14 for nano-banana-pro

**Example:**
```
Use MCP tool: generate_image
- prompt: "A modern dashboard UI with dark theme, showing analytics charts"
- output_path: "projects/<project>/evidence/mockup-v1.png"
- model: "nano-banana-pro"
- aspect_ratio: "16:9"
```

#### list_models

List available Gemini models and their capabilities.

```
Use MCP tool: list_models
```

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
2. PLAN → plan.md (task-appropriate phases)
3. EXECUTE → evidence/ (versioned artifacts)
4. VERIFY → /verify <project> (independent check)
5. DELIVER → final output to user
```

**Always**: Version everything. Verify before done. Commit every change.
