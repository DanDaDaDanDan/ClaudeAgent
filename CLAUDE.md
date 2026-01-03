# ClaudeWriter - Self-Organizing Agent Framework

Task-agnostic, iterative work with independent verification. Supports multi-model workflows via MCP.

## Philosophy

1. **Fail fast** - Don't try to work around issues. Surface problems immediately rather than papering over them.
2. **Be curious** - Explore, question assumptions, dig deeper. Curiosity leads to understanding.
3. **Don't guess, research** - When uncertain, investigate first. If still inconclusive after research, ask the user.
4. **No mock code** - Never generate placeholder, stub, or mock implementations. Write real, functional code or don't write it at all.
5. **No silent rollbacks** - Don't fall back to previous approaches or revert changes just because something fails. Surface the failure and wait for explicit direction.
6. **Finish the job** - Always verify work was completed as requested. Never stop mid-task. If completion is blocked, call it out prominently—don't bury it or move on silently.
7. **Commit early, commit often** - We use git. Commit after every meaningful change. The revision history is our safety net—we can always go back, so be bold.

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

---

## MCP Architecture

Three MCP servers provide specialized capabilities. Each has a clear purpose—avoid overlap by using the right tool for the job.

### Server Overview

| Server | Provider | Primary Purpose | API Key Env Var |
|--------|----------|-----------------|-----------------|
| `mcp-gemini` | Google AI | Thinking, multimodal analysis, deep research | `GEMINI_API_KEY` |
| `mcp-fal` | fal.ai | Image generation (dedicated) | `FAL_KEY` |
| `mcp-xai` | xAI/Grok | Real-time search, social, news, code execution | `XAI_API_KEY` |

### When to Use What

| Task | Server | Tool | Why |
|------|--------|------|-----|
| **Text Generation** ||||
| Deep reasoning/thinking | `mcp-gemini` | `generate_text` | Gemini 3 Pro with thinking levels |
| Search-augmented generation | `mcp-xai` | `generate_text` | Grok with live web/X/news search |
| **Image Generation** ||||
| All image generation | `mcp-fal` | `generate_image` | Dedicated service, most reliable |
| **Research** ||||
| Long-form autonomous research | `mcp-gemini` | `deep_research` | 5-30 min comprehensive reports |
| Real-time multi-source research | `mcp-xai` | `research` | X + web + news combined, fast |
| **Search** ||||
| X/Twitter posts | `mcp-xai` | `x_search` | Social media, handles, threads |
| Web pages | `mcp-xai` | `web_search` | Domain filtering, analysis |
| News articles | `mcp-xai` | `news_search` | Aggregated news sources |
| RSS feeds | `mcp-xai` | `rss_fetch` | Feed fetching and analysis |
| **Code Execution** ||||
| Sandboxed Python | `mcp-xai` | `code_execute` | NumPy, Pandas, SciPy, Matplotlib |
| **Multimodal Input** ||||
| Analyze images/PDFs/video | `mcp-gemini` | `generate_text` | Use `files: [paths]` parameter |

### Tool Reference

#### mcp-gemini (Google AI)

| Tool | Description |
|------|-------------|
| `generate_text` | Text generation with Gemini 3 Pro (thinking enabled) |
| `generate_image` | **DO NOT USE** - Use mcp-fal instead |
| `deep_research` | Autonomous web research agent (5-30 min) |
| `list_models` | List available models |

**Key parameters for `generate_text`:**
- `thinking_level`: `"high"` (default, complex reasoning) or `"low"` (faster)
- `files`: Array of file paths for multimodal input (images, PDFs, video, audio)
- `system_prompt`: Optional system instructions
- `temperature`: 0-1 (default 0.7)

**Supported file types:** Images (jpg, png, webp, heic, heif), Audio (wav, mp3, aac, ogg, flac), Video (mp4, mov, avi, webm), Documents (pdf), Text (txt, md, html, json, csv, etc.)

#### mcp-fal (fal.ai)

| Tool | Description |
|------|-------------|
| `generate_image` | Image generation with Nano Banana models |
| `list_models` | List available models |

**Key parameters for `generate_image`:**
- `model`: `"nano-banana"` (fast, ~$0.04) or `"nano-banana-pro"` (quality, ~$0.15)
- `output_path`: Where to save the image (required)
- `reference_images`: URLs, local paths, or data URLs for editing/composition
- `aspect_ratio`: `"1:1"`, `"16:9"`, `"9:16"`, `"auto"` (for edits), etc.

**Max references:** 3 for nano-banana, 14 for nano-banana-pro

#### mcp-xai (xAI/Grok)

| Tool | Description |
|------|-------------|
| `x_search` | Search X/Twitter posts, users, threads |
| `web_search` | Search web with domain filtering |
| `news_search` | Search aggregated news sources |
| `rss_fetch` | Fetch and analyze RSS feeds |
| `research` | Multi-source agentic research |
| `code_execute` | Execute Python in sandbox (NumPy, Pandas, SciPy) |
| `generate_text` | Text generation with optional live search |
| `list_models` | List available models |

**Key parameters for search tools:**
- `query`: Search query (supports advanced syntax)
- `from_date` / `to_date`: Date range (YYYY-MM-DD)
- `allowed_domains` / `allowed_x_handles`: Filter to specific sources
- `max_results`: Limit results (1-50)
- `prompt`: Natural language prompt for analysis

**Key parameters for `research`:**
- `prompt`: Research question
- `sources`: `["x", "web", "news"]` (default all)
- `output_format`: `"markdown"`, `"json"`, or `"structured"`

**Key parameters for `generate_text`:**
- `enable_search`: Enable live search augmentation
- `search_sources`: `["web", "x", "news"]`
- `model`: `"grok-4-1-fast"` (default), `"grok-4"`, etc.

### Common Patterns

**Text generation with deep thinking:**
```
mcp__mcp-gemini__generate_text
  prompt: "Analyze the architectural trade-offs..."
  thinking_level: "high"
```

**Text generation with live search:**
```
mcp__mcp-xai__generate_text
  prompt: "What are the latest developments in..."
  enable_search: true
  search_sources: ["web", "news"]
```

**Image generation:**
```
mcp__mcp-fal__generate_image
  prompt: "A sunset over mountains"
  output_path: "/tmp/sunset.png"
  model: "nano-banana-pro"
```

**Image editing with reference:**
```
mcp__mcp-fal__generate_image
  prompt: "Add a hat to the person"
  reference_images: ["D:/photos/portrait.png"]
  output_path: "/tmp/edited.png"
```

**Real-time research:**
```
mcp__mcp-xai__research
  prompt: "Latest AI agent frameworks and trends"
  sources: ["x", "web"]
  x_handles: ["LangChainAI", "AnthropicAI"]
```

**Deep autonomous research:**
```
mcp__mcp-gemini__deep_research
  query: "Comprehensive analysis of quantum computing advances"
  timeout_minutes: 30
```

**Multimodal analysis:**
```
mcp__mcp-gemini__generate_text
  prompt: "Analyze this screenshot and explain the UI issues"
  files: ["D:/screenshots/ui.png"]
```

**X/Twitter search:**
```
mcp__mcp-xai__x_search
  query: "AI agents"
  allowed_x_handles: ["anthropic", "xai"]
  from_date: "2025-12-01"
```

### Server Documentation

For full parameter details:
- `../mcp-gemini/README.md` - Gemini text, images, deep research
- `../mcp-fal/README.md` - fal.ai image generation
- `../mcp-xai/README.md` - xAI search, research, code execution

---

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
