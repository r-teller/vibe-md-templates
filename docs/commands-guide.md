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

### `gogogo.md` - Session Startup

**Purpose:** Start a new Claude Code session by loading project context, checking git status, and preparing for work.

**What it does:**
1. Checks if your dev server is running (and starts it if needed)
2. Reviews git status and recent commits
3. Loads all project context files (claude.md, prd.md, workflow.md, infra.md)
4. Checks beads (`bd ready`, `bd list`) for in-progress and pending issues
5. Summarizes recent changelog entries
6. Presents options for what to work on

**Example usage:**

```
/gogogo
```

---

### `wrapup.md` - Session Wrap-up

**Purpose:** Cleanly close a Claude Code session by committing changes, syncing beads, and creating a handoff for the next session.

**What it does:**
1. Commits any uncommitted changes
2. Updates beads issue statuses (`bd close`, `bd update`)
3. Syncs beads with git (`bd sync`)
4. Runs build verification
5. Provides a session summary (completed, in progress, blockers)
6. Pushes to remote and creates a handoff message

**Example usage:**

```
/wrapup
```

---

### `story.md` - Add Feature to PRD

**Purpose:** Conversational tool to add new feature user stories to your existing PRD.

**Example usage:**

```
/story export my data to PDF
```
