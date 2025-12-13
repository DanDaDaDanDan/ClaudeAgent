# ClaudeWriter

A self-organizing agent framework for Claude Code with iteration and verification.

## Quick Start

```bash
# Just start - project is auto-created
/soa
```

## Example: Any Task

```
You: Write a short story with a twist ending, iterate until it's A+ quality
You: /soa

Claude: [Creates projects/task-20250115-143022/]
        [Writes goals.md with success criteria]
        [Plans approach in plan.md]
        [Writes draft → evidence/story-v1.md]
        [Self-critiques, iterates → v2, v3...]
        [Runs /verify]

Verifier: FAIL - Twist is predictable, needs better foreshadowing

Claude: [Revises → evidence/story-v4.md]
        [Runs /verify]

Verifier: PASS

Claude: [Delivers polished story]
```

## Commands

| Command | Purpose |
|---------|---------|
| `/soa` | Self-organizing agent - auto-creates project, starts work |
| `/soa --model gemini` | Use Gemini for generation |
| `/verify [project]` | Independent quality check (defaults to latest) |

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

**MCP Servers**:
- `mcp-gemini` - Text generation with Gemini 3 Pro (thinking/reasoning)
- `mcp-fal` - Image generation with Nano Banana / Nano Banana Pro (always use for images)

See `../mcp-gemini/README.md` and `../mcp-fal/README.md` for setup.

## Philosophy

1. **Fail fast** - Surface problems immediately rather than papering over them
2. **Be curious** - Explore, question assumptions, dig deeper
3. **Don't guess, research** - When uncertain, investigate first

## How It Works

1. **Auto-creates projects** - Timestamped folders like `task-20250115-143022`
2. **Iteration triggers** - Words like "until", "iterate", "refine", "A+" trigger iteration mode
3. **Version everything** - Artifacts are v1, v2, v3... never overwritten
4. **Verify before done** - Independent verification prevents premature completion
5. **Task-agnostic** - The LLM determines appropriate phases based on task type
