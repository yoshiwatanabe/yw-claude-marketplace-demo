---
name: skill-with-references
description: Demonstrates progressive disclosure by loading reference documentation on demand. Shows how skills can include additional detailed documentation without loading everything upfront.
---

# Skill with References

**Description:** Demonstrates progressive disclosure by loading reference documentation on demand.

**When to use:** When explaining how skills can include additional documentation without loading everything upfront.

## Workflow

1. Initially, only this SKILL.md is loaded
2. When detailed information is needed, load the appropriate reference document
3. References are in the `references/` subdirectory

## Available References

- `guidelines.md` - Detailed guidelines and best practices
- Load these only when specifically needed

## Key Points

- References are NOT loaded automatically
- Load references only when the conversation requires them
- This reduces token usage while maintaining deep knowledge availability
- Progressive disclosure = better performance

## Example Usage

**User asks:** "What are the guidelines?"
**Response:** Load `references/guidelines.md` and provide the information.

**User asks:** "Tell me about this skill"
**Response:** Explain from this SKILL.md only (don't load references yet).
