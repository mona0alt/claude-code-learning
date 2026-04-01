# Team Tools Prompts

## TeamCreate Tool

Create a new team to coordinate multiple agents working on a project.

### When to Use

- User explicitly asks to use a team, swarm, or group of agents
- User mentions agents working together, coordinating, or collaborating
- Task is complex enough to benefit from parallel work (e.g., full-stack feature with frontend and backend)

### Choosing Agent Types

- **Read-only agents** (Explore, Plan): Cannot edit/write files. Only for research, search, planning.
- **Full-capability agents**: Have all tools including file editing. For implementation work.
- **Custom agents** in `.claude/agents/`: Check their descriptions for tool restrictions.

### Team Workflow

1. **Create a team** with TeamCreate
2. **Create tasks** using Task tools (automatically use team's task list)
3. **Spawn teammates** using Agent tool with `team_name` and `name` parameters
4. **Assign tasks** using TaskUpdate with `owner`
5. **Teammates work** and mark tasks completed
6. **Shutdown team** via SendMessage with `message: {type: "shutdown_request"}`

### Task Coordination

- Tasks shared at `~/.claude/tasks/{team-name}/`
- Check TaskList after completing each task
- Prefer lowest ID tasks when multiple available
- Coordinate via task list status

### Teammate Communication

- Messages from teammates delivered automatically
- Refer to teammates by NAME (not UUID)
- Idle is normal between turns
- SendMessage to communicate

---

## SendMessage Tool

Send a message to another agent.

### Addressing

| `to` value | Meaning |
|------------|---------|
| `"researcher"` | Teammate by name |
| `"*"` | Broadcast to all teammates |
| `"uds:/path/to.sock"` | Local Claude session socket |
| `"bridge:session_..."` | Remote Control peer session |

### Important

- Your plain text output is NOT visible to other agents
- Use SendMessage to communicate
- Messages from teammates delivered automatically

### Protocol Responses

For JSON messages with `type: "shutdown_request"` or `type: "plan_approval_request"`:

```json
{"to": "team-lead", "message": {"type": "shutdown_response", "request_id": "...", "approve": true}}
```
