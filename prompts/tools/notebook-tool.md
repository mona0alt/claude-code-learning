# NotebookEdit Tool Prompt

## Overview

Completely replaces the contents of a specific cell in a Jupyter notebook.

## Key Information

- Works with `.ipynb` files (Jupyter notebooks)
- Notebook cells can contain code, text, and visualizations
- Commonly used for data analysis and scientific computing

## Parameters

- **notebook_path**: Absolute path to the notebook file (not relative)
- **cell_id**: ID of the cell to edit
- **new_source**: New content for the cell
- **cell_type**: Type of cell - "code" or "markdown"

## Edit Modes

- **replace** (default): Replace the cell contents
- **insert**: Add a new cell at the specified index
- **delete**: Delete the cell at the specified index

## Cell Number

Cell numbers are 0-indexed.
