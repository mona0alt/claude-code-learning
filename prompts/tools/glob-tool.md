# Glob Tool Prompt

## Overview

Fast file pattern matching tool that works with any codebase size.

## Key Features

- Supports glob patterns like `**/*.js` or `src/**/*.ts`
- Returns matching file paths sorted by modification time
- Use this tool when you need to find files by name patterns

## When to Use

- When you need to find files by name patterns
- When doing open-ended searches

## When NOT to Use

- When you already know the specific file path (use Read instead)
- When searching for file contents (use Grep instead)

## Note

When you are doing an open-ended search that may require multiple rounds of globbing and grepping, consider using the Agent tool instead.
