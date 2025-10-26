# Vibe MD Templates

A comprehensive collection of Markdown templates designed to streamline AI-assisted software development workflows. These templates provide structured documentation frameworks that help both developers and AI assistants understand project requirements, architecture, and implementation strategies.

## 🎯 Purpose

This repository contains a set of interconnected Markdown templates that serve as context files for AI development assistants (like Claude, ChatGPT, etc.). The templates are designed to:

- **Standardize project documentation** across different development scenarios
- **Enable autonomous AI development** by providing clear context and constraints
- **Facilitate consistent project setup** for students and indie developers
- **Support both local and cloud-based applications** with appropriate templates
- **Integrate feature-based planning and execution** through `.claude/implementation/` and `features.json`

## 📁 Template Structure

Each template serves a specific purpose in the development workflow:

| File              | Purpose                                                             | Priority |
| ----------------- | ------------------------------------------------------------------- | -------- |
| `claude.md`       | Master context file with conflict resolution rules                  | High     |
| `prd.md`          | Product Requirements Document - features and goals                  | High     |
| `infra.md`        | Infrastructure and technical foundation                             | High     |
| `workflow.md`     | Development workflow, feature-based planning, and execution process | High     |
| `security.md`     | Security requirements and best practices                            | Medium   |
| `sbom.md`         | Software Bill of Materials - approved dependencies                  | Medium   |
| `tests.md`        | Testing strategy and frameworks                                     | Low      |
| `changelog.md`    | Version history and change tracking                                 | Low      |
| `first_prompt.md` | Interactive setup guide for populating templates                    | Utility  |

## 🚀 Quick Start

1. **Clone or download** this repository
2. **Copy the templates** to your new project directory
3. **Run the interactive setup** by following the `first_prompt.md` guide
4. **Initialize feature workspace** — Claude Code will create `.claude/implementation/` and `features.json` for tracking
5. **Customize each template** with your project-specific information
6. **Use with your AI assistant** to build and manage features

### Example Usage

```bash
# Create a new project directory
mkdir my-awesome-app
cd my-awesome-app

# Copy the templates
cp /path/to/vibe-md-templates/*.md .

# Follow the first_prompt.md guide to populate the templates
# The setup will initialize `.claude/implementation/` and `features.json`
# Then use with your AI assistant to build and manage feature plans
```

## 🎨 Template Features

### Conflict Resolution System

The templates include a sophisticated conflict resolution matrix that ensures AI assistants make consistent decisions when different documentation sources conflict.

### Feature-Based Planning

The new workflow supports multiple autonomous feature plans:

- Each feature has its own plan file (`plan.v1.json`, `plan.v2.json`, etc.)
- Plans are stored under `.claude/implementation/{feature}/`
- All active features are tracked in `features.json`

### Technology Agnostic

Templates work with any programming language or framework:

- **Local Applications**: Python scripts, desktop apps, CLI tools
- **Web Applications**: Next.js, React, Vue, vanilla JavaScript
- **Mobile Applications**: React Native, Flutter, native development
- **Backend Services**: Node.js, Python, Go, Rust

### Security-First Approach

Built-in security considerations and best practices for:

- Secret management
- Dependency security
- Authentication and authorization
- Data sensitivity classification

## 📋 Template Details

### Core Templates (Required)

**`claude.md`** - The master context file that:

- Lists all required context files
- Defines conflict resolution precedence
- Establishes global project conventions

**`prd.md`** - Product Requirements Document that captures:

- Project goals and user stories
- Feature specifications
- UI/UX requirements
- Scope limitations
- Identifies initial feature shortnames to be tracked in `features.json`

**`infra.md`** - Infrastructure documentation covering:

- Technology stack and frameworks
- Development environment setup
- Deployment architecture
- Data storage strategies

**`workflow.md`** - Development process that defines:

- Plan creation and execution
- Feature-based implementation tracking in `.claude/implementation/{feature}/`
- Versioned plan management via `plan.v*.json` files
- Git commit workflows
- Self-optimization routines
- Error handling and recovery procedures

### Supporting Templates (Recommended)

**`security.md`** - Security framework including:

- Data sensitivity classification
- Authentication methods
- Dependency security policies
- Secrets management

**`sbom.md`** - Software Bill of Materials with:

- Approved technology stack
- Version management strategy
- Documentation links
- Update policies

**`tests.md`** - Testing strategy covering:

- Testing philosophy and goals
- Framework selection
- Key test scenarios
- Quality assurance processes

**`changelog.md`** - Version tracking with:

- Semantic versioning rules
- Change categorization
- Release notes format

## 🛠️ Customization

Each template includes:

- **Clear placeholders** for project-specific information
- **Example content** for common scenarios
- **Guided questions** to help populate fields
- **Best practice recommendations**
- **Integration-ready structure** for autonomous workflow plans

## 🤝 Contributing

We welcome contributions! Please:

1. **Fork the repository**
2. **Create a feature branch**
3. **Make your improvements**
4. **Submit a pull request**

### Areas for Contribution

- Additional template variants for specific frameworks
- More example scenarios and use cases
- Improved conflict resolution rules
- Additional security best practices
- Testing strategy enhancements
- Enhancements for feature-based planning and workflow automation

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by the need for consistent AI-assisted development workflows
- Built for the developer community to streamline project setup
- Designed to work with various AI assistants and development tools
- Updated to support multi-feature planning, version tracking, and autonomous execution

## 📞 Support

If you have questions or need help:

1. **Check the examples** in each template file
2. **Review the first_prompt.md** interactive setup guide
3. **Open an issue** for bugs or feature requests
4. **Start a discussion** for questions or ideas

---

**Happy coding! 🚀**

_These templates are designed to make AI-assisted development more consistent, secure, and feature-driven. Use them as a foundation and customize them to fit your specific project needs._
