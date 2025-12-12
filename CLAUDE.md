# ClaudeWriter - Self-Organizing Agent Framework

Task-agnostic, iterative work with independent verification. Supports multi-model workflows via MCP.

## Philosophy

1. **Fail fast** - Don't try to work around issues. Surface problems immediately rather than papering over them.
2. **Be curious** - Explore, question assumptions, dig deeper. Curiosity leads to understanding.
3. **Don't guess, research** - When uncertain, investigate first. If still inconclusive after research, ask the user.

## Commands

| Command | Purpose |
|---------|---------|
| `/soa` | Self-organizing agent - auto-creates project, starts work |
| `/soa --model gemini` | Use Gemini for generation |
| `/verify [project]` | Independent verification (defaults to latest project) |

Each command file contains detailed instructions. Run the command to see full guidance.

## Multi-Model Support

Commands support `--model <name>` flag or project-level configuration in `goals.md`:

**Configuration hierarchy**: Command flag > Project config > Default (claude)

**Available models**:
- `claude` (default) - Direct generation, no MCP required
- `gemini` - Google Gemini via MCP (thinking enabled)

**MCP Servers**:

| Server | Provider | Tools | Use For |
|--------|----------|-------|---------|
| `mcp-gemini` | Google AI | `generate_text`, `list_models` | Text generation only |
| `mcp-fal` | fal.ai | `generate_image`, `list_models` | All image generation |

**Tool Usage**:
- `mcp__mcp-gemini__generate_text` - Text generation with Gemini 3 Pro (thinking/reasoning)
- `mcp__mcp-fal__generate_image` - **Always use this for images** (fast: nano-banana, high-quality: nano-banana-pro)

**Note**: Both servers may expose image generation tools, but always use `mcp-fal` for images.

### Key MCP Patterns

**Text generation** (`mcp__mcp-gemini__generate_text`):
- `thinking_level: "high"` for complex reasoning (default)
- `thinking_level: "low"` for faster simple tasks
- `images: [paths]` for multimodal input (analyze screenshots, etc.)

**Image generation** (`mcp__mcp-fal__generate_image`):
- `model: "nano-banana"` for fast drafts
- `model: "nano-banana-pro"` for high-quality final output
- `reference_images: [urls]` for consistency across multiple images (character sheets, style guides)
- Max references: 3 for nano-banana, 14 for nano-banana-pro

See `../mcp-gemini/README.md` and `../mcp-fal/README.md` for full parameter documentation.

## Core Rules

1. **Detect iteration triggers** - words like "until", "iterate", "refine", "A+", "comprehensive" enable iteration mode
2. **Version everything** - create v1, v2, v3... never overwrite
3. **Verify before done** - run `/verify` before claiming completion
4. **Commit every change** - `git add -A && git commit -m "description"`
5. **Keep README.md in sync** - when updating CLAUDE.md, update README.md to match

## Files

Projects are auto-created in `projects/task-YYYYMMDD-HHMMSS/`:
- `goals.md` - Success criteria and quality bar
- `plan.md` - Approach and progress tracking
- `verification-log.md` - Verification history
- `evidence/` - Versioned artifacts

## Workflow

```
/soa → Create Project → Understand → Plan → Execute → Iterate → /verify → Deliver
                                                ↑                    │
                                                └─── FAIL: fix gaps ─┘
```

## Reference

- `README.md` - Quick start guide with example
- Each `/command` file - Detailed guidance for that command
