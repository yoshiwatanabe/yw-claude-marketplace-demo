# yw-claude-marketplace-demo

> A **Claude Marketplace** — a working example of how to package and distribute plugins for Anthropic's Claude Code.

## What Is This?

This is a **marketplace repository** that demonstrates Anthropic Claude's plugin extensibility system. It contains a collection of low-cognitive-load examples and demos showcasing various Claude extensibility features.

### Key Intent

- **Educational focus**: Each demo is intentionally minimal to illustrate ONE concept clearly
- **Hands-on learning**: Copy, modify, and adapt examples to understand Claude extensibility
- **Extensibility showcase**: Demonstrates core Claude extension mechanisms like Skills, MCP Servers, CLAUDE.md, Slash Commands, Subagents, Hooks, and more

## ⚠️ Important Platform Limitations

**This marketplace is designed exclusively for Claude Code** (Anthropic's Claude environment). 

- ✅ Works with: Claude Code (Claude IDE)
- ❌ Does NOT work with: GitHub Copilot in VS Code, or other third-party AI environments
- ❌ Cannot be imported as a standard VS Code extension marketplace

The plugin mechanism described here is specific to Anthropic's Claude platform and cannot be ported to other environments.

## Installation (Claude Code)

```bash
# Step 1: Add this marketplace
/plugin marketplace add https://github.com/yoshiwatanabe/yw-claude-marketplace-demo.git

# Step 2: Browse available demo plugins
/plugin

# Step 3: Install a specific demo plugin
/plugin install <plugin-name>@yw-claude-marketplace-demo
```

## Plugin Catalog

A detailed catalog of available plugins, features, and installation instructions will be published here as more content is added to this repository.

In the meantime, see the [plugins/](plugins/) directory for available examples.
