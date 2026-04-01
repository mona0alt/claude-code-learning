# Team 工具提示词

## TeamCreate 工具

创建新团队来协调多个智能体工作。

### 何时使用

- 用户明确要求使用团队、群或智能体组
- 用户提到智能体需要一起工作、协调或合作
- 任务复杂到需要并行工作（例如：前后端俱全的全栈功能）

### 选择智能体类型

- **只读智能体**（Explore、Plan）：不能编辑/写文件。仅用于研究、搜索、规划。
- **全功能智能体**：拥有所有工具包括文件编辑。用于实现工作。
- **自定义智能体**（在 `.claude/agents/` 中）：查看描述了解工具限制。

### 团队工作流

1. **创建团队**用 TeamCreate
2. **创建任务**用 Task 工具（自动使用团队任务列表）
3. **生成队友**用 Agent 工具加 `team_name` 和 `name` 参数
4. **分配任务**用 TaskUpdate 加 `owner`
5. **队友工作**并标记任务完成
6. **关闭团队**通过 SendMessage 加 `message: {type: "shutdown_request"}`

### 任务协调

- 任务共享在 `~/.claude/tasks/{team-name}/`
- 每完成一个任务后检查 TaskList
- 有多个可用任务时优先选最低 ID
- 通过任务列表状态协调

### 队友通信

- 队友消息自动投递
- 用名字称呼队友（不是 UUID）
- turn 之间空闲是正常的
- 用 SendMessage 通信

---

## SendMessage 工具

向另一个智能体发送消息。

### 寻址

| `to` 值 | 含义 |
|---------|------|
| `"researcher"` | 按名字称呼队友 |
| `"*"` | 向所有队友广播 |
| `"uds:/path/to.sock"` | 本地 Claude session socket |
| `"bridge:session_..."` | Remote Control 对等 session |

### 重要

- 你的纯文本输出对其他智能体**不可见**
- 用 SendMessage 通信
- 队友的消息自动投递

### 协议响应

对于带 `type: "shutdown_request"` 或 `type: "plan_approval_request"` 的 JSON 消息：

```json
{"to": "team-lead", "message": {"type": "shutdown_response", "request_id": "...", "approve": true}}
```
