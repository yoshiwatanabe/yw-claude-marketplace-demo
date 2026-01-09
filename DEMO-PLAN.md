# Claude Plugin Marketplace Demo - Implementation Plan

> **Repository:** `twatana-msft-private` (Enterprise GitHub, Private)  
> **What This Demonstrates:** How to build and publish a plugin marketplace  
> **Purpose:** "Hello World" demos for every Claude extensibility feature  
> **Key Concept:** ONE marketplace repository delivers MULTIPLE plugins  
> **Goal:** Breadth over depth - low-cognitive-load samples for hands-on learning & future reference  
> **Audience:** Myself (and future self)

---

## 🔌 This Repository IS a Plugin Marketplace

This repo demonstrates **how the marketplace packaging mechanism works**:
- ONE repository can distribute MULTIPLE plugins
- `.claude-plugin/marketplace.json` acts as the catalog
- Each plugin lives in `plugins/<plugin-name>/` with its own `plugin.json`
- Users install the marketplace once, then cherry-pick individual plugins

**Key Learning:** You can create your own marketplace to distribute a collection of related plugins!

### Installation

```bash
# Add this marketplace (from Claude Code)
/plugin marketplace add https://microsoft.ghe.com/twatana/twatana-msft-private.git

# List available demo plugins
/plugin

# Install a specific demo plugin
/plugin install demo-skills@twatana-private
```

### Repository Structure

```
twatana-msft-private/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace definition (lists all demo plugins)
├── DEMO-PLAN.md                   # This file
├── README.md                      # Marketplace README
├── brain-storming-ideas/          # Planning docs (not plugins)
│
└── plugins/                       # All demo plugins
    ├── demo-claudemd/             # Demo 01: CLAUDE.md patterns
    ├── demo-skills/               # Demo 02: Skills examples
    ├── demo-mcp/                  # Demo 03: MCP Server examples
    ├── demo-commands/             # Demo 04: Slash Commands
    ├── demo-subagents/            # Demo 05: Subagents
    ├── demo-hooks/                # Demo 06: Hooks
    ├── demo-full-plugin/          # Demo 07: Complete plugin example
    ├── demo-model-routing/        # Demo 11: LiteLLM integration
    └── ...
```

---

## Environment Notes

| Environment | Best For | Features Available |
|-------------|----------|-------------------|
| **VS Code + Copilot** | Skills, MCP Servers | Skills (via Copilot), MCP Servers, some Copilot-specific features |
| **Claude Code (CLI)** | Full extensibility | All 7 mechanisms (Skills, MCP, Commands, Subagents, Hooks, Plugins, CLAUDE.md) |

> 📝 For features only in Claude Code, switch to WSL where Claude Code is installed.

---

## Demo Plugin Collection

### Core 7 Extensibility Mechanisms

| # | Feature | Plugin Name | Demo Status | Location |
|---|---------|-------------|-------------|----------|
| 1 | CLAUDE.md | `demo-claudemd` | ☐ Todo | `plugins/demo-claudemd/` |
| 2 | Skills | `demo-skills` | ☐ Todo | `plugins/demo-skills/` |
| 3 | MCP Servers | `demo-mcp` | ☐ Todo | `plugins/demo-mcp/` |
| 4 | Slash Commands | `demo-commands` | ☐ Todo | `plugins/demo-commands/` |
| 5 | Subagents | `demo-subagents` | ☐ Todo | `plugins/demo-subagents/` |
| 6 | Hooks | `demo-hooks` | ☐ Todo | `plugins/demo-hooks/` |
| 7 | Full Plugin | `demo-full-plugin` | ☐ Todo | `plugins/demo-full-plugin/` |

### Additional Mechanisms

| # | Feature | Plugin Name | Demo Status | Location |
|---|---------|-------------|-------------|----------|
| 8 | Extended Thinking | `demo-thinking` | ☐ Todo | `plugins/demo-thinking/` |
| 9 | Headless Mode | (standalone scripts) | ☐ Todo | `standalone/headless-mode/` |
| 10 | Settings | `demo-settings` | ☐ Todo | `plugins/demo-settings/` |
| 11 | Model Routing | `demo-model-routing` | ☐ Todo | `plugins/demo-model-routing/` |
| 12 | MCP in VS Code | (standalone config) | ☐ Todo | `standalone/vscode-mcp/` |

---

## Detailed Plugin Implementations

