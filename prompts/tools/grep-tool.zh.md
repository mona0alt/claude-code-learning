# Grep 工具提示词

## 概述

基于 ripgrep 构建的强大搜索工具。

## 关键说明

### 始终使用 Grep 工具

- **始终**使用 Grep 进行搜索任务
- **永远不要**将 `grep` 或 `rg` 作为 Bash 命令调用
- Grep 已经为正确的权限和访问进行了优化

### 功能

- 支持完整正则语法（例如 `"log.*Error"`、`"function\\s+\\w+"`）
- 用 glob 参数过滤文件（例如 `"*.js"`、`"**/*.tsx"`）
- 按类型过滤（例如 `"js"`、`"py"`、`"rust"`）
- 输出模式：
  - `"content"` - 显示匹配行
  - `"files_with_matches"` - 仅显示文件路径（默认）
  - `"count"` - 显示匹配数量

### 模式语法

- 使用 ripgrep 语法（不是 grep）
- 字面大括号需要转义：在 Go 代码中找 `interface{}` 用 `interface\\{\\}`

### 多行匹配

- 默认情况下，模式仅在单行内匹配
- 对于跨行模式如 `struct \\{[\\s\\S]*?field`，使用 `multiline: true`

### 开放性搜索

对于需要多轮 grep 的搜索，使用 Agent 工具代替。
