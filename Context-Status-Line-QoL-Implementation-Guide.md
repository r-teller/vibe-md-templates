# Claude Code Status Line Implementation Guide

## Overview

This guide documents how to add a persistent context usage status line to Claude Code CLI. The status line displays real-time token usage with color-coded warnings.

**Scope:** User-level configuration - applies to ALL Claude Code sessions across all projects.

---

## What You Get

A persistent status bar at the bottom of your terminal showing:

```
Claude Opus 4.5 | Used: 20k/200k | 90% free | in:3k cache:16k out:1k
```

**Color coding:**
- **Green:** >40% free (comfortable)
- **Yellow:** 20-40% free (getting tight)
- **Red + Bold:** <20% free (danger zone, autocompact imminent)

---

## Implementation Steps

### Step 1: Create the Status Line Script

Create file `~/.claude/statusline.sh`:

```bash
#!/bin/bash
# Claude Code Status Line - Enhanced with colors
#
# TO REMOVE THIS FEATURE:
# 1. Delete this file: rm ~/.claude/statusline.sh
# 2. Remove "statusLine" block from ~/.claude/settings.json
#

input=$(cat)

# Parse JSON values
MODEL=$(echo "$input" | jq -r '.model.display_name // "Unknown"')
CONTEXT_SIZE=$(echo "$input" | jq -r '.context_window.context_window_size // 0')
USAGE=$(echo "$input" | jq '.context_window.current_usage // null')

# ANSI color codes
RESET="\033[0m"
DIM="\033[2m"
BOLD="\033[1m"
GREEN="\033[32m"
YELLOW="\033[33m"
RED="\033[31m"
CYAN="\033[36m"

if [ "$USAGE" != "null" ] && [ "$CONTEXT_SIZE" != "0" ]; then
    # Extract token breakdown
    INPUT=$(echo "$USAGE" | jq '.input_tokens // 0')
    CACHE_CREATE=$(echo "$USAGE" | jq '.cache_creation_input_tokens // 0')
    CACHE_READ=$(echo "$USAGE" | jq '.cache_read_input_tokens // 0')
    OUTPUT=$(echo "$USAGE" | jq '.output_tokens // 0')

    # Calculate totals
    CURRENT=$((INPUT + CACHE_CREATE + CACHE_READ))
    FREE=$((CONTEXT_SIZE - CURRENT))
    FREE_K=$((FREE / 1000))
    TOTAL_K=$((CONTEXT_SIZE / 1000))
    CURRENT_K=$((CURRENT / 1000))
    PERCENT_FREE=$((FREE * 100 / CONTEXT_SIZE))

    # Choose color based on free percentage
    if [ "$PERCENT_FREE" -lt 20 ]; then
        FREE_COLOR="${RED}${BOLD}"
    elif [ "$PERCENT_FREE" -lt 40 ]; then
        FREE_COLOR="${YELLOW}"
    else
        FREE_COLOR="${GREEN}"
    fi

    # Format: Model | Used/Total | Free % | Breakdown
    printf "${DIM}${CYAN}%s${RESET} ${DIM}|${RESET} " "$MODEL"
    printf "${DIM}Used:${RESET} %dk/%dk " "$CURRENT_K" "$TOTAL_K"
    printf "${DIM}|${RESET} ${FREE_COLOR}%d%% free${RESET} " "$PERCENT_FREE"
    printf "${DIM}| in:%dk cache:%dk out:%dk${RESET}" "$((INPUT/1000))" "$(((CACHE_CREATE+CACHE_READ)/1000))" "$((OUTPUT/1000))"
else
    printf "${DIM}${CYAN}%s${RESET} ${DIM}| Context: Ready${RESET}" "$MODEL"
fi
```

### Step 2: Make Script Executable

```bash
chmod +x ~/.claude/statusline.sh
```

### Step 3: Update Claude Code Settings

Add the `statusLine` block to `~/.claude/settings.json`:

```json
{
  "statusLine": {
    "type": "command",
    "command": "~/.claude/statusline.sh",
    "padding": 0
  }
}
```

**If you already have settings**, merge the `statusLine` block with your existing config:

```json
{
  "statusLine": {
    "type": "command",
    "command": "~/.claude/statusline.sh",
    "padding": 0
  },
  "hooks": {
    ...your existing hooks...
  }
}
```

### Step 4: Restart Claude Code

