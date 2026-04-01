# Claude Code Prompts 提示词目录

This directory contains all prompts used by Claude Code, organized by category.

本目录包含 Claude Code 使用的所有提示词，按类别组织。

## Directory Structure 目录结构

```
prompts/
├── README.md                    # This file / 本文件
├── system/                      # Main system prompts / 主系统提示词
├── tools/                       # Tool-specific prompts / 工具专用提示词
├── coordinator/                  # Coordinator mode prompts / 协调模式提示词
├── agents/                      # Built-in agent prompts / 内置智能体提示词
└── skill/                       # Skill tool prompts / 技能工具提示词
```

## Categories 类别说明

### System Prompts (系统提示词)
- Main system prompt covering task execution, tool usage, output efficiency

### Tool Prompts (工具提示词) - 18 tools
Agent, Bash, Edit, Glob, Grep, Read, Write, Task (Create/Update/List/Get/Stop), WebSearch, WebFetch, LSP, Sleep, AskUserQuestion, NotebookEdit, Config, Team (Create/SendMessage), Brief, Worktree (Enter/Exit)

### Coordinator Prompts (协调模式提示词)
- Multi-agent orchestration instructions
- Worker delegation protocols

### Agent Prompts (智能体提示词)
- Built-in agent definitions (Explore Agent)

### Skill Prompts (技能提示词)
- Skill tool instructions

## File Count 文件数量

Total: 40 files (20 English + 20 Chinese)
总计：40 个文件（20 个英文 + 20 个中文）

## File Naming 文件命名
- English version: `<category>.<name>.md`
- Chinese version: `<category>.<name>.zh.md`
