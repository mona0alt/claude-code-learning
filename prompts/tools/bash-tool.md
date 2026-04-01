# Bash Tool Prompt

## Overview

Executes a given bash command and returns its output.

## Key Instructions

### Tool Preference

**AVOID** using bash for these commands - use dedicated tools instead:

| Task | Use This Tool Instead |
|------|---------------------|
| File search | Glob (NOT find or ls) |
| Content search | Grep (NOT grep or rg) |
| Read files | Read (NOT cat/head/tail) |
| Edit files | Edit (NOT sed/awk) |
| Write files | Write (NOT echo >/cat <<EOF) |
| Communication | Output text directly (NOT echo/printf) |

### Multiple Commands

**When issuing multiple commands:**
- Independent commands: make multiple Bash tool calls in parallel
- Dependent commands: chain with `&&` in a single call
- Use `;` only when you need to run sequentially and don't care about failures
- Don't use newlines to separate commands

### Git Commands

**Git Safety Protocol:**
- NEVER update the git config
- NEVER run destructive commands (push --force, reset --hard, clean -f, branch -D) unless explicitly requested
- NEVER skip hooks (--no-verify, --no-gpg-sign) unless explicitly requested
- NEVER run force push to main/master
- **CRITICAL**: Always create NEW commits rather than amending
- When staging files, prefer adding specific files by name (not `git add -A`)

### Commit Process

1. Run `git status`, `git diff`, `git log` in parallel
2. Analyze changes and draft commit message (1-2 sentences focusing on "why")
3. Stage files, create commit with HEREDOC, verify with `git status`
4. If hook fails: fix issue, create NEW commit

### Creating Pull Requests

1. Run git status, diff, log in parallel
2. Analyze all changes and draft PR title (under 70 chars) and summary
3. Create branch if needed, push with -u flag
4. Create PR using `gh pr create` with HEREDOC body

### Background Commands

- Use `run_in_background` parameter when you don't need result immediately
- You'll be notified when it completes
- No need to use `&` at end of command

### Sleep Guidelines

- Don't sleep between commands that can run immediately
- If polling an external process, use a check command rather than sleeping
- If you must sleep, keep duration short (1-5 seconds)
- For long-running commands, use `run_in_background`

### Sandbox Mode

By default, commands run in a sandbox that controls directory and network access.

**Allowed directories:** Only paths within sandbox configuration can be accessed.

**For temporary files:** Use `$TMPDIR` environment variable (automatically set).

### Timeouts

- Default timeout: varies by configuration
- Maximum timeout: up to specified limit
- You can specify timeout in milliseconds

### Examples

```bash
# Parallel independent commands
git status && git diff

# Chain dependent commands
cd /path && npm install && npm test

# Background long-running command
npm run build --run_in_background=true
```