---

## Plugin 01: demo-claudemd - CLAUDE.md Patterns

**Feature:** Project-scoped always-on context  
**Install:** `/plugin install demo-claudemd@twatana-private`  
**Cognitive Load:** ⭐ Very Low

> ⚠️ **Note:** CLAUDE.md itself can't be distributed via plugin (it's a project file).  
> This plugin provides **example CLAUDE.md templates** as skills + reference docs.

### Plugin Structure

```
plugins/demo-claudemd/
├── plugin.json                  # Plugin metadata
├── README.md                    # Demo instructions
├── skills/
│   └── claudemd-templates/
│       ├── SKILL.md             # "Generate CLAUDE.md for this project"
│       └── references/
│           ├── minimal.md       # Minimal template
│           ├── tech-stack.md    # Tech stack template
│           ├── with-commands.md # With commands template
│           ├── with-conventions.md # With coding rules
│           └── full-example.md  # Complete example
└── commands/
    └── generate-claudemd.md     # /generate-claudemd command
```

### What to Demonstrate

- [ ] **Template: Minimal** - Just project name + description
- [ ] **Template: Tech Stack** - Next.js + Prisma + Tailwind declaration
- [ ] **Template: Commands** - npm scripts, make targets documentation
- [ ] **Template: Conventions** - Coding standards, file naming rules
- [ ] **Template: Full** - Complete example with all sections
- [ ] **Skill** - Auto-generate CLAUDE.md based on project analysis
- [ ] **Command** - `/generate-claudemd` to create one manually

### Test Scenarios

1. Install plugin, run `/generate-claudemd`
2. Ask "Create a CLAUDE.md for this project"
3. Skill should analyze project and generate appropriate CLAUDE.md

---

## Plugin 02: demo-skills - Skills Examples

**Feature:** Progressive-disclosure knowledge files  
**Install:** `/plugin install demo-skills@twatana-private`  
**Cognitive Load:** ⭐⭐ Low

### Plugin Structure

```
plugins/demo-skills/
├── plugin.json
├── README.md
├── skills/
│   ├── minimal-skill/
│   │   └── SKILL.md             # Simplest possible skill
│   ├── skill-with-references/
│   │   ├── SKILL.md
│   │   └── references/
│   │       └── guidelines.md    # Referenced documentation
│   ├── skill-with-scripts/
│   │   ├── SKILL.md
│   │   └── scripts/
│   │       └── helper.py        # Executable script
│   ├── skill-with-assets/
│   │   ├── SKILL.md
│   │   └── assets/
│   │       └── config.json      # Bundled data file
│   └── greeting-skill/
│       └── SKILL.md             # "When user says hello, respond warmly"
```

### What to Demonstrate

- [ ] **Minimal Skill** - SKILL.md with just description + workflow
- [ ] **With References** - Skill that loads reference docs on demand
- [ ] **With Scripts** - Skill that executes Python/Bash scripts
- [ ] **With Assets** - Skill with bundled JSON/template files
- [ ] **Auto-trigger** - Skill that activates on keyword detection

### Test Scenarios

1. Install plugin
2. Say "hello" → greeting-skill should auto-trigger
3. Ask about something matching skill descriptions
4. Verify progressive disclosure (metadata → content → resources)

---

## Plugin 03: demo-mcp - MCP Server Examples

**Feature:** Model Context Protocol for tool integration  
**Install:** `/plugin install demo-mcp@twatana-private`  
**Cognitive Load:** ⭐⭐⭐ Medium

### Plugin Structure

```
plugins/demo-mcp/
├── plugin.json
├── README.md
├── .mcp.json                    # MCP server configurations
├── servers/
│   ├── echo-server/
│   │   ├── server.py            # Minimal: just echoes input
│   │   └── requirements.txt
│   ├── calculator-server/
│   │   ├── server.py            # add, subtract, multiply tools
│   │   └── requirements.txt
│   ├── file-info-server/
│   │   ├── server.py            # get_file_info, list_directory
│   │   └── requirements.txt
│   └── weather-server/
│       ├── server.py            # Uses env var for API key
│       ├── requirements.txt
│       └── .env.example         # Template for credentials
```

### .mcp.json Configuration

