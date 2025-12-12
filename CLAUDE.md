# ClaudeWriter - Self-Organizing Agent Framework

Task-agnostic, iterative work with independent verification. Supports multi-model workflows via MCP.

## Philosophy

1. **Fail fast** - Don't try to work around issues. Surface problems immediately rather than papering over them.
2. **Don't guess, research** - When uncertain, investigate first. If still inconclusive after research, ask the user.

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
- `gemini` - Google Gemini via MCP (deep thinking enabled)

See `mcp-other-llms/README.md` for MCP server setup.

## Core Rules

1. **Detect iteration triggers** - words like "until", "iterate", "refine", "A+", "comprehensive" enable iteration mode
2. **Version everything** - create v1, v2, v3... never overwrite
3. **Verify before done** - run `/verify` before claiming completion
4. **Commit every change** - `git add -A && git commit -m "description"`

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
