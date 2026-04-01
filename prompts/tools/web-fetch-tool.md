# WebFetch Tool Prompt

## Overview

Fetches content from a specified URL and processes it using an AI model.

## How It Works

1. Takes a URL and a prompt as input
2. Fetches URL content, converts HTML to markdown
3. Processes content with prompt using a fast model
4. Returns the model's response about the content

## Usage Notes

- **Prefer MCP-provided web fetch tools** if available (fewer restrictions)
- URL must be fully-formed and valid
- HTTP URLs automatically upgraded to HTTPS
- Results may be summarized if content is very large
- 15-minute cache for faster repeated access
- **For GitHub URLs**, prefer using `gh` CLI via Bash instead

## What to Include in Prompt

Describe what information you want to extract from the page.

## Redirect Handling

If URL redirects to a different host, you'll be informed with the redirect URL. Make a new WebFetch request with the redirect URL.

## Important

- This tool is **read-only** and does not modify any files
