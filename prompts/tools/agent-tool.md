# Agent Tool Prompt

## Overview

The Agent tool launches specialized agents (subprocesses) that autonomously handle complex tasks.

## Key Instructions

### When to Use

Use the Agent tool with specialized agents when the task at hand matches the agent's description. Subagents are valuable for:
- Parallelizing independent queries
- Protecting the main context window from excessive results

Avoid duplicating work that subagents are already doing.

### Available Agent Types

Agent types and their tools are listed in system reminders. Each type has specific capabilities.

### Usage Notes

1. **Always include a short description** (3-5 words) summarizing what the agent will do
2. **To continue a previously spawned agent**, use SendMessage with the agent's ID or name
3. **Clearly tell the agent** whether you expect it to write code or just do research
4. **Results** are returned to you and should be summarized for the user
5. **You can optionally run agents in background** using the `run_in_background` parameter

### When NOT to Use

- If you want to read a specific file path, use Read or Glob instead
- If you are searching for a specific class definition, use Grep instead
- If you are searching within specific files, use Read instead

### Writing Agent Prompts

**Brief the agent like a smart colleague** who just walked into the room:
- Explain what you're trying to accomplish and why
- Describe what you've already learned or ruled out
- Give enough context for judgment calls
- If you need a short response, say so

**Never delegate understanding:**
- Don't write "based on your findings, fix the bug"
- Write prompts that prove you understood: include file paths, line numbers, specific changes

**Terse command-style prompts produce shallow, generic work.**

### Concurrency

- Launch multiple agents concurrently whenever possible
- To launch in parallel, use a single message with multiple tool calls

### Continuing Agents

When continuing a worker with SendMessage, it has full context from its previous run. Provide specific, synthesized instructions.

### Examples

```typescript
// Research task
AgentTool({
  description: "Investigate auth bug",
  subagent_type: "worker",
  prompt: "Investigate the auth module in src/auth/. Find where null pointer exceptions could occur..."
})

// Continue with implementation
SendMessageTool({
  to: "agent-a1b",
  message: "Fix the null pointer in src/auth/validate.ts:42. Add a null check before accessing user.id..."
})
```
