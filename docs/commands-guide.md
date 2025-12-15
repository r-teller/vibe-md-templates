# Commands Guide

Commands are **conversational automation tools** that live in your `.claude/commands/` directory. They guide you through specific tasks using structured, interactive dialogues with Claude Code. Think of them as "smart shortcuts" that combine knowledge of your project context with step-by-step assistance.

Unlike templates (which provide static context), commands are **dynamic and interactive** - they ask questions, gather information, make decisions, and directly update your project files.

## What Commands Do

Commands help you:

- Run common workflows with guided assistance
- Maintain consistency across repetitive tasks
- Reduce context switching and cognitive load

**Remember:** Commands are tools to make your workflow smoother, not rigid scripts. Feel free to adapt them to your specific needs!

## Create a Command
You can use the [create-command.prompt](../prompts/create-command.prompt) prompt to create the command. 

Then add the command to your `.claude/commands/` directory.

## Available Commands

### `story.md` - Add Feature to PRD

**Purpose:** Conversational tool to add new feature user stories to your existing PRD.

**Example usage:**

```
/story export my data to PDF
```