```json
{
  "mcpServers": {
    "echo": {
      "command": "python",
      "args": ["${CLAUDE_PLUGIN_ROOT}/servers/echo-server/server.py"]
    },
    "calculator": {
      "command": "python",
      "args": ["${CLAUDE_PLUGIN_ROOT}/servers/calculator-server/server.py"]
    },
    "file-info": {
      "command": "python",
      "args": ["${CLAUDE_PLUGIN_ROOT}/servers/file-info-server/server.py"]
    },
    "weather": {
      "command": "python",
      "args": ["${CLAUDE_PLUGIN_ROOT}/servers/weather-server/server.py"],
      "env": {
        "WEATHER_API_KEY": "${WEATHER_API_KEY}"
      }
    }
  }
}
```

### What to Demonstrate

- [ ] **Echo Server** - Minimal MCP (single tool, returns input)
- [ ] **Calculator Server** - Multiple tools in one server
- [ ] **File Info Server** - Tools that interact with filesystem
- [ ] **Weather Server** - Tool requiring environment variable credentials
- [ ] **MCP with Resources** - Expose data as MCP resources
- [ ] **MCP with Prompts** - Provide prompt templates via MCP

### Test Scenarios

1. Install plugin, run `/mcp` to see servers
2. Ask "what is 2 + 3?" → calculator should be used
3. Ask "echo hello world" → echo server
4. Verify env var handling with weather server

---

## Plugin 04: demo-commands - Slash Commands

**Feature:** User-triggered saved prompts  
**Install:** `/plugin install demo-commands@twatana-private`  
**Cognitive Load:** ⭐ Very Low

### Plugin Structure

```
plugins/demo-commands/
├── plugin.json
├── README.md
├── commands/
│   ├── hello.md                 # Simplest: just "Say hello"
│   ├── greet.md                 # With $ARGUMENTS: "Greet $ARGUMENTS"
│   ├── analyze-file.md          # "Analyze the file: $ARGUMENTS"
│   ├── summarize.md             # Multi-step workflow
│   ├── with-skill-ref.md        # References a skill
│   └── with-subagent.md         # Invokes a subagent
```

### Example Commands

**commands/hello.md:**
```markdown
Say "Hello from demo-commands plugin!" in a friendly way.
```

**commands/greet.md:**
```markdown
Please greet $ARGUMENTS warmly. Include a fun fact about their name if possible.
```

**commands/summarize.md:**
```markdown
Summarize the current project:

1. Read CLAUDE.md if it exists
2. List the main directories
3. Identify the tech stack
4. Provide a 3-sentence summary
```

### What to Demonstrate

- [ ] **Simple Command** - Just a static prompt
- [ ] **With Arguments** - Using $ARGUMENTS placeholder
- [ ] **Multi-step** - Workflow with numbered steps
- [ ] **Skill Reference** - Command that leverages a skill
- [ ] **Subagent Invocation** - Command that uses a subagent

### Test Scenarios

1. Install plugin
2. Type `/` and see new commands in autocomplete
3. Run `/hello`
4. Run `/greet Yoshi`
5. Run `/summarize`

---

## Plugin 05: demo-subagents - Subagent Examples

**Feature:** Isolated agents with separate context  
**Install:** `/plugin install demo-subagents@twatana-private`  
**Cognitive Load:** ⭐⭐ Low

### Plugin Structure

```
plugins/demo-subagents/
├── plugin.json
├── README.md
├── agents/
│   ├── minimal-agent/
│   │   └── AGENT.md             # Simplest possible agent
│   ├── reader-agent/
│   │   └── AGENT.md             # Only Read, Grep, Glob tools
│   ├── writer-agent/
│   │   └── AGENT.md             # Read + Write + Edit tools
│   ├── haiku-agent/
│   │   └── AGENT.md             # Uses claude-haiku model
│   ├── skilled-agent/
│   │   └── AGENT.md             # References skills
│   └── researcher/
│       └── AGENT.md             # Web research specialist
```

### Example Agent Definition

**agents/minimal-agent/AGENT.md:**
```markdown
---
name: minimal-agent
description: A minimal demonstration agent
tools: Read
---

You are a simple helper agent. 
When asked to do something, acknowledge the request and complete it.
```

**agents/haiku-agent/AGENT.md:**
```markdown
---
name: haiku-agent
description: Fast responses using Claude Haiku
model: claude-haiku-4-5-20251001
tools: Read, Grep
---

You are a fast helper optimized for quick responses.
Keep answers concise and efficient.
```

