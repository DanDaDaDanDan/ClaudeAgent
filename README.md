# ClaudeWriter

A self-organizing agent framework for Claude Code with iteration and verification.

## Quick Start

```bash
# Just start - project is auto-created
/soa
```

## Example: Any Task

```
You: Refactor the user API to use async/await, iterate until clean
You: /soa

Claude: [Creates projects/task-20250115-143022/]
        [Writes goals.md with success criteria]
        [Plans approach in plan.md]
        [Implements v1 → evidence/implementation-v1.ts]
        [Self-assesses, iterates → v2, v3...]
        [Runs /verify]

Verifier: FAIL - Missing error handling in auth endpoint

Claude: [Addresses gap → evidence/implementation-v4.ts]
        [Runs /verify]

Verifier: PASS

Claude: [Delivers final implementation]
```

## Commands

| Command | Purpose |
|---------|---------|
| `/soa` | Self-organizing agent - auto-creates project, starts work |
| `/soa --model gemini` | Use Gemini for generation |
| `/verify [project]` | Independent quality check (defaults to latest) |
| `/iterate [project]` | Force continuation (defaults to latest) |

## Multi-Model Support

Use different AI models for generation or verification:

```bash
# Use Gemini for generation
/soa --model gemini

# Or configure per-project in goals.md:
## Model Configuration
- **default_model**: gemini
- **verification_model**: claude
```

Requires MCP server setup - see `mcp-other-llms/README.md`.

## How It Works

1. **Auto-creates projects** - Timestamped folders like `task-20250115-143022`
2. **Iteration triggers** - Words like "until", "iterate", "refine", "A+" trigger iteration mode
3. **Version everything** - Artifacts are v1, v2, v3... never overwritten
4. **Verify before done** - Independent verification prevents premature completion
5. **Task-agnostic** - The LLM determines appropriate phases based on task type
