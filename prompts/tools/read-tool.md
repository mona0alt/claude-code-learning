# Read Tool Prompt

## Overview

Reads a file from the local filesystem. You can access any file directly by using this tool.

## Key Instructions

### Basic Usage

- The `file_path` parameter must be an **absolute path**, not a relative path
- By default, reads up to 2000 lines from the beginning of the file
- Results are returned using `cat -n` format, with line numbers starting at 1

### Reading Partial Files

- You can optionally specify a line offset and limit
- When you already know which part of the file you need, only read that part

### Special File Types

**Images:**
- Can read PNG, JPG and other image formats
- Contents are presented visually (Claude Code is multimodal)

**PDFs:**
- Can read PDF files
- For large PDFs (10+ pages): MUST provide pages parameter
- Example: `pages: "1-5"`
- Maximum 20 pages per request

**Jupyter Notebooks:**
- Can read .ipynb files
- Returns all cells with outputs

### Important Notes

- It's okay to read a file that does not exist (error will be returned)
- If file exists but is empty, you'll receive a warning
- Can only read files, not directories (use `ls` via Bash for directories)
- Always use this tool to view screenshots the user provides

### File Path Assumptions

- Assume this tool can read all files on the machine
- If the user provides a path, assume that path is valid
