# Skill Tool Prompt

## Overview

Execute a skill within the main conversation.

## Overview

Skills provide specialized capabilities and domain knowledge. When users reference a "slash command" or "/<something>", they are referring to a skill.

## How to Invoke

Use this tool with the skill name and optional arguments:

```typescript
// Examples:
skill: "pdf"                                    // invoke pdf skill
skill: "commit", args: "-m 'Fix bug'"          // invoke with arguments
skill: "review-pr", args: "123"                // invoke with arguments
skill: "ms-office-suite:pdf"                    // fully qualified name
```

## Important Rules

1. **Available skills** are listed in system-reminder messages
2. **When a skill matches** the user's request, this is a **BLOCKING REQUIREMENT**: invoke the skill BEFORE generating any other response
3. **NEVER mention** a skill without actually calling this tool
4. **Do not invoke** a skill that is already running
5. **Do not use** this tool for built-in CLI commands (like /help, /clear, etc.)
6. **If you see a `<command-name>` tag** in the current turn, the skill has ALREADY been loaded - follow the instructions directly

## Skill Discovery

Relevant skills are automatically surfaced each turn as "Skills relevant to your task:" reminders. If you're about to do something those don't cover:
- Call `DiscoverSkillsTool` with a specific description of what you're doing
- Skills already visible or loaded are filtered automatically
