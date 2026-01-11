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

### `setup-statusline.md` - Context Status Line Setup

**Purpose:** Configure a persistent status bar showing real-time token usage at the bottom of your terminal.

**What it does:**
1. Checks if `jq` is installed (required dependency)
2. Creates `~/.claude/statusline.sh` with the status line script
3. Updates `~/.claude/settings.json` to enable the status line
4. Explains what was installed and how to verify

**Why use it:** The status line shows "% until compact" - how much context remains before autocompact triggers. This helps you:
- Know when to start a fresh session
- Avoid losing important context to autocompact
- Stay aware of token usage during longer sessions

**This is a one-time setup** that applies to all Claude Code sessions across all projects.

**Example usage:**

```
/setup-statusline
```

After running, restart Claude Code to see the status bar.

---

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

---

## Prompt Engineering Commands

These commands help you create and improve prompts for AI interactions. They use the **R.G.C.O.A. framework** (Role, Goal, Context, Output, Ask/Refinement) to ensure your prompts are comprehensive and effective.

### `create-prompt.md` - Build New Prompts

**Purpose:** Transform a basic idea into a well-structured prompt using the R.G.C.O.A. framework.

**What it does:**
1. Takes your rough idea (e.g., "help with code reviews")
2. Asks targeted questions to understand role, audience, format, and tone
3. Builds a complete, structured prompt ready for use with any LLM

**Why use it:** Vague prompts get vague results. This command guides you through adding the specificity that makes AI responses dramatically more useful.

**Example usage:**

```
/create-prompt
```

Or with an initial idea:

```
/create-prompt help me write better error messages for my API
```

---

### `create-research-prompt.md` - Build Deep Research Prompts

**Purpose:** Create prompts optimized for in-depth research tasks like competitive analysis, technical deep-dives, or market research.

**What it does:**
1. Takes your research topic
2. Asks about scope (time range, sources, depth)
3. Identifies what to exclude (outdated info, things you already know)
4. Structures output requirements (citations, uncertainty flags, themes)
5. Builds a comprehensive research prompt

**Why use it:** Research prompts need additional structure that general prompts don't—scope boundaries, source preferences, and explicit handling of uncertainty. This command ensures you don't miss critical research parameters.

**Example usage:**

```
/create-research-prompt
```

Or with a topic:

```
/create-research-prompt competitive analysis of AI coding assistants since 2023
```

---

### `improve-prompt.md` - Fix Existing Prompts

**Purpose:** Review and improve a prompt that isn't working as expected.

**What it does:**
1. Takes an existing prompt (from a file or pasted directly)
2. Understands what's going wrong (from your description or conversation context)
3. Analyzes structural and clarity issues
4. Applies targeted fixes while preserving original intent
5. Explains what changed and why (for complex fixes)

**Why use it:** When a prompt produces wrong formats, irrelevant responses, or misses the point, this command diagnoses the issue and fixes it without over-engineering.

**Example usage:**

```
/improve-prompt
```

Or with a file path:

```
/improve-prompt prompts/my-broken-prompt.md
```

**Tip:** If you've been discussing a problematic prompt in conversation, just run `/improve-prompt`—Claude will use the context to understand what needs fixing.

---

## Context-Aware Features

All prompt engineering commands are **context-aware**:

- They read your conversation history to avoid asking redundant questions
- They can reference your project files (`.claude/prd.md`, README, etc.) for context
- They infer and confirm rather than asking everything from scratch

This means if you've been discussing a feature and then run `/create-prompt`, Claude might say: "Based on our discussion about your authentication system, I'm assuming this prompt is for security-focused code review. Is that right?"
