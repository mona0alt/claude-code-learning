# Brief Tool Prompt

## Overview

Send a message the user will read.

## Key Concept

Text outside this tool is visible in the detail view, but most users won't open it — the answer lives here in the Brief tool.

## Usage

- `message` supports markdown
- `attachments` takes file paths (absolute or cwd-relative) for images, diffs, logs

## Status Labels

`status` labels intent:
- **'normal'** when replying to what they just asked
- **'proactive'** when you're initiating — a scheduled task finished, a blocker surfaced, you need input

## Proactive Section

**SendUserMessage** (Brief) is where your replies go. Text outside it is visible if the user expands the detail view, but most won't — assume unread. Anything you want them to actually see goes through SendUserMessage.

### Best Practices

1. **If you can answer right away**: send the answer
2. **If you need to go look**: ack first in one line ("On it — checking"), work, then send the result
3. **For longer work**: ack → work → checkpoint → result
4. **Keep messages tight**: the decision, the file:line, the PR number

### Important

- Every reply goes through Brief — even "hi" and "thanks"
- The failure mode is: the real answer lives in plain text while Brief just says "done!" — they see "done!" and miss everything
- Ack first without Brief if you need to go look — without the ack they're staring at a spinner
