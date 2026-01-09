# Skill Guidelines and Best Practices

This is a reference document that demonstrates progressive disclosure.

## When to Create a Skill

Create a skill when:
- Information is needed occasionally, not constantly
- You want to reduce always-on context
- The knowledge is specialized or domain-specific
- You need to bundle related documentation together

## Skill Best Practices

### 1. Keep SKILL.md Lightweight
- Summarize what the skill provides
- List available references
- Don't duplicate reference content

### 2. Use Progressive Disclosure
- Load references only when needed
- Don't eagerly load all files
- Trust the skill system to fetch what's required

### 3. Organize References Logically
- Group related docs together
- Use clear, descriptive filenames
- Create subdirectories for complex skills

### 4. Include Usage Examples
- Show when to use the skill
- Provide example workflows
- Document trigger conditions

## Anti-Patterns to Avoid

❌ Loading all references immediately  
❌ Duplicating content between SKILL.md and references  
❌ Creating skills for always-needed information (use CLAUDE.md instead)  
❌ Making SKILL.md too long (defeats progressive disclosure)

## This Reference's Purpose

This file demonstrates that:
- It wasn't loaded until explicitly needed
- It contains detailed information not in SKILL.md
- It only consumes tokens when accessed
- Multiple reference files can coexist
