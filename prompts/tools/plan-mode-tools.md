# Plan Mode Tools

## EnterPlanMode Tool

Use this tool when you're about to start a **non-trivial implementation task**. Getting user sign-off before writing code prevents wasted effort.

### When to Use

**Use EnterPlanMode** for implementation tasks when:

1. **New Feature Implementation** - Adding meaningful new functionality
2. **Multiple Valid Approaches** - Task solved in several ways
3. **Code Modifications** - Changes affecting existing behavior
4. **Architectural Decisions** - Choosing between patterns/technologies
5. **Multi-File Changes** - Task will likely touch more than 2-3 files
6. **Unclear Requirements** - Need to explore before understanding scope
7. **User Preferences Matter** - Implementation could go multiple ways

### When NOT to Use

Skip for simple tasks:
- Single-line fixes (typos, obvious bugs)
- Adding a single function with clear requirements
- Tasks with very specific, detailed instructions
- Pure research/exploration tasks (use Agent tool instead)

### What Happens in Plan Mode

1. Explore codebase using Glob, Grep, Read
2. Understand existing patterns and architecture
3. Design an implementation approach
4. Present plan to user for approval
5. Use AskUserQuestion if you need clarification
6. Exit plan mode when ready to implement

---

## ExitPlanMode Tool

Use this tool when you have finished writing your plan and are ready for user approval.

### How It Works

- You should have already written your plan to the plan file
- This tool does NOT take plan content as parameter
- Simply signals you're done planning
- User will see your plan file contents

### When NOT to Use

For research tasks where you're just gathering information — do NOT use this tool.

### Before Using

Ensure your plan is complete:
- Use AskUserQuestion for unresolved questions first
- Once finalized, use this tool to request approval

### Important

Do NOT use AskUserQuestion to ask "Is this plan okay?" — that's exactly what ExitPlanMode does.
