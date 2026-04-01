# Worktree Tools Prompts

## EnterWorktree Tool

Create an isolated git worktree and switch the current session into it.

### When to Use

**ONLY** when the user explicitly asks to work in a worktree:
- "start a worktree"
- "work in a worktree"
- "create a worktree"
- "use a worktree"

### When NOT to Use

- User asks to create a branch or switch branches — use git commands instead
- User asks to fix a bug or work on a feature — use normal git workflow
- Never use unless user explicitly mentions "worktree"

### Requirements

- Must be in a git repository, OR have WorktreeCreate/WorktreeRemove hooks configured
- Must not already be in a worktree

### Behavior

- In a git repository: creates a new git worktree inside `.claude/worktrees/` with a new branch based on HEAD
- Switches the session's working directory to the new worktree
- Use ExitWorktree to leave the worktree mid-session

### Parameters

- `name` (optional): A name for the worktree. Random name generated if not provided.

---

## ExitWorktree Tool

Exit a worktree session and return to the original working directory.

### Scope

This tool **ONLY** operates on worktrees created by EnterWorktree in this session. It will NOT touch:
- Worktrees you created manually with `git worktree add`
- Worktrees from a previous session
- The directory you're in if EnterWorktree was never called

If called outside an EnterWorktree session, it's a **no-op**.

### When to Use

Only when the user explicitly asks:
- "exit the worktree"
- "leave the worktree"
- "go back"

### Parameters

- `action` (required): `"keep"` or `"remove"`
  - `"keep"`: Leave worktree intact on disk
  - `"remove"`: Delete worktree directory and branch
- `discard_changes` (optional): Required when removing worktree with uncommitted changes

### Behavior

- Restores session's working directory to original location
- Clears CWD-dependent caches