### What to Demonstrate

- [ ] **Minimal Agent** - Simplest AGENT.md
- [ ] **Limited Tools** - Agent with restricted tool access
- [ ] **Different Model** - Agent using Haiku for speed/cost
- [ ] **With Skills** - Agent that references skills
- [ ] **Parallel Agents** - Multiple agents working together

### Test Scenarios

1. Install plugin
2. Ask "use minimal-agent to read README.md"
3. Observe context isolation
4. Compare haiku-agent speed vs default

---

## Plugin 06: demo-hooks - Event-Driven Automation

**Feature:** Deterministic shell commands on lifecycle events  
**Install:** `/plugin install demo-hooks@twatana-private`  
**Cognitive Load:** ⭐⭐⭐ Medium

### Plugin Structure

```
plugins/demo-hooks/
├── plugin.json
├── README.md
├── hooks/
│   └── settings.json            # Hook configurations
├── scripts/
│   ├── log-session.sh           # Log session start
│   ├── format-file.sh           # Format edited files
│   ├── notify.sh                # Desktop notification
│   └── validate-edit.sh         # Validate before write
```

### Example hooks/settings.json

```json
{
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "${CLAUDE_PLUGIN_ROOT}/scripts/log-session.sh"
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Edit",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'File edited: ${file}'"
          }
        ]
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PLUGIN_ROOT}/scripts/validate-edit.sh ${file}"
          }
        ]
      }
    ]
  }
}
```

### What to Demonstrate

- [ ] **SessionStart Hook** - Log when session begins
- [ ] **PostToolUse Hook** - Action after file edits
- [ ] **PreToolUse Hook** - Validate/block before actions
- [ ] **PermissionRequest Hook** - Auto-approve patterns
- [ ] **Notification Hook** - Desktop notification

### Test Scenarios

1. Install plugin
2. Start new session → see log output
3. Edit a file → see post-edit hook run
4. Try to write to blocked file → see pre-hook block

---

## Plugin 07: demo-full-plugin - Complete Example

**Feature:** All components bundled together  
**Install:** `/plugin install demo-full-plugin@twatana-private`  
**Cognitive Load:** ⭐⭐⭐ Medium

### Plugin Structure

```
plugins/demo-full-plugin/
├── plugin.json
├── README.md
├── .mcp.json                    # MCP servers
├── skills/
│   └── project-analyzer/
│       ├── SKILL.md
│       └── references/
│           └── analysis-template.md
├── commands/
│   └── analyze.md               # /analyze command
├── agents/
│   └── analyzer/
│       └── AGENT.md             # Analysis subagent
├── hooks/
│   └── settings.json            # Hooks configuration
└── servers/
    └── project-info/
        └── server.py            # MCP server for project info
```

### What to Demonstrate

- [ ] **All 6 components** in one plugin
- [ ] **Component interaction** - skill uses MCP, command uses skill
- [ ] **Proper plugin.json** - Complete metadata
- [ ] **README** - Installation and usage docs

### Test Scenarios

1. Install plugin
2. Verify all components loaded
3. Test each component works
4. Test components work together

---

## Plugin 08: demo-thinking - Extended Thinking

**Feature:** Give Claude more compute time  
**Install:** `/plugin install demo-thinking@twatana-private`  
**Cognitive Load:** ⭐ Very Low

### Plugin Structure

```
plugins/demo-thinking/
├── plugin.json
├── README.md
├── commands/
│   ├── think.md                 # Trigger "think" mode
│   ├── think-hard.md            # Trigger "think hard" mode
│   └── ultrathink.md            # Trigger "ultrathink" mode
├── skills/
│   └── complex-reasoning/
│       ├── SKILL.md             # When to use extended thinking
│       └── references/
│           └── test-problems.md # Example problems
```

### What to Demonstrate

- [ ] **Think triggers** - "think", "think hard", "ultrathink"
- [ ] **Problem types** - When extended thinking helps
- [ ] **Comparison** - Same problem with/without thinking

---

## Plugin 10: demo-settings - Configuration Patterns

**Feature:** Project/user/plugin settings  
**Install:** `/plugin install demo-settings@twatana-private`  
**Cognitive Load:** ⭐⭐ Low

### Plugin Structure

