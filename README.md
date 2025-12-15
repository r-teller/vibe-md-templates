# Claude Code Starter Kit

A comprehensive collection of templates and prompts designed to help you get started with Claude Code quickly and effectively. This starter kit provides everything you need to set up AI-assisted software development workflows for any type of project.

## 🚀 Quick Start

**New to Claude Code?** Start here:

1. **Copy the templates** to your project directory
2. **Run the setup prompt** to customize templates for your project
3. **Initialize the feature workspace** — Claude Code will create a `.claude/implementation/` directory and `features.json` registry for plan tracking
4. **Start building** with Claude Code using your populated templates

```bash
# Copy templates to your project
cp -r templates/* /path/to/your/project/.claude

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
- **`workflow.md`** - Defines development workflow, including autonomous feature planning, versioned execution, and tracking via `.claude/implementation/`
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
- **`workflow.md`** manages feature-based plan creation, stored under `.claude/implementation/`, and tracks progress in `features.json`
- Each template serves a specific purpose in defining your project
- The conflict resolution system ensures consistent decision-making

### 3. Start Building

Once your templates are populated, Claude Code will use them to:

- Understand your project requirements
- Register features in `features.json`
- Autonomously execute versioned implementation plans under `.claude/implementation/{feature}/`
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

- Defines how plans are created and executed
- Manages autonomous feature implementation in `.claude/implementation/{feature}/plan.v*.json`
- Tracks all features in `features.json`
- Outlines error handling, self-optimization, and changelog integration

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
- Each command or module can be represented as its own feature plan in `.claude/implementation/`

**APIs and Services**

- Detail endpoints and data models in `prd.md`
- Use `infra.md` for scalability and performance requirements
- Emphasize authentication and rate limiting in `security.md`

### Adaptation Strategies

**Small Projects**

- Start with just `claude.md`, `prd.md`, and `workflow.md`
- Use the setup prompt to create your first feature plan (e.g., `core_api` or `auth_flow`)
- Additional features can be added later via new entries in `features.json`

**Large Projects**

- Fully populate all templates from the start
- Create multiple feature plans under `.claude/implementation/`
- Use versioning (`plan.v1.json`, `plan.v2.json`, etc.) to refine implementation

**Team Projects**

- Assign features to contributors via `features.json`
- Treat plan files as self-contained development roadmaps
- Regularly review and merge feature progress through `workflow.md`

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
