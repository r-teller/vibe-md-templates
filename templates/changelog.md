# Changelog

Purpose: This file is a running log that tracks all notable changes, new features, and workflow updates for the project over time.  
It now also serves as a record of **feature-based plan completions** from `.claude/implementation/` and corresponding `features.json` updates.

> The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),  
> and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## Version Numbering Rules

We follow **Semantic Versioning (SemVer)** for all projects:

- **MAJOR (X.0.0):** Incompatible or breaking workflow or API changes.
- **MINOR (0.X.0):** New features, plan types, or template enhancements added in a backwards-compatible way.
- **PATCH (0.0.X):** Bug fixes, template corrections, or workflow refinements that don’t break existing functionality.

> For student or prototype projects:
>
> - Use **0.x.x** versions while iterating (pre-1.0).
> - Bump to **1.0.0** only when the workflow and feature registry (`features.json`) are stable and production-ready.

---

## Plan Logging Rules

Each autonomous feature plan completion must append an entry in this changelog with the following format:

---

### Feature Plan Entry Example

**Feature:** `auth_flow`  
**Plan Version:** `plan.v2.json`  
**Status:** `completed`  
**Summary:** Implemented secure login and registration flow with Firebase Auth.  
**Commit Reference:** `feat(auth_flow): complete plan.v2.json`  
**Date:** 2025-10-24

---

This ensures transparency and traceability for all AI-executed workflows.

---

## [Unreleased]

### Changed

- Integrated `.claude/implementation/` directory into project workflow for autonomous feature planning.
- Updated `workflow.md` to manage versioned plans (`plan.v1.json`, `plan.v2.json`, etc.) and feature registry (`features.json`).
- Clarified changelog role in tracking **plan completions** and **feature lifecycle**.

### Added

- Introduced `features.json` for centralized tracking of feature metadata and statuses.
- Added example feature plan directories under `.claude/implementation/`.
- Enhanced self-optimization logic and documentation integration in `workflow.md`.

### Deprecated

- Removed references to linear/manual development workflow — now handled by autonomous planning.

---

## [0.1.1] - 2025-09-15

### Added

- Introduced initial autonomous workflow logic:
  - `.claude/implementation/` directory structure
  - Versioned plan files (`plan.v1.json`, etc.)
  - Feature status management (`pending`, `in_progress`, `completed`)
- Updated `workflow.md` and `claude.md` to define plan creation and execution behavior.

### Changed

- Revised `tests.md` to support automatic test execution after each feature step.
- Added changelog integration rules for workflow plan completions.

---

## [0.1.0] - 2025-08-31

### Added

- Created initial set of Markdown context files (`claude.md`, `prd.md`, `infra.md`, `workflow.md`, `security.md`, `sbom.md`, `tests.md`).
- Added `changelog.md` to track project history.
- Added `first_prompt.md` as interactive setup guide for template population.
- Defined examples for both local Python applications and Next.js + Supabase applications to guide new students.

### Notes

- This is the first structured version of the project templates.
- Future releases will focus on workflow automation, changelog integration, and feature-based plan versioning.
