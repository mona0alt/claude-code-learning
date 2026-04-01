# AskUserQuestion Tool Prompt

## Overview

Ask the user multiple choice questions to gather information, clarify ambiguity, understand preferences, make decisions, or offer choices.

## When to Use

- Gather user preferences or requirements
- Clarify ambiguous instructions
- Get decisions on implementation choices as you work
- Offer choices about what direction to take

## Usage Notes

- Users will always be able to select "Other" to provide custom text input
- Use `multiSelect: true` to allow multiple answers for a question
- If you recommend a specific option, make that the first option and add "(Recommended)"

## Preview Feature

For options requiring visual comparison, use the optional `preview` field:
- ASCII mockups of UI layouts or components
- Code snippets showing different implementations
- Diagram variations
- Configuration examples

Preview content is rendered as markdown in a monospace box. When any option has a preview, the UI switches to a side-by-side layout.

## Plan Mode Note

In plan mode, use this tool to clarify requirements or choose between approaches **BEFORE** finalizing your plan.

Do NOT use this tool to ask "Is my plan ready?" or "Should I proceed?" — use ExitPlanMode instead.

**Important:** Do not reference "the plan" in your questions (e.g., "Does the plan look good?") because the user cannot see the plan until you call ExitPlanMode.
