# Write Tool Prompt

## Overview

Writes a file to the local filesystem.

## Key Instructions

### Before Writing

**If this is an existing file, you MUST use the Read tool first** to read the file's contents. This tool will fail if you did not read the file first.

### Important Rules

1. **This tool will OVERWRITE existing files** at the provided path
2. **Prefer the Edit tool** for modifying existing files — it only sends the diff
3. **Only use Write for:**
   - Creating new files
   - Complete rewrites
4. **NEVER create documentation files** (*.md) or README files unless explicitly requested
5. **Only use emojis** if the user explicitly requests it

### When to Use Write vs Edit

| Situation | Use |
|-----------|-----|
| Modifying existing file | **Edit** tool |
| Creating new file | **Write** tool |
| Complete rewrite of existing file | **Write** tool |
