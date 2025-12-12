# Debug Analysis: Why SOA Failed to Iterate Properly

## Issues Identified

### 1. Weak Planning - No Stage Decomposition
**What happened**: Jumped straight from "define joke" to "generate all panels"
**Should have**: Iterate on TEXT (joke concept) until A+ FIRST, then switch to images

**Root cause in soa.md**:
- Line 120-164: Phase examples are generic and shallow
- No guidance for multi-stage tasks where one artifact must be complete before next begins
- "You decide what phases make sense" is too permissive

### 2. No Reference Image Strategy
**What happened**: Used detailed text descriptions hoping for consistency
**Should have**: Created standalone character reference images FIRST, then used them as `reference_images` for each panel

**Root cause in soa.md**:
- Line 285-286 mentions `reference_images` parameter exists
- NO guidance on WHEN to use this strategy
- No pattern for "consistency requirement → create references first"

### 3. Rated B+/A- But Asked User Instead of Iterating
**What happened**: Self-assessed below A+ goal, then asked user if done
**Should have**: Automatically iterate when below quality bar

**Root cause in soa.md**:
- Line 215-226: Iteration loop is DESCRIPTIVE, not PRESCRIPTIVE
- Shows "Gaps remain? → Next iteration" but doesn't MANDATE it
- No hard rule: "If below bar, MUST iterate, do NOT ask user"
- Anti-patterns section (line 324-331) says don't do single pass, but enforcement is weak

### 4. verify.md Was Never Used
**What happened**: Did informal self-assessment, never ran /verify
**Should have**: Used the formal verification process

**Root cause**:
- soa.md line 314-319 says "When you believe all criteria are met: Run /verify"
- But I stopped at self-assessment and asked user before reaching that point
- No checkpoint forcing verification before ANY user interaction about completion

## Did Removing /iterate Cause This?

**NO.**

The /iterate command was for MANUAL iteration (user triggering another round). The SOA command is supposed to handle AUTOMATIC iteration based on detected triggers. The weakness is in SOA's iteration enforcement, not the absence of /iterate.

## Core Problem: Guidance is Suggestive, Not Mandatory

The soa.md uses soft language:
- "plan for multiple iterations" (plan, not DO)
- "you decide when" (too discretionary)
- "At appropriate points" (vague)
- Iteration loop diagram shows flow but doesn't force it

## What Would Have Fixed This Run

### Better Plan Should Have Been:
```
Phase 1: Joke Development (iterate until A+)
  1.1 Draft joke concept v1
  1.2 Self-assess against A+ humor bar
  1.3 Iterate joke v2, v3... until genuinely hilarious

Phase 2: Character References (before panels)
  2.1 Generate viking character reference sheet
  2.2 Generate wife character reference sheet

Phase 3: Panel Generation (using references)
  3.1 Generate panel 1 with reference images
  3.2 Generate panel 2 with reference images
  3.3 Generate panel 3 with reference images

Phase 4: Verification
  4.1 Run /verify
  4.2 Address gaps, re-iterate if needed
```

### Self-Assessment Should Have Triggered:
When I wrote "B+/A-" and goal was "A+":
→ Immediate next iteration, not user question
