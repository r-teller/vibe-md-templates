# Claude Context Blueprint - File Organizer CLI Tool

Purpose: This is the main context file that tells the AI which documents to read, how to interpret their contents, and how to resolve conflicting instructions between them.  
It also ensures the AI understands the **feature-based workflow architecture** introduced in the updated system, where each feature is managed under `.claude/implementation/` and tracked via `features.json`.

---

## Required Context Files

To fully understand the project requirements, my operating instructions, and the development plan, I must read the following files in this directory:

- **`prd.md`**: The Product Requirements Document, which details the features, user stories, and command-line specifications for the file organization CLI tool. It also defines the initial feature shortnames to be registered in `features.json`.
- **`workflow.md`**: The development workflow, which includes the autonomous plan creation, versioned feature management, and sequential task execution for implementing the Python CLI application with proper testing and distribution.
- **`infra.md`**: The infrastructure documentation, which describes the Python development setup, packaging with Poetry, and distribution via PyPI.
- **`security.md`**: The security documentation, which details file system security, input validation, and safe file operations.
- **`sbom.md`**: The Software Bill of Materials, which provides a comprehensive inventory of all Python dependencies and CLI libraries used in the project.
- **`tests.md`**: The testing documentation, which outlines pytest strategies, file operation test cases, and quality assurance procedures for the CLI functionality.

I will always consult these files to ensure I have the most up-to-date information before proceeding with any implementation or plan execution.

---

## Implementation Workspace

This project uses a **feature-based autonomous workflow system** stored in `.claude/implementation/`.

**Structure:**

---

.claude/implementation/
├── features.json # Registry of all tracked features
├── file_sorting/ # Example feature directory
│ ├── plan.v1.json
│ └── plan.v2.json
└── metadata_parser/
├── plan.v1.json
└── plan.v2.json

---

**Purpose:**

- Each feature has its own versioned plan (`plan.v*.json`) that defines execution steps.
- The `features.json` file tracks global feature states (`pending`, `in_progress`, `completed`).
- This ensures independent planning and execution for each component of the CLI tool (e.g., file sorting, metadata extraction, config parsing).

---

## Changelog Usage

- **`changelog.md`**: The project changelog, which tracks version history, feature additions, bug fixes, and CLI improvements throughout the development lifecycle.  
  Each completed plan should append an entry summarizing the feature’s implementation and version tag.

---

## Conflict Resolution Matrix

When instructions in different context files conflict, you **MUST** follow this order of precedence:

- **Priority 1 - Safety & Supply Chain:** **`security.md`** and **`sbom.md`** (File system safety & approved Python libraries) — **Override all other documents.**
- **Priority 2 - Runtime Environment:** **`infra.md`** (Python/Poetry/PyPI setup) — **Override** feature requests that are incompatible with the tech stack.
- **Priority 3 - Global Conventions:** **`claude.md`** (This file - coding standards and workflow authority) — Defines core rules for multi-feature management.
- **Priority 4 - Feature Requirements:** **`prd.md`** (CLI features, commands, and feature definitions) — May refine global rules but **must not violate** higher-level constraints.
- **Priority 5 - Process & Workflow:** **`workflow.md`** (Development and testing process) — Governs plan creation, feature execution order, and changelog updates.

---

### Conflict Resolution Process

If a conflict arises, you **MUST**:

1. **State the conflict clearly** — Identify the specific conflicting instructions and their source files.
2. **Apply precedence** — Use the matrix above to determine which rule or instruction governs.
3. **Recommend minimal edits** — Suggest changes to harmonize lower-priority documents first (e.g., `workflow.md` or `prd.md`), keeping the project’s structure consistent across all plans.
4. **Update affected feature plans** — If the conflict affects a specific feature, mark its plan as `needs_review` in `features.json` and pause execution until resolved.