```
plugins/demo-settings/
├── plugin.json
├── README.md
├── skills/
│   └── settings-explainer/
│       ├── SKILL.md             # Explain settings hierarchy
│       └── references/
│           ├── project-settings.md
│           ├── user-settings.md
│           └── env-vars.md
├── commands/
│   └── show-settings.md         # Display current settings
├── examples/
│   ├── project-settings.json    # Example .claude/settings.json
│   ├── user-settings.json       # Example ~/.claude/settings.json
│   └── local-settings.json      # Example .claude/settings.local.json
```

---

## Plugin 11: demo-model-routing - LiteLLM Integration

**Feature:** Use different LLMs with Claude Code  
**Install:** `/plugin install demo-model-routing@twatana-private`  
**Cognitive Load:** ⭐⭐⭐ Medium

### Plugin Structure

```
plugins/demo-model-routing/
├── plugin.json
├── README.md
├── .mcp.json                    # External LLM tools via MCP
├── skills/
│   └── multi-model/
│       ├── SKILL.md             # When to use which model
│       └── references/
│           └── model-comparison.md
├── agents/
│   ├── gpt-agent/
│   │   └── AGENT.md             # model: gpt-4o (via LiteLLM)
│   ├── gemini-agent/
│   │   └── AGENT.md             # model: gemini-pro
│   └── haiku-agent/
│       └── AGENT.md             # model: claude-haiku (fast/cheap)
├── servers/
│   └── external-llm/
│       ├── server.py            # MCP server calling external LLMs
│       └── requirements.txt
├── config/
│   ├── litellm_config.yaml      # LiteLLM proxy configuration
│   └── start-proxy.sh           # Start LiteLLM proxy
```

### What to Demonstrate

- [ ] **LiteLLM Setup** - Proxy configuration
- [ ] **Model Aliases** - gpt-4o, gemini-pro, claude-haiku
- [ ] **Subagent Routing** - Different models per agent
- [ ] **MCP Tool** - Call external LLMs as tools
- [ ] **Cost Comparison** - When to use which tier

---

## Standalone Demos (Not Plugins)

Some features can't be distributed as plugins or are better as standalone references:

### standalone/headless-mode/

**Feature:** CI/CD integration with Claude Code  
**Not a plugin because:** Headless mode is about running Claude, not extending it

```
standalone/headless-mode/
├── README.md
├── basic-usage.sh               # claude -p "prompt" --print
├── stream-json.sh               # --output-format stream-json
├── with-allowed-tools.sh        # --allowedTools Read,Grep
├── github-actions/
│   └── claude-review.yml        # PR review workflow
└── azure-pipelines/
    └── azure-pipelines.yml      # Azure DevOps workflow
```

### standalone/vscode-mcp/

**Feature:** MCP configuration in VS Code  
**Not a plugin because:** VS Code uses different config mechanism

```
standalone/vscode-mcp/
├── README.md
├── user-settings-example.json   # User-level MCP config
├── workspace-settings-example.json # Workspace-level MCP
└── servers/
    └── echo-server.py           # Same server, VS Code config
```

### standalone/user-level/

**Feature:** User-level skills/commands/agents  
**Not a plugin because:** Demonstrates ~/.claude/ usage

```
standalone/user-level/
├── README.md                    # Instructions for ~/.claude/
├── example-skills/              # Copy to ~/.claude/skills/
├── example-commands/            # Copy to ~/.claude/commands/
└── example-agents/              # Copy to ~/.claude/agents/
```

---

## Marketplace Configuration

### .claude-plugin/marketplace.json

```json
{
  "name": "twatana-private",
  "description": "Claude Extensibility Demo Collection - Hello World examples for all features",
  "owner": {
    "name": "Takashi Watanabe",
    "email": "twatana@microsoft.com"
  },
  "plugins": [
    {
      "name": "demo-claudemd",
      "source": "./plugins/demo-claudemd",
      "description": "CLAUDE.md template generator and examples"
    },
    {
      "name": "demo-skills",
      "source": "./plugins/demo-skills",
      "description": "Skill patterns: minimal, references, scripts, assets"
    },
    {
      "name": "demo-mcp",
      "source": "./plugins/demo-mcp",
      "description": "MCP server examples: echo, calculator, with env vars"
    },
    {
      "name": "demo-commands",
      "source": "./plugins/demo-commands",
      "description": "Slash command patterns: simple, arguments, workflows"
    },
    {
      "name": "demo-subagents",
      "source": "./plugins/demo-subagents",
      "description": "Subagent patterns: minimal, limited tools, different models"
    },
    {
      "name": "demo-hooks",
      "source": "./plugins/demo-hooks",
      "description": "Hook patterns: pre/post tool use, session events"
    },
    {
      "name": "demo-full-plugin",
      "source": "./plugins/demo-full-plugin",
      "description": "Complete plugin with all 6 components"
    },
    {
      "name": "demo-thinking",
      "source": "./plugins/demo-thinking",
      "description": "Extended thinking triggers and examples"
    },
    {
      "name": "demo-settings",
      "source": "./plugins/demo-settings",
      "description": "Settings hierarchy and configuration patterns"
    },
    {
      "name": "demo-model-routing",
      "source": "./plugins/demo-model-routing",
      "description": "LiteLLM integration for multi-model routing"
    }
  ]
}
```

