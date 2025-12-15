---
description: Wrap up the current session - commit changes, update docs, and prepare for next session
---

## Session Wrap-Up Checklist

Please perform the following wrap-up tasks to close this session cleanly:

### 1. Git & Code Status
- Run `git status` to check for any uncommitted changes
- If there are changes, stage and commit them using Conventional Commits format
- Push all commits to the remote repository

### 2. Documentation Updates
Check and update the following files as needed:
- `.claude/changelog.md` - Add entries for any completed features or bug fixes from this session
- `.claude/implementation/features.json` - Update status of any features worked on
- Any active `plan.v*.json` files - Update step statuses and summaries

### 3. Build Verification
- Run your project's build command to ensure everything compiles (e.g., `npm run build`, `cargo build`, `go build`, etc.)
- Note any warnings or errors that should be addressed in the next session

> **Note:** Customize the build command for your specific project stack.

### 4. Session Summary
Provide a brief summary including:
- **Completed:** What was accomplished in this session
- **In Progress:** Any work that is partially complete and its current state
- **Blockers:** Any issues or blockers encountered
- **Next Steps:** Clear list of what to work on next

### 5. Handoff Message
End with a clear handoff message that can be used to resume work, such as:
"Ready to resume. Next session: [specific task or feature to continue]"

### 6. Improve Session Startup (Optional)
Evaluate if anything learned during this session should be added to `.claude/commands/gogogo.md` to help future sessions:
- New context files that should be loaded at startup
- Additional checks that would have been helpful
- Project-specific setup steps discovered during work
- Environment variables or dependencies that caused issues

If improvements are identified, offer to update the gogogo.md file.
