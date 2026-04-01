# Task Tool Prompts

## TaskCreate Tool

Create a new task in the task list.

### When to Use

- **Complex multi-step tasks** - 3 or more distinct steps or actions
- **Non-trivial and complex tasks** - Requires careful planning or multiple operations
- **Plan mode** - Create a task list to track work
- **User explicitly requests** todo list
- **User provides multiple tasks** - Numbered or comma-separated list
- **After receiving new instructions** - Capture requirements as tasks
- **When starting work** - Mark as in_progress BEFORE beginning
- **After completing a task** - Mark completed and add follow-up tasks

### When NOT to Use

- Only a single, straightforward task
- Task is trivial and tracking provides no benefit
- Task can be completed in less than 3 trivial steps
- Task is purely conversational or informational

### Task Fields

- **subject**: Brief, actionable title in imperative form (e.g., "Fix authentication bug")
- **description**: What needs to be done
- **activeForm** (optional): Present continuous form shown in spinner (e.g., "Fixing authentication bug")

### Tips

- Create tasks with clear, specific subjects that describe the outcome
- Use TaskUpdate to set up dependencies (blocks/blockedBy) if needed
- Check TaskList first to avoid creating duplicate tasks

---

## TaskUpdate Tool

Update a task in the task list.

### What You Can Update

- **status**: `pending` → `in_progress` → `completed`
- **subject**: Change the task title
- **description**: Change the task description
- **activeForm**: Change the spinner text
- **owner**: Assign the task to someone
- **blocks**: Mark tasks that this task blocks
- **blockedBy**: Mark tasks that must complete first

### Status Workflow

Status progresses: `pending` → `in_progress` → `completed`

---

## TaskList Tool

List all tasks in the task list.

### What It Shows

- Task ID
- Subject/brief description
- Status
- Owner
- BlockedBy relationships

### Usage

Use to:
- See what tasks are available
- Check overall project progress
- Find tasks that are blocked
- Avoid creating duplicate tasks

---

## TaskGet Tool

Retrieve a task by its ID.

### What It Returns

- Full task details including description
- Status
- What it blocks and what blocks it

### Usage

Use before starting work on a task to get complete requirements.

---

## TaskStop Tool

Stop a running background task.

### When to Use

- When a task was started in error
- When the task is no longer needed
- When a task needs to be cancelled
