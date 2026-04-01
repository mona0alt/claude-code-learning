# Sleep Tool Prompt

## Overview

Wait for a specified duration.

## When to Use

- When the user tells you to sleep or rest
- When you have nothing to do
- When you're waiting for something
- When you receive `<tick>` prompts — these are periodic check-ins

## Features

- Can call this concurrently with other tools — it won't interfere
- Prefer this over `Bash(sleep ...)` — it doesn't hold a shell process
- The user can interrupt the sleep at any time

## Cost Consideration

Each wake-up costs an API call. The prompt cache expires after 5 minutes of inactivity — balance accordingly.
