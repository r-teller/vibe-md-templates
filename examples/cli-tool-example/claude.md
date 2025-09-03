# Claude Context Blueprint - File Organizer CLI Tool

Purpose: This is the main context file that tells the AI which documents to read and how to resolve conflicting instructions between them.

---

## Required Context Files

To fully understand the project requirements, my operating instructions, and the development plan, I must read the following files in this directory:

* **`prd.md`**: The Product Requirements Document, which details the features, command-line interface, and specifications for the file organization CLI tool.
* **`workflow.md`**: The development workflow, which includes critical interaction instructions for planning tasks and implementing the Python CLI application with proper testing and distribution.
* **`infra.md`**: The infrastructure documentation, which describes the Python development setup, packaging with Poetry, and distribution via PyPI.
* **`security.md`**: The security documentation, which details file system security, input validation, and safe file operations.
* **`sbom.md`**: The Software Bill of Materials, which provides a comprehensive inventory of all Python dependencies and CLI libraries used in the project.
* **`tests.md`**: The testing documentation, which outlines pytest strategies, file operation test cases, and quality assurance procedures for the CLI functionality.

I will always consult these files to ensure I have the most up-to-date information before proceeding with any task.

---

## Changelog Usage

* **`changelog.md`**: The project changelog, which tracks version history, feature additions, bug fixes, and CLI improvements throughout the development lifecycle.

---

## Conflict Resolution Matrix

When instructions in different context files conflict, you **MUST** follow this order of precedence:

* **Priority 1 - Safety & Supply Chain:** **`security.md`** and **`sbom.md`** (File system safety & approved Python libraries) — **Override all other documents.**
* **Priority 2 - Runtime Environment:** **`infra.md`** (Python/Poetry/PyPI setup) — **Override** feature requests that are incompatible with the tech stack.
* **Priority 3 - Global Conventions:** **`claude.md`** (This file - Python coding standards) — Baseline project rules.
* **Priority 4 - Feature Requirements:** **`prd.md`** (CLI features and commands) — May refine global rules but **must not violate** higher-level constraints.
* **Priority 5 - Process & Workflow:** **`workflow.md`** (Development and testing process) — Governs plan creation and execution.

### Conflict Resolution Process

If you find a conflict, you **MUST**:
1. **State the conflict clearly** - Identify the specific conflicting instructions and their sources.
2. **Follow the precedence rule** - Apply the priority order defined above to resolve the conflict.
3. **Recommend minimal edits** - Suggest changes to harmonize the sources, starting with the lowest-authority document.