---

## Quick Reference Card

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

---

## Implementation Priority

### Phase 1: Bootstrap Marketplace (Do First!)
1. ☐ Create `.claude-plugin/marketplace.json`
2. ☐ Create root `README.md` for the marketplace
3. ☐ Create `plugins/` directory structure

### Phase 2: Core Plugins (Foundations)
4. ☐ Plugin 02: demo-skills (most fundamental)
5. ☐ Plugin 04: demo-commands (very easy)
6. ☐ Plugin 03: demo-mcp (medium complexity)

### Phase 3: Advanced Plugins
7. ☐ Plugin 05: demo-subagents
8. ☐ Plugin 06: demo-hooks
9. ☐ Plugin 01: demo-claudemd (templates)

### Phase 4: Complete Examples
10. ☐ Plugin 07: demo-full-plugin
11. ☐ Plugin 08: demo-thinking
12. ☐ Plugin 10: demo-settings

### Phase 5: Multi-Model & Standalone
13. ☐ Plugin 11: demo-model-routing
14. ☐ standalone/headless-mode
15. ☐ standalone/vscode-mcp

---

## Getting Started

### Step 1: Create the marketplace structure

```bash
cd twatana-msft-private

# Create marketplace directory
mkdir -p .claude-plugin
mkdir -p plugins

# Create initial plugins directories
mkdir -p plugins/demo-skills/skills
mkdir -p plugins/demo-commands/commands
mkdir -p plugins/demo-mcp/servers
```

### Step 2: Create marketplace.json

Create `.claude-plugin/marketplace.json` with the content above.

### Step 3: Create your first demo plugin

Start with `demo-skills` - it's the most fundamental.

### Step 4: Test the marketplace

```bash
# In Claude Code (WSL)
/plugin marketplace add https://microsoft.ghe.com/twatana/twatana-msft-private.git

# List available plugins
/plugin

# Install a demo
/plugin install demo-skills@twatana-private
```

---

## Files to Create (Bootstrap)

### 1. .claude-plugin/marketplace.json
(See Marketplace Configuration section above)

### 2. README.md (Root)

```markdown
# twatana-private - Claude Extensibility Demo Collection

> Private demo marketplace for learning Claude Code extensibility features

## Installation

\`\`\`bash
# Add this marketplace
/plugin marketplace add https://microsoft.ghe.com/twatana/twatana-msft-private.git

# List available demo plugins
/plugin

# Install any demo
/plugin install demo-skills@twatana-private
\`\`\`

## Available Demos

| Plugin | Feature | Description |
|--------|---------|-------------|
| demo-skills | Skills | Auto-triggered workflows |
| demo-mcp | MCP Servers | External tool integration |
| demo-commands | Slash Commands | Manual shortcuts |
| demo-subagents | Subagents | Specialized agents |
| demo-hooks | Hooks | Event-driven automation |
| demo-full-plugin | Complete | All components together |

## Purpose

Low-cognitive-load "hello world" demos for hands-on learning.
Each plugin demonstrates ONE extensibility feature with minimal complexity.

See [DEMO-PLAN.md](DEMO-PLAN.md) for full implementation details.
```

### 3. plugins/demo-skills/plugin.json

```json
{
  "name": "demo-skills",
  "version": "1.0.0",
  "description": "Skill patterns: minimal, references, scripts, assets"
}
```

---

## Notes

- All demo plugins are installable via `/plugin install`
- Each plugin is self-contained with its own README
- Standalone demos are for features that don't fit plugin model
- This is YOUR sandbox - experiment freely!
