# Development Workflow Blueprint

Purpose: This file explains the step-by-step process the AI will follow to autonomously build and implement the project features.

> Use this file to outline the development workflow and execution process for your project. This guide ensures consistent implementation practices and helps your AI assistant understand how to systematically build and maintain your application.

<!-- Don’t worry if this feels advanced. The AI handles most of this automatically.-->

---

## 1. Plan Creation Process

This section describes how development plans are created and structured for systematic implementation.

When the user requests to implement the application or a new feature, I will perform the following steps:

1. **Create the base directory**:  
   If it does not already exist, I will create a directory named `.claude/implementation` in the project root.

2. **Determine feature name**:  
   Generate a concise, lowercase feature shortname (e.g., `auth_tests`, `contacts_api`, `docker_setup`).

3. **Update feature registry**:  
   I will create or update a file named `features.json` in `.claude/implementation`.  
   This registry tracks all active features and their current versions.  
   Example:
   ```json
   {
     "auth_tests": {
       "shortname": "auth_tests",
       "description": "Implement comprehensive pytest test suite for authentication endpoints",
       "created_at": "2025-01-25T10:30:00Z",
       "updated_at": "2025-01-25T10:30:00Z",
       "current_version": "v1",
       "status": "pending"
     }
   }
   ```

4. **Create feature directory**:  
   For each feature, create a dedicated directory under `.claude/implementation/{feature_shortname}/`.

5. **Determine plan version**:  
   - If first time: `plan.v1.json`  
   - If refining an existing plan: increment (e.g., `plan.v2.json`, `plan.v3.json`).

6. **Create the plan file**:  
   Inside `.claude/implementation/{feature_shortname}/`, create `plan.v{N}.json`.

7. **Define plan structure**:  
   Each plan file contains both plan metadata and a list of step objects:
   ```json
   {
     "feature": "auth_tests",
     "version": "v1",
     "description": "Implement authentication tests",
     "created_at": "2025-01-25T10:30:00Z",
     "updated_at": "2025-01-25T10:30:00Z",
     "status": "pending",
     "plan": [
       {
         "step": 1,
         "prompt": "Detailed instruction for this step...",
         "status": "pending",
         "git_hash": null,
         "summary": null,
         "timestamp": null
       }
     ]
   }
   ```

8. **Preserve history**:  
   All previous plan versions are retained for reference.  
   The `features.json` entry will always indicate the current active version.

**Feature naming convention:**  
Use lowercase words separated by underscores (2–4 words max). Example:  
`auth_tests`, `docker_setup`, `contacts_api`, `recordings_upload`.

---

## 2. Plan Execution and Updates

> This section outlines how the development plan is executed and how progress is tracked throughout the implementation process.

Once the user gives the green light to start implementation, I will execute all steps in the feature’s active plan sequentially and autonomously.  
I will not ask for permission to proceed between steps.

### Execution Process

1. Identify the active plan from `features.json` (e.g., `"auth_tests"` → `plan.v2.json`).  
2. Set plan and feature status to `"in_progress"`.  
3. Execute each step in order, updating both the plan file and registry as progress occurs.

After each completed step, I will silently:

1. Update the step’s `status` to `"completed"`.  
2. Set `summary` and `timestamp`.  
3. Record the `git_hash` of any commit made.  
4. Update `updated_at` timestamps for the plan and feature.  
5. Write the updated data back to disk.

When all steps complete successfully:

1. Update plan and feature `status` to `"completed"`.  
2. Record final timestamps.  
3. Communicate a summary of the completed plan to the user.

If a step fails, execution will pause immediately, the status will be updated to `"failed"`, and I will request user guidance before continuing.

---

## 3. Managing Multiple Plans

> This section explains how to organize and track multiple active feature plans.

Each feature in `features.json` maintains its own independent plan file and version history.  
Multiple plans can exist simultaneously, each in different states (`pending`, `in_progress`, `completed`, `failed`).

### Viewing all features

```bash
cat .claude/implementation/features.json
```

### Viewing a specific feature’s plans

```bash
ls -la .claude/implementation/{feature_name}/
```

### Typical structure

```
.claude/implementation/
├── features.json
├── auth_tests/
│   ├── plan.v1.json
│   ├── plan.v2.json
│   └── plan.v3.json
└── contacts_api/
    ├── plan.v1.json
    └── plan.v2.json
```

---

## 4. Execution Constraints and Error Handling

> This section defines the boundaries and error handling procedures during plan execution.

If any step fails, I will stop execution, update the status to "failed", log the error summary, and immediately seek guidance from the user before proceeding.

---

## 5. Self-Optimization Routine (Required Default Behavior)

> This section describes the mandatory self-improvement process that occurs after every code generation or tool use action.

After every code generation or tool use action you perform, you MUST follow this self-optimization routine:

### Analyze
Briefly analyze the user's last action (e.g., did they correct your code, provide a clarification, rerun a command with a new flag?). Also, analyze the changes you just made to the filesystem.

### Compare
Compare this analysis against the current state of all .md context files (claude.md, prd.md, sbom.md, etc.).

### Recommend
If you identify a pattern of correction or a potential for future streamlining, recommend a specific, minimal edit to one of the .md files. For each recommendation, you MUST include:
- **Proposed Change:** The exact text to be added, removed, or changed.
- **Reasoning (Why):** A concise explanation of how this change will improve future interactions (e.g., "This adds the --fix flag to the lint command, which the user has added manually three times, saving a future step.").
- **Risk / New Burden:** Any potential risks or new responsibilities this change introduces for the user.

Please note, it is perfectly ok if you do NOT identify a pattern for improvement and no changes need to be made. We want to improve slowly and iteratively.

### Propose Diff
If the user accepts the recommendation, propose the exact diff or patch to apply the change to the relevant .md file.

---

## 6. Code Commit Workflow and Changelog Execution

When a step in the plan results in a code change, I will create a git commit.

* **Commit Message Style:** Commit messages should follow the Conventional Commits format:  
  https://www.conventionalcommits.org/en/v1.0.0/  
  Example: `feat: add user login button`
* **Changelog:** After a set of features is complete, I will update the `changelog.md` file.
