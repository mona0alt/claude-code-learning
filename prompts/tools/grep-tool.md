# Grep Tool Prompt

## Overview

A powerful search tool built on ripgrep.

## Key Instructions

### Always Use Grep Tool

- **ALWAYS** use Grep for search tasks
- **NEVER** invoke `grep` or `rg` as a Bash command
- Grep has been optimized for correct permissions and access

### Features

- Supports full regex syntax (e.g., `"log.*Error"`, `"function\\s+\\w+"`)
- Filter files with glob parameter (e.g., `"*.js"`, `"**/*.tsx"`)
- Filter by type (e.g., `"js"`, `"py"`, `"rust"`)
- Output modes:
  - `"content"` - shows matching lines
  - `"files_with_matches"` - shows only file paths (default)
  - `"count"` - shows match counts

### Pattern Syntax

- Uses ripgrep syntax (not grep)
- Literal braces need escaping: use `interface\\{\\}` to find `interface{}` in Go code

### Multiline Matching

- By default, patterns match within single lines only
- For cross-line patterns like `struct \\{[\\s\\S]*?field`, use `multiline: true`

### Open-Ended Searches

For searches requiring multiple rounds of grepping, use the Agent tool instead.
