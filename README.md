# Claude Code Starter Kit

A comprehensive collection of templates and prompts designed to help you get started with Claude Code quickly and effectively. This starter kit provides everything you need to set up AI-assisted software development workflows for any type of project.

## 📦 Dependencies

This starter kit requires the following tools to be installed:

### Claude Code

Claude Code is Anthropic's official CLI for AI-assisted development.

```bash
# Install Claude Code globally
npm install -g @anthropic-ai/claude-code

# Verify installation
claude --version
```

For more information, see the [Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code).

### Beads

Beads is a lightweight issue tracking CLI designed for AI-agent workflows. It provides local-first issue management with support for priorities, dependencies, labels, and multi-agent coordination.

```bash
# Install beads globally
npm install -g beads-ts

# Verify installation
bd --version

# Initialize beads in your project
bd quickstart
```

For more information, see the [beads GitHub repository](https://github.com/r-teller/beads).

#### Key Beads Commands

| Command | Description |
|---------|-------------|
| `bd quickstart` | Initialize beads in a new project |
| `bd create "title" --type feature` | Create a new issue |
| `bd list` | List all issues |
| `bd ready --json` | Get unblocked work as structured data |
| `bd update <id> --status in_progress` | Update issue status |
| `bd close <id>` | Close a completed issue |
| `bd setup claude` | Install Claude Code hooks for automatic context |

## 🚀 Quick Start

**New to Claude Code?** Start here:

1. **Install dependencies** — Ensure Claude Code and beads are installed (see [Dependencies](#-dependencies))
2. **Copy the templates** to your project directory
3. **Run the setup prompt** to customize templates for your project
4. **Initialize beads** — Run `bd quickstart` to set up issue tracking for your project
5. **Start building** with Claude Code using your populated templates

```bash
# Copy templates to your project
cp -r templates/*.md /path/to/your/project/.claude

# Initialize beads for issue tracking
bd quickstart

# Use the interactive setup prompt
# Copy and paste the content of prompts/setup-project.prompt into Claude Code
```

## 📁 What's Included

### 🎯 Interactive Prompts (`/prompts/`)

- **`setup-project.prompt`** - Interactive onboarding to populate all templates
- **`create-prd.prompt`** - Guided Product Requirements Document creation
- **`create-command.prompt`** -  Guided custom slash commands creation

### 📋 Template Files (`/templates/`)

- **`claude.md`** - Master context file with conflict resolution rules
- **`prd.md`** - Product Requirements Document template
- **`infra.md`** - Infrastructure and technical architecture
- **`workflow.md`** - Defines development workflow, including beads-based issue tracking, branching strategy, and PR workflows
- **`security.md`** - Security requirements and best practices
- **`sbom.md`** - Software Bill of Materials
- **`tests.md`** - Testing strategy and frameworks
- **`changelog.md`** - Version tracking and change history

### 📚 Documentation (`/docs/`)

- **`commands-guide.md`** - Guide to creating custom slash commands
- **`quick-start.md`** - 5-minute setup guide
- **`template-guide.md`** - Detailed explanation of each template

### 🔧 Commands (`/commands/`)

- **`gogogo.md`** - Session startup command - load context, check git, and prepare for work
- **`wrapup.md`** - Session wrap-up command - commit changes, update docs, and create handoff
- **`story.md`** - Slash command to create a new story in your `prd.md`

### 💡 Examples (`/examples/`)

- **`web-app-example/`** - Complete web application project setup
- **`cli-tool-example/`** - Command-line tool project setup

## 🎯 How It Works

### 1. Choose Your Approach

**🤖 Guided Setup (Recommended for beginners)**  
Use the interactive prompts to have Claude Code walk you through the entire setup process:

```bash
# Copy the setup prompt content and paste into Claude Code
cat prompts/setup-project.prompt
```

**⚡ Manual Setup (For experienced users)**  
Copy the templates directly and customize them yourself:

```bash
# Copy all templates to your project
cp templates/* /your/project/directory/.claude
```

### 2. Template System

These templates work together as a **context system** for Claude Code:

- **`claude.md`** acts as the master file that tells Claude Code which other files to read
- **`workflow.md`** manages issue-based planning with beads (`bd`), tracking work through priorities, dependencies, and status updates
- Each template serves a specific purpose in defining your project
- The conflict resolution system ensures consistent decision-making

### 3. Start Building

Once your templates are populated, Claude Code will use them to:

- Understand your project requirements
- Create and track issues with beads (`bd create`, `bd update`, `bd close`)
- Autonomously execute work items with full dependency and priority management
- Follow your preferred coding standards
- Maintain security and quality standards

## 📖 Template Guide

### Core Templates (Required)

**`claude.md`** - The control center

- Lists all context files Claude Code should read
- Defines priority order for conflicting instructions
- Sets global project conventions

**`prd.md`** - Your project blueprint

- Project goals and target users
- Feature specifications as user stories
- UI/UX requirements and design guidelines

**`infra.md`** - Technical foundation

- Technology stack and framework choices
- Development environment setup
- Deployment and hosting architecture

**`workflow.md`** - How you work

- Defines issue creation and execution with beads (`bd`)
- Manages work tracking with priorities, dependencies, and labels
- Includes branching strategy and PR workflow with beads references
- Outlines error handling, self-optimization, and multi-agent coordination

### Supporting Templates (Recommended)

**`security.md`** - Keep it safe

- Data sensitivity classification
- Authentication and authorization
- Secrets management and best practices

**`sbom.md`** - Dependency management

- Approved libraries and versions
- Update policies and security scanning
- License compatibility tracking

**`tests.md`** - Quality assurance

- Testing philosophy and strategy
- Framework selection and setup
- Key test scenarios and coverage goals

**`changelog.md`** - Track your progress

- Version numbering strategy
- Change categorization system
- Release notes formatting

## 🛠️ Customization Tips

### For Different Project Types

**Web Applications**

- Focus on `prd.md` for user experience details
- Use `infra.md` for deployment and scaling concerns
- Emphasize security in `security.md` for user data protection

**CLI Tools**

- Keep `prd.md` focused on command-line interface design
- Use `infra.md` for distribution and installation
- Focus on input validation in `security.md`
- Each command or module can be tracked as separate beads issues with `--parent` for hierarchy

**APIs and Services**

- Detail endpoints and data models in `prd.md`
- Use `infra.md` for scalability and performance requirements
- Emphasize authentication and rate limiting in `security.md`

### Adaptation Strategies

**Small Projects**

- Start with just `claude.md`, `prd.md`, and `workflow.md`
- Run `bd quickstart` and create your first issues (e.g., `bd create "Implement core API" --type feature`)
- Additional work items can be added anytime with `bd create`

**Large Projects**

- Fully populate all templates from the start
- Create epics with child issues using `bd create --parent` for hierarchy
- Use labels and priorities to organize work across multiple features

**Team Projects**

- Assign work to contributors with `bd update --assignee`
- Use `--actor` flags for multi-agent coordination and audit trails
- Track progress with `bd list --assignee` and `bd ready`

## 🤝 Contributing

We welcome improvements and additions! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Ideas for Contributions

- Additional template variants for specific frameworks
- More example projects and use cases
- Improved prompts and user guidance
- Better conflict resolution rules

## 📄 License

MIT License - feel free to use, modify, and distribute.

## 💬 Support

- Check the `/docs/` folder for detailed guides
- Review the `/examples/` for inspiration
- Open an issue for bugs or feature requests
- Start a discussion for questions or ideas

---

**Ready to start building with Claude Code?** 🚀

Copy the templates, run through the setup prompts, and start creating amazing software with AI assistance that truly understands your project!