Start a new Claude Code session to see the status line.

---

## One-Liner Installation

For quick setup, run this compound command:

```bash
cat > ~/.claude/statusline.sh << 'SCRIPT'
#!/bin/bash
input=$(cat)
MODEL=$(echo "$input" | jq -r '.model.display_name // "Unknown"')
CONTEXT_SIZE=$(echo "$input" | jq -r '.context_window.context_window_size // 0')
USAGE=$(echo "$input" | jq '.context_window.current_usage // null')
RESET="\033[0m"; DIM="\033[2m"; BOLD="\033[1m"
GREEN="\033[32m"; YELLOW="\033[33m"; RED="\033[31m"; CYAN="\033[36m"
if [ "$USAGE" != "null" ] && [ "$CONTEXT_SIZE" != "0" ]; then
    INPUT=$(echo "$USAGE" | jq '.input_tokens // 0')
    CACHE_CREATE=$(echo "$USAGE" | jq '.cache_creation_input_tokens // 0')
    CACHE_READ=$(echo "$USAGE" | jq '.cache_read_input_tokens // 0')
    OUTPUT=$(echo "$USAGE" | jq '.output_tokens // 0')
    CURRENT=$((INPUT + CACHE_CREATE + CACHE_READ))
    FREE=$((CONTEXT_SIZE - CURRENT))
    PERCENT_FREE=$((FREE * 100 / CONTEXT_SIZE))
    if [ "$PERCENT_FREE" -lt 20 ]; then FREE_COLOR="${RED}${BOLD}"
    elif [ "$PERCENT_FREE" -lt 40 ]; then FREE_COLOR="${YELLOW}"
    else FREE_COLOR="${GREEN}"; fi
    printf "${DIM}${CYAN}%s${RESET} ${DIM}|${RESET} " "$MODEL"
    printf "${DIM}Used:${RESET} %dk/%dk " "$((CURRENT/1000))" "$((CONTEXT_SIZE/1000))"
    printf "${DIM}|${RESET} ${FREE_COLOR}%d%% free${RESET} " "$PERCENT_FREE"
    printf "${DIM}| in:%dk cache:%dk out:%dk${RESET}" "$((INPUT/1000))" "$(((CACHE_CREATE+CACHE_READ)/1000))" "$((OUTPUT/1000))"
else
    printf "${DIM}${CYAN}%s${RESET} ${DIM}| Context: Ready${RESET}" "$MODEL"
fi
SCRIPT
chmod +x ~/.claude/statusline.sh
```

Then manually add the `statusLine` block to your `~/.claude/settings.json`.

---

## Uninstallation

To remove the status line feature:

```bash
# Remove the script
rm ~/.claude/statusline.sh

# Remove statusLine block from settings.json (manual edit)
# Or use this sed command (macOS):
sed -i '' '/statusLine/,/^  },/d' ~/.claude/settings.json
```

---

## Requirements

- **jq**: JSON processor (install via `brew install jq` on macOS)
- **Claude Code CLI**: v2.1.0 or later (statusLine feature)
- **Bash**: Standard shell

---

## How It Works

1. Claude Code calls your script every 300ms with JSON payload via stdin
2. Script parses the JSON for context window stats
3. Script outputs formatted, colorized text
4. Claude Code displays the output as a persistent status bar

**Available JSON fields:**
- `.model.display_name` - Current model name
- `.context_window.context_window_size` - Total context window tokens
- `.context_window.current_usage.input_tokens` - Input tokens used
- `.context_window.current_usage.output_tokens` - Output tokens used
- `.context_window.current_usage.cache_creation_input_tokens` - Cache creation tokens
- `.context_window.current_usage.cache_read_input_tokens` - Cache read tokens

---

## Customization Ideas

**Minimal version** (just percentage):
```bash
printf "%d%% free" "$PERCENT_FREE"
```

**Add session cost** (if available):
```bash
COST=$(echo "$input" | jq -r '.session.cost // "N/A"')
printf "Cost: $%s" "$COST"
```

**Different color thresholds:**
```bash
# More aggressive warnings
if [ "$PERCENT_FREE" -lt 30 ]; then ...
```

---

## Notes

- **Applies globally**: This config lives in `~/.claude/` so it works for all projects
- **No autocompact control**: The autocompact threshold cannot be configured
- **Performance**: Script runs every 300ms; keep it lightweight
