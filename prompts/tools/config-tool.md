# Config Tool Prompt

## Overview

Get or set Claude Code configuration settings.

## Usage

- **Get current value:** Omit the "value" parameter
- **Set new value:** Include the "value" parameter

## Global Settings (stored in ~/.claude.json)

- `allowWrite`: Enable write operations - true/false
- `allowRead`: Enable read operations - true/false
- `allowBash`: Enable bash command execution - true/false
- `verbose`: Enable verbose output - true/false

## Project Settings (stored in settings.json)

- `permissions.defaultMode`: Default permission mode - "accept", "review", "refuse", "plan"
- `permissions.allowPr`: Allow pull request creation - true/false
- `theme`: Color theme - "light", "dark", "system"
- `editorMode`: Editor mode - "default", "vim", "emacs"

## Examples

```json
{ "setting": "theme" }
{ "setting": "theme", "value": "dark" }
{ "setting": "editorMode", "value": "vim" }
{ "setting": "permissions.defaultMode", "value": "plan" }
```
