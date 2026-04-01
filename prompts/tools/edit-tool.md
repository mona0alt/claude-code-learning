# Edit Tool Prompt

## Overview

Performs exact string replacements in files.

## Key Instructions

### Before Editing

**You must use the Read tool at least once before editing.** This tool will error if you attempt an edit without reading the file first.

### Edit Format

When editing text from Read tool output:
- Preserve the **exact indentation** (tabs/spaces) as it appears after the line number prefix
- The line number prefix format is: `line number + tab`
- Never include any part of the line number prefix in `old_string` or `new_string`

### Edit Rules

1. **Prefer editing existing files** to creating new ones
2. **NEVER write new files** unless explicitly required
3. **Edit will FAIL** if `old_string` is not unique in the file
   - Provide more context to make it unique, OR
   - Use `replace_all` to change every instance
4. **Use `replace_all`** for replacing/renaming strings across the file

### Minimal Uniqueness

Use the smallest `old_string` that's clearly unique — usually 2-4 adjacent lines is sufficient. Avoid including 10+ lines of context when less uniquely identifies the target.

### Emoji Policy

- Only use emojis if the user explicitly requests it
- Avoid adding emojis to files unless asked
