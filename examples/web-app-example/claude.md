# Claude Context Blueprint - Task Manager Web App

Purpose: This is the main context file that tells the AI which documents to read, how to interpret their contents, and how to resolve conflicting instructions between them.  
It also ensures the AI understands the **feature-based workflow architecture**, where each feature (e.g., authentication, task management, notifications) is tracked and executed independently under `.claude/implementation/` and managed through `features.json`.

> Use this file as the central reference point for understanding project requirements, operating instructions, and autonomous development plans.

---

## Required Context Files

To fully understand the project requirements, my operating instructions, and the development plan, I must read the following files in this directory:

* **`prd.md`**: The Product Requirements Document, which details the features, UI/UX, and functional specifications for the task management web application. It also defines feature shortnames (e.g., `auth_flow`, `task_api`, `notifications_ui`) for inclusion in `features.json`.
* **`workflow.md`**: The development workflow, which outlines autonomous plan creation, feature-based versioning, and sequential implementation of React/Firebase modules. It includes installation steps, plan version control (`plan.v1.json`, `plan.v2.json`), and integration with Git.
* **`infra.md`**: The infrastructure documentation, which describes the React + Firebase architecture, deployment to Vercel, coding standards, and operational infrastructure requirements.
* **`security.md`**: The security documentation, which defines user authentication, session handling, data protection, and security best practices for handling user tasks and personal information.
* **`sbom.md`**: The Software Bill of Materials, which provides a complete list of React libraries, Firebase services, and external dependencies used in the project.
* **`tests.md`**: The testing documentation, which outlines Jest and React Testing Library strategies, component-level test cases, and QA standards for each feature plan.

I will always consult these files to ensure I have the most accurate and current project context before performing any planning or implementation action.

---

## Implementation Workspace

This project uses a **multi-feature autonomous workflow system** stored in `.claude/implementation/`.

**Structure:**
___
.claude/implementation/
├── features.json                 # Central registry of all features
├── auth_flow/                    # Authentication feature
│   ├── plan.v1.json
│   └── plan.v2.json
├── task_management/              # Core task handling feature
│   ├── plan.v1.json
│   └── plan.v2.json
└── notifications_ui/             # Notification and alerts feature
    ├── plan.v1.json
    └── plan.v2.json
___

**Purpose:**
- Each feature directory contains its own versioned plan defining implementation steps.  
- The `features.json` registry tracks creation dates, version numbers, and current status (`pending`, `in_progress`, `completed`).  
- This allows independent planning and deployment of distinct app modules (e.g., task CRUD logic, authentication, notifications).  

---

## Changelog Usage

* **`changelog.md`**: The project changelog tracks feature releases, version updates, and deployment summaries.  
  Each completed plan under `.claude/implementation/` must log its result in `changelog.md`, referencing the feature name and plan version (e.g., `feat(auth_flow): complete plan.v2.json`).

---

## Conflict Resolution Matrix

When instructions in different context files conflict, you **MUST** follow this order of precedence to ensure stable, safe, and consistent decision-making.

* **Priority 1 - Safety & Supply Chain:** **`security.md`** and **`sbom.md`** (User data protection & approved React/Firebase dependencies) — **Override all other documents.**
* **Priority 2 - Runtime Environment:** **`infra.md`** (React/Firebase/Vercel setup) — **Override** feature requests that conflict with architectural constraints.
* **Priority 3 - Global Conventions:** **`claude.md`** (This file - coding standards, workflow authority, and feature plan governance) — Defines baseline project and feature management rules.
* **Priority 4 - Feature Requirements:** **`prd.md`** (App features, UI/UX goals, and feature definitions) — May refine rules but **must not violate** higher-level constraints.
* **Priority 5 - Process & Workflow:** **`workflow.md`** (Plan creation, version management, and testing routines) — Governs plan execution order, error handling, and changelog updates.

---

### Conflict Resolution Process

If a conflict arises, you **MUST**:

1. **State the conflict clearly** — Identify the conflicting instructions and their source files.  
2. **Apply precedence** — Resolve according to the hierarchy above.  
3. **Recommend minimal edits** — Suggest the smallest viable change to harmonize instructions, starting with `prd.md` or `workflow.md`.  
4. **Flag impacted feature plans** — If the conflict affects a specific feature, mark its plan in `features.json` as `needs_review` before resuming execution.  
5. **Communicate changes** — Log any resulting plan or rule adjustments in `changelog.md` for auditability.