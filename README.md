# Claude Code Starter Kit

**Get productive with Claude Code in minutes.** This starter kit gives you ready-to-use templates that help Claude Code understand your project and work more effectively.

## What This Does

When you use Claude Code, it works best when it understands your project's context—what you're building, how you want to work, and what standards to follow. This kit provides:

- **Templates** that teach Claude Code about your project
- **Slash commands** for common workflows (start session, wrap up, create stories)
- **Issue tracking** via [Beads](https://github.com/steveyegge/beads) to manage work items

**Before:** You explain your project context every session.
**After:** Claude Code reads your templates and already knows how to help.

---

## Quick Start

### Step 1: Install the Tools

**Claude Code** (pick one method):

```bash
# Option A: Native binary (recommended)
curl -fsSL https://claude.ai/install.sh | bash

# Option B: npm
npm install -g @anthropic-ai/claude-code
```

**Beads** (issue tracking):

```bash
npm install -g beads-ts
```

Verify both are installed:

```bash
claude --version
bd --version
```

### Step 2: Set Up Your Project

```bash
# 1. Create a .claude folder in your project
mkdir -p /path/to/your/project/.claude

# 2. Copy the templates
cp templates/*.md /path/to/your/project/.claude/

# 3. Initialize beads for issue tracking
cd /path/to/your/project
bd quickstart

# 4. (Optional) Set up Claude Code hooks for automatic context
bd setup claude
```

### Step 3: Customize Your Templates

Open Claude Code in your project and paste the setup prompt:

```bash
cd /path/to/your/project
claude

# Then paste the contents of prompts/setup-project.prompt
```

Claude Code will walk you through customizing each template for your project.

---

## What's in the Kit

```
├── templates/          # Core context files for Claude Code
│   ├── claude.md       # Master file - tells Claude which files to read
│   ├── prd.md          # Product requirements (what you're building)
│   ├── workflow.md     # How you work (branching, PRs, issue tracking)
│   ├── infra.md        # Tech stack and architecture
│   ├── security.md     # Security requirements
│   ├── tests.md        # Testing strategy
│   ├── sbom.md         # Approved dependencies
│   └── changelog.md    # Version history
│
├── commands/           # Slash commands for Claude Code
│   ├── gogogo.md       # /gogogo - Start a work session
│   ├── wrapup.md       # /wrapup - End session, commit, sync
│   └── story.md        # /story - Create a new user story
│
├── prompts/            # Interactive setup helpers
│   ├── setup-project.prompt    # Full project setup wizard
│   ├── create-prd.prompt       # PRD creation helper
│   └── create-command.prompt   # Custom command creator
│
├── docs/               # Detailed guides
└── examples/           # Sample project setups
    ├── web-app-example/
    └── cli-tool-example/
```

---

## How It Works

### The Template System

Your `.claude/` folder contains markdown files that Claude Code reads for context:

| File | Purpose |
|------|---------|
| `claude.md` | **Control center** - Lists which files Claude should read and in what priority |
| `prd.md` | **What you're building** - Features, user stories, requirements |
| `workflow.md` | **How you work** - Git workflow, PR process, issue tracking with beads |
| `infra.md` | **Tech decisions** - Stack, architecture, deployment |

When you start Claude Code, it reads these files and understands your project without you having to explain it.

### Issue Tracking with Beads

Beads is a lightweight CLI for tracking work items. It integrates with your git workflow:

```bash
# Create an issue
bd create "Add user login" --type feature

# See what's ready to work on
bd ready

# Start working on something
bd update ABC-1 --status in_progress

# Mark it done
bd close ABC-1
```

The `/gogogo` and `/wrapup` slash commands automatically check and update beads status.

### Slash Commands

After setup, use these commands in Claude Code:

| Command | What it does |
|---------|--------------|
| `/gogogo` | Loads context, checks git status, shows ready work items |
| `/wrapup` | Commits changes, updates beads, creates handoff notes |
| `/story` | Creates a new user story in your PRD |

---

## Getting Started by Project Size

### Small Projects

Start minimal—you can always add more later:

1. Copy just `claude.md`, `prd.md`, and `workflow.md`
2. Run `bd quickstart`
3. Create your first issue: `bd create "Build MVP" --type feature`

### Larger Projects

Use all templates from the start:

1. Copy all templates to `.claude/`
2. Run through the full `setup-project.prompt`
3. Create an epic with child issues:
   ```bash
   bd create "User Authentication" --type epic
   bd create "Login endpoint" --type feature --parent AUTH-1
   bd create "Password reset" --type feature --parent AUTH-1
   ```

### Team Projects

Add coordination features:

```bash
# Assign work
bd update ABC-1 --assignee "alice"

# Track who did what (for multi-agent setups)
bd update ABC-1 --status in_progress --actor "claude-1"
```

---

## Common Beads Commands

| Command | Description |
|---------|-------------|
| `bd quickstart` | Initialize beads in your project |
| `bd create "title" --type feature` | Create an issue (types: bug, feature, task, epic, chore) |
| `bd list` | Show all issues |
| `bd ready` | Show issues ready to work on (no blockers) |
| `bd update <id> --status in_progress` | Start working on an issue |
| `bd close <id>` | Mark an issue complete |
| `bd show <id>` | View issue details |

See the [Beads documentation](https://github.com/steveyegge/beads) for the full command reference.

---

## Customization Tips

### For Web Apps
- Focus on `prd.md` for user experience details
- Use `security.md` for authentication and data protection
- Detail deployment in `infra.md`

### For CLI Tools
- Keep `prd.md` focused on command design
- Track each command as a beads issue with `--parent` for hierarchy
- Focus `security.md` on input validation

### For APIs
- Document endpoints in `prd.md`
- Emphasize rate limiting and auth in `security.md`
- Detail scaling requirements in `infra.md`

---

## Troubleshooting

**Claude Code doesn't seem to read my templates**
- Make sure templates are in `.claude/` folder (not `.claude/templates/`)
- Check that `claude.md` lists the other files correctly

**Beads commands not working**
- Verify installation: `bd --version`
- Make sure you ran `bd quickstart` in your project folder
- Check that `.beads/` folder exists in your project

**Slash commands not found**
- Copy command files to `.claude/commands/` in your project
- Restart Claude Code after adding commands

---

## Contributing

We welcome improvements! To contribute:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

Ideas: More example projects, framework-specific templates, improved prompts.

---

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Beads Issue Tracker](https://github.com/steveyegge/beads)
- [Examples](/examples) - Sample project setups
- [Detailed Guides](/docs) - In-depth documentation

## License

MIT License - free to use, modify, and distribute.
