# yw-claude-marketplace-demo - Claude Marketplace Package Demo

> **This is a CLAUDE MARKETPLACE (package) demo** - a working marketplace package that shows the folder structure, metadata layout, and live Claude extensibility components (e.g., Claude Skills).
>
> Learn the marketplace packaging mechanism by seeing 10+ demo plugins in action.

## What Is This?

This repository demonstrates **Claude's plugin marketplace mechanism**:
- One repo = Multiple plugins
- `.claude-plugin/marketplace.json` lists all available plugins
- Users add the marketplace once, then install individual plugins
- Each plugin in `plugins/` directory is independently installable

## Installation

```bash
# Step 1: Add this marketplace (one time)
/plugin marketplace add https://github.com/yoshiwatanabe/yw-claude-marketplace-demo.git

# Step 2: List available plugins from this marketplace
/plugin

# Step 3: Install any individual demo plugin
/plugin install demo-skills@yw-claude-marketplace-demo
/plugin install demo-mcp@yw-claude-marketplace-demo
```

## Available Demos

| Plugin | Feature | Description |
|--------|---------|-------------|
| demo-skills | Skills | Auto-triggered workflows |
| demo-mcp | MCP Servers | External tool integration |
| demo-commands | Slash Commands | Manual shortcuts |
| demo-subagents | Subagents | Specialized agents |
| demo-hooks | Hooks | Event-driven automation |
| demo-claudemd | CLAUDE.md | Project context templates |
| demo-full-plugin | Complete | All components together |
| demo-thinking | Extended Thinking | Compute time triggers |
| demo-settings | Settings | Configuration patterns |
| demo-model-routing | Model Routing | LiteLLM integration |

## Purpose

Low-cognitive-load "hello world" demos for hands-on learning.
Each plugin demonstrates ONE extensibility feature with minimal complexity.

## Quick Reference

```
┌──────────────────────────────────────────────────────────────────┐
│                    CLAUDE EXTENSIBILITY                          │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  CLAUDE.md      → Always-on context (project constitution)      │
│  Skills         → Auto-triggered workflows (.claude/skills/)    │
│  MCP Servers    → External tools/data (.mcp.json)               │
│  Slash Commands → Manual prompts (.claude/commands/)            │
│  Subagents      → Isolated agents (.claude/agents/)             │
│  Hooks          → Event automation (.claude/settings.json)      │
│  Plugins        → Bundle everything (.claude-plugin/)           │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│  Extended Thinking → "think" / "think hard" / "ultrathink"      │
│  Headless Mode     → claude -p "prompt" --print                 │
│  Model Routing     → LiteLLM / ANTHROPIC_BASE_URL               │
│  VS Code MCP       → settings.json > mcp.servers                │
└──────────────────────────────────────────────────────────────────┘
```

See [DEMO-PLAN.md](DEMO-PLAN.md) for full implementation details.
