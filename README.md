# Claude Code Starter Kit

A comprehensive collection of templates and prompts designed to help you get started with Claude Code quickly and effectively. This starter kit provides everything you need to set up AI-assisted software development workflows for any type of project.

## 🚀 Quick Start

**New to Claude Code?** Start here:

1. **Copy the templates** to your project directory
2. **Run the setup prompt** to customize templates for your project
3. **Start building** with Claude Code using your populated templates

```bash
# Copy templates to your project
cp -r templates/* /path/to/your/project/

# Use the interactive setup prompt
# Copy and paste the content of prompts/setup-project.prompt into Claude Code
```

## 📁 What's Included

### 🎯 Interactive Prompts (`/prompts/`)
- **`setup-project.prompt`** - Interactive onboarding to populate all templates
- **`create-prd.prompt`** - Guided Product Requirements Document creation

### 📋 Template Files (`/templates/`)
- **`claude.md`** - Master context file with conflict resolution rules
- **`prd.md`** - Product Requirements Document template
- **`infra.md`** - Infrastructure and technical architecture
- **`workflow.md`** - Development workflow and processes
- **`security.md`** - Security requirements and best practices
- **`sbom.md`** - Software Bill of Materials
- **`tests.md`** - Testing strategy and frameworks
- **`changelog.md`** - Version tracking and change history

### 📚 Documentation (`/docs/`)
- **`quick-start.md`** - 5-minute setup guide
- **`template-guide.md`** - Detailed explanation of each template

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
cp templates/* /your/project/directory/
```

### 2. Template System

These templates work together as a **context system** for Claude Code:

- **`claude.md`** acts as the master file that tells Claude Code which other files to read
- Each template serves a specific purpose in defining your project
- The conflict resolution system ensures consistent decision-making

### 3. Start Building

Once your templates are populated, Claude Code will use them to:
- Understand your project requirements
- Follow your preferred coding standards
- Implement features according to your specifications
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
- Development process and Git workflow
- Planning and execution procedures
- Quality assurance steps

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

**APIs and Services**
- Detail endpoints and data models in `prd.md`
- Use `infra.md` for scalability and performance requirements
- Emphasize authentication and rate limiting in `security.md`

### Adaptation Strategies

**Small Projects**
- Start with just `claude.md`, `prd.md`, and `workflow.md`
- Add other templates as your project grows
- Keep entries simple and focused

**Large Projects**
- Fully populate all templates from the start
- Consider creating additional specialized templates
- Use the conflict resolution system to manage complexity

**Team Projects**
- Involve team members in populating templates
- Use templates as living documentation
- Regularly review and update as requirements change

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