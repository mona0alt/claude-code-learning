# Worktree 工具提示词

## EnterWorktree 工具

创建隔离的 git worktree 并将会话切换到其中。

### 何时使用

**仅当**用户明确要求在 worktree 中工作时：
- "start a worktree"
- "work in a worktree"
- "create a worktree"
- "use a worktree"

### 何时不使用

- 用户要求创建分支或切换分支 — 使用 git 命令
- 用户要求修复 bug 或开发功能 — 使用正常 git 工作流
- 除非用户明确提到 "worktree"，否则不要使用

### 要求

- 必须在 git 仓库中，或在 settings.json 中配置了 WorktreeCreate/WorktreeRemove hooks
- 不能已在 worktree 中

### 行为

- 在 git 仓库中：在 `.claude/worktrees/` 内创建基于 HEAD 的新分支的 git worktree
- 将会话的工作目录切换到新 worktree
- 使用 ExitWorktree 离开 worktree

### 参数

- `name`（可选）：worktree 的名称。如未提供则生成随机名称。

---

## ExitWorktree 工具

退出 worktree 会话并返回原始工作目录。

### 范围

此工具**仅**对 EnterWorktree 在此会话中创建的 worktree 操作。不会影响：
- 你手动用 `git worktree add` 创建的 worktree
- 之前会话中的 worktree
- 如果从未调用 EnterWorktree，则不影响当前目录

如果在实际未使用 EnterWorktree 时调用，则为**空操作**。

### 何时使用

仅当用户明确要求时：
- "exit the worktree"
- "leave the worktree"
- "go back"

### 参数

- `action`（必需）：`"keep"` 或 `"remove"`
  - `"keep"`：保留 worktree 目录和分支在磁盘上
  - `"remove"`：删除 worktree 目录及其分支
- `discard_changes`（可选）：当要删除有未提交更改的 worktree 时需要

### 行为

- 恢复会话的工作目录到原始位置
- 清除 CWD 相关的缓存
