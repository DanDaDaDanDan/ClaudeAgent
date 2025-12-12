# Proposed Fixes to SOA and Verify Commands

## Problem Summary

The current soa.md is SUGGESTIVE, not MANDATORY. It describes good behavior but doesn't enforce it.

Key failures:
1. Planning allowed shallow "do everything at once" approaches
2. Iteration below quality bar allowed asking user instead of iterating
3. No guidance for artifact dependencies (text before images, references before production)
4. Verification step skipped because informal self-assessment happened first

---

## Fix 1: Add HARD RULES Section to soa.md

Add after ANTI-PATTERNS:

```markdown
## HARD RULES (Non-Negotiable)

These rules override your discretion. Follow them exactly.

### Rule 1: Below Bar = Iterate Immediately
If your self-assessment is below the quality bar defined in goals.md:
- **DO NOT** ask the user if they want to continue
- **DO NOT** present the work as potentially complete
- **MUST** immediately begin next iteration
- Only ask user after 3+ iterations haven't reached the bar

### Rule 2: Complete Dependencies Before Proceeding
If artifact B depends on artifact A being high-quality:
- **MUST** iterate on A until it meets its quality bar
- **ONLY THEN** proceed to B
- Example: Text joke must be A+ before generating images

### Rule 3: Consistency Requirements Need References
If task requires visual/stylistic consistency across artifacts:
- **MUST** create reference artifacts first
- **MUST** use those references when creating production artifacts
- Example: Character design → Character reference images → Panels using references

### Rule 4: Verify Before ANY Completion Signal
Before presenting work as complete or asking if user is satisfied:
- **MUST** run /verify first
- If verify fails → iterate and re-verify
- Only present to user after PASS or 3 failed attempts
```

---

## Fix 2: Strengthen Planning Requirements

Replace the vague "You decide what phases make sense" with mandatory planning questions:

```markdown
## STEP 2: PLAN THE APPROACH

### Mandatory Planning Questions

Before writing plan.md, answer these:

1. **Artifact Dependencies**: What must be complete before something else can begin?
   - List: "X must be done before Y because..."
   - If any dependencies exist → plan iterates X to completion before starting Y

2. **Quality Gates**: Which artifacts have their own quality bar?
   - Each gated artifact gets its own iteration cycle
   - Don't batch everything into one "iterate if needed" step

3. **Consistency Requirements**: Does anything need to match/be consistent?
   - If yes → identify what reference artifacts are needed
   - Plan: create references first, then use them

4. **Iteration Strategy**: For each major artifact:
   - What does A+ look like for THIS artifact specifically?
   - How will you know when to stop iterating?

### Plan Structure Must Include

```markdown
## Artifact Dependency Graph
[What depends on what - be explicit]

## Quality Gates
| Artifact | Quality Bar | How to Assess |
|----------|-------------|---------------|
| [name]   | [bar]       | [method]      |

## Phases (Ordered by Dependencies)
[Phases where earlier phases complete before later ones begin]
```
```

---

## Fix 3: Add Multi-Modal/Creative Task Guidance

Add a new section with explicit examples:

```markdown
## SPECIAL CASE: Multi-Modal Creative Tasks

Tasks involving text + images (comics, illustrated stories, visual content):

### Phase Order
1. **Text/Concept Phase** - Iterate until text component is A+
   - Draft concept v1
   - Self-assess against text quality bar
   - Iterate v2, v3... until text quality bar met

2. **Reference Phase** - Create consistency anchors
   - For each recurring element (character, style, setting):
   - Generate dedicated reference image
   - These are NOT production outputs, they're tools

3. **Production Phase** - Use references for consistency
   - Generate production images WITH reference_images parameter
   - Assess consistency AND quality
   - Iterate if either fails

### Why This Order Matters
- Bad joke + great art = bad comic (text must be A+ first)
- Inconsistent characters break immersion (references needed)
- Can't fix upstream problems downstream (dependencies matter)
```

---

## Fix 4: Strengthen Self-Assessment

Make it MANDATORY and BEHAVIORAL:

```markdown
### Self-Assessment Protocol (MANDATORY)

After EVERY versioned artifact:

1. **Rate explicitly**: "This is [X] against the [target] bar"
2. **Compare to goal**: Is X >= target?
3. **Branch immediately**:
   - If X >= target → proceed to next phase or verify
   - If X < target → "Below bar. Starting iteration [N+1]."

**DO NOT**:
- Rate below bar and ask user
- Rate below bar and justify why it's "good enough"
- Skip rating entirely

**Assessment must be in evidence file**, not just thought process.
```

---

## Fix 5: Rename "Evidence Trail" to Include Mandatory Assessments

```markdown
## Evidence Trail (Required Files)

Every project must produce:
- `assessment-after-[artifact]-v[N].md` - Self-rating after each version
- Artifact versions themselves
- Final verification request and result

The assessment files create accountability and force explicit quality checks.
```

---

## Summary of Changes

| Problem | Current State | Fix |
|---------|---------------|-----|
| Below bar → asks user | Descriptive iteration loop | HARD RULE: Below bar = iterate, not ask |
| Shallow planning | "You decide" | Mandatory planning questions + dependency graph |
| No reference strategy | Parameters mentioned but no guidance | HARD RULE: Consistency = references first |
| Verification skipped | "When you believe criteria met" | HARD RULE: Verify before ANY completion signal |
| Vague self-assessment | "At appropriate points" | MANDATORY protocol after every artifact |

---

## Implementation

These changes are task/prompt agnostic - they apply to ANY task type without being specific to comics or images.
