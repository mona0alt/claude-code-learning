# WebSearch Tool Prompt

## Overview

Allows searching the web and using results to inform responses.

## Key Features

- Provides up-to-date information for current events and recent data
- Returns search results formatted as search result blocks with markdown links
- Use for accessing information beyond Claude's knowledge cutoff

## Critical Requirement

**After answering the user's question, you MUST include a "Sources:" section:**

```
[Your answer here]

Sources:
- [Source Title 1](https://example.com/1)
- [Source Title 2](https://example.com/2)
```

This is **MANDATORY** - never skip including sources.

## Usage Notes

- Domain filtering is supported (include or block specific websites)
- Web search is only available in the US

## Current Date

The current month is shown in the environment. **Use the correct year** when searching for:
- Recent information
- Documentation
- Current events

Example: If asking for "latest React docs", search with the current year, NOT last year.
