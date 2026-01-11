# Demo: Skills

**Feature:** Progressive-disclosure knowledge files  
**Cognitive Load:** ⭐⭐ Low

## What This Demonstrates

Skills are knowledge files that Claude can discover and load on-demand. They use progressive disclosure to minimize token usage while providing deep context when needed.

## Skills Included

### 1. Minimal Skill
**Path:** `skills/minimal-skill/`  
**Demo:** Simplest possible skill with just description + workflow

### 2. Skill with References
**Path:** `skills/skill-with-references/`  
**Demo:** Skill that loads additional documentation on demand

### 3. Skill with Scripts
**Path:** `skills/skill-with-scripts/`  
**Demo:** Skill that can execute helper scripts

### 4. Skill with Assets
**Path:** `skills/skill-with-assets/`  
**Demo:** Skill with bundled configuration files

### 5. Greeting Skill
**Path:** `skills/greeting-skill/`  
**Demo:** Auto-triggered skill that responds to keywords

## Test Scenarios

1. **Install the plugin**
   ```bash
   /plugin install demo-skills@yw-claude-marketplace-demo
   ```

2. **Test auto-trigger**
   - Say "hello" and observe the greeting-skill activate

3. **Test progressive disclosure**
   - Ask about something that matches a skill description
   - Observe how metadata loads first, then content as needed

4. **Test scripts**
   - Trigger the skill-with-scripts and observe execution

## Skill Structure

Each skill follows this structure:
```
skill-name/
├── SKILL.md          # Main skill definition
├── references/       # Optional: Reference docs
│   └── *.md
├── scripts/          # Optional: Executable scripts
│   └── *.py, *.sh
└── assets/           # Optional: Data files
    └── *.json, *.yaml
```

## Learning Points

- Skills use progressive disclosure (load only what's needed)
- Skills can auto-trigger based on keywords/context
- Skills can bundle references, scripts, and assets
- Skills reduce always-on context compared to CLAUDE.md
