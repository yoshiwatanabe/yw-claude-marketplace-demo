# demo-commands - Slash Commands Demo

Hello World examples for Claude Code slash commands.

## Installation

```
/plugin install demo-commands@yw-claude-marketplace-demo
```

## Available Commands

| Command | Type | Example |
|---------|------|---------|
| `/hello` | Static prompt | `/hello` |
| `/greet` | With arguments | `/greet Alice` |
| `/summarize` | Project analysis | `/summarize` |
| `/analyze-code` | Code file analysis | `/analyze-code src/main.ts` |
| `/explain-code` | Code explanation | `/explain-code src/main.ts` |
| `/check-types` | TypeScript checker | `/check-types` |
| `/test-report` | Test suite runner | `/test-report` |

## What This Demonstrates

Each command shows a different slash command pattern:
- **Simple static prompts** (`/hello`)
- **Commands with arguments** (`/greet $ARGUMENTS`)
- **Multi-step workflows** (`/summarize`)
- **Tool integration** (`/check-types`, `/test-report`)

## How to Use

After installation, commands are available immediately:

1. Type `/` in Claude Code
2. Select a command from the autocomplete
3. Provide arguments if needed (shown with `$ARGUMENTS`)

## Examples

```
/hello
→ Friendly greeting message

/greet Yoshi
→ Personalized greeting with fun facts about the name

/summarize
→ Analysis of the current project

/analyze-code src/main.ts
→ Analysis of the specified file
```

## Testing

See TESTING.md in the plugin directory for detailed testing instructions.