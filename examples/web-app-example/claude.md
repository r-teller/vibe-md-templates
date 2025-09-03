# Claude Context Blueprint - Task Manager Web App

Purpose: This is the main context file that tells the AI which documents to read and how to resolve conflicting instructions between them.

> Use this file to provide the master context for the project. This document serves as the central reference point for understanding project requirements, operating instructions, and development plans.

---

## Required Context Files

To fully understand the project requirements, my operating instructions, and the development plan, I must read the following files in this directory:

* **`prd.md`**: The Product Requirements Document, which details the features, UI/UX, and technical specifications for the task management web application.
* **`workflow.md`**: The development workflow, which includes critical interaction instructions for planning tasks and implementing those tasks. This also includes installation instructions and a detailed, step-by-step development process for building the React application.
* **`infra.md`**: The infrastructure documentation, which describes the React + Firebase architecture, deployment to Vercel, coding standards, and operational infrastructure requirements.
* **`security.md`**: The security documentation, which details user authentication, data protection, and security best practices for handling user tasks and personal data.
* **`sbom.md`**: The Software Bill of Materials, which provides a comprehensive inventory of all React libraries, Firebase services, and dependencies used in the project.
* **`tests.md`**: The testing documentation, which outlines Jest + React Testing Library strategies, user interaction test cases, and quality assurance procedures for the task management features.

I will always consult these files to ensure I have the most up-to-date information before proceeding with any task.

---

## Changelog Usage

Whenever I am asked about previous commits, or I need to understand previous changes that were made, or I need to create a new commit, I will consult the following file in this directory.

* **`changelog.md`**: The project changelog, which tracks version history, feature additions, bug fixes, and other important updates throughout the development lifecycle.

---

## Conflict Resolution Matrix

When instructions in different context files conflict, you **MUST** follow this order of precedence to resolve conflicts and ensure consistent decision-making.

* **Priority 1 - Safety & Supply Chain:** **`security.md`** and **`sbom.md`** (User data protection & approved React libraries) — **Override all other documents.**
* **Priority 2 - Runtime Environment:** **`infra.md`** (React/Firebase/Vercel architecture) — **Override** feature requests that are incompatible with the tech stack. You must surface these conflicts to the user for guidance.
* **Priority 3 - Global Conventions:** **`claude.md`** (This file - React coding standards) — Baseline project rules.
* **Priority 4 - Feature Requirements:** **`prd.md`** (Task management features) — May refine global rules but **must not violate** higher-level constraints. You must surface these conflicts to the user for guidance.
* **Priority 5 - Process & Workflow:** **`workflow.md`** (Git workflow and component development) — Governs plan creation and execution.

### Conflict Resolution Process

If you find a conflict, you **MUST**:
1. **State the conflict clearly** - Identify the specific conflicting instructions and their sources.
2. **Follow the precedence rule** - Apply the priority order defined above to resolve the conflict.
3. **Recommend minimal edits** - Suggest changes to harmonize the sources, starting with the lowest-authority document (`prd.md` or `workflow.md`